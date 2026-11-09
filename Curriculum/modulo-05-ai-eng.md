# Módulo 5: Agentes Autónomos

**Cuatro sub-módulos, catorce lecciones, un proyecto final.** Este módulo cierra técnicamente el bootcamp. Aquí pasas de construir sistemas (RAG del M4, automatizaciones del M3) a orquestar agentes autónomos que razonan, deciden y actúan. Cuatro sub-módulos secuenciales, cada uno con sus lecciones y ejercicios, culminando en un proyecto final individual que integra todo. El pseudocódigo de esta guía es didáctico: te muestra la arquitectura y los patrones; el código real lo escribes tú.

## Índice de sub-módulos

| Sub-módulo | Contenido |
|---|---|
| **SM0 · Setup del stack** | Python 3.11, versiones fijadas, cuentas y claves, Claude Desktop, verificación de entorno. |
| **SM1 · LangChain, LCEL y LangGraph** | Del LangChain que viste en M4 al dominio real. LCEL, streaming, grafos de estado con LangGraph. |
| **SM2 · Agentes con memoria y tool use** | Tool use con Pydantic, checkpoints persistentes, memoria semántica, human-in-the-loop. |
| **SM3 · Multi-agente: CrewAI y AutoGen** | Dos frameworks nuevos, patrones (supervisor, workers), criterios de elección profesional. |
| **SM4 · MCP + proyecto final** | Model Context Protocol, servidores propios, Claude Desktop, proyecto integrador y defensa. |
| **Especificación completa** | Requisitos, criterios de calidad, formato de defensa, plantilla del README. |

---

## Preparar el entorno para 40 horas de agentes

Este módulo es el más exigente del bootcamp en dependencias, versiones y coste de API. Antes de la primera sesión, deja el entorno listo. Un problema de setup en la sesión 1 te hace perder dos horas irrecuperables y arranca el módulo con mal pie.

> **Este es el módulo más caro del bootcamp.** Los agentes hacen muchas llamadas LLM: un agente ReAct típico gasta entre 5 y 15 llamadas por consulta. Estimación para completar todos los ejercicios + proyecto: **8–15 USD**. Es más que el M4 (menos de 5 USD) pero razonable frente al valor formativo.
>
> **Regla operativa:** configura límites estrictos en Anthropic y OpenAI desde el día 1. Es lo profesional real: en empresa se trabaja con presupuestos. Aprender a diseñar agentes rentables es parte del módulo.

- Crea un entorno virtual limpio para este módulo. No reutilices el del M4: hay conflictos de versión con LangChain 0.3+.
- Crea un archivo `.env` en la raíz de tu proyecto del módulo. Nunca lo subas a GitHub (añádelo al `.gitignore`).
- Ejecuta este pseudo-check para confirmar que todo el stack se importa sin errores. Si algo falla, resuélvelo **antes** de la primera sesión, no en clase.

### Estructura de carpetas recomendada

Crea una carpeta raíz `bootcamp-m5-agentes/` con subcarpetas por sub-módulo. Cada ejercicio en su propio notebook o script. El proyecto final en carpeta separada con estructura de proyecto real (`README`, `requirements`, `src`, `tests`). Empieza con la disciplina desde el día 1: es lo que llevarás a GitHub y a entrevistas.

---

## SM1 · Del LangChain que viste en M4 al dominio real

En el M4 usaste LangChain para RAG copiando patrones. Ahora entiendes su arquitectura, dominas LCEL como lenguaje de composición y construyes tus primeros grafos con LangGraph desde cero. Este sub-módulo es la base técnica sobre la que se apoyan los tres siguientes.

### La arquitectura real de LangChain: paquetes, Runnables y el pipe

En el M4 lo usaste como *caja de herramientas para RAG*. Ahora vas a entender por qué está diseñado como está: LangChain es una **abstracción compositiva** sobre LLMs. Todo en LangChain implementa una interfaz común llamada `Runnable`, y esa interfaz es lo que hace que puedas encadenar componentes con el operador pipe.

Desde 2024, LangChain no es un único paquete monolítico sino una familia. Consecuencia práctica: cuando importas, importa desde el paquete específico, no del monolito. Snippets antiguos con `from langchain import ...` suelen estar rotos en versiones actuales.

Cualquier componente de LangChain implementa `Runnable`. Un `Runnable` tiene siempre estos métodos. Modelo, prompt, parser, retriever, tool: todo es Runnable. Y como todos comparten interfaz, se pueden componer. Este código funciona pero es verboso. LCEL viene a resolver eso. LangChain sobrecarga el operador `|` de Python para que puedas encadenar Runnables. El pipe no es magia: es azúcar sintáctico para `RunnableSequence`.

#### Cuatro superpoderes en una línea

Al componer con el pipe obtienes automáticamente:

- **Streaming**: tokens llegando en tiempo real.
- **Batching paralelo**: procesar varios inputs a la vez.
- **Ejecución asíncrona**: variantes con prefijo `a`.
- **Trazabilidad con LangSmith**: cada paso de la cadena se ve en el dashboard si tienes LangSmith activo.

Todo esto sin cambiar una línea de tu cadena.

> **Juicio profesional:** si tu código termina siendo más simple sin LangChain, quítalo. La abstracción tiene coste; solo vale la pena cuando el beneficio compensa.

*Lecturas obligatorias de esta lección.*

### LCEL como lenguaje de composición: paralelización, streaming, gestión de errores

LCEL (LangChain Expression Language) no es un lenguaje nuevo. Es **Python con sobrecarga del operador pipe** más un puñado de utilidades: `RunnableLambda`, `RunnablePassthrough`, `RunnableParallel`, `RunnableBranch`. Con estas piezas construyes pipelines complejos sin salirte de la abstracción Runnable.

- **`RunnableLambda`**: si tienes una función Python normal y quieres meterla en una cadena LCEL, envuélvela con `RunnableLambda`. Ahora es un Runnable que hereda `.invoke()`, `.stream()`, etc.
- **`RunnablePassthrough`**: útil cuando necesitas *preservar el input original* mientras el flujo también hace algo con él. Aparece muchísimo en pipelines RAG.
- **`RunnableParallel`**: cuando necesitas hacer dos cosas en paralelo con el mismo input. Cada rama corre concurrentemente; el resultado es un diccionario con las salidas. Efecto práctico: si cada cadena tarda 3 segundos, secuencialmente son 6 s; en paralelo son 3 s. Sin cambiar código de las cadenas individuales.
- **Streaming**: es parte gratuita de la abstracción. Sustituye `.invoke()` por `.stream()` y obtienes un generador.
- **`RunnableBranch`** y gestión de errores: dos utilidades que hacen tus pipelines más robustos con una sola línea.

#### El límite claro

LCEL es perfecto para composición lineal: input → paso 1 → paso 2 → ... → output. Cuando necesitas **estado que evoluciona entre pasos**, **ciclos** (repetir hasta que se cumpla una condición), **ramas condicionales complejas** o **varios agentes conversando**, LCEL se vuelve incómodo. Ese es el momento de pasar a LangGraph.

> **Regla del pulgar:** si tu cadena LCEL empieza a tener más de un `RunnableBranch` anidado o necesitas guardar estado que consultas después, pasa a LangGraph.

*Lecturas obligatorias de esta lección.*

### LangGraph: grafos de estado para lógica que LCEL no cubre

Hasta ahora pensabas en **funciones encadenadas**: input entra por un lado, sale por otro, en el medio hay pasos secuenciales. LangGraph introduce un modelo mental distinto: **un estado compartido que evoluciona a medida que pasa por nodos**.

Piensa en un diagrama de flujo. Cada caja es un **nodo**. Las flechas entre cajas son **aristas**. Hay un **estado** (un diccionario) que va viajando de nodo en nodo, siendo actualizado por cada uno. Puede haber aristas condicionales (si X, ve al nodo A; si Y, ve al B), ciclos (vuelve al nodo anterior hasta que se cumpla algo), y varios caminos posibles.

#### Los nodos devuelven parcial, LangGraph fusiona

Cuando un nodo devuelve `{"respuesta": "..."}`, no está sustituyendo el estado entero. LangGraph **fusiona** el diccionario devuelto con el estado existente. La `pregunta` original sigue ahí. Este comportamiento es distinto al típico Python donde asignar un dict lo reemplaza. Si necesitas control fino (por ejemplo, un campo que es una lista a la que quieres *añadir* en lugar de reemplazar), usa `Annotated[list, operator.add]` en el TypedDict.

- Cuando el siguiente nodo depende del estado actual, usa **aristas condicionales**.
- Un **ciclo** en LangGraph es simplemente una arista que vuelve a un nodo anterior. Se usa constantemente en agentes: el nodo «piensa» decide si necesita más información, y si sí, vuelve al nodo «actuar»; si no, va al final.

> **Consejo:** antes de ejecutar, dibuja tu grafo. Ver los nodos y flechas ayuda muchísimo a detectar bugs de lógica.

*Lecturas obligatorias de esta lección.*

### Práctica del SM1 · Tres ejercicios progresivos

1. Construye una cadena LCEL que, dado un texto en cualquier idioma, produzca en paralelo tres cosas: un resumen en español (3 líneas), una traducción al inglés y una clasificación de sentimiento (positivo/neutro/negativo). Todo en una sola llamada compuesta.
2. Toma la cadena del ejercicio anterior. Añade robustez de producción.
3. Construye un grafo LangGraph que simule un asistente de redacción iterativo.

---

## SM2 · Del agente sin estado al agente persistente

Aquí construyes tu primer agente autónomo serio: uno que usa tools tipadas con Pydantic, mantiene memoria persistente entre invocaciones, permite intervención humana en pasos sensibles y emite eventos en streaming. Es el sub-módulo donde el mercado laboral separa junior de mid-level.

### Tools tipadas: Pydantic como contrato entre LLM y código

Un LLM por sí solo genera texto. Con tool use, puede **invocar funciones que tú defines**: buscar en una base vectorial, consultar el tiempo, calcular algo, escribir en una base de datos. El LLM decide cuándo llamar, con qué argumentos, y procesa el resultado.

Técnicamente, el LLM no ejecuta código: devuelve un JSON que describe qué función quiere llamar y con qué argumentos. Tu código Python lee ese JSON, ejecuta la función real, y le devuelve el resultado. El LLM decide qué hacer con ese resultado (llamar otra tool, responder al usuario, seguir razonando).

Tres cosas críticas para que el LLM sepa usar bien tu tool:

- Los type hints simples cubren casos básicos. Para validaciones más ricas (rangos, formatos, campos obligatorios opcionales), usa Pydantic. LangChain lo soporta nativamente.
- Si el LLM intenta invocar la tool con `personas=15`, Pydantic rechaza antes de ejecutar. LangChain devuelve el error al LLM, que puede reintentar corrigiendo o pedir aclaración al usuario.
- Caso relacionado: quieres que la **respuesta** del LLM tenga estructura, no ejecutar una función. Usa `with_structured_output()`.

#### `create_react_agent`

LangGraph incluye `create_react_agent` de `langgraph.prebuilt`, que hace todo lo anterior en una sola línea. Es útil para prototipar. Pero para el módulo, aprende a construirlo desde `StateGraph` a mano: entiendes qué hay debajo y podrás modificar comportamiento cuando el prebuilt no te sirva.

*Lecturas obligatorias de esta lección.*

### Los tres niveles de memoria: short-term, long-term, semántica

Un agente sin memoria es una función que responde a inputs aislados. Con memoria, es un **colaborador** que recuerda conversaciones anteriores, aprende preferencias, mantiene contexto entre sesiones. La diferencia práctica entre un chatbot demo y un asistente útil. Distingue tres tipos, cada uno con su tecnología.

- **Short-term / checkpoints**: LangGraph tiene un sistema de checkpoints que guarda el estado del grafo tras cada nodo. Al reanudar con el mismo `thread_id`, continúa desde donde se quedó.
  > **El error clásico con thread_id:** al probar, muchos alumnos usan el mismo `thread_id` hardcodeado para todos sus tests. Luego se sorprenden cuando el agente «recuerda cosas raras» de tests anteriores. Genera un `thread_id` nuevo por conversación real (por ejemplo, con `str(uuid.uuid4())`). Solo reutiliza cuando quieres explícitamente continuar una conversación previa.
  > Puedes inspeccionar cualquier checkpoint guardado, incluso hacer «time travel»: retroceder a un estado anterior y ejecutar desde ahí con cambios.
- **Semántica**: los checkpoints guardan el estado completo del grafo, incluida la lista de mensajes. Pero si tras 100 conversaciones el usuario menciona «como te dije, soy alérgico al gluten», el checkpoint no destila esa información como **hecho**: sigue enterrado en mensajes. Ahí entra la **memoria semántica**: extraer, almacenar y recuperar hechos estructurados. Mem0 es la librería más simple para empezar.

*Lecturas obligatorias de esta lección.*

### Cuando el agente pide permiso y cuando emite eventos en tiempo real

Un agente que puede enviar emails, borrar archivos o gastar dinero no debería hacerlo sin aprobación humana. LangGraph implementa esto con **interrupts**: nodos que pausan la ejecución esperando a que un humano diga adelante o cancele.

**Patrones profesionales de HITL.** También sirve para:

- *Curar outputs*: el agente propone, humano ajusta antes de publicar.
- *Desambiguar*: el agente detecta que le faltan datos y pregunta.
- *Revisar decisiones críticas*: aprobar una compra, un cambio de configuración, un mensaje a un cliente.

En producción, casi todo agente serio tiene HITL en algunos puntos. LangGraph emite eventos a tres granularidades. Elige según lo que quieras mostrar en la UI. En producción, los agentes se sirven vía API o WebSocket y necesitas streaming async para no bloquear.

*Lecturas obligatorias de esta lección.*

### Práctica del SM2 · Tu primer agente serio

---

## SM3 · Cuando un solo agente no basta

Sistemas donde varios agentes especializados colaboran para resolver una tarea compleja. Aprendes CrewAI (roles definidos), AutoGen v0.4 (conversaciones dinámicas), patrones arquitectónicos agnósticos del framework, y adquieres criterio para elegir el enfoque correcto según cada caso.

### CrewAI: equipos de agentes con roles definidos

CrewAI modela un sistema multi-agente como si fuera un **equipo de personas**. Cada agente tiene un rol (por ejemplo, «Investigador senior»), un objetivo («Encontrar información contrastada sobre X») y un trasfondo (backstory) que le da personalidad y contexto. El sistema se llama **Crew** (tripulación). Cuatro conceptos base. Dos procesos disponibles.

#### El arte de escribir bien los agents

Con roles vagos («ayudante») y goals genéricos («ayudar al usuario»), los agentes CrewAI hacen cualquier cosa. Con prescripciones excesivas, no aportan sobre un LLM simple. El punto medio: role concreto («Analista de datos financieros senior»), goal específico («Detectar anomalías en series temporales de ventas y explicar causas probables»), backstory con contexto que informe el estilo («Has trabajado 10 años en consultoría, priorizas rigor sobre velocidad»). Prueba dos versiones del mismo agent y compara resultados.

*Lecturas obligatorias de esta lección.*

### AutoGen: conversaciones entre agentes con arquitectura async

AutoGen es un framework de Microsoft. En enero de 2025 lanzaron la v0.4 que **reescribió por completo el sistema**: nueva arquitectura basada en actor model, todo async, mejor observabilidad. Los tutoriales anteriores a esa fecha son obsoletos: usan `pyautogen` (deprecated) en lugar de `autogen-agentchat` (actual). En este módulo trabajas exclusivamente con la v0.4+. Si buscas material en internet, filtra por fecha 2025+ y verifica que use el nuevo paquete.

**Fortalezas comparadas.** AutoGen brilla cuando:

1. La conversación entre agents es **dinámica** y no encaja en un flujo secuencial.
2. Necesitas **selección inteligente** de quién habla siguiente en cada turno.
3. Construyes sistemas donde varios agents pueden colaborar de formas no predeterminadas.

CrewAI brilla cuando el flujo es más lineal y los roles claramente separados.

*Lecturas obligatorias de esta lección.*

### Patrones agnósticos del framework: supervisor, workers, evaluator

Anthropic publicó en diciembre de 2024 un artículo que se ha convertido en **referencia obligada**: «Building Effective Agents». Define workflows vs agents e identifica los patrones principales. Léelo antes de esta lección.

> **Regla operativa:** empieza siempre por el patrón más simple que funcione. Un prompt chaining resuelve el 60% de los casos. Solo pasa a orchestrator-workers cuando la tarea genuinamente requiere decisión en runtime sobre qué sub-tareas ejecutar. Complejidad no es sofisticación.

*Lecturas obligatorias de esta lección.*

### LangGraph vs CrewAI vs AutoGen: cuándo cada uno

En sistemas reales de 2026 es habitual combinar. Un patrón típico: **LangGraph como orquestador principal** (por su control y checkpoints) + **una tool que internamente ejecuta un Crew de CrewAI** para sub-tareas donde la simplicidad de CrewAI compensa. O **agents de AutoGen dentro de un nodo de LangGraph** cuando esa sub-tarea es una discusión dinámica.

Ante un problema nuevo, pregúntate en este orden:

1. ¿Se puede resolver con un solo agente bien construido?
2. ¿Necesita múltiples pasos secuenciales (Prompt Chaining)?
3. ¿Necesita decisión dinámica en runtime (Orchestrator-Workers)?
4. ¿Necesita conversación dinámica entre iguales (AutoGen)?

> **El framework es medio, no fin.** En una entrevista técnica, cuando expliques por qué elegiste un framework, la respuesta correcta nunca es «porque me gusta más» o «porque es lo que viene ahora». La respuesta correcta es «porque para este caso, este framework aporta X, Y, Z frente a las alternativas». Ese razonamiento es lo que se evalúa profesionalmente y lo que se te evaluará en el tribunal del proyecto final.

### Práctica del SM3 · Multi-agente en tres formas

---

## SM4 · MCP + Proyecto Final

Model Context Protocol y el **proyecto integrador**. MCP es el estándar emergente para conectar cualquier LLM con cualquier tool o dato: el equivalente al USB-C de las integraciones IA. Aprendes a construir tus propios servidores MCP, integrarlos con Claude Desktop y Cursor, y culminar el módulo con un proyecto final que integra todo el bootcamp.

### Qué es MCP y por qué importa tanto

Antes de MCP, cada aplicación IA (Claude Desktop, Cursor, tu chatbot custom, etc.) tenía que implementar su propia forma de integrarse con cada fuente de datos y cada tool: Gmail, Notion, tu base de datos, tu API interna. Con M aplicaciones y N fuentes, tienes M×N integraciones custom. Explosión combinatoria.

MCP resuelve esto con un **protocolo estándar**: cualquier aplicación (cliente MCP) puede conectarse a cualquier fuente que exponga un servidor MCP. Tu servidor lo escribes una vez y funciona con Claude Desktop, Cursor, Windsurf, Zed y cualquier cliente futuro. Pasas de M×N integraciones a M+N.

MCP fue anunciado por Anthropic en **noviembre de 2024** como protocolo abierto. En un año, el ecosistema explotó: OpenAI lo adoptó en 2025, Google lo integró en herramientas de desarrollo, los IDEs de código (Cursor, Windsurf, Zed) lo soportan nativamente, y la comunidad ha publicado cientos de servidores. En 2026 es prácticamente el estándar de facto para integraciones LLM con sistemas externos.

Un AI Engineer que sabe construir servidores MCP es directamente empleable en cualquier empresa que use estas herramientas.

Un servidor MCP expone tres tipos de recursos:

1. **Tools**: Funciones que el cliente puede invocar (ej. buscar, escribir, calcular).
2. **Resources**: Datos legibles por URI (ej. archivos, bases de datos).
3. **Prompts**: Plantillas predefinidas para interacciones comunes.

> Antes de escribir servidores, familiarízate con **MCP Inspector**: una herramienta que se conecta a cualquier servidor MCP y te muestra qué expone, permitiéndote invocar tools, leer resources y probar prompts. Es al MCP lo que Postman es al HTTP.

#### Los servidores oficiales que deberías conocer

Anthropic mantiene una colección de servidores MCP de referencia (`github.com/modelcontextprotocol/servers`). Los más relevantes:

- `filesystem` (leer/escribir archivos)
- `git` (operaciones en repositorios)
- `postgres` (consultar bases de datos)
- `fetch` (descargar URLs)
- `memory` (memoria persistente)

La comunidad ha añadido cientos más: Slack, GitHub, Notion, Jira, Linear, y un largo etcétera.

*Lecturas obligatorias de esta lección.*

### Tu propio servidor MCP en Python

El SDK oficial de Python (`mcp`) proporciona todo lo necesario para construir servidores.

**Instalación:**

```bash
pip install mcp
```

Con ese archivo tienes un servidor MCP funcional. Lo pruebas con:

```bash
mcp dev tu_servidor.py
```

Nunca uses print() en un servidor stdio. Con transporte stdio, el protocolo usa stdout para JSON-RPC. Cualquier print() en tu código rompe la comunicación. Usa el logging del framework o escribe a stderr explícitamente. Es el error más común al depurar servidores MCP; lo verás si no eres estricto con esto.

*Lecturas obligatorias de esta lección.*

### Conectar tu servidor a clientes reales

Claude Desktop lee su configuración de MCP desde `claude_desktop_config.json`.

Ubicación:

- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`
- Linux: `~/.config/Claude/claude_desktop_config.json`

Sin excusas: Claude Desktop necesita paths absolutos. No funciona con paths relativos, no expande `~/`, no reconoce variables de entorno. En Windows, usa forward slash (`/`) o backslash escapado (`\\`) en el JSON. Un path incorrecto es la causa número uno de «el servidor no aparece en Claude».

Tras editar la config, reinicia Claude Desktop. Verás los servidores conectados en la parte inferior de la interfaz. Prueba pidiéndole a Claude algo que use tus tools: «usa mi-servidor-demo para saludar a Ana».

Cursor tiene su propia configuración MCP. Ajustes → Features → MCP → Add new MCP server. Formato similar al de Claude Desktop pero desde la UI de Cursor.

Puedes escribir clientes MCP con el SDK. Útil cuando integras MCP en tu propia aplicación (por ejemplo, tu proyecto final).

En tu proyecto final vas a combinar un agente LangGraph con tu servidor MCP. El patrón:

- El agente LangGraph orquesta la lógica.
- El servidor MCP expone las tools específicas del dominio.
- El cliente (Claude/Cursor) interactúa con el agente vía MCP.

*Lecturas obligatorias de esta lección.*

### El Proyecto Integrador: Todo el módulo en un sistema

Un sistema agéntico completo que integra lo mejor de todo lo aprendido en el módulo: LangGraph como orquestador, agente con memoria persistente, tools bien tipadas, servidor MCP propio, integración con un cliente MCP real, y opcionalmente sistema multi-agente si aporta al caso.

- Es individual.
- Es lo que llevas al portfolio.
- Es lo que defiendes ante el tribunal.
- Y es lo que un reclutador verá cuando le compartas tu GitHub.

### Los cinco tropiezos frecuentes

- **Ambición mal calibrada:** querer integrar todo (memoria semántica + multi-agente + OAuth + streaming + UI) y no llegar a nada terminado. Mejor un sistema pequeño y terminado que uno grande y a medias.
- **Dominio genérico:** «asistente que responde preguntas» no vende. Elige un caso concreto y particular.
- **Servidor MCP con tools trivial:** tools tipo «calcular 2+2» no cuentan. Al menos una tool debe hacer algo útil (consulta a BD, API real, procesamiento no trivial).
- **Sin defensa técnica preparada:** llegar al tribunal sin haber ensayado las respuestas a «¿por qué X y no Y?».
- **README pobre:** sin arquitectura visible, sin setup claro, sin decisiones documentadas. Muchos reclutadores solo miran el README.

Todo lo que necesitas para completar y defender tu proyecto. Esta sección detalla los criterios de calidad, formato de entrega, rúbrica de evaluación y plantilla del README. Léela entera antes de decidir tu dominio. Los mejores proyectos empiezan por leer bien la especificación.

### Elegir bien el dominio · el 40% del éxito

Algunas ideas de dominio recomendadas:

#### Agente de análisis técnico + ejecución simulada de trades

- Agente que analiza indicadores técnicos (RSI, medias móviles, MACD) de acciones o cripto, genera hipótesis de trading, y prepara órdenes que un humano aprueba antes de ejecutar (HITL).
- Servidor MCP propio que expone tools para consultar precios en tiempo real (vía API de un broker sandbox) y gestionar el portafolio simulado.
- Memoria persistente del track record del agente.

#### Asistente de triaje sintomático (no diagnóstico)

- Agente que hace triaje inicial de síntomas para orientar (nunca diagnosticar) sobre urgencia relativa y especialidad probable.
- Servidor MCP que consulta guías clínicas de fuentes acreditadas.
- Memoria de la conversación con derivación a profesional real en cuanto detecta señales de alarma.
- HITL para toda recomendación con impacto. Documenta claramente los límites éticos y disclaimers.

#### Agente de code review con MCP sobre GitHub

- Agente que revisa pull requests de un repo.
- Servidor MCP propio con tools para leer diffs, comentar en líneas específicas, aprobar/pedir cambios.
- Memoria del histórico de reviews en el repo (evita repetir sugerencias ya rechazadas).
- HITL antes de publicar comentarios oficiales.
- Multi-agente opcional: reviewer + security auditor + style checker.

#### Asistente de revisión de contratos

- Agente que ayuda a revisar contratos comerciales (NDAs, contratos de servicios) identificando cláusulas problemáticas según un playbook definido.
- Servidor MCP con tools para acceder al playbook (documento de reglas de la firma) y a un histórico de contratos aprobados.
- HITL en cada recomendación de cambio.
- Memoria del contrato en revisión y de patrones detectados.

#### Agente educativo con seguimiento de progreso

- Tutor de una materia técnica (Python, matemáticas, cualquier área en la que domines) que se adapta al nivel del alumno.
- Servidor MCP con tools para gestionar el temario y los ejercicios.
- Memoria persistente del progreso, errores frecuentes y conceptos dominados.
- HITL cuando el alumno pide validación de una solución compleja.

### Siete dimensiones que determinarán tu nota

El tribunal evalúa el proyecto en siete dimensiones. Cada una con tres niveles: mínimo (apruebas), notable (buen trabajo), excelente (destaca sobre el resto).

El proyecto final se aprueba con nivel mínimo o superior en todas las dimensiones; una dimensión bajo mínimo suspende.

#### Repositorio GitHub · Estructura obligatoria

El vídeo demo es lo primero que un reclutador ve.

Graba en pantalla con voz. No hace falta editar como profesional; sí hace falta que se entienda y se vea nítido. Herramientas gratis: Loom, OBS Studio, QuickTime en Mac.

#### La Plantilla Obligatoria del README

El README debe seguir esta estructura. Puedes añadir secciones, no puedes omitir las marcadas. Es la plantilla que también usarás cuando publiques proyectos profesionales.

- **Título y Descripción:** Qué hace el proyecto y por qué es útil.
- **Diagrama de Arquitectura:** Visual claro de los componentes (LangGraph, MCP, Memoria, etc.).
- **Setup:** Instrucciones paso a paso para instalar y configurar el entorno.
- **Uso:** Ejemplos de cómo interactuar con el agente.
- **Decisiones Técnicas:** Por qué elegiste ciertos frameworks, patrones o herramientas.
- **Limitaciones:** Qué no hace el proyecto y por qué.
- **Demo:** Enlace al vídeo.

**Antes de dar por terminado:** prepara la defensa como si fuera una entrevista técnica real.

### La Defensa del Proyecto

La defensa del proyecto final es la simulación más fiel a una entrevista técnica real que vas a hacer en el bootcamp. Los reclutadores de empresas que contratan AI Engineers usan exactamente este formato: presentación breve, demo, preguntas duras.

#### Cómo transcurre una defensa típica

La defensa dura entre 20 y 25 minutos, dividida en:

- **Presentación (5-7 min):** Contexto, arquitectura, decisiones clave.
- **Demo (5-7 min):** Mostrar el sistema funcionando en tiempo real.
- **Preguntas del Tribunal (10-15 min):** Preguntas técnicas y de diseño.

#### Adelántate a las preguntas

Cuando tomes decisiones controvertidas (elegir un framework sobre otro, usar SQLite en lugar de Postgres, no implementar OAuth), menciona por qué en tu presentación. Adelantar la justificación desactiva la pregunta y demuestra que fue decisión consciente, no descuido. Es lo que hace un profesional junior/mid vs uno senior.

#### Doce preguntas que casi seguro te harán

Prepara respuestas a cada una de estas antes de la defensa. Escríbelas. Ensáyalas en voz alta. Cronometra cada respuesta (idealmente 60-90 segundos por pregunta).

- «¿Por qué elegiste LangGraph sobre otros orquestadores?»
- «¿Cómo manejas la memoria a largo plazo?»
- «¿Qué harías si el LLM alucina en una tool crítica?»
- «¿Cómo garantizas la seguridad de tus tools?»
- «¿Por qué MCP y no una API REST directa?»
- «¿Cómo escalarías este sistema a 1000 usuarios?»
- «¿Qué patrones multi-agente usarías y por qué?»
- «¿Cómo mides el coste de API de tu agente?»
- «¿Qué harías si el servidor MCP falla durante la ejecución?»
- «¿Cómo pruebas tu grafo de LangGraph?»
- «¿Qué limitaciones éticas tiene tu proyecto?»
- «¿Y si te digo que tu enfoque no es el correcto?»

A veces el tribunal reta directamente una decisión para ver cómo defiendes. La respuesta no es cambiar de opinión ante la primera duda: la respuesta es explicar el razonamiento detrás y estar dispuesto a matizar si el reto es válido. Un profesional sabe distinguir entre «me han hecho ver un ángulo que no consideré» y «me lo dice alguien con autoridad así que cambio». Ambas actitudes son señales opuestas.

#### Cuatro dimensiones que el tribunal puntúa

- **Dominio Técnico:** Muestras que entiendes lo que hiciste y por qué. Puedes responder preguntas sobre el código, el grafo, las tools, el servidor MCP sin dudar en lo básico.
- **Claridad y Comunicación:** Explicas conceptos técnicos con claridad. El diagrama de arquitectura es entendible. La demo se ve, se oye y se sigue. Vas al grano sin perderte en detalles irrelevantes. Respetas el tiempo.
- **Justificación de Decisiones:** Justificas elecciones con razones concretas, no con «porque me gusta más» o «porque es lo que se usa ahora». Nombras alternativas descartadas y por qué. Muestras conciencia de trade-offs.
- **Honestidad y Profesionalismo:** Escuchas la pregunta entera antes de responder. Si no sabes algo, lo dices con naturalidad y ofreces cómo lo averiguarías. No te pones defensivo ante crítica constructiva. Distingues entre reto válido (matizas) y reto forzado (defiendes tu razonamiento).

La defensa es la mitad. La nota final del proyecto integra la calidad del trabajo entregado (rúbrica de 7 dimensiones del proyecto) y la calidad de la defensa (rúbrica de 4 dimensiones). Un proyecto excelente con defensa pobre baja hasta notable. Un proyecto solo notable con defensa excelente sube. Ambas cuentan.

#### Ensayar la defensa como se ensaya una presentación

La defensa del proyecto no termina en el tribunal. Con el mismo proyecto y guion pulido, prepara:

- Una versión corta para LinkedIn o portafolio web.
- Una versión para entrevistas técnicas informales.
- Un "elevator pitch" de 30 segundos.

### Conclusión: Has llegado al final del último módulo técnico

Cuarenta horas después, tienes en las manos un stack que el mercado paga bien en 2026:

- LangGraph para orquestación.
- LangChain como capa de composición.
- CrewAI y AutoGen como alternativas cuando el patrón cambia.
- Memoria persistente robusta.
- Tool use tipado con Pydantic.
- Y sobre todo MCP: el protocolo que en un año se ha convertido en el estándar para integrar LLMs con cualquier fuente.

Este módulo es el más denso técnicamente del bootcamp y también el más determinante para tu empleabilidad. Los AI Engineers que hoy construyen agentes de producción usan exactamente estas herramientas. Y los que dominan MCP están directamente empleables: en 2026 muchas empresas están reescribiendo integraciones internas sobre este protocolo y necesitan gente que sepa construir servidores propios.

**Lo que sigue en tu trayectoria:**

- Terminar el proyecto final con calidad y defenderlo con criterio.
- Publicarlo bien: README pulido, vídeo demo, post en LinkedIn.
- Apoyarte en el equipo de carreras profesionales de Neoland para el proceso de búsqueda: entrevistas simuladas, revisión de tu proyecto por reclutadores, contactos del ecosistema.

El módulo termina aquí; el bootcamp continúa hasta que consigas encaje profesional real.

---

*Una nota sobre este material. Todo lo que has leído en esta guía —la estructura pedagógica, el pseudocódigo ilustrativo, los ejercicios progresivos, los ejemplos de dominios para el proyecto final, las rúbricas, los guiones de defensa— es el resultado de años de iteración sobre lo que funciona en formación técnica intensiva. Ese material es propiedad intelectual exclusiva de Neoland School SL. Se te entrega para tu formación individual. Confiamos en que respetes su uso.*

Buena suerte con el proyecto y con la defensa. Estamos deseando verlo.
