Módulo 3 · Automatización con n8n y Make · Bootcamp en AI Engineering · Neoland

# Automatización con n8n & Make

Construirás automatizaciones potentes conectando IA con cientos de herramientas sin escribir apenas código. Dominarás las plataformas low-code que permiten lanzar productos en horas, no semanas.

 40 horas 4 sub-módulos 13 lecciones autoguiadas Ejercicios prácticos en cada lección Software gratuito y open-source 

## Lo que vas a construir

Este módulo dura aproximadamente 40 horas repartidas en cuatro sub-módulos. En el primero descubres n8n y construyes tu primer workflow conectando una API de IA con un webhook. En el segundo aprendes Make (antes Integromat) y orquestas integraciones empresariales con lógica condicional. En el tercero te llevas n8n a tu propia infraestructura con Docker, primero en local y después en un servidor real. En el cuarto cierras el módulo construyendo un sistema multi-agente que combina varios LLMs trabajando juntos en un workflow productivo.

No necesitas saber programar para completar el módulo. Conviene tener instalada una terminal, una cuenta de correo activa y disposición para crear cuentas gratuitas en las plataformas que vamos a usar (n8n cloud, Make, OpenAI, Anthropic, Google AI Studio). Todas las herramientas que vamos a usar tienen versión gratuita o plan trial con crédito suficiente para completar el módulo entero sin gastar un euro.

00 · PREVIO

#### Cómo usar esta guía

Estructura de cada lección, herramientas que necesitas, cuentas gratuitas a crear antes de empezar.

#### n8n · workflows, webhooks y nodos

De qué va el low-code, primer workflow en n8n cloud, anatomía de nodos y webhooks reales.

SUB-MÓDULO 2 · 10 h

#### Make e integraciones empresariales

Make como alternativa a n8n, lógica condicional con routers, conectar IA con Make.

SUB-MÓDULO 3 · 10 h

#### Self-hosting de n8n con Docker

Docker básico, n8n en local, despliegue en VPS gratuito, HTTPS con dominio propio.

SUB-MÓDULO 4 · 10 h

#### Multi-agent workflows low-code

Varios LLMs colaborando, memoria y estado, proyecto final con agente comercial multi-paso.

#### Recursos para seguir

Síntesis, autoevaluación y hoja de ruta para profundizar más allá del módulo.

## El método de trabajo

Este módulo está diseñado para autoaprendizaje guiado. Puedes seguir el ritmo que marquen tus clases o avanzar a tu propio paso. Lo importante es que cada lección termina con un ejercicio práctico que conviene hacer antes de pasar a la siguiente: el low-code se aprende construyendo, no leyendo.

#### Cinco bloques que se repiten

Objetivos. Tres a cinco frases con lo que deberías saber hacer al terminar la lección. Léelos antes de empezar para tener un norte.

Teoría. Texto explicativo con los conceptos clave. Va de menos a más. Si algo no se entiende, sigue leyendo: muchas veces se aclara en el ejemplo posterior.

Ejemplos. Casos concretos de uso real con capturas o descripciones detalladas. Te dan referencia visual de cómo se aplica la teoría.

Ejercicio práctico. Lo construyes tú en la plataforma correspondiente. Es la parte que más fija lo aprendido.

FAQs y recursos. Preguntas habituales y materiales abiertos para profundizar. Consultas estos bloques cuando te quedes atascado o quieras ir más allá.

#### Crea las siguientes antes de empezar el módulo

Todas son gratuitas o tienen plan inicial gratuito suficiente para completar el módulo:

- n8n Cloud (trial 14 días) en n8n.io. Tras los 14 días pasamos a self-hosted (Sub-módulo 3) que es gratuito de por vida.
- Make en make.com. Plan Free incluye 1.000 operaciones al mes y 2 escenarios activos. Más que suficiente para los ejercicios.
- OpenAI Platform en platform.openai.com. Crédito inicial de 5 USD para nuevos developers (puede variar). Si se agota, hablamos de alternativas.
- Anthropic Console en console.anthropic.com. Pequeño crédito gratuito para probar la API de Claude.
- Google AI Studio en aistudio.google.com. Gemini API con tier gratuito generoso (60 peticiones por minuto en modelos Flash).
- GitHub en github.com. Para guardar workflows como respaldo y código de ejercicios.
- Docker Desktop (solo a partir del Sub-módulo 3) en docker.com/products/docker-desktop. Gratis para uso personal.

#### Por qué nos centramos en gratuito

Casi todas las plataformas que vamos a usar tienen planes de pago avanzados: n8n Pro y Enterprise, Make Pro y Teams, claves de API con presupuestos altos, etc. Esos planes existen y los mencionaremos cuando aporten algo relevante (más ejecuciones por minuto, integraciones premium, sso, soporte profesional), pero el objetivo del módulo es que aprendas a construir sin gastar. Cuando empieces a vender automatizaciones a clientes o las pongas en producción real, valorarás qué plan necesitas según tu volumen. Hasta entonces, los planes gratuitos sobran.

Si un ejercicio requiere algo que solo está en un plan de pago, te lo decimos explícitamente y proponemos una alternativa equivalente con herramientas open-source o gratuitas.

#### Plan de estudio sugerido

Cada sub-módulo está pensado para unas 10 horas de trabajo, repartibles según te convenga: cinco días de 2 horas, dos jornadas largas de 5 horas, una semana intensiva, etc. Lo que importa es que termines cada ejercicio antes de pasar al siguiente: la curva de aprendizaje del low-code se aplana muy rápido cuando construyes, y se aplana muy lento cuando solo lees.

El plan recomendado de cuatro semanas:

- Semana 1 · Sub-módulo 1 (n8n básico + webhooks). El más cargado de conceptos nuevos; ve sin prisa.
- Semana 2 · Sub-módulo 2 (Make). Más ágil porque ya conoces la lógica del low-code.
- Semana 3 · Sub-módulo 3 (Docker + self-hosting). Sales del navegador y entras en terminal. Curva de aprendizaje empinada pero contenida.
- Semana 4 · Sub-módulo 4 (multi-agent). Aplicas todo lo anterior al proyecto final.

## n8n · workflows, webhooks y nodos

Tu primer contacto con la automatización low-code. Construyes workflows desde cero en n8n cloud, entiendes la anatomía de un nodo y conectas el mundo exterior con webhooks.

 10 horas totales 3 lecciones 3 ejercicios prácticos n8n Cloud (trial) 

## Automatización low-code · por qué importa

Qué es exactamente low-code, dónde encaja en el stack de un AI Engineer moderno, y por qué saber montar workflows ya es competencia profesional verificable y no curiosidad.

#### Al final de esta lección sabrás:

- Explicar qué es la automatización low-code y cómo se diferencia de programar a mano.
- Identificar al menos tres procesos automatizables en tu día a día profesional o personal.
- Reconocer en qué punto del stack moderno de un AI Engineer encajan herramientas como n8n y Make.
- Tener clara la diferencia entre n8n, Make, Zapier y otras herramientas similares del mercado.

La pregunta de partida

Imagina que cada vez que llega un correo de un cliente potencial, alguien lo lee, lo clasifica por prioridad, busca al cliente en el CRM, le añade la información del correo, redacta un primer borrador de respuesta, y se lo deja al comercial preparado para revisar. Si ese trabajo lo hace una persona, lleva entre 5 y 15 minutos por correo. Si llegan 50 correos al día, son entre cuatro y diez horas de trabajo humano cualificado, todos los días, repetido y monótono.

Ese flujo se puede automatizar entero. No con código a medida desarrollado por un equipo de ingenieros durante semanas, sino con un workflow visual construido en una tarde por una persona con sensibilidad técnica. La diferencia entre poder hacerlo y no poder hacerlo no es ya el dominio de un lenguaje de programación: es el dominio de una herramienta low-code.

#### Low-code no es no-code, y tampoco es programar menos

Low-code significa que la mayor parte de la lógica se construye con bloques visuales conectados, pero cuando hace falta lógica específica puedes escribir pequeños trozos de código (típicamente JavaScript o Python) en nodos dedicados. Es distinto del no-code puro (donde no hay código bajo ningún supuesto) y muy distinto de programar a mano (donde escribes todo el flujo). Esa flexibilidad es lo que lo hace adecuado para automatizaciones reales de producción, no solo para juguetes de demo.

Dónde encaja el low-code en el stack del AI Engineer

El perfil moderno de AI Engineer no se reduce a entrenar modelos: en realidad la mayoría del trabajo profesional consiste en conectar capacidades. Los LLMs (Claude, GPT, Gemini) son capacidades. Las APIs de Slack, Notion, Google Calendar, Stripe, HubSpot, Airtable, Telegram, WhatsApp Business, son capacidades. Las bases de datos vectoriales, los CRMs, los ERPs son capacidades. Lo que las une y las pone a producir valor es una capa de orquestación.

Esa capa se puede construir de tres formas:

- Código a medida (Python, Node.js, Go). Máxima flexibilidad, máximo coste de desarrollo y mantenimiento. Adecuado cuando el flujo es muy complejo, debe escalar a millones de ejecuciones o tiene requisitos extremos de rendimiento.
- Frameworks de agentes (LangChain, LangGraph, CrewAI, Pydantic AI). Punto medio: estructura preestablecida pero todo se escribe en código. Mucha curva de aprendizaje y de mantenimiento.
- Herramientas low-code (n8n, Make, Zapier, Workato). Aceleración brutal: lo que en código sería un día de trabajo, son veinte minutos. Limitación: ciertos casos extremos o personalizaciones muy específicas no encajan bien. Adecuado para 80-90% de los casos reales de automatización empresarial y de side projects.

Como AI Engineer, lo profesional es saber cuándo usar cada vía. En este módulo nos centramos en la tercera, pero no es porque sea «la opción fácil»: es porque saber low-code te hace mucho más productivo y porque, en el mercado laboral actual, una agencia que necesita un automation engineer para construir flujos con LLMs busca exactamente esto.

#### Casos reales para que veas dónde brilla low-code

Caso 1 · clasificación y respuesta a leads. Llega un email a una bandeja compartida. Un workflow lee el correo, lo pasa por un LLM que lo clasifica por intención (consulta de precio, soporte técnico, demo, etc.), busca al remitente en el CRM, redacta un borrador de respuesta personalizado y crea una tarea en el sistema interno asignada al comercial correspondiente. Hecho en n8n: 1-2 días. Hecho a código: 1-2 semanas.

Caso 2 · sincronización de datos entre sistemas. Una empresa tiene Pipedrive (CRM), Notion (documentación interna), Slack (comunicación) y un Google Sheet maestro. Cada vez que cambia el estado de un deal en Pipedrive, se actualiza Notion, se manda mensaje a Slack, y se anota en el Sheet con fecha. Hecho en Make: 3-4 horas. Hecho a código: varios días de integraciones API + autenticaciones.

Caso 3 · generación automática de contenido. Una vez al día, un workflow lee las últimas 20 noticias de un sector (vía RSS feeds o APIs públicas), las pasa por un LLM que las resume, las pasa por otro LLM que evalúa relevancia según un criterio dado, monta un email digest y lo envía a una lista. Hecho en n8n: medio día. Hecho a código: una semana.

Panorama del mercado · n8n, Make, Zapier y compañía

Las tres herramientas más usadas en el mercado de automatización con IA hoy son:

- n8n. Open-source con licencia fair-code. Self-hosting gratuito de por vida (lo veremos en SM3) y plan cloud de pago con trial gratuito. Es la herramienta más completa para AI Engineering: trae nodos nativos para todos los LLMs grandes, soporta código JavaScript/Python en nodos function, y los workflows complejos se ven y mantienen bien. Es la pieza central del módulo.
- Make (antes Integromat). SaaS puro (no se puede self-hostear). Plan Free de 1.000 operaciones al mes y 2 escenarios activos. Catálogo de integraciones gigantesco (~1.700+ apps oficialmente conectadas). Interfaz extremadamente pulida. Lo veremos en SM2 porque sigue siendo la opción favorita de muchos equipos empresariales por su robustez y soporte oficial.
- Zapier. SaaS líder de mercado en el segmento simple. Plan Free muy limitado (100 tareas/mes, solo 2 pasos por «zap»). Su fortaleza es la simplicidad para casos lineales (cuando pasa X, haz Y). Para automatizaciones con IA y flujos complejos, n8n y Make son mejor opción.

Hay otras herramientas relevantes pero menos centrales: Workato (empresa, enterprise, sin plan gratuito), Pipedream (developer-first, plan gratuito generoso), Activepieces (open-source más nuevo), Power Automate de Microsoft (si tu organización ya vive en M365). Las mencionamos para que sepas que existen; el grueso del aprendizaje lo haces en n8n y Make porque son las que más probabilidades tienes de encontrarte en una entrevista laboral o en un proyecto freelance.

#### No es exactamente open-source pero a efectos prácticos sí

n8n usa la licencia «Sustainable Use License». Esto significa que puedes usarlo gratis para tus proyectos, para uso interno de tu empresa y para clientes, incluso comerciales, pero no puedes vender n8n como producto SaaS competidor a la propia n8n. Para el 99% de los casos prácticos, se comporta exactamente como un software open-source: descargas el código, lo modificas si quieres, lo despliegas donde quieras, lo usas con clientes y se acabó.

#### Ejercicio 1.1 · mapeo de tu propio flujo automatizable

El objetivo es que termines la lección con una visión clara de qué automatizaciones reales aporta valor a ti o a alguien de tu entorno. No hay herramienta todavía, solo papel y pensamiento.

1. Identifica tres procesos repetitivos que hagas tú o alguien cercano (familia, amigos, empresa donde trabajas o donde quisieras trabajar). Repetitivo significa que ocurre al menos varias veces por semana y sigue siempre los mismos pasos.
2. Para cada proceso, escribe en tu cuaderno o en un documento: (a) qué dispara el proceso (un email, una hora del día, un clic, un cambio en un sistema), (b) qué pasos se siguen exactamente, (c) qué decisiones se toman en cada paso, (d) qué herramientas o sistemas intervienen, (e) dónde podría aportar un LLM (clasificación, generación, resumen, extracción).
3. Marca el más viable de los tres como candidato para tu proyecto del SM4. No tiene que ser ambicioso: cuanto más acotado, mejor.

El error más común aquí es elegir un proceso enorme y vago («automatizar todo el marketing de mi empresa»). Cuanto más acotado y concreto («cuando llega un email con palabra X, hacer Y y Z»), más fácil de automatizar y más fácil de aprender.

¿Esto sustituye a saber programar?

No. Lo complementa. Saber programar sigue siendo un activo enorme: te permite escribir nodos function con lógica que no existe de serie, hacer scripts de soporte cuando tu workflow toca un caso raro, y debuggear con criterio cuando algo falla. Pero saber low-code te permite construir cosas útiles muchísimo más rápido, y combinar las dos vías te hace mucho más valioso que dominar solo una.

¿Para automatizaciones serias en producción se usa esto realmente?

Sí, y cada vez más. Empresas como Cisco, Deloitte, Adobe usan n8n en producción para flujos internos. Make tiene clientes enterprise muy grandes. Lo importante es saber cuándo conviene y cuándo no. Para flujos con muy alto volumen (millones de ejecuciones día) o que requieren rendimiento extremo, el código a medida sigue siendo la opción. Para el resto (que es la mayoría), low-code gana en velocidad de desarrollo y mantenibilidad.

¿Por qué empezamos con n8n y no con Make?

Tres razones. Primero, n8n se puede self-hostear gratis de por vida, lo que veremos en SM3, y eso te da control total cuando lleves esto a producción real. Segundo, n8n trae soporte de primera para LLMs (nodos AI Agent, vector stores nativos, chains, memory). Tercero, su modelo de workflow es más cercano al pensamiento de un ingeniero (flujos con bifurcaciones, código embebido cuando hace falta) y eso te entrena mejor para todo lo demás.

¿Cuánto cuesta poner una automatización en producción real?

Depende de volumen. Para volúmenes bajos (menos de 5.000 ejecuciones/mes), normalmente es gratuito o casi: n8n self-hosted en un VPS de 5 €/mes y APIs de LLMs con consumo bajo. Para volúmenes medios-altos, hablamos típicamente de 20-100 €/mes en infraestructura + APIs. Lo veremos con números reales en el SM3 y SM4.

#### Materiales abiertos para entender el panorama

- n8n Documentation. Documentación oficial completa, gratuita y abierta. La fuente más fiable para cualquier duda concreta. docs.n8n.io
- Make Help Center. Documentación oficial de Make, con tutoriales por integración. help.make.com
- Awesome n8n. Listado open-source en GitHub con workflows de ejemplo, recursos y plantillas comunitarias. github.com/restyler/awesome-n8n
- Workflow Automation Subreddit. Comunidad activa que comparte casos reales, problemas y soluciones. Útil para ver qué se está haciendo ahora mismo. reddit.com/r/n8n

Fin lección 1.1 · Sigue lección 1.2

## Primer workflow en n8n cloud

Crear cuenta, dashboard, anatomía de un workflow, triggers manuales y programados, y construir un primer flujo real que reciba datos, los transforme y los envíe a otro lugar.

#### Al final de esta lección sabrás:

- Crear cuenta en n8n cloud y moverte por el dashboard.
- Crear, ejecutar manualmente y revisar la ejecución de un workflow básico.
- Distinguir entre los tres tipos de triggers fundamentales: manual, cron y webhook.
- Construir un workflow que combine al menos tres nodos haciendo algo realmente útil.
- Leer correctamente las salidas (output) de cada nodo y entender el formato JSON que circula entre ellos.

Cuenta y planes · qué elegir

n8n tiene dos modalidades de uso: n8n Cloud (hosted por ellos, de pago con trial gratuito de 14 días) y n8n self-hosted (lo despliegas tú, gratis de por vida con la Community Edition). Para esta lección y todo el sub-módulo 1 usaremos Cloud porque acelera mucho el arranque (no hay nada que instalar, está todo configurado). En el SM3 te llevarás todo a self-hosted gratuito.

#### Lo que necesitas saber sobre precios

Trial gratuito · 14 días. Sin tarjeta. Ideal para este sub-módulo. Equivalente al plan Starter (2.500 ejecuciones de workflow al mes, 5 workflows activos).

Plan Starter · 20 €/mes. 2.500 ejecuciones, 5 workflows activos. Para automatizaciones personales o de pequeño negocio.

Plan Pro · 50 €/mes. 10.000 ejecuciones, 15 workflows activos.

Plan Enterprise. Bajo cotización. SSO, control de acceso por roles, soporte 24/7.

Para este módulo y para el 95% de tus side projects, el plan Free self-hosted en tu propio servidor te basta de por vida. Empezamos en Cloud por comodidad, migramos a self-hosted en SM3.

Pasos para crear cuenta:

1. Vete a n8n.io/cloud y pulsa Start free.
2. Regístrate con tu email o con Google. No hace falta tarjeta de crédito para el trial.
3. Te asignan una URL personal del tipo tuempresa.app.n8n.cloud. Esa es tu instancia.
4. La primera vez que entras te aparece el editor con un workflow vacío llamado My workflow. Esa es tu pantalla principal de trabajo.

Anatomía de un workflow

Un workflow en n8n es básicamente una secuencia de nodos conectados que se ejecuta de izquierda a derecha. Cada nodo recibe datos del nodo anterior, hace algo con ellos, y los pasa al siguiente. Los elementos principales que vas a manejar son nodos trigger, nodos de acción, nodos de lógica, nodos function y conexiones que llevan los datos entre ellos.

- Nodo trigger. El primer nodo de todo workflow. Define cuándo se ejecuta: manualmente (clicas el botón), por cron (cada hora, cada día), por webhook (cuando llega una petición HTTP), por evento de otra app (nuevo email, nuevo registro en Notion, etc.). Todo workflow tiene exactamente un trigger.
- Nodos de acción. Hacen algo: consultar una API, transformar datos, escribir en una base de datos, enviar un email. La mayoría de nodos son de este tipo.
- Nodos de lógica. IF (condicional), Switch (múltiples salidas según valor), Merge (unir flujos), Loop Over Items (iterar sobre listas). Te permiten bifurcar y reunir flujos.
- Nodos function. Code (escribir JavaScript o Python para transformar datos), Edit Fields (Set) (definir o modificar campos). Para cuando la lógica visual no llega.
- Conexiones. Las líneas entre nodos. Llevan datos. Lo que sale de un nodo (en formato JSON, lista de items) entra al siguiente.

#### En n8n, los datos viajan como lista de items JSON

Esto es lo que más cuesta a quien empieza. Entre cada nodo no viaja «un dato», viaja una lista de items donde cada item es un objeto JSON. Si un nodo devuelve 50 emails, entran 50 items al siguiente nodo, que se ejecuta una vez por cada item (a menos que esté configurado para procesar todo el lote junto). Esto se llama execution mode: por defecto «Run Once for Each Item», y a veces te interesa cambiarlo a «Run Once for All Items» para procesar batch.

Cuando algo no funciona como esperas en un workflow, el 80% de las veces es porque has confundido el modo de ejecución de algún nodo. Lee siempre con calma el output del nodo anterior antes de configurar el siguiente.

Triggers fundamentales · los tres que vas a usar siempre

Trigger manual. El más simple. Tienes un botón Execute Workflow en el editor y lo ejecutas cuando quieres. Es perfecto para desarrollo y pruebas, no para producción.

Schedule Trigger (cron). Ejecuta el workflow en horarios definidos: cada 5 minutos, todos los días a las 9:00, cada lunes a las 14:00. Es el trigger más común para automatizaciones recurrentes (reportes diarios, sincronizaciones nocturnas, polls a APIs).

Webhook Trigger. Activa el workflow cuando llega una petición HTTP a una URL concreta que n8n te genera. Es el trigger más potente: te permite integrar n8n con cualquier sistema externo que pueda hacer una llamada HTTP (formularios, otras apps, scripts, eventos de Stripe, mensajes de Telegram, etc.). Lo veremos en profundidad en la lección 1.3.

Hay decenas de triggers específicos para apps concretas (Gmail trigger, Notion trigger, Telegram trigger, etc.) que son básicamente webhooks preconfigurados. Vienen muy bien cuando integras con apps populares.

#### Workflow: «Cada mañana a las 9, envíame un resumen del tiempo a mi correo»

Vamos a montar este workflow mentalmente para que veas la lógica antes de tu ejercicio. Tendrá tres nodos:

Nodo 1 · Schedule Trigger. Configurado para ejecutarse todos los días a las 9:00. Output: un item con la fecha y hora de ejecución.

Nodo 2 · HTTP Request. Llama a la API gratuita de Open-Meteo (no requiere API key) pidiendo el tiempo para Madrid:

Method: GET URL: https://api.open-meteo.com/v1/forecast Query Parameters: latitude: 40.4168 longitude: -3.7038 current: temperature_2m,precipitation,wind_speed_10m timezone: Europe/Madrid

Output: un item con un objeto JSON que contiene la temperatura actual, precipitación y velocidad de viento.

Nodo 3 · Send Email (SMTP) o Gmail. Envía un correo a tu propia dirección con el contenido formateado. En el campo Text usas expresiones de n8n para interpolar los valores del nodo anterior:

Subject: Tiempo en Madrid hoy Text: Buenos días. Temperatura actual: {{ $json.current.temperature_2m }}°C Precipitación: {{ $json.current.precipitation }} mm Viento: {{ $json.current.wind_speed_10m }} km/h Que tengas buen día.

Cada `{{ $json.campo }}` es una expresión de n8n: dentro de las llaves dobles, accedes al JSON del nodo anterior. Las verás muchísimo en el resto del módulo.

Credenciales · cómo se manejan en n8n

La mayoría de nodos que conectan con servicios externos (Gmail, OpenAI, Slack, Notion) requieren autenticación. n8n maneja esto con un sistema de Credentials: las configuras una vez, las guardas con un nombre, y luego las reutilizas en cualquier nodo del mismo tipo.

Para Gmail, por ejemplo, n8n te lleva por OAuth automáticamente cuando configuras la primera credencial. Para OpenAI, tienes que copiar tu API key desde platform.openai.com/api-keys y pegarla en el campo correspondiente. Una vez configuradas, las credenciales son por workspace: cualquier workflow tuyo puede usarlas.

#### Nunca subas un workflow exportado con credenciales reales a GitHub

Cuando exportas un workflow desde n8n (botón Download), por defecto no se incluyen las credenciales (se sustituyen por placeholders), pero ten cuidado si pegas API keys directamente en campos del workflow en lugar de en Credentials. Esos sí se exportan. Y un API key de OpenAI publicado en GitHub se puede consumir entero en horas por bots que escanean repositorios públicos buscando claves.

#### Ejercicio 1.2 · tu primer workflow funcional

Tiempo estimado · 90-100 minutos

El objetivo es que termines la lección con un workflow real corriendo en tu cuenta de n8n cloud, que se ejecute manualmente y haga algo medianamente útil.

1. Crea cuenta en n8n cloud y entra al editor. Renombra el workflow vacío a algo descriptivo, por ejemplo «Resumen meteorológico diario».
2. Añade un trigger manual (nodo Manual Trigger). Aún no programamos horarios; vamos a probar ejecutándolo a mano.
3. Añade un nodo HTTP Request que llame a la API de Open-Meteo (gratuita, no requiere registro) con los parámetros del ejemplo anterior pero para tu ciudad (busca tu latitud y longitud en cualquier mapa).
4. Ejecuta hasta aquí y mira el output del nodo HTTP. Familiarízate con cómo se ve el JSON devuelto. Identifica dónde está la temperatura, la precipitación y el viento dentro del objeto.
5. Añade un tercer nodo que envíe el resumen a algún sitio: Gmail (Send Message), Telegram (con un bot que creas en BotFather, gratis), Discord, Slack, o un Webhook a webhook.site para verlo en una página web sin más.
6. Ejecuta el workflow completo y verifica que recibes el mensaje con los datos del tiempo correctamente formateados.
7. Cambia el trigger a Schedule Trigger configurado para ejecutarse todos los días a las 9:00. Activa el workflow (toggle en la esquina superior derecha). A partir de mañana a las 9, te llegará el resumen automáticamente.

Si te quedas atascado en credenciales OAuth (que es donde más gente se atasca al principio), céntrate en la opción Telegram o webhook.site: son las más rápidas de configurar.

¿Si activo el workflow consume ejecuciones aunque no haga nada útil?

Sí. En n8n cloud, cada ejecución cuenta sea exitosa o no. Si tu plan tiene 2.500 ejecuciones al mes y configuras un schedule que se ejecuta cada minuto, en menos de dos días te has gastado el cupo. Para tareas frecuentes (cada minuto, cada 5 minutos) conviene self-hostear (SM3) o usar plan superior.

¿Cómo veo qué pasó en una ejecución que falló?

En la pestaña Executions del workflow (lateral izquierdo del editor). Ves la lista de todas las ejecuciones, su estado (success/error), y al hacer clic en una concreta abres el editor con los datos exactos que circularon en esa ejecución. Es la herramienta de debug número 1 de n8n. Acostúmbrate desde el principio.

¿Puedo importar workflows hechos por otros?

Sí, n8n exporta e importa workflows en JSON. Hay templates oficiales en n8n.io/workflows que puedes importar de un clic. Es una manera excelente de aprender: importas algo que ya funciona, lo desmontas para entender cómo está hecho, lo modificas para tu caso.

¿Las expresiones de n8n son JavaScript o algo propio?

Son JavaScript con algunas variables y helpers añadidos por n8n. Dentro de `{{ }}` puedes escribir cualquier expresión válida de JavaScript. Variables especiales: `$json` es el JSON del item actual del nodo anterior, `$now` es la fecha y hora de ejecución, `$node["nombre"]` accede al output de un nodo concreto por su nombre. Estas son las que más vas a usar.

#### Materiales abiertos sobre n8n básico

- n8n Documentation · Getting Started. Tutorial oficial paso a paso para los primeros workflows. Gratuito y completo. docs.n8n.io/getting-started
- n8n Template Library. Repositorio oficial de workflows de ejemplo para casi todos los casos comunes. Importables con un clic. n8n.io/workflows
- n8n Community Forum. Comunidad oficial donde se preguntan dudas y se comparten soluciones. Muy activa. community.n8n.io
- Open-Meteo API Documentation. La API gratuita de meteorología que usaremos en el ejercicio. Sin clave, sin registro, generosa en límite. open-meteo.com/en/docs

## Webhooks y nodos avanzados

Qué es exactamente un webhook, cómo se diferencia de una API call, tipos de nodos, expresiones avanzadas, nodos function con código, manejo de errores y conexión con tu primer LLM en n8n.

#### Al final de esta lección sabrás:

- Explicar qué es un webhook y cómo se distingue de una llamada API tradicional.
- Configurar un Webhook Trigger en n8n y probarlo con peticiones reales.
- Usar expresiones avanzadas para transformar datos entre nodos.
- Escribir lógica personalizada en un nodo Code (JavaScript) cuando los nodos visuales no llegan.
- Manejar errores con nodos Error Trigger y reintentos.
- Conectar n8n con un LLM (Claude, OpenAI o Gemini) y devolver la respuesta a quien llamó al webhook.

Webhook vs API call · la dirección del flujo

Casi todo el mundo confunde estos dos conceptos al principio, y es importante tenerlo claro:

- API call: tú haces una petición HTTP a un servicio externo y esperas su respuesta. Eres el cliente. Lo hicimos en el ejercicio anterior cuando consultamos Open-Meteo: tú preguntaste, ellos respondieron.
- Webhook: otro servicio hace una petición HTTP a una URL que tú expones, y tu workflow se activa para procesarla. Eres el servidor. Cuando alguien envía un formulario en tu web, cuando llega un nuevo mensaje en Telegram, cuando Stripe registra un pago, todos pueden disparar webhooks a tu n8n.

La diferencia es la dirección del flujo: en API call vas tú a por la información; en webhook la información viene a ti. Los workflows reales suelen combinar ambos: un webhook recibe el dato inicial, una serie de API calls enriquecen la información, y al final otro servicio recibe el resultado.

#### Sin webhooks, todo es polling, y el polling es caro

La alternativa a recibir webhooks es preguntar constantemente «¿hay algo nuevo?». Eso se llama polling y consume recursos: cada 5 minutos haces una petición que la mayoría de veces devuelve «no, nada». Con un webhook, te enteras instantáneamente cuando algo ocurre, sin gastar peticiones. Para automatizaciones que reaccionan a eventos externos, los webhooks son siempre la vía superior cuando están disponibles.

Configurar un Webhook Trigger en n8n

Pasos básicos:

1. Crea un workflow nuevo. Como primer nodo, añade Webhook.
2. Configura el método HTTP (GET, POST, etc.). POST es lo más común para recibir datos.
3. Define un path (la parte final de la URL que n8n te genera). Por ejemplo, recibir-lead.
4. n8n te da dos URLs: una de test (solo activa cuando estás escuchando manualmente desde el editor) y una de production (siempre activa si el workflow está en estado Active).
5. Pulsa Listen for test event en n8n. Ahora envía una petición HTTP a la URL de test (puedes usar Postman, Insomnia, una herramienta online como reqbin.com, o curl desde terminal).
6. Cuando llegue la petición, n8n captura el body, los headers y los query params. Todo eso queda disponible para los siguientes nodos.

#### Caso de uso: webhook que recibe un lead nuevo

Imagina que tienes una landing page con un formulario simple (nombre, email, mensaje). El formulario, al enviarse, hace POST a tu URL de webhook de n8n. La payload típica:

POST https://tuempresa.app.n8n.cloud/webhook/recibir-lead Content-Type: application/json { "nombre": "María García", "email": " [email protected]", "mensaje": "Me interesa una demo de vuestro producto" }

En el nodo siguiente accedes a esos campos con expresiones n8n:

{{ $json.body.nombre }} → "María García" {{ $json.body.email }} → " [email protected]" {{ $json.body.mensaje }} → "Me interesa una demo..."

A partir de ahí puedes hacer cualquier cosa: clasificar el mensaje con un LLM, guardar el lead en Notion, mandar un Slack al equipo comercial, enviar email automático de confirmación, etc.

Tipos de nodos en profundidad

Nodos action específicos por app. n8n tiene cientos: Gmail, Notion, Slack, Airtable, Google Sheets, Discord, Stripe, HubSpot, Pipedrive, MongoDB, Postgres, Telegram, WhatsApp Business, etc. Cada uno expone las operaciones más comunes de su API en formato visual. Cuando un nodo específico existe, úsalo: es más cómodo que HTTP Request a pelo.

HTTP Request. El nodo universal: con él puedes hablar con cualquier API del mundo aunque no exista nodo específico. Esencial para servicios menos populares o internos. Soporta todos los métodos HTTP, todos los tipos de autenticación, manejo de paginación, etc.

Code (Function). Te permite escribir JavaScript o Python directamente para transformar datos. Útil cuando necesitas lógica compleja que no se expresa bien con nodos visuales. Ejemplo: parsear un texto con regex, calcular un score complejo, generar IDs únicos, etc.

Edit Fields (Set). Crea o modifica campos en el JSON que circula. Es el nodo más usado del módulo, lo verás por todas partes. Te permite construir el JSON exacto que necesita el siguiente nodo sin tener que escribir código.

IF y Switch. Bifurcan el flujo según condiciones. IF tiene dos salidas (true/false), Switch puede tener muchas (una por cada caso definido). Para reaccionar distinto según el contenido de un mensaje, una categoría, un valor, etc.

AI Agent y nodos LLM. n8n tiene soporte de primera clase para LLMs. Hay nodos específicos para OpenAI, Anthropic, Google Gemini, Mistral, Ollama (local), Hugging Face, AWS Bedrock, Azure OpenAI. Y un nodo especial llamado AI Agent que orquesta varios LLM calls con memoria, tools y razonamiento iterativo. Este último lo veremos a fondo en el SM4.

#### El balance entre visual y código

Sí usa Code cuando: necesitas parsear texto con regex, hacer transformaciones que requieren un loop personalizado, calcular un score con varias variables, normalizar datos entre dos formatos muy distintos.

No uses Code cuando: un nodo Set te basta (al principio se tiende a usar Code para todo; resiste la tentación). Si el workflow se llena de bloques Code grandes, conviene revisar si no estarías mejor en código a pelo. El sweet spot de low-code es que la mayoría del workflow sea visual.

Expresiones avanzadas · más allá de $json.campo

Algunas expresiones útiles que verás repetidamente:

- `{{ $json.body.email.toLowerCase() }}` — métodos de JavaScript directamente: lowercase, split, replace, includes, etc.
- `{{ $now.format('yyyy-MM-dd') }}` — manejo de fechas con la librería luxon que viene incluida.
- `{{ $node["Webhook"].json.body.nombre }}` — acceder al output de un nodo concreto por nombre, no solo del anterior.
- `{{ $items().length }}` — número de items en la ejecución actual.
- `{{ $json.precio > 100 ? 'caro' : 'barato' }}` — ternarios para lógica simple inline.
- `{{ $json.nombre || 'Sin nombre' }}` — valores por defecto con el operador OR.

Manejo de errores en producción

Cuando un workflow se ejecuta automáticamente cientos o miles de veces, algún error siempre acaba ocurriendo: la API externa cae, el formato de un dato cambia, una credencial expira. Saber manejar errores es la diferencia entre un workflow que se rompe sin avisar y uno que aguanta producción.

Tres mecanismos clave:

- Configuración por nodo · Retry on Fail. En cada nodo, en la pestaña Settings, puedes activar reintentos automáticos con espera entre ellos. Para llamadas a APIs que a veces fallan transitoriamente, conviene activarlo (3 reintentos cada 5 segundos suele bastar).
- Continue On Fail. También en Settings de cada nodo. Si lo activas, cuando el nodo falla el workflow no se detiene: continúa al siguiente nodo con un campo `error` en el JSON que puedes verificar. Útil para escenarios «si falla, intentar plan B».
- Error Trigger. Un workflow secundario que se activa automáticamente cuando otro workflow falla. Útil para mandar alertas a Slack o a tu correo: «el workflow X ha fallado, error: Y». La práctica profesional habitual es tener un único Error Trigger genérico que gestiona errores de todos los workflows críticos.

#### Workflow integrador: clasificador de leads con Claude

Diseño del workflow:

Nodo 1 · Webhook. POST en `/clasificar-lead`. Recibe nombre, email, mensaje del lead.

Nodo 2 · Anthropic Chat Model (nodo nativo de n8n). Configurado con tu API key de Anthropic. Modelo: claude-haiku-4-5 (rápido y barato para tareas de clasificación). System prompt:

User prompt: `{{ $json.body.mensaje }}`

Nodo 3 · Edit Fields (Set). Construye el JSON final que vamos a devolver:

lead_email: {{ $('Webhook').item.json.body.email }} lead_nombre: {{ $('Webhook').item.json.body.nombre }} clasificacion: {{ $json.message.content }} recibido_en: {{ $now.toISO() }}

Nodo 4 · Respond to Webhook. Devuelve el JSON construido al cliente que llamó al webhook original.

Con cuatro nodos has construido un microservicio inteligente: el formulario de tu landing puede ahora llamarlo y recibir directamente la clasificación.

#### Ejercicio 1.3 · workflow webhook + LLM end-to-end

El objetivo es montar tu primer workflow que reciba datos del exterior, los procese con un LLM y devuelva respuesta o haga algo útil. Esta arquitectura es la base de prácticamente todo lo que viene en el resto del módulo.

1. Crea un nuevo workflow en n8n y añade un Webhook Trigger. Configura method POST y path significativo (por ejemplo, `analizar-texto`). Anota la URL de test.
2. Prueba el webhook haciendo una petición POST desde reqbin.com o desde tu terminal con curl, enviando un body JSON con un campo `texto` conteniendo un párrafo cualquiera.
3. Añade un nodo LLM: Anthropic (Claude Haiku), OpenAI (gpt-4o-mini) o Google Gemini Flash. Configura la credencial con tu API key. System prompt: «Analizas el sentimiento (positivo, negativo, neutro) y extraes 3 palabras clave del texto que recibes. Devuelves solo un JSON con campos sentimiento y palabras_clave (lista)». User prompt: el texto recibido del webhook.
4. Añade un nodo Edit Fields para construir un objeto de respuesta limpio: el texto original, el análisis del LLM, y la fecha y hora de procesamiento.
5. Añade un nodo Respond to Webhook que devuelva ese objeto.
6. Activa el workflow y prueba la URL de production con varios textos: una review positiva, una queja, un texto neutro. Verifica que la respuesta tenga sentido.
7. Bonus: añade un nodo IF después del LLM que, si el sentimiento es negativo, también envíe un Slack o Telegram avisando al equipo. Mantén el Respond to Webhook al final con la respuesta normal en cualquier caso.

Guarda este workflow. Te servirá de plantilla para el resto del módulo: el patrón webhook → procesado con LLM → respuesta aparecerá una y otra vez.

¿Mi URL de webhook es pública? ¿Cualquiera puede llamarla?

Sí, técnicamente cualquiera con la URL puede hacer una petición. Para casos sensibles, n8n soporta autenticación en el nodo Webhook (Basic Auth, Header Auth con token secreto). Para casos no sensibles (ej. te llama tu propio formulario público), no suele hacer falta más que mantener la URL razonablemente larga e impredecible.

¿Cuánto cuesta usar Claude/GPT/Gemini desde n8n?

Pagas por uso a la plataforma del LLM, no a n8n. Tarifas orientativas a fecha de 2026: Claude Haiku 4.5 ~0,25-1 USD por millón de tokens; GPT-4o-mini ~0,15-0,60 USD por millón; Gemini Flash 2.x tier gratuito generoso y luego ~0,07-0,30 USD por millón. Para los ejercicios del módulo, el consumo total será de céntimos. Verifica los precios actuales en la web del proveedor antes de poner algo en producción.

¿Cómo testeo el workflow sin gastar API calls reales mientras desarrollo?

Tres opciones. (a) Usa modelos baratísimos durante desarrollo (Haiku, Flash, gpt-4o-mini); las pruebas cuestan céntimos. (b) Cachea respuestas: configura el nodo en modo «Pin Data» para reutilizar el output de una ejecución exitosa mientras testeas los nodos posteriores. (c) Para tests muy intensivos, instala Ollama localmente y usa un modelo open-source en lugar de API; gratis y sin límite, aunque más lento.

¿Qué pasa si el webhook recibe muchas peticiones a la vez?

n8n las pone en cola y las procesa según los recursos disponibles. En cloud, hay límites de concurrencia según plan. En self-hosted, puedes configurar el modo de ejecución «queue» con workers, lo que permite escalar horizontalmente. Para volúmenes muy altos (decenas de miles de webhooks/día), conviene self-hostear con varios workers y Redis como backend.

#### Sobre webhooks, expresiones y LLMs en n8n

- n8n Documentation · Webhook node. Documentación completa del nodo webhook con todos los modos y opciones. docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.webhook
- n8n Expressions Reference. Lista completa de expresiones, variables y métodos disponibles. docs.n8n.io/code/expressions
- n8n AI Agent. Introducción al concepto de AI Agent en n8n, la base de los workflows con LLMs avanzados. docs.n8n.io/advanced-ai
- webhook.site. Herramienta gratuita para inspeccionar webhooks: te da una URL, capturas peticiones, y ves exactamente qué llega. Útil para depurar. webhook.site

## Make e integraciones empresariales

Make como alternativa pulida a n8n. Cuándo conviene cada herramienta, lógica condicional con routers, filtros y aggregators, y conectar IA a Make para construir clasificadores empresariales reales.

 10 horas totales 3 lecciones 3 ejercicios prácticos Make Free 1.000 ops/mes 

## Make vs n8n · panorama y primer escenario

Cuándo elige el mercado Make sobre n8n y al revés, plan Free de Make, primer escenario funcional integrando Gmail con Google Sheets, y traducción de conceptos n8n → Make.

#### Al final de esta lección sabrás:

- Decidir entre Make y n8n para un caso de uso dado.
- Crear cuenta en Make y construir tu primer escenario funcional.
- Traducir conceptos de n8n al vocabulario de Make: workflow → escenario, nodo → módulo, expresión → mapping.
- Entender el modelo de coste de Make basado en «operations» y planificar tu workflow para no excederte del plan gratuito.

Diferencias clave · cuándo elegir cada uno

Make y n8n compiten en el mismo mercado pero tienen filosofías distintas y conviene saber cuándo usar uno u otro:

#### Casos donde Make es claramente mejor opción

Catálogo de integraciones más amplio. Make tiene ~1.700+ apps oficialmente conectadas, n8n tiene ~500. Para apps de nicho empresarial (SAP, Workday, Salesforce avanzado), Make suele tener mejor soporte oficial.

Equipo no técnico. La interfaz de Make es la más amigable del mercado para no-developers. Los flujos circulares y visuales se entienden a la primera.

Compliance empresarial. Make tiene certificaciones (SOC 2, GDPR, HIPAA Business Associate) que algunas empresas exigen y que en n8n cloud no siempre están en planes bajos.

No quieres saber nada de servidores. Make es SaaS puro; nunca tendrás que tocar Docker ni desplegar nada. Si self-hosting no te interesa para nada, Make es más simple.

#### Casos donde n8n es claramente mejor opción

Self-hosting. n8n se puede ejecutar gratis en tu servidor de por vida; Make no.

Soporte de LLMs avanzados. n8n tiene el nodo AI Agent nativo, vector stores, chains, memory; Make tiene módulos para LLMs pero con menos abstracciones de alto nivel. Para construir agentes serios, n8n gana.

Código embebido. n8n permite escribir JavaScript o Python en nodos Code. Make tiene la opción pero más limitada.

Control de costes con alto volumen. Self-hosted en VPS de 5 €/mes te permite procesar cientos de miles de ejecuciones. Make en volúmenes similares cuesta 200-500 €/mes.

En la práctica profesional, muchos automation engineers usan ambos en distintos proyectos. Make para integraciones empresariales rápidas con clientes que valoran la interfaz pulida. n8n para automatizaciones técnicas con IA, multi-agentes, o cuando el cliente quiere infraestructura propia.

Plan Free de Make · lo que necesitas saber

El plan Free de Make incluye:

- 1.000 operations al mes. Una operación = una acción que hace un módulo (recibir un email = 1, enviar un Slack = 1, procesar 50 items en un iterator = 50). Para uso personal y prototipos, sobra. Para producción, te quedas corto.
- 2 escenarios activos simultáneamente. Puedes tener muchos guardados, pero solo 2 corriendo a la vez.
- Intervalo mínimo entre ejecuciones: 15 minutos. No puedes correr un escenario cada minuto en el Free. Si necesitas frecuencia alta, plan Core (9 USD/mes) baja a 1 minuto.
- Sin restricción de duración de los datos. Los escenarios pueden procesar payloads grandes.

#### Cuándo subir de plan y qué desbloquea

Plan Core · 9 USD/mes. 10.000 operations, intervalo de 1 minuto, escenarios activos ilimitados. Para uso intensivo personal o un único cliente pequeño.

Plan Pro · 16 USD/mes. 10.000 operations + features avanzadas: variables custom, prioridad de cola, full-text search en histórico.

Plan Teams · 29 USD/mes. Multi-usuario, roles, control de acceso. Para equipos pequeños.

Para todo este módulo y para empezar tu carrera de automation engineer, el plan Free te basta. Subes de plan cuando un cliente te paga lo suficiente como para que tenga sentido.

Traducción de conceptos · n8n a Make

Si ya viste el SM1, esta tabla de equivalencias te ahorra horas de confusión:

| Concepto en n8n | Equivalente en Make | Nota |
| --- | --- | --- |
| Workflow | Scenario (Escenario) | Mismo concepto, nombre distinto. |
| Nodo | Module (Módulo) | En Make los módulos se conectan con líneas curvas, en n8n con líneas rectas. |
| Trigger | Trigger (mismo nombre) | Primer módulo del escenario. |
| Expresión `{{$json.x}}` | Mapping (drag-and-drop) | En Make arrastras campos visualmente desde el panel lateral; no hay sintaxis textual. |
| IF / Switch | Router | Mismo concepto. El router de Make también permite filtros por ruta. |
| Loop Over Items | Iterator | Procesa items uno por uno. |
| Merge | Array Aggregator | Une múltiples items en una estructura única. |
| Webhook trigger | Custom Webhook | Igual. URL única por escenario. |
| HTTP Request | HTTP > Make a request | Mismo nodo universal. |
| Code node (JS/Python) | Tools > Set variable + custom functions | Más limitado que n8n; lo veremos. |
| Credentials | Connections | Mismo sistema reutilizable. |
| Active/Inactive | ON/OFF (scheduling) | Toggle igual. |

#### Escenario: «Cuando llega un email a Gmail con palabra clave, guardarlo en Google Sheets»

El equivalente clásico al «hello world» del mundo Make. Vamos paso a paso:

Módulo 1 · Gmail > Watch emails. Trigger. Configura la conexión OAuth con tu cuenta de Gmail. Especifica: carpeta = Inbox, marcar como leído = no, filtro = «from:cualquiera», máximo 10 emails por ejecución. Make hará polling cada 15 minutos en plan Free.

Módulo 2 · Router. Bifurca el flujo según el contenido del email. Una salida si el asunto contiene «factura», otra si contiene «soporte», una tercera por defecto.

Módulo 3 · Google Sheets > Add a row. En cada rama del router, añade una fila distinta a una pestaña distinta del mismo Sheet: pestaña «Facturas», pestaña «Soporte», pestaña «Otros». Mapeas los campos del email (asunto, remitente, fecha, body) a las columnas correspondientes.

Cuando guardas y activas, Make hace polling de tu Gmail cada 15 minutos, detecta emails nuevos, los pasa por el router y los guarda según la categoría. Sin código, sin servidor, sin instalar nada.

Operations · cómo planificar para no gastarte el cupo

Cada módulo que se ejecuta consume operations. Mecánica:

- Un módulo que se ejecuta con éxito = 1 operation.
- Un trigger que detecta 5 emails nuevos = 5 operations en el trigger + multiplica todo lo que venga después.
- Un iterator que recorre 100 elementos = 100 operations en el iterator + las operations de cada módulo dentro del loop.
- Los módulos de tipo Tools (set variable, BasicAggregator) suelen ser «free of charge» pero no todos.

Trucos para reducir consumo de operations:

- Filtra cuanto antes en el escenario. Si un email no cumple criterio, descártalo en el trigger con un filtro y no entres al resto del flujo.
- Si tu trigger procesa muchos items, considera procesarlos en batch (un solo módulo HTTP que reciba la lista entera) en vez de uno a uno.
- Schedules más espaciados consumen menos.
- Antes de activar, lee la columna Operations en el panel derecho de cada módulo para ver cuántas consume cada uno.

#### Ejercicio 2.1 · tu primer escenario en Make

Replica el ejemplo de Gmail → Google Sheets con tus propias cuentas. El objetivo es familiarizarte con la interfaz de Make y construir tu primera integración funcional.

1. Crea cuenta en Make en make.com. Plan Free. No requiere tarjeta.
2. Crea un nuevo escenario. Renómbralo a algo descriptivo.
3. Añade módulo Gmail · Watch emails. Configura la conexión OAuth con tu Gmail. Especifica filtro: emails de tu propia dirección o de una específica (para tener control sobre las pruebas).
4. Crea un Google Sheet con columnas: Fecha, Remitente, Asunto, Cuerpo, Categoría.
5. Añade módulo Router tras el Gmail. Define dos rutas: una con filtro «si asunto contiene 'urgente'» y otra «por defecto».
6. En cada ruta del router, añade módulo Google Sheets · Add a row. Mapea los campos del email a las columnas. En la ruta «urgente», pon Categoría = «URGENTE». En la otra, Categoría = «Normal».
7. Ejecuta el escenario una vez con el botón Run once. Envíate dos emails (uno con «urgente» en el asunto, otro sin) y verifica que aparecen en las filas correctas del Sheet.
8. Activa el escenario con el toggle ON. A partir de ahora, cada 15 minutos Make revisa tu Gmail y guarda los nuevos automáticamente.
9. Bonus: añade un módulo Slack o Telegram en la rama «urgente» que también te avise.

Si OAuth con Gmail te da problemas (Google a veces es complicado), prueba con Gmail Trigger por IMAP en su lugar (más directo) o cambia a IMAP de cualquier proveedor que tengas a mano (Outlook, Yahoo, Fastmail, etc.).

¿Las operations se renuevan al mes? ¿Cuándo exactamente?

Sí, se renuevan el día 1 de cada mes natural. Si te quedas a cero en mitad de mes, tus escenarios dejan de ejecutarse hasta el día 1 o hasta que pases a plan superior. Make te avisa cuando llegas al 80% y al 100% del consumo.

¿Puedo pasar workflows de Make a n8n o al revés?

No de forma automática. La estructura y los conceptos son parecidos pero los formatos no son compatibles. Lo que se hace en la práctica: replicar manualmente. Suele ser rápido porque la lógica es la misma, solo cambian las herramientas. Hay algunos proyectos open-source que intentan importar de Make a n8n con resultados parciales; búscalos si te interesa.

¿Make tiene API para crear escenarios programáticamente?

Sí, tiene API en planes Pro y superiores. En Free se gestiona todo desde la UI. Para automation engineers que llevan muchos clientes, la API es útil porque permite versionado y reutilización; en plan Free no es accesible.

¿Por qué Make sigue siendo tan popular si n8n existe?

Tres razones. (a) Reputación: Make (antes Integromat) lleva más años y muchas empresas grandes ya lo usan. (b) Catálogo de integraciones más amplio para apps de nicho empresarial. (c) Interfaz más amigable para perfiles no-developer. Coexisten porque atacan segmentos ligeramente distintos del mercado. Saber los dos te abre más puertas.

#### Materiales abiertos sobre Make

- Make Help Center. Documentación oficial completa, gratuita y abierta. help.make.com
- Make Academy. Curso gratuito oficial de Make con vídeos cortos y ejercicios. academy.make.com
- Make Templates Gallery. Galería de escenarios prediseñados importables con un clic. make.com/en/templates
- Make Community. Foro oficial donde se piden y comparten escenarios. community.make.com

## Routers, filtros y aggregators

La lógica de Make en profundidad. Cómo bifurcar flujos con routers, filtrar con condiciones expresivas, iterar listas y agregar resultados en estructuras nuevas. La materia que separa el «hola mundo» del escenario real.

#### Al final de esta lección sabrás:

- Diseñar escenarios con múltiples rutas usando Router y filtros condicionales.
- Iterar sobre listas de elementos con Iterator y procesar cada item.
- Agregar resultados de un iterator en estructuras como Array Aggregator, Text Aggregator o Table Aggregator.
- Manejar errores con Error Handlers y rutas alternativas.
- Usar Data Stores para guardar estado entre ejecuciones sin necesidad de base de datos externa.

Router · bifurcar flujos

El módulo Router es la pieza central de cualquier escenario que toma decisiones. Crea múltiples rutas paralelas que pueden ejecutarse según condiciones. Lo encuentras en Tools → Router.

Tres modos de funcionamiento del router:

- Sin filtro en ninguna ruta. Todas las rutas se ejecutan siempre. Útil para hacer cosas en paralelo (mandar email Y guardar en Sheets Y notificar Slack).
- Filtros excluyentes. Cada ruta tiene un filtro y se ejecuta la primera que cumple. Equivalente a Switch en n8n. Para clasificar y mandar cada caso por su sitio.
- Filtros independientes. Cada ruta evalúa su filtro independientemente. Una ejecución puede activar varias rutas. Útil para casos donde un mismo item dispara varias acciones a la vez (ej. si es urgente Y de cliente VIP).

#### El corazón de la lógica condicional

Los filtros en Make se definen visualmente arrastrando campos al área de condiciones. La estructura es: campo · operador · valor. Operadores disponibles:

- Text: Equal, Does not equal, Contains, Does not contain, Starts with, Ends with, Matches pattern (regex), Is empty, Is not empty.
- Number: Equal, Greater than, Less than, Between, etc.
- Date: Equal, Before, After, Within last X days, etc.
- Boolean: Is true, Is false.
- Array: Contains, Length equal to, Length greater than, etc.

Puedes combinar condiciones con AND/OR. Para casos complejos (más de 4-5 condiciones), considera dividir el flujo en routers anidados: más fácil de mantener que un único filtro gigantesco.

Iterator · procesar listas elemento a elemento

Si un módulo te devuelve una lista (ej. 50 emails, 200 filas de Sheet, todos los miembros de un canal de Slack), por defecto Make procesa cada elemento independientemente. Pero a veces lo que recibes es un único objeto que contiene un array, y necesitas «desempaquetarlo» para procesar cada elemento por separado. Para eso está el Iterator.

Ejemplo: una API te devuelve `{"productos": [...]}` con 30 productos. Configuras Iterator con array `{{productos}}`, y a partir de ahí Make procesa el flujo 30 veces, una por producto.

Importante: cada iteración cuenta como operations. Un iterator que recorre 100 elementos + 2 módulos dentro = 100 × 3 = 300 operations. Planifica con cabeza si tu plan es Free.

Aggregators · juntar resultados después de iterar

El compañero natural del Iterator es el Aggregator. Hay tres tipos principales:

- Array Aggregator. Junta los items de un loop en un único array. Útil cuando quieres seguir procesando todos como conjunto después del loop.
- Text Aggregator. Concatena un campo de todos los items en un único string. Útil para generar un texto resumen, una lista de nombres separados por comas, etc.
- Table Aggregator. Construye una estructura de tabla con filas y columnas a partir de los items iterados. Útil para enviar tablas como atadhmrnt en emails o Slack.

#### Escenario: «Resumir todos los emails no leídos en un único mensaje de Slack»

El diseño:

Módulo 1 · Schedule. Trigger. Ejecuta cada hora en horario laboral.

Módulo 2 · Gmail · Search emails. Trae los emails no leídos de la última hora. Output: un objeto que contiene un array de emails.

Módulo 3 · Iterator. Despliega el array para procesar uno a uno.

Módulo 4 · Tools · Set variable. Para cada email, construye una línea de resumen: «De: X · Asunto: Y · Hora: Z».

Módulo 5 · Text Aggregator. Reúne todas las líneas en un único texto separadas por saltos de línea. Marca «Aggregator source: Iterator del paso 3».

Módulo 6 · Slack · Create a message. Envía el texto agregado al canal que toque. Recibe un único mensaje con el resumen completo, no 50 mensajes Slack uno por email.

Sin iterator + aggregator, este escenario haría 50 publicaciones separadas en Slack (cansino y consume 50 operations). Con aggregator, hace 1 sola publicación (limpio y consume solo 1 op del Slack al final).

Error handlers · manejo de fallos por ruta

En Make, cada módulo puede tener su propio error handler: una ruta alternativa que se ejecuta solo si ese módulo falla. Click derecho sobre el módulo → Add error handler. Tipos disponibles:

- Resume. Continúa el escenario con un valor por defecto que tú defines (útil si el fallo no es crítico).
- Commit. Marca la ejecución como exitosa pese al error. Solo en escenarios transaccionales.
- Rollback. Deshace lo hecho hasta ese punto.
- Break. Detiene el escenario y guarda el incomplete execution para reintentar después manualmente.
- Ignore. Continúa el flujo principal saltándose el módulo fallido.

Para escenarios críticos (cobros, sincronizaciones financieras), considera Break o Rollback con notificación a Slack. Para escenarios menos críticos (notificaciones, sincronizaciones de baja prioridad), Resume con valor por defecto suele bastar.

Data Stores · estado persistente sin base de datos

Una de las features distintivas de Make es Data Store: una pequeña base de datos integrada en la plataforma. Sirve para guardar datos entre ejecuciones sin tener que configurar nada externo. Ejemplos típicos:

- Llevar registro de «ya he procesado este email» para no duplicar trabajo.
- Mantener un contador entre ejecuciones (cuántos leads esta semana).
- Guardar un mapeo entre IDs externos e IDs internos.
- Cachear resultados costosos (una llamada LLM cara) para reutilizarlos.

Los Data Stores tienen tres operaciones esenciales: Add, Update, Search/Get. En el plan Free, el tamaño total de tu Data Store es limitado (unos MB), pero para casi cualquier uso de prototipo o pequeño negocio basta.

#### Señales de que necesitas algo externo

Data Store funciona bien hasta unos miles de registros. Para volúmenes mayores o queries complejas, conecta Make con Airtable, Notion (databases), Google Sheets, o una base de datos externa (Postgres, MongoDB) vía módulos específicos. Cuando llegas a este punto, replantéate también si el caso de uso es más natural en n8n con base de datos propia.

#### Ejercicio 2.2 · escenario con routers, iterator y aggregator

Construye un escenario que combine las tres herramientas: lógica condicional, iteración y agregación.

Escenario propuesto: «Cada mañana, leer los headlines de varios RSS feeds, filtrar por palabra clave, resumir y enviar a Slack/Telegram.»

1. Trigger. Schedule diario a las 8:00.
2. Módulo RSS · Retrieve RSS feed items. Usa un feed público (Hacker News, TechCrunch, Wired, etc.). Configura para traer las últimas 24h.
3. Iterator sobre los items del feed (si no llega ya iterado).
4. Router con dos rutas: 

- Ruta A · Filtro: el título o descripción contiene alguna palabra clave de tu interés (ej. «AI», «automation», «n8n», «LLM»).
- Ruta B · Filtro: por defecto, descartar (no hacer nada, no consume operations posteriores).
5. En la ruta A · Tools · Set variable formateando cada item como una línea «📰 [Título] · [URL]».
6. Text Aggregator uniendo todas las líneas que pasaron el filtro.
7. Módulo Slack/Telegram enviando el texto agregado como digest matinal.
8. Bonus: añade un Data Store «headlines_enviados» que guarde los URLs ya enviados, y antes del aggregator filtra los que ya estén en el Data Store, para no repetir noticias en días sucesivos.

RSS público recomendado para pruebas: `https://news.ycombinator.com/rss` (Hacker News) o `https://feeds.feedburner.com/TechCrunch`. Sin autenticación, sin límites prácticos.

¿Cómo distingo cuándo necesito Iterator y cuándo no?

Mira el output del módulo anterior. Si te muestra «Bundles» (lotes) numerados, ya está iterado y no necesitas Iterator. Si te muestra un único bundle con un array dentro, necesitas Iterator para desempaquetar. La duda se resuelve mirando el resultado de una ejecución de prueba.

¿Cuándo un router con filtros excluyentes y cuándo independientes?

Excluyentes (la opción «Stop processing after a route met its condition») cuando los casos son mutuamente exclusivos: facturas vs soporte vs otros. Independientes cuando un mismo item puede disparar varias acciones: ej. si es urgente avisar a Slack Y si es de cliente VIP avisar también al manager.

¿Hay forma de hacer loops con condición de salida tipo while?

Make no tiene un módulo while directo, pero se puede simular con la opción «Repeat» que repite el escenario tras finalizar, o con encadenamiento de escenarios. Para loops con lógica compleja de salida, este es uno de los puntos donde n8n con Code node es más natural.

¿Puedo ver cuántas operations consumió cada ejecución?

Sí. En el historial de ejecuciones (icono de reloj en el escenario), cada ejecución muestra el detalle de operations consumidas por cada módulo. Cuando optimizas para bajar consumo, este detalle es esencial: te dice exactamente dónde se te van las operations.

#### Sobre lógica avanzada en Make

- Make Help · Routers and filters. Documentación oficial detallada de routers, filtros y operadores. help.make.com/routers-and-filters
- Make Help · Iterators and aggregators. Cobertura completa de los módulos de iteración y agregación con ejemplos. help.make.com/iterators-and-aggregators
- Make Help · Data stores. Cómo crear, consultar y mantener data stores. help.make.com/data-stores
- Awesome Make · Community list. Recopilación open-source de escenarios, plantillas y trucos avanzados de la comunidad. github.com/topics/make-com

## Conectando IA con Make · OpenAI, Claude, Gemini

Módulos oficiales y HTTP genéricos para llamar a los LLMs grandes desde Make. Cuándo conviene cada modelo, gestión de prompts complejos, parseo de respuestas JSON, y construcción de un clasificador empresarial real.

#### Al final de esta lección sabrás:

- Conectar Make con OpenAI usando el módulo oficial.
- Llamar a Claude (Anthropic) y Gemini (Google) desde Make vía HTTP cuando no hay módulo oficial.
- Decidir qué modelo usar según el caso de uso (precio, latencia, calidad de razonamiento).
- Estructurar prompts para obtener salidas JSON parseables que el resto del escenario pueda usar.
- Construir un clasificador empresarial completo: entrada estructurada, decisión LLM, ruteo a sistemas distintos.

Módulo OpenAI oficial · el camino más directo

Make tiene un módulo oficial mantenido por su equipo: OpenAI (ChatGPT, Whisper, DALL-E). Lo encuentras buscando «openai» en el panel de módulos. Las operaciones más útiles para AI Engineering:

- Create a Completion (Chat). El equivalente al endpoint `/chat/completions` de OpenAI. Configuras modelo (gpt-4o, gpt-4o-mini, gpt-4-turbo, etc.), mensajes (system + user) y parámetros (temperature, max_tokens). Devuelve la respuesta del modelo lista para usar.
- Generate an Image (DALL-E). Para casos donde necesitas generar imágenes dentro del workflow.
- Create a Transcription (Whisper). Audio a texto. Útil para flujos que reciben mensajes de voz (Telegram, WhatsApp) y necesitan procesarlos.
- Create an Embedding. Genera embeddings de texto para búsqueda semántica. Lo veremos algo más en el SM4.

Para usar el módulo, necesitas tu API key de OpenAI:

1. Vete a platform.openai.com/api-keys.
2. Crea una nueva secret key (botón Create new secret key). Pon nombre descriptivo: «make-modulo-3».
3. Copia la key (empieza por `sk-...`). Solo se muestra una vez; guárdala en un lugar seguro.
4. En Make, al configurar el módulo OpenAI, te pedirá la API key en una Connection. Pégala, dale nombre, y queda guardada.

#### Lo que necesitas saber sobre coste de OpenAI

OpenAI suele dar un pequeño crédito inicial (típicamente 5 USD) a cuentas nuevas, que dura unos meses. Una vez agotado, necesitas cargar saldo con tarjeta para seguir usando la API. Las tarifas orientativas a 2026 son:

- gpt-4o-mini: el más barato. ~0,15 USD por millón de tokens de input, ~0,60 USD por millón de output. Excelente para clasificación, extracción y tareas simples.
- gpt-4o: el flagship. ~2,50 USD input, ~10 USD output por millón. Para razonamiento complejo o generación de calidad.
- o1-mini / o3-mini: modelos de razonamiento. Más caros pero excepcionales en problemas complejos paso a paso.

Para los ejercicios del módulo, el coste total no debería pasar de 1-2 USD. Si tu crédito inicial sigue, no necesitas cargar tarjeta. Comprueba siempre los precios actuales en openai.com/api/pricing antes de poner algo en producción.

Claude (Anthropic) vía HTTP · sin módulo oficial

Anthropic, la empresa detrás de Claude, todavía no tiene un módulo oficial en Make en el momento en que se escribe esta guía. La buena noticia es que su API es muy estándar y el módulo HTTP · Make a request de Make permite llamarla sin problemas.

Configuración del módulo HTTP para llamar a Claude:

URL: https://api.anthropic.com/v1/messages Method: POST Headers: x-api-key: tu_api_key_de_anthropic anthropic-version: 2023-06-01 content-type: application/json Body type: Raw, JSON (application/json) Body: { "model": "claude-haiku-4-5", "max_tokens": 1024, "system": "Eres un clasificador de mensajes...", "messages": [ {"role": "user", "content": "{{ aquí_el_input }}"} ] }

Output: Make recibe el JSON de respuesta de Anthropic y lo deja accesible para los siguientes módulos. El texto de respuesta está en `{{ content[0].text }}`.

Para obtener tu API key:

1. Crea cuenta en console.anthropic.com.
2. Sección «API keys», botón Create Key.
3. Anthropic suele dar un pequeño crédito gratis para nuevos desarrolladores (varía con el tiempo).

Gemini (Google) vía HTTP · alternativa con tier gratuito

Google Gemini tiene el tier gratuito más generoso del mercado a 2026: con Google AI Studio puedes hacer hasta 60 peticiones por minuto a Gemini Flash en el plan gratuito, suficiente para muchos casos prácticos sin pagar nada.

Configuración del módulo HTTP:

URL: https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=TU_API_KEY Method: POST Headers: content-type: application/json Body type: Raw, JSON Body: { "contents": [ { "parts": [ {"text": "Tu prompt aquí, system y user juntos"} ] } ] }

Output: el texto está en `{{ candidates[0].content.parts[0].text }}`.

Para obtener tu API key:

1. Vete a aistudio.google.com/app/apikey.
2. Genera una nueva key. Asóciala a un proyecto de Google Cloud si te lo pide (es gratis).
3. Listo. La key funciona inmediatamente.

Cuándo elegir cada modelo · guía práctica

| Caso de uso | Modelo recomendado | Por qué |
| --- | --- | --- |
| Clasificación simple | Gemini Flash / GPT-4o-mini / Claude Haiku | Cualquiera basta. Elige por precio o tier gratuito. |
| Extracción de datos estructurados | GPT-4o-mini con response_format JSON | El soporte JSON estructurado de OpenAI es muy fiable. |
| Razonamiento complejo | Claude Opus / GPT-4o / Gemini Pro | Modelos flagship. Más caros pero distinguen. |
| Generación de contenido largo | Claude (cualquier nivel) | Reputado por escribir bien y mantener tono. |
| Multimodal (imágenes + texto) | GPT-4o / Gemini Pro Vision / Claude Sonnet | Los tres lo soportan; Gemini es el más barato. |
| Volumen muy alto + bajo coste | Gemini Flash | Tier gratuito + barato cuando se paga. |
| Latencia mínima | Gemini Flash / Claude Haiku | Pensados para respuesta rápida. |

Obtener JSON parseable del LLM

Cuando el LLM forma parte de un workflow, casi siempre quieres que devuelva JSON estructurado que el resto de módulos pueda usar directamente. Tres técnicas para conseguirlo de forma fiable:

- Pedirlo explícitamente en el system prompt. «Devuelve únicamente un JSON con la estructura X. Sin texto adicional, sin explicaciones, sin markdown.»
- response_format JSON (OpenAI). En el módulo OpenAI puedes especificar response_format: `{"type": "json_object"}`. Te garantiza JSON válido sintácticamente.
- Structured outputs (OpenAI, también Anthropic). Especifica un schema exacto. El modelo se ajusta. Es el método más fiable pero requiere más configuración.

Una vez recibido el JSON, en Make lo parseas con el módulo Tools · Parse JSON que convierte el string en estructura accesible para los siguientes módulos.

#### Escenario empresarial completo end-to-end

Caso: empresa de software recibe tickets vía formulario web. Quiere automáticamente clasificar cada ticket (bug, feature request, billing, otros), priorizar (alta/media/baja), asignar al equipo correspondiente en Notion, y notificar a Slack si es prioridad alta.

Módulo 1 · Custom Webhook. Recibe ticket desde el formulario web. Payload: nombre, email, asunto, mensaje.

Módulo 2 · OpenAI · Create a Completion. Modelo gpt-4o-mini con response_format JSON. System:

Eres un clasificador de tickets de soporte. Analiza el mensaje y devuelve un JSON con: - categoria: "bug" | "feature" | "billing" | "otros" - prioridad: "alta" | "media" | "baja" - equipo_asignado: "tech" | "product" | "finance" | "general" - resumen_corto: una frase de máximo 100 caracteres Devuelve solo el JSON, sin texto adicional.

User prompt: «{{ webhook.body.asunto }} · {{ webhook.body.mensaje }}»

Módulo 3 · Tools · Parse JSON. Convierte el string de respuesta de OpenAI en estructura.

Módulo 4 · Notion · Create database item. Añade el ticket a la base de datos «Tickets» en Notion, con campos categoria, prioridad, equipo asignado, resumen, email del cliente, ticket completo.

Módulo 5 · Router con condición «prioridad = alta».

Módulo 6 (solo ruta alta) · Slack · Create a message. Posteo en el canal #soporte-urgente: «🚨 Ticket prioridad alta de {nombre}: {resumen_corto}. Ver en Notion: {url}».

Cinco minutos de trabajo humano que ahorra horas a la semana al equipo de soporte. Y todo dentro del plan Free de Make + crédito gratuito de OpenAI.

#### Ejercicio 2.3 · clasificador inteligente real

Tiempo estimado · 90-100 minutos

Construye un clasificador completo combinando webhook, LLM, parseo y ruteo. Adapta el caso a algo que te resulte útil personalmente.

1. Elige tu caso de uso. Algunos ejemplos: clasificador de tareas que recibes por email; clasificador de mensajes de Telegram; clasificador de respuestas de un formulario de Tally; cualquier otro flujo donde tengas texto entrante y quieras decisión automática.
2. Crea un escenario nuevo en Make con un Custom Webhook como trigger.
3. Diseña tu schema de clasificación: 3-5 categorías mutuamente excluyentes, un campo de prioridad (3 niveles), y al menos un campo de extracción adicional (entidad mencionada, urgencia, sentimiento, etc.).
4. Añade el módulo LLM. Elige uno: OpenAI (oficial), Claude (HTTP), Gemini (HTTP, tier gratuito). System prompt claro pidiendo JSON con tu schema. Si usas OpenAI, activa response_format JSON.
5. Añade módulo Parse JSON para procesar la respuesta.
6. Añade Router con al menos 2 rutas distintas según categoría o prioridad. Cada ruta hace algo diferente: guardar en Sheet, notificar Slack, crear tarea en Trello/Notion, enviar email automático, etc.
7. Prueba con 5-10 inputs reales y verifica que cada uno se ruta correctamente. Ajusta el system prompt si la clasificación falla en casos concretos.
8. Documenta tu escenario: anota qué hace, qué decisiones tomó el LLM, qué tasa de acierto observas. Esto te sirve para tu portfolio.

Si quieres exhibir esto en tu portfolio (CV, LinkedIn, futuras entrevistas), graba un mini vídeo de 60 segundos mostrando el escenario en acción y cuélgalo en YouTube no listado. Es la forma más efectiva de demostrar capacidad técnica real.

¿Cómo gestiono el coste si el LLM se dispara?

Tres palancas: (a) modelo más barato (Haiku, Flash, gpt-4o-mini); (b) max_tokens limitado (no dejes que el modelo escriba 4000 tokens si con 200 basta); (c) caché de respuestas para inputs repetidos usando Data Store de Make. Adicionalmente, para volúmenes serios, considera Gemini Flash gratuito hasta cierto cupo.

¿Y si el LLM devuelve JSON malformado a veces?

Pasa, sobre todo con prompts complejos. Estrategias: (1) activa response_format JSON en OpenAI, que garantiza JSON válido sintácticamente; (2) añade error handler al módulo Parse JSON para que en caso de fallo reintente con prompt más estricto; (3) revisa tu system prompt - normalmente la ambigüedad del prompt es la causa.

¿Puedo poner varias llamadas LLM en serie?

Sí, totalmente. El patrón «cadena de prompts» funciona muy bien en Make. Ejemplo: primer LLM clasifica, segundo LLM (solo si la categoría es X) genera respuesta personalizada, tercer LLM (opcional) verifica que la respuesta es apropiada antes de enviarla. Cada llamada es un módulo. Cuidado con el coste acumulado.

¿Make o n8n para flujos con muchos LLMs?

Si vas a hacer multi-agente serio (varios LLMs colaborando, con memoria persistente y herramientas), n8n con el nodo AI Agent es más natural. Lo veremos en el SM4. Para flujos lineales sencillos con uno o dos LLMs (clasificar + responder), Make funciona perfectamente y la interfaz es más amigable.

#### LLMs y APIs en automatización low-code

- OpenAI API Documentation. Documentación oficial de la API. La parte de Chat Completions y Structured Outputs es lo más relevante para automation. platform.openai.com/docs/api-reference/chat
- Anthropic API Documentation. Documentación completa de la API de Claude, incluyendo guías de prompt engineering específicas. docs.anthropic.com/en/api
- Google AI for Developers. Documentación de la API de Gemini con énfasis en el tier gratuito. ai.google.dev/docs
- Awesome LLM Apps. Repositorio open-source con casos de uso de LLMs integrados en workflows, incluyendo plantillas para Make y n8n. github.com/Shubhamsaboo/awesome-llm-apps

Fin del sub-módulo 2 · Sigue sub-módulo 3 · Docker y self-hosting

## Self-hosting de n8n con Docker

Sales del navegador y montas tu propia infraestructura. Docker en 90 minutos, n8n local con persistencia y, finalmente, despliegue en un VPS real con dominio propio y HTTPS automático.

 10 horas totales 3 lecciones 3 ejercicios prácticos Docker + VPS gratuito 

LECCIÓN 3.1· ~3 horas · Sub-módulo 3

## Docker básico · contenedores en 90 minutos

Qué es Docker, por qué importa para self-hosting, conceptos clave (imagen, contenedor, volumen, red), instalación en tu máquina y primeros comandos para levantar servicios reales en local.

#### Al final de esta lección sabrás:

- Explicar qué es un contenedor y cómo se distingue de una máquina virtual.
- Instalar Docker Desktop (Mac/Win) o Docker Engine (Linux) y verificar que funciona.
- Levantar tu primer contenedor con un solo comando y entender qué pasa.
- Diferenciar imagen, contenedor, volumen y red.
- Escribir un docker-compose.yml básico y entender qué hace cada bloque.

El problema que resuelve Docker

Antes de Docker, cuando querías ejecutar una aplicación en tu servidor pasaban dos cosas. Primero, tenías que instalar todas sus dependencias (versiones específicas de Python o Node, bases de datos, librerías del sistema). Segundo, esa instalación dependía de tu sistema operativo: lo que funcionaba en tu Mac no funcionaba igual en el servidor Ubuntu, y viceversa. Resultado: horas perdidas resolviendo el clásico «en mi máquina funciona».

Docker resuelve esto empaquetando una aplicación junto con todas sus dependencias en una unidad ejecutable llamada contenedor. Un contenedor incluye el código, las librerías, las variables de entorno, los archivos de configuración. Lo que hagas dentro de un contenedor se comporta igual en tu Mac que en Linux que en un servidor en la nube. Es portabilidad real.

#### Un contenedor es un proceso aislado, no una máquina virtual

Mucha gente confunde contenedores con máquinas virtuales (VMs). Las VMs simulan un ordenador entero (incluido su sistema operativo) sobre el tuyo: consumen mucho, son lentas de arrancar, ocupan gigas. Los contenedores comparten el kernel del sistema operativo huésped y solo aíslan procesos, sistema de archivos y red. Resultado: arrancan en segundos, ocupan megas, y puedes tener decenas corriendo a la vez. Por eso es realista que tu n8n, una base de datos PostgreSQL y un servidor web corran simultáneamente en un VPS pequeño de 5 €/mes.

Conceptos clave

- Imagen. Plantilla de solo lectura desde la que se crean contenedores. Es como una clase en programación: una receta. Ejemplo: la imagen `n8nio/n8n` contiene n8n listo para ejecutarse.
- Contenedor. Instancia ejecutándose de una imagen. Es como un objeto: una clase instanciada. De una misma imagen puedes crear varios contenedores corriendo a la vez.
- Volumen. Sistema para persistir datos fuera del contenedor. Sin volumen, todo lo que escriba un contenedor se pierde cuando se destruye. Con volumen, los datos sobreviven a reinicios y actualizaciones de la imagen.
- Red. Conexión virtual entre contenedores. Para que n8n hable con su base de datos PostgreSQL en otro contenedor, los pones en la misma red.
- Docker Hub. El registro público de imágenes oficiales. Como GitHub pero para contenedores. Aquí están las imágenes oficiales de n8n, postgres, redis, nginx, etc.
- docker-compose. Herramienta para definir y ejecutar aplicaciones multi-contenedor con un único archivo YAML. La forma profesional de orquestar dos o más contenedores (n8n + su base de datos, típicamente).

Instalación · paso a paso por sistema operativo

macOS y Windows: instala Docker Desktop desde docker.com/products/docker-desktop. Es gratuito para uso personal, educativo, y para pequeñas empresas (menos de 250 empleados y menos de 10 M USD anuales). Para empresas grandes, requiere licencia Docker Business.

Linux (Ubuntu/Debian): instala Docker Engine directamente sin la interfaz gráfica:

# Actualizar repositorios sudo apt update sudo apt install -y ca-certificates curl gnupg # Añadir clave oficial GPG de Docker sudo install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \ sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg # Añadir repositorio de Docker echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \ https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \ sudo tee /etc/apt/sources.list.d/docker.list # Instalar sudo apt update sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin # Habilitar uso sin sudo (cerrar y volver a abrir sesión después) sudo usermod -aG docker $USER

Verifica que funciona:

docker --version docker compose version docker run hello-world

Comandos básicos · los siete que vas a usar todos los días

- `docker run [imagen]`. Crea y arranca un contenedor a partir de una imagen. Si la imagen no la tienes localmente, la descarga automáticamente.
- `docker ps`. Lista los contenedores en ejecución. Con `-a` incluye también los detenidos.
- `docker stop [nombre]`. Detiene un contenedor.
- `docker rm [nombre]`. Elimina un contenedor detenido.
- `docker logs [nombre]`. Ver los logs de un contenedor. Con `-f` los ves en tiempo real (sale con Ctrl+C).
- `docker exec -it [nombre] sh`. Entrar al contenedor para inspeccionarlo desde dentro (como un SSH).
- `docker compose up -d`. Levantar todos los contenedores definidos en un docker-compose.yml en modo background.

#### Tu primer contenedor «útil» en 2 comandos

nginx es un servidor web. Vamos a levantar uno y servir una página de bienvenida en tu localhost:

# Levantar nginx en el puerto 8080 de tu máquina docker run -d -p 8080:80 --name mi-nginx nginx # Abre http://localhost:8080 en tu navegador # Verás la página "Welcome to nginx!" # Cuando te canses, para y limpia docker stop mi-nginx docker rm mi-nginx

Lo que ha pasado: Docker descargó la imagen oficial de nginx desde Docker Hub, creó un contenedor llamado mi-nginx, lo arrancó en modo background (`-d` = detached) y mapeó el puerto 80 del contenedor al puerto 8080 de tu máquina (`-p 8080:80`). Para levantar un servidor web has tardado segundos y no has instalado nada permanente en tu sistema.

docker-compose · cuando hay más de un contenedor

Cuando empiezas a tener dos o tres contenedores (típico: una app + su base de datos), pasar parámetros a `docker run` se vuelve tedioso. docker-compose te permite definir todo en un archivo YAML y arrancar/parar con un comando.

Ejemplo mínimo de `docker-compose.yml`:

services: nginx: image: nginx ports: - "8080:80" restart: unless-stopped

Y para levantarlo: `docker compose up -d` en el directorio donde está el archivo. Para pararlo: `docker compose down`. Para ver logs: `docker compose logs -f`. En la lección 3.2 escribiremos uno mucho más interesante para n8n con su base de datos.

#### Ejercicio 3.1 · primer contacto con Docker

Familiarízate con los comandos básicos. No hay que entender todo a la perfección, basta con que cojas soltura mecánica.

1. Instala Docker en tu sistema según las instrucciones de arriba. Verifica con `docker --version`.
2. Ejecuta `docker run hello-world`. Lee la salida: Docker te explica paso a paso lo que ha hecho.
3. Levanta nginx en localhost:8080 como en el ejemplo. Abre el navegador. Confirma que ves la página de bienvenida.
4. Inspecciona el contenedor: ejecuta `docker ps` (lo ves corriendo), `docker logs mi-nginx` (ves accesos), `docker exec -it mi-nginx sh` (entras dentro: prueba `ls` y `cat /etc/nginx/nginx.conf`, luego `exit`).
5. Modifica la página servida. Crea en tu máquina un archivo `index.html` con un texto cualquiera. Para el contenedor (`docker stop mi-nginx` y `docker rm mi-nginx`) y vuelve a arrancarlo montando el archivo como volumen: 

docker run -d -p 8080:80 \ -v $(pwd)/index.html:/usr/share/nginx/html/index.html \ --name mi-nginx nginx

 Recarga el navegador. Ahora ves tu página, no la de nginx por defecto.
6. Crea un docker-compose.yml que haga lo mismo (con el volumen del index.html). Para todo (`docker compose down`) y vuelve a levantarlo (`docker compose up -d`) para comprobar que funciona.
7. Limpieza final: `docker compose down` + `docker system prune -a` (con cuidado, esto borra todas las imágenes que no estés usando).

Si algún comando falla con permisos en Linux, asegúrate de haber añadido tu usuario al grupo docker y haber cerrado/abierto sesión. En Mac y Windows, asegúrate de que Docker Desktop esté abierto.

¿Docker Desktop es realmente gratis?

Para uso personal, educativo, open-source y pequeñas empresas (menos de 250 empleados y menos de 10 M USD anuales de facturación), sí, es completamente gratuito. Para empresas grandes requiere licencia Docker Business (~21 USD/usuario/mes). Si te molesta depender de la herramienta de pago aunque la uses gratis, en Linux puedes usar Docker Engine directamente sin Docker Desktop (es 100% open-source) y en Mac/Win hay alternativas como OrbStack, Colima o Podman Desktop.

¿Consume muchos recursos del ordenador?

Sí, especialmente Docker Desktop en Mac y Windows (que usa una pequeña VM Linux internamente). En Mac Apple Silicon, el consumo es razonable; en Windows con WSL2 también. En Linux nativo apenas se nota porque no hay capa intermedia. Para desarrollo local con 2-3 contenedores corriendo a la vez, un portátil moderno lo lleva sin problema.

¿Necesito saber Kubernetes después?

No para este módulo ni para automatizaciones de tamaño pequeño/medio. Kubernetes es para orquestar contenedores a escala (decenas, cientos, miles) en clusters de servidores. Para un n8n autohospedado en un VPS, docker-compose te basta. Saber Kubernetes es útil si vas a roles de plataforma/SRE, pero no es necesario para AI Engineering low-code.

¿Por qué dice «fair-code» n8n y no «open-source» a secas?

El código fuente está disponible, lo puedes leer, modificar, desplegar, contribuir. La única restricción es que no puedes vender n8n directamente como producto SaaS competidor a n8n cloud. A efectos prácticos del 99% de los usuarios (incluido tú), se comporta como software open-source: gratis para siempre, todo el control.

#### Docker desde cero, gratis

- Docker Documentation. Documentación oficial. La sección «Get started» es excelente para empezar. docs.docker.com/get-started
- Play with Docker. Entorno gratuito en navegador para practicar con Docker sin instalar nada. Sesiones de 4 horas. labs.play-with-docker.com
- Awesome Docker. Lista open-source en GitHub con recursos, herramientas y tutoriales de la comunidad. github.com/veggiemonk/awesome-docker
- Docker Curriculum. Curso gratuito comunitario muy bien valorado para principiantes. docker-curriculum.com

## n8n local con Docker

De n8n Cloud a tu máquina. Diferencias prácticas con la versión cloud, docker-compose listo para producción, persistencia, primer arranque, migración de workflows existentes y nodos comunitarios.

#### Al final de esta lección sabrás:

- Levantar n8n self-hosted en tu máquina con docker-compose y persistencia de datos.
- Configurar usuario administrador, password y zona horaria correctamente.
- Exportar workflows desde n8n Cloud e importarlos en tu instancia local.
- Instalar nodos community (extensiones de terceros) que no están en cloud.
- Saber cómo actualizar n8n a versiones nuevas sin perder workflows.

Cloud vs Self-Hosted · qué cambia

Lo que mantienes igual: la interfaz, los nodos, las expresiones, la mecánica de credenciales. Si supiste hacer un workflow en cloud, sabes hacerlo en self-hosted.

Lo que ganas con self-hosted:

- Ejecuciones ilimitadas. No hay cupo mensual. Puedes correr workflows cada segundo si quieres (y tu CPU aguanta).
- Workflows activos ilimitados. No hay límite de 5, 15 o el que sea.
- Nodos community. Extensiones desarrolladas por la comunidad que no están disponibles en cloud por motivos de seguridad.
- Control total de tus datos. Los datos que pasan por workflows nunca salen de tu servidor.
- Coste fijo y predecible. 5-10 €/mes de VPS + lo que consuman APIs externas. Sin sorpresas.

Lo que pierdes (que se puede recuperar pero requiere más trabajo):

- HTTPS automático. En cloud te viene gratis con dominio de n8n.cloud. En self-hosted tienes que configurarlo (lo veremos en L3.3).
- OAuth de un clic. En cloud los redirects OAuth funcionan automáticamente. En self-hosted tienes que configurar cada OAuth con la URL pública correcta.
- Backups automáticos. En cloud n8n los hace. En self-hosted los configuras tú.
- Soporte oficial. En cloud Pro tienes soporte por chat. En self-hosted, comunidad y documentación.

#### Empieza en local, después VPS

Para esta lección, monta n8n en tu propio ordenador. No necesitas comprar un servidor todavía: en tu Mac/PC/Linux es perfectamente válido para aprender, desarrollar y probar. En la lección 3.3 daremos el salto a VPS real con dominio propio. Si no consigues que funcione en local primero, no intentes saltarte al VPS directamente. Los problemas de configuración son más fáciles de debuggear en local.

docker-compose.yml mínimo funcional

Crea un directorio nuevo (por ejemplo `~/n8n-local`) y dentro un archivo `docker-compose.yml`:

services: n8n: image: docker.n8n.io/n8nio/n8n restart: unless-stopped ports: - "5678:5678" environment: - N8N_HOST=localhost - N8N_PORT=5678 - N8N_PROTOCOL=http - WEBHOOK_URL=http://localhost:5678/ - GENERIC_TIMEZONE=Europe/Madrid - TZ=Europe/Madrid volumes: - n8n_data:/home/node/.n8n volumes: n8n_data:

Y desde el terminal en ese directorio:

docker compose up -d docker compose logs -f n8n

La primera vez tarda 1-2 minutos en descargar la imagen. Cuando veas «Editor is now accessible via: http://localhost:5678/», abre esa URL en el navegador. La primera vez te pide crear el usuario administrador (email y password). Esos credenciales se guardan en el volumen `n8n_data`, así que sobreviven a reinicios.

Variables de entorno · las que importan al principio

- `N8N_HOST`. El hostname desde donde se va a acceder. En local, localhost. En VPS, tu dominio.
- `N8N_PORT`. Puerto interno. 5678 por defecto. No suele tocarse.
- `N8N_PROTOCOL`. http en local. https en VPS con SSL configurado.
- `WEBHOOK_URL`. URL pública completa. Crítica: si está mal, los webhooks no funcionan. En local: http://localhost:5678/.
- `GENERIC_TIMEZONE` y `TZ`. Zona horaria. Importante para los cron triggers.
- `N8N_BASIC_AUTH_ACTIVE`, `N8N_BASIC_AUTH_USER`, `N8N_BASIC_AUTH_PASSWORD`. Autenticación HTTP Basic antes de llegar a la interfaz. Opcional pero recomendable si expones a internet.
- `N8N_ENCRYPTION_KEY`. Clave para cifrar credenciales guardadas. Guárdala en algún sitio seguro: si la pierdes, perderás acceso a todas las credenciales almacenadas. Si no la pones, n8n genera una y la guarda en el volumen, pero si reconstruyes el volumen sin esa clave, perderás credenciales.

Persistencia · entender bien los volúmenes

En el docker-compose anterior, la línea `- n8n_data:/home/node/.n8n` hace que el directorio `/home/node/.n8n` dentro del contenedor (donde n8n guarda su base de datos SQLite con todos tus workflows, credenciales, ejecuciones) se monte sobre un volumen llamado n8n_data. Ese volumen vive fuera del contenedor.

Consecuencia: cuando paras el contenedor con `docker compose down`, el volumen sigue ahí. Cuando lo arrancas otra vez con `docker compose up -d`, n8n encuentra todos sus datos como los dejaste. Para hacer backup: copiar ese volumen. Para destruir todo: `docker compose down -v` (la -v borra los volúmenes asociados).

#### Cómo no perder lo construido en SM1 y SM2

n8n exporta e importa workflows en formato JSON, sin credenciales (por seguridad). El proceso:

1. Exportar desde Cloud. En tu n8n cloud, abre cada workflow. Menú superior derecho · «Download». Te descargas un `.json`.

2. Importar en local. En tu n8n local recién montado, panel lateral · botón «+» · «Import from File». Seleccionas el JSON. El workflow aparece tal cual estaba.

3. Reconfigurar credenciales. Las credenciales no se exportan. Para cada nodo que usaba OAuth o API keys, vuelve a configurarlas en local (panel Credentials). En local, OAuth puede ser más complicado porque las apps externas (Google, GitHub) no aceptan callbacks a localhost sin configuración previa. Trucos:

- Para OAuth con apps que sí aceptan localhost (Telegram bot tokens, API keys directas como OpenAI o Anthropic): funciona sin más.
- Para OAuth con apps quisquillosas (Google, Microsoft): te tocará usar un dominio público. Lo veremos en L3.3 con ngrok o despliegue en VPS.

4. Probar ejecuciones. Ejecuta los workflows migrados manualmente para asegurarte de que funcionan. Los webhooks ahora apuntan a tu localhost; si necesitas que algo externo los llame, requerirás ngrok o dominio público.

Nodos community · ampliar n8n

n8n self-hosted permite instalar nodos creados por la comunidad. Hay cientos: integraciones con apps menos comunes (Tally Forms, Plausible, Posthog), utilidades adicionales (PDF parser, OCR, audio processing) y nodos avanzados para IA. Para instalarlos:

1. En la interfaz, ve a Settings · Community nodes.
2. Pulsa Install a community node.
3. Pega el nombre del paquete npm. Por ejemplo: `n8n-nodes-pdf-parse` para parsear PDFs.
4. n8n descarga, instala y reinicia (toma unos segundos).

#### Cuidado con los nodos community en producción crítica

Los nodos community los desarrollan terceros, sin garantía oficial de n8n. La mayoría son fiables, pero conviene revisar el código en GitHub antes de instalar uno en un sistema que va a producción. Para experimentación y proyectos personales, sin problema. Para flujos críticos de cliente, evalúa caso a caso.

Actualizar n8n a versiones nuevas

n8n publica versiones cada semana o dos. Para actualizar tu instancia local:

cd ~/n8n-local docker compose pull # Descarga la última imagen docker compose down # Para el contenedor actual docker compose up -d # Arranca con la nueva imagen docker compose logs -f n8n # Verifica que arranca bien

Como los datos están en el volumen, persisten. La migración interna (si la hay) se ejecuta al arrancar. Si quieres fijar versión concreta (recomendable en producción para evitar sorpresas), cambia la imagen del compose:

image: docker.n8n.io/n8nio/n8n:1.115.0

#### Ejercicio 3.2 · n8n local con migración de workflows

Reconstruye en local el setup que tenías en cloud y verifica que todo funciona.

1. Crea el directorio `~/n8n-local` y dentro el `docker-compose.yml` del ejemplo.
2. Levanta n8n: `docker compose up -d` y abre http://localhost:5678. Crea usuario administrador.
3. Exporta tus 3 workflows del SM1 desde n8n Cloud (los del trial). Descarga los JSON.
4. Importa los 3 workflows en tu n8n local. Para cada uno, reconfigura las credenciales (API keys de OpenAI/Anthropic/Gemini, tokens de Telegram, etc.).
5. Ejecuta cada workflow manualmente y verifica que funciona como en cloud.
6. Instala un nodo community: ve a Settings · Community nodes e instala `n8n-nodes-pdf-parse`. Verifica que aparece como nodo disponible en el editor.
7. Para n8n con `docker compose down`. Confirma con `docker ps -a` que ya no está corriendo. Vuelve a arrancarlo con `docker compose up -d`. Verifica que tus workflows siguen ahí (persistencia funciona).
8. Bonus avanzado: añade al docker-compose una base de datos PostgreSQL como segundo servicio y configura n8n para usar Postgres en lugar de SQLite. Esto es lo que harías en producción real para rendimiento y robustez. Documentación oficial en docs.n8n.io/hosting/configuration/supported-databases-settings.

Si algún workflow no funciona tras la migración, casi siempre es por las URLs de webhook (cambiaron) o por OAuth (no configurado en local). Para OAuth con Gmail/Google, salta esta parte en local y déjala para cuando tengas dominio público en L3.3.

¿Puedo seguir usando n8n local cuando apago el ordenador?

No. n8n solo se ejecuta mientras Docker (y por tanto tu ordenador) esté encendido. Para automatizaciones 24/7 que se ejecuten incluso mientras duermes, necesitas un VPS (siguiente lección). En local va perfecto para desarrollo y workflows que tú dispares manualmente.

¿Cómo hago backup de mis workflows?

Tres opciones según seriedad. (1) Manual: exportar cada workflow como JSON periódicamente. (2) Backup del volumen Docker: `docker run --rm -v n8n-local_n8n_data:/data -v $(pwd):/backup alpine tar czf /backup/n8n-backup-$(date +%F).tar.gz -C /data .`. (3) Workflow de backup automático en el propio n8n: workflow que cada noche exporta todos los workflows a un GitHub o Google Drive.

¿Y si pierdo el password del usuario administrador?

Puedes resetear desde la línea de comandos: `docker compose exec n8n n8n user-management:reset [email protected]`. Eso genera un nuevo password temporal que verás en los logs. Cambia inmediatamente desde la interfaz tras entrar.

¿Es seguro exponer mi localhost a internet con ngrok para pruebas?

Sí pero con cuidado. ngrok te da una URL pública temporal que tunneliza a tu localhost. Útil para probar OAuth y recibir webhooks reales. Para uso temporal de desarrollo, perfecto. No lo uses como solución permanente: asegúrate de tener autenticación n8n activada y de cerrar ngrok cuando termines.

#### n8n self-hosted en detalle

- n8n Documentation · Docker. Guía oficial de instalación con Docker. Incluye opciones avanzadas (Postgres, queue mode, etc.). docs.n8n.io/hosting/installation/docker
- n8n Self-Hosted AI Starter Kit. Repo oficial que incluye n8n + Postgres + Qdrant + Ollama en docker-compose listo para usar. github.com/n8n-io/self-hosted-ai-starter-kit
- Awesome Selfhosted. Lista open-source enorme con software self-hostable, organizado por categoría. github.com/awesome-selfhosted/awesome-selfhosted
- n8n Community Nodes Registry. Catálogo oficial de nodos community con búsqueda. www.npmjs.com/search?q=n8n-nodes-

## Despliegue en VPS · Hetzner, DigitalOcean, Oracle Cloud

El último salto del SM3: tu n8n disponible 24/7 en internet con dominio propio y HTTPS automático. VPS gratuitos (Oracle), baratos (Hetzner) y con crédito (DigitalOcean), backups, actualizaciones y monitoreo.

#### Al final de esta lección sabrás:

- Elegir un proveedor VPS según presupuesto y necesidades.
- Conectar por SSH a un servidor remoto y aprovisionarlo desde cero.
- Desplegar n8n con docker-compose en un VPS.
- Configurar HTTPS automático con Caddy y dominio propio (DuckDNS gratis o uno comprado).
- Hacer backups automatizados y planificar actualizaciones sin downtime.

Por qué un VPS y no localhost

Localhost funciona para desarrollo pero tiene tres limitaciones obvias: tu ordenador se apaga, tu IP cambia, y nadie de fuera puede llamar a tus webhooks sin ngrok. Un VPS (Virtual Private Server) resuelve los tres problemas: está siempre encendido, tiene IP fija, es accesible desde internet. A cambio cuesta entre 0 y 10 €/mes según opción.

#### La opción más generosa que existe

Oracle Cloud ofrece 2 máquinas virtuales ARM Ampere A1 con 4 GB de RAM cada una, siempre gratis, sin caducidad. También 200 GB de disco entre las dos y 10 TB de tráfico mensual. Más que suficiente para n8n con varios workflows activos.

Pegas: el registro pide tarjeta de crédito (no se cobra nada, solo para verificar), Oracle limita disponibilidad de máquinas ARM en algunas regiones (a veces tienes que reintentar varios días), la interfaz es densa y no es la más amigable. Pero el precio es imbatible. Si tu objetivo es no gastar nada, esta es tu opción.

#### Buena para empezar sin compromiso

DigitalOcean ofrece 200 USD de crédito gratis durante 60 días a cuentas nuevas a través de su programa para developers. Un VPS básico (Droplet de 1 GB RAM, 25 GB SSD) cuesta 6 USD/mes, así que tienes para 33 meses gratis si solo necesitas uno. Interfaz muy clean, perfecta para aprender DevOps. Cuando se acabe el crédito, los 6 USD/mes son asequibles.

#### La opción de los profesionales europeos

Hetzner (alemana) no es gratuita pero es la opción más barata del mercado profesional: VPS de 2 vCPU + 4 GB RAM por ~4-5 €/mes. Datacenters en Alemania y Finlandia (relevante para GDPR). Sin trial, pago directo. La opción si decides invertir 50-60 €/año en infraestructura sólida.

#### Para casos específicos

Render y Railway tienen planes gratuitos limitados pero te abstraen del VPS. Son más caros que un VPS clásico cuando creces, pero útiles si quieres saltarte la curva de aprendizaje de SSH y servidor.

AWS, Google Cloud, Azure tienen tiers gratuitos generosos pero la complejidad inicial es alta. No los recomendamos para empezar; sí los aprenderás si vas a roles de plataforma.

Conexión SSH · acceder a tu servidor

Una vez creado el VPS (la mayoría de proveedores te dan un Ubuntu 24.04 LTS por defecto, que es lo que recomendamos), te proporcionan una IP pública y una forma de conectarte. Pasos básicos:

1. Genera una clave SSH en tu máquina (si no tienes ya):

ssh-keygen -t ed25519 -C " [email protected]" # Te pide ubicación (acepta la default) y passphrase (puedes dejarla vacía para testing) # Genera dos archivos: ~/.ssh/id_ed25519 (privada, NO compartir) # y ~/.ssh/id_ed25519.pub (pública, esta se sube) cat ~/.ssh/id_ed25519.pub # Copia el contenido completo

2. Añade la clave pública al VPS. La mayoría de proveedores te permite añadir claves SSH en el momento de crear el servidor, o copiar tu clave a un servidor existente con `ssh-copy-id usuario@ip-del-vps`.

3. Conecta:

ssh [email protected] # o si tu usuario por defecto es ubuntu ssh [email protected]

Aprovisionar el servidor · instalar Docker y básicos

Ya dentro del servidor, instala lo necesario:

# Actualizar paquetes sudo apt update && sudo apt upgrade -y # Instalar Docker (mismo proceso que vimos en L3.1) curl -fsSL https://get.docker.com | sudo sh sudo usermod -aG docker $USER # Crear un usuario no-root si estás como root adduser n8nuser usermod -aG docker,sudo n8nuser # Reconectar como ese usuario (más seguro que root para todo) exit ssh [email protected]

Dominio · gratis con DuckDNS o comprado

Para tener HTTPS funcionando, necesitas un dominio (o un subdominio). Dos opciones:

- Gratuita · DuckDNS. duckdns.org. Te da subdominios del tipo tunombre.duckdns.org gratis para siempre, apuntando a tu IP. Login con GitHub/Google, dos clics, listo. Suficiente para proyectos personales y aprendizaje.
- Comprado · Namecheap, Cloudflare Registrar, Porkbun. Dominios .com, .io, .dev, etc. desde ~10 €/año. Más profesional si vas a presentar el sistema a un cliente. Cloudflare Registrar vende dominios al precio de coste (sin margen) y es el más barato del mercado.

Configurar el dominio para apuntar a tu VPS: añade un registro A con valor igual a la IP del VPS. Espera unos minutos a que se propague (puedes verificar con `ping tudominio.com`).

HTTPS automático · Caddy es lo más simple

Caddy es un servidor web que obtiene y renueva certificados SSL de Let's Encrypt automáticamente. Sin configurar nada. Lo añadimos al docker-compose para que actúe de reverse proxy frente a n8n.

#### n8n + Caddy con HTTPS automático y dominio propio

En tu VPS, crea un directorio (`~/n8n`) y dentro estos dos archivos:

docker-compose.yml:

services: caddy: image: caddy:2 restart: unless-stopped ports: - "80:80" - "443:443" volumes: - ./Caddyfile:/etc/caddy/Caddyfile - caddy_data:/data - caddy_config:/config n8n: image: docker.n8n.io/n8nio/n8n restart: unless-stopped environment: - N8N_HOST=n8n.tudominio.com - N8N_PORT=5678 - N8N_PROTOCOL=https - NODE_ENV=production - WEBHOOK_URL=https://n8n.tudominio.com/ - GENERIC_TIMEZONE=Europe/Madrid - TZ=Europe/Madrid volumes: - n8n_data:/home/node/.n8n volumes: caddy_data: caddy_config: n8n_data:

Caddyfile (sin extensión):

n8n.tudominio.com { reverse_proxy n8n:5678 }

Y arranca: `docker compose up -d`. Caddy detecta el dominio, contacta con Let's Encrypt, obtiene el certificado, configura HTTPS y empieza a servir n8n protegido. Todo en menos de un minuto.

Abre `https://n8n.tudominio.com` en el navegador. Crea tu usuario administrador. Ya tienes n8n en producción real, con HTTPS válido, 24/7.

Backups · automatizados con cron

En producción, perder los workflows por un fallo es inadmisible. Setup mínimo de backups:

Haz el script ejecutable: `chmod +x backup-n8n.sh`. Programa con cron:

crontab -e # Añade esta línea para ejecutar todos los días a las 3 AM: 0 3 * * * /home/n8nuser/backup-n8n.sh

Para backups offsite (en otro lugar, por si el VPS se va al traste), añade al final del script un `rclone copy` a un Google Drive personal o Backblaze B2 (10 GB gratis para siempre, mucho más que suficiente para tu base de datos n8n) o cualquier S3 compatible.

Monitoreo · saber si se ha caído

Setup mínimo de alerta gratuita:

- UptimeRobot (uptimerobot.com). Plan gratuito te permite monitorizar 50 endpoints cada 5 minutos. Te avisa por email/Slack/Telegram si n8n.tudominio.com deja de responder. Setup: 2 minutos.
- Logs en directo: `docker compose logs -f n8n` cuando algo no funciona. Para sentirte cómodo, hazlo una vez al día durante la primera semana de despliegue.

Actualizaciones · sin perder el sueño

Mismo patrón que en local: `docker compose pull && docker compose down && docker compose up -d`. En producción, hazlo en horario de bajo tráfico (madrugada, fin de semana) y con un backup justo antes. Conviene fijar la versión exacta de n8n en lugar de usar la última automáticamente, así controlas cuándo subes.

#### Ejercicio 3.3 · n8n en VPS con dominio y HTTPS

El proyecto más ambicioso del módulo hasta ahora. Si lo terminas, has hecho un despliegue real de producción end-to-end.

1. Crea cuenta en uno de los proveedores VPS: Oracle Cloud Free Tier (recomendado si quieres gratis), DigitalOcean (con su crédito), o Hetzner si decides pagar.
2. Crea un VPS Ubuntu 24.04 LTS con 2-4 GB de RAM. Añade tu clave SSH durante la creación.
3. Conecta por SSH y actualiza el sistema. Crea un usuario no-root.
4. Instala Docker con el script oficial.
5. Configura un dominio: o registras gratis en DuckDNS o usas uno comprado. Apunta un registro A a la IP del VPS.
6. Crea el docker-compose.yml y el Caddyfile del ejemplo, sustituyendo el dominio.
7. Levanta n8n: `docker compose up -d`. Mira los logs y espera a que Caddy emita el certificado (~30-60 segundos).
8. Accede a https://tudominio.com. Crea usuario administrador.
9. Migra los workflows del SM2 (los del ejercicio 2.3 o equivalente) desde n8n cloud a tu instancia VPS. Reconfigura credenciales. Verifica que webhooks funcionan llamándolos desde fuera (con curl o reqbin).
10. Configura el script de backup y prográmalo con cron. Verifica al día siguiente que el archivo del backup existe.
11. Configura UptimeRobot apuntando a tu dominio. Comprueba que recibes alerta cuando paras manualmente n8n y otra cuando lo vuelves a levantar.

¿Qué tamaño de VPS necesito para n8n?

Para uso personal y profesional con docenas de workflows activos, 2 GB de RAM y 1 vCPU es suficiente (de hecho excesivo). 4 GB con 2 vCPUs te da margen para varios servicios extra (Postgres, Redis, otro stack). Solo si pones esto a procesar miles de ejecuciones por minuto necesitas algo más grande. Empieza pequeño y escala cuando lo notes.

¿Es seguro tener n8n expuesto a internet?

Con buenas prácticas, sí. Pasos esenciales: (1) usuario administrador con password fuerte; (2) activar `N8N_BASIC_AUTH` con segundo nivel de protección; (3) tener Caddy actualizado; (4) limitar IPs si solo tú accedes (firewall del VPS); (5) backups regulares; (6) actualizar n8n periódicamente. Para casos muy sensibles, considera VPN o tunnel privado (Tailscale, Cloudflare Tunnel).

¿Cómo cambio de Cloud a Self-Hosted sin perder histórico?

Los workflows se migran exportando/importando JSON (ya lo viste en L3.2). El histórico de ejecuciones no se migra: queda en cloud. Para casos profesionales donde el histórico importa, exporta las ejecuciones críticas a CSV o S3 antes de cancelar n8n cloud.

¿Y si el VPS se cae y pierdo todo?

Por eso los backups son críticos. Con tu script de backup diario + copia offsite (Backblaze B2 gratis), aunque pierdas el VPS entero puedes restaurarlo en otro proveedor en menos de 30 minutos: aprovisionas VPS nuevo, instalas Docker, restauras volumen desde backup, levantas docker-compose. Pruébalo al menos una vez para tener confianza en el procedimiento.

#### Self-hosting profesional y DevOps básico

- Oracle Cloud Free Tier · documentación oficial. Setup de la máquina ARM Ampere gratuita siempre. oracle.com/cloud/free
- Caddy Documentation. El servidor web con HTTPS automático que usamos. Documentación muy bien escrita. caddyserver.com/docs
- Awesome Self-Hosted. Recursos masivos sobre cómo hostear tus propios servicios. github.com/awesome-selfhosted/awesome-selfhosted
- n8n · Production setup guide. Documentación oficial específica para producción. docs.n8n.io/hosting/installation/server-setups

## Multi-agent workflows low-code

El último paso: orquestar varios LLMs colaborando en un mismo workflow. Patrones de multi-agente, conexión de varios modelos en paralelo o secuencia, memoria persistente, y un proyecto final integrador que combina todo el módulo.

 10 horas totales 4 lecciones 4 ejercicios prácticos Proyecto final integrador 

## Qué es un multi-agent system

Definición, patrones clásicos (orquestador-trabajadores, debate, refinamiento iterativo, router-experts), por qué low-code encaja bien con multi-agente, riesgos a tener en cuenta y diseño en papel antes de construir nada.

#### Al final de esta lección sabrás:

- Definir qué es un multi-agent system y cómo se distingue de una llamada simple a un LLM.
- Reconocer los cuatro patrones más comunes: orquestador-trabajadores, debate, refinamiento iterativo y router-experts.
- Argumentar por qué low-code es buena opción para construir multi-agentes (al menos para los primeros).
- Anticipar los tres riesgos principales: latencia acumulada, coste acumulado y dificultad de evaluación.
- Diseñar en papel un sistema multi-agente para un caso concreto antes de tocar n8n o Make.

La idea central

Hasta ahora, en el módulo, hemos hecho una llamada a un LLM por workflow. El modelo recibe un prompt, devuelve una respuesta, y el resto del workflow procesa esa respuesta. Eso funciona muy bien para tareas concretas (clasificar, extraer, resumir), pero se queda corto cuando la tarea requiere razonamiento por fases.

Un multi-agent system es un workflow donde varias llamadas a LLMs colaboran para resolver un problema más grande. Cada llamada juega un rol concreto: una clasifica, otra investiga, otra redacta, otra revisa. El conjunto produce mejores resultados que un único LLM intentando hacerlo todo en una llamada gigante.

#### Agente vs llamada simple vs multi-agente

Llamada simple a un LLM: una pregunta, una respuesta. Lo que hemos hecho hasta ahora.

Agente (singular): un LLM con herramientas (tools) que puede llamar para enriquecer su respuesta (buscar en web, leer una base de datos, ejecutar código). El LLM decide cuándo usar cada herramienta. n8n tiene un nodo nativo llamado AI Agent para esto.

Multi-agente: varios agentes (o varias llamadas a LLM) coordinados para resolver un problema en pasos sucesivos. Cada uno tiene rol especializado. El workflow orquesta el flujo entre ellos.

La distinción importa porque la mayoría de problemas reales se resuelven mejor con multi-agente que con un único agente megalómano. Dividir y especializar suele ganar.

Cuatro patrones que cubren la mayoría de casos

1 · Orquestador-trabajadores (orchestrator-workers). Un primer LLM (el orquestador) recibe la tarea, la divide en sub-tareas y decide a qué agentes asignar cada parte. Los trabajadores ejecutan sus sub-tareas en paralelo o en secuencia. Un agente final consolida los resultados. Útil para tareas que tienen partes naturales bien definidas (investigar un tema con varias dimensiones, redactar un informe con varias secciones).

2 · Debate (multi-agent debate). Dos o más LLMs discuten entre sí sobre la misma pregunta. Cada uno argumenta, refuta al otro, y al final un tercer LLM (juez) decide. Útil para preguntas con respuesta no obvia donde múltiples perspectivas mejoran la calidad. Coste alto en tokens; reservarlo para casos donde la calidad justifica el coste.

3 · Refinamiento iterativo (refine). Un primer LLM produce un borrador. Un segundo LLM (con prompt distinto, normalmente más crítico) lo revisa y propone mejoras. El primero corrige basándose en la crítica. Iteras 2-3 veces. Util para redacción de calidad o código.

4 · Router-experts (mixture of experts a mano). Un primer LLM clasifica la entrada y decide qué «experto» (otro LLM con prompt especializado) debe procesarla. Por ejemplo, en un chatbot de empresa: un router decide si la consulta es de soporte técnico, comercial, o legal, y rutea al LLM especializado en cada área. Es lo más cercano al patrón switch + nodos que has usado en SM1 y SM2.

#### Tarea: «Redacta un email comercial respondiendo a esta consulta de un lead»

Versión simple (sin multi-agente): un único LLM con un prompt grande recibe consulta + tono deseado + contexto y devuelve email. Funciona, pero a veces sale plano o se le escapan matices.

Versión orquestador-trabajadores: LLM1 clasifica la consulta y extrae los puntos a abordar. LLM2 redacta el cuerpo del email. LLM3 propone asunto. LLM4 ajusta el tono final. Resultado más sólido, 4× más llamadas, 4× más coste y latencia.

Versión refinamiento: LLM1 redacta borrador. LLM2 lo revisa con prompt crítico («busca elementos genéricos, jerga vacía, frases sin valor concreto»). LLM1 corrige. Salida final mucho mejor que el borrador inicial.

Versión router-experts: LLM1 detecta tipo de consulta (precio, demo, soporte, otra). Según el tipo, llama a LLM2A (redactor especializado en precio), LLM2B (redactor de demos), etc. Cada experto está finamente afinado en su escenario y produce respuestas más naturales en su nicho.

La pregunta no es «¿cuál es mejor?» sino «¿cuál encaja con mi caso?». Para consultas muy variadas en tono y contenido, router-experts. Para emails con un patrón común que solo necesita pulido, refinamiento. Para flujos complejos con muchas piezas, orquestador-trabajadores.

Por qué low-code encaja con multi-agente

Construir un sistema multi-agente en código a pelo (Python con LangChain o LangGraph) tiene curva de aprendizaje considerable. La coordinación entre agentes, el paso de mensajes, el manejo de errores en cada paso, la memoria compartida: todo eso lo escribes tú. En low-code, gran parte de esa orquestación es visual: ves el flujo, lo entiendes a la primera, lo modificas sin tocar código.

Tres ventajas concretas:

- Visualización clara. Cada agente es un nodo o un grupo de nodos. La línea entre dos nodos es literalmente la conexión entre dos agentes. Para depurar, miras el flujo. Para explicar a un cliente o a un compañero, le enseñas la imagen.
- Iteración rápida. Cambiar el orden de los agentes, añadir un paso intermedio, sustituir un LLM por otro, es cuestión de minutos. En código son horas de refactor.
- Debug nodo a nodo. Si el sistema falla, identificas qué agente falló y miras su input/output exacto. No tienes que recorrer un stack trace.

Limitación a tener clara: para sistemas con muchos agentes (más de 6-8), bucles complejos o lógica de control muy fina, low-code se queda corto y conviene pasar a frameworks como LangGraph en código. Pero los primeros multi-agentes prácticamente siempre encajan bien en n8n o Make.

Tres riesgos a tener en cuenta

Riesgo 1 · Latencia acumulada. Cada llamada LLM tarda entre 1 y 15 segundos según modelo. Un workflow con 4 llamadas en secuencia tarda 4-60 segundos. Si el usuario espera una respuesta inmediata (chat, webhook síncrono), esto es problema. Mitigaciones: paralelizar agentes que no dependan entre sí; usar modelos más rápidos (Haiku, Flash) donde la calidad lo permita; mostrar estados intermedios al usuario.

Riesgo 2 · Coste acumulado. Si un workflow simple cuesta 0,001 USD, uno multi-agente con 5 llamadas cuesta 0,005 USD por ejecución. Con 10.000 ejecuciones al mes, son 50 USD. Y el coste crece rápido si usas modelos grandes en cada paso. Mitigaciones: clasificadores baratos primero (Haiku, Flash), modelo grande solo donde realmente hace falta; cachear respuestas a inputs repetidos; limitar max_tokens.

Riesgo 3 · Dificultad de evaluación. Cuando un workflow tiene una sola llamada, comprobar que «funciona» es directo: pruebas inputs y ves outputs. Con varias llamadas encadenadas, identificar dónde falla es más complicado y los errores se propagan. Mitigación principal: añadir logs intermedios en cada agente (en n8n se ve por defecto en Executions; en Make en historial de ejecuciones) para poder revisar qué decidió cada uno.

#### Ejercicio 4.1 · diseño en papel de tu sistema multi-agente

Antes de construir nada, vas a diseñar el sistema completo. La calidad del diseño determinará la del resultado.

1. Recupera el flujo que identificaste en el ejercicio 1.1 como tu candidato a proyecto. Si entonces era muy abstracto, concrétalo ahora a algo ejecutable.
2. Decide qué patrón usa tu sistema: orquestador-trabajadores, debate, refinamiento, o router-experts. Justifica la elección en una frase.
3. Enumera los agentes (entre 2 y 5 para un primer multi-agente). Para cada uno, anota: nombre, rol exacto, input que recibe, output que produce, modelo recomendado (Haiku/Flash si tarea simple, Sonnet/4o/Pro si requiere razonamiento).
4. Dibuja el flujo en papel o herramienta gráfica simple (Excalidraw, Miro, una hoja A4 y bolígrafo). Las flechas indican paso de información; etiqueta cada flecha con qué viaja en ella.
5. Anticipa los errores: ¿qué pasa si el agente 1 falla? ¿Qué pasa si el agente 2 devuelve algo inesperado? ¿Tienes plan B para cada paso?
6. Estima coste y latencia: cuántos tokens en total, cuántos segundos. Si supera tu umbral aceptable, simplifica.

Mantén el primer multi-agente simple y honesto: dos o tres agentes encadenados con un patrón claro. Resiste la tentación de meter siete agentes en debate iterativo: lo más probable es que no llegues a hacerlo funcionar bien. Mejor un sistema pequeño que funcione perfectamente que uno grande que casi.

¿Multi-agente siempre es mejor que un único LLM bien promptado?

No. A veces un único LLM con un prompt cuidadosamente diseñado supera a un sistema multi-agente mal estructurado. Multi-agente brilla cuando: (a) la tarea tiene fases naturales y distintas; (b) cada fase requiere optimizaciones diferentes; (c) el coste de equivocarse en una fase compensa la inversión en validación separada. Para muchas tareas, un prompt bien hecho a Claude Sonnet o GPT-4o es suficiente.

¿Puedo mezclar modelos de proveedores distintos en un mismo sistema?

Sí, y es buena práctica. Patrón habitual: clasificador rápido con Gemini Flash o Claude Haiku, razonamiento principal con Claude Sonnet o GPT-4o, generación creativa con Claude (por su estilo), verificaciones rápidas con modelos pequeños. Cada proveedor tiene fortalezas distintas; aprovecharlas conjuntamente te da lo mejor de cada uno.

¿Cómo evalúo si mi multi-agente «funciona bien»?

Tres niveles. (1) Funcional: para 10-20 inputs representativos, comprueba manualmente que el output es razonable. (2) Comparativo: pasa los mismos inputs por una versión single-LLM y compara cualitativamente con la versión multi-agente. (3) Métrica concreta: si tu sistema clasifica, calcula precisión sobre un set etiquetado; si redacta, pide a un tercer LLM independiente que puntúe los resultados de 1 a 5.

¿Cuándo conviene saltar de n8n a LangGraph o frameworks similares?

Cuando tu sistema necesita: bucles complejos basados en condiciones del LLM, control fino sobre estado compartido entre muchos agentes, integración con tooling avanzado de evaluación (LangSmith, etc.), o despliegue como microservicio independiente con APIs especializadas. Para el 80% de los multi-agentes prácticos, n8n con su nodo AI Agent es suficiente y mucho más rápido de construir.

#### Sobre multi-agente y patrones de orquestación

- Anthropic · Building Effective Agents. Guía oficial open-access de Anthropic con los patrones de agentes y multi-agentes mejor documentados. Lectura imprescindible. anthropic.com/research/building-effective-agents
- n8n AI Agent · Documentation. Documentación específica del nodo AI Agent de n8n y de cómo orquestar varios agentes en un workflow. docs.n8n.io/advanced-ai/intro-tutorial
- Awesome LLM Agents. Lista open-source en GitHub con frameworks, papers y ejemplos de agentes y multi-agentes. github.com/kyrolabs/awesome-langchain
- Multi-Agent Collaboration · LangChain. Documentación abierta de LangChain sobre patrones de colaboración entre agentes. Conceptualmente útil aunque después lo implementes en n8n. python.langchain.com/docs/use_cases/multi_agent

## Conectar varios LLMs en un workflow

El nodo AI Agent de n8n en profundidad, varias llamadas LLM en paralelo y en serie, Make con OpenAI y Claude en el mismo escenario, y guía práctica de qué modelo usar para qué tarea.

#### Al final de esta lección sabrás:

- Usar el nodo AI Agent de n8n para construir agentes con herramientas.
- Encadenar múltiples llamadas LLM en serie y en paralelo dentro de un mismo workflow.
- Combinar modelos de proveedores distintos (Claude + GPT + Gemini) en un escenario de Make.
- Elegir conscientemente qué modelo usar para cada rol del sistema multi-agente.

El nodo AI Agent de n8n

n8n tiene un nodo especial llamado AI Agent que es exactamente el «agente con herramientas» que vimos en la lección anterior. Le configuras: un modelo (Chat Model), opcionalmente una memoria (Memory), y opcionalmente herramientas (Tools). El nodo gestiona internamente el bucle de razonamiento: el LLM decide qué herramienta usar, recibe el resultado, decide si llamar otra, hasta que tiene respuesta final.

Estructura típica de un AI Agent en n8n:

- AI Agent (el nodo principal). Recibe el input y produce el output final.
- Chat Model: conectado por debajo del agente. Es el LLM concreto que «piensa». Puedes elegir OpenAI Chat Model, Anthropic Chat Model, Google Gemini, etc.
- Memory: opcional. Si quieres que el agente recuerde la conversación entre llamadas. Lo veremos en L4.3.
- Tools: opcional, una o varias. Cada herramienta es básicamente otro nodo de n8n (HTTP Request a una API, consulta a base de datos, búsqueda en Notion, llamada a otro workflow). El agente decide cuándo usar cada una.

#### La pregunta clave

Usa el nodo AI Agent cuando: el LLM debe decidir dinámicamente qué herramientas usar y en qué orden; necesitas memoria conversacional; el input es una pregunta abierta donde el modelo razona iterativamente.

Usa varias llamadas LLM separadas (nodos Chat Model independientes conectados secuencialmente) cuando: el flujo es predecible (siempre los mismos pasos); quieres control total sobre qué LLM se llama en cada momento; los costes y la latencia importan mucho y quieres optimizar paso a paso.

En la práctica profesional, los workflows más sólidos combinan ambos: agentes con herramientas para las partes que requieren razonamiento, llamadas directas para las partes deterministas.

Encadenamiento en serie · varias llamadas secuenciales

El patrón más sencillo: el output de un LLM alimenta el prompt del siguiente. En n8n simplemente conectas un nodo Chat Model tras otro, pasando datos entre ellos con expresiones.

#### Workflow: «Recibir queja de cliente, redactar respuesta, revisar tono»

Nodo 1 · Webhook. Recibe la queja: `{ "queja": "Llevo 3 semanas esperando..." }`.

Nodo 2 · Anthropic Chat Model (Claude Sonnet). System: «Eres responsable de atención al cliente. Recibes una queja y redactas una respuesta profesional, empática y con compromiso concreto. Devuelves solo el texto de la respuesta». User: `{{ $json.body.queja }}`.

Nodo 3 · Anthropic Chat Model (Claude Haiku). System: «Eres un revisor de tono. Recibes una respuesta a una queja y la revisas buscando: tono condescendiente, vaguedades como 'haremos lo posible', compromisos sin fecha. Si encuentras alguno, lo reescribes; si no, devuelves la respuesta tal cual. Devuelves solo el texto final.» User: `{{ $('Nodo 2').item.json.message.content }}`.

Nodo 4 · Respond to Webhook. Devuelve la respuesta revisada al sistema que llamó.

Resultado: una respuesta de mayor calidad que la primera, con un revisor barato (Haiku) que captura los errores típicos. Coste total por ejecución: céntimos. Latencia: 5-15 segundos.

Llamadas en paralelo · dividir y consolidar

Cuando varios agentes pueden trabajar en paralelo (no dependen del output de otro), conviene lanzarlos a la vez para reducir latencia. En n8n esto se hace conectando varios nodos Chat Model en paralelo desde un mismo nodo previo, y luego juntando los resultados con un Merge.

#### Workflow: «Analizar un email comercial desde 3 ángulos en paralelo»

Nodo 1 · Webhook. Recibe email.

Nodos 2A, 2B, 2C en paralelo:

- 2A · LLM con system «Analiza el sentimiento del cliente en este email».
- 2B · LLM con system «Detecta urgencia (alta/media/baja) en este email».
- 2C · LLM con system «Extrae 3 entidades mencionadas (productos, fechas, personas)».

Nodo 3 · Merge (en modo Combine). Junta los tres resultados en un único item con los tres análisis.

Nodo 4 · Edit Fields. Construye el JSON final con todos los campos consolidados.

Tres llamadas se ejecutan a la vez en lugar de secuencialmente. Si cada una tarda 3 segundos, latencia total ~3s en paralelo vs ~9s en serie. El coste total es el mismo, pero la experiencia mejora notablemente.

Combinación de proveedores · cada modelo en su rol

Una de las decisiones más relevantes en un multi-agente es qué modelo usar para qué rol. Recomendaciones basadas en uso real a fecha de 2026:

| Rol en el sistema | Modelo recomendado | Razón |
| --- | --- | --- |
| Clasificación rápida / router | Gemini Flash · Claude Haiku · GPT-4o-mini | Más baratos, más rápidos. La precisión suele bastar. |
| Razonamiento complejo (orquestador) | Claude Sonnet · GPT-4o | Mejor razonamiento. Justifican el coste si la decisión es importante. |
| Redacción de calidad | Claude (cualquier nivel) | Reputado por tono natural y matiz. |
| Tareas con muchas herramientas (agente) | GPT-4o · Claude Sonnet | Buen function calling, razonamiento iterativo fiable. |
| Generación masiva (muchos outputs) | Gemini Flash · Claude Haiku | Coste por token bajo permite volumen alto. |
| Tareas de revisión / crítica | Claude Haiku · GPT-4o-mini | Suficiente capacidad para detectar errores típicos. |
| Razonamiento paso a paso explícito | o1-mini · o3-mini | Diseñados para razonamiento en cadena. |
| Multimodal (imagen + texto) | Gemini Pro · GPT-4o · Claude Sonnet | Todos soportan; Gemini es el más barato. |

Make multi-agente · varios módulos LLM en un escenario

En Make el patrón es similar pero con la sintaxis propia de la plataforma:

- OpenAI via módulo oficial.
- Claude via módulo HTTP (URL `https://api.anthropic.com/v1/messages`).
- Gemini via módulo HTTP (URL `generativelanguage.googleapis.com/v1beta/...`).

Para hacer llamadas paralelas en Make, usa un Router con tres ramas sin filtros (todas se ejecutan), cada una con su llamada LLM, y al final un Array Aggregator que junta los outputs. Funciona pero es más visual que en n8n. Para sistemas multi-agente complejos, n8n suele ser más cómodo.

#### Ejercicio 4.2 · workflow con dos LLMs colaborando

Construye un workflow con al menos dos llamadas LLM cooperando en un caso real. Usa tu n8n self-hosted del SM3 (o cloud si todavía estás en cloud).

1. Caso sugerido (puedes adaptarlo): «Analizador de noticias». Webhook que recibe el link de una noticia. Primer LLM: clasifica la noticia en una categoría temática y extrae el headline limpio. Segundo LLM: redacta un resumen de 2 frases para Slack. Tercer paso (opcional): publica en un canal de Slack o lo guarda en Notion.
2. Webhook trigger recibiendo URL. Si quieres saltarte la parte de descargar la página, asume que llega el texto ya extraído.
3. LLM 1 · Clasificador con un modelo barato (Haiku o Flash). System: «Clasifica el texto recibido en una de estas categorías: tecnología, política, economía, deporte, cultura, otros. Devuelve solo el nombre de la categoría».
4. LLM 2 · Resumidor con un modelo de calidad (Claude Sonnet o GPT-4o). System: «Resume el texto en exactamente 2 frases claras y atractivas para publicar en Slack. Sin emoji, sin markdown, español de España».
5. Edit Fields para componer el output final: categoría, resumen, URL original, timestamp.
6. Respond to Webhook con ese objeto o, alternativa, módulo Slack que publica directamente.
7. Prueba con 5 URLs reales de noticias variadas. Verifica que cada paso funciona correctamente. Mira el output intermedio de cada LLM en Executions.
8. Bonus: añade un tercer LLM revisor que verifica que el resumen no contiene frases vagas («un evento importante», «implicaciones significativas») y si las encuentra, regenera el resumen pidiendo al LLM 2 que sea más concreto.

Aprovecha esta lección para experimentar con la mezcla de modelos. Usa Gemini Flash en el clasificador (tier gratuito generoso), Claude Sonnet o GPT-4o en el resumidor, Haiku en el revisor. Verás en la práctica las diferencias de tono y precisión entre proveedores.

Preguntas frecuentes

¿Es muy complicado usar el nodo AI Agent comparado con un Chat Model directo?

Conceptualmente sí: tienes que entender el bucle herramientas-razonamiento-más herramientas. La buena noticia es que para muchos casos no necesitas el AI Agent: un Chat Model directo con prompt cuidadoso basta. Reserva AI Agent para cuando quieras que el LLM decida dinámicamente qué herramientas usar, no cuando el flujo es predecible.

¿Las llamadas en paralelo cuestan más que en serie?

No, el coste total en tokens es el mismo independientemente del orden. La diferencia es de tiempo de espera para el usuario final. Lo que sí varía es el «mantenimiento mental»: workflows en paralelo son ligeramente más difíciles de debuggear porque las ejecuciones ocurren a la vez.

¿Cómo sé si un caso requiere multi-agente o un buen prompt basta?

Empieza siempre con un buen prompt single-LLM. Si no da la calidad que necesitas tras varios intentos de mejorar el prompt, divide la tarea en sub-tareas naturales y pasa a multi-agente. La regla práctica: «si puedes describir la tarea como un proceso en pasos claros, multi-agente probablemente ayudará». Si es una transformación atómica («clasifica esto»), un prompt basta.

¿Y si quiero que un LLM llame a otro LLM dentro de su razonamiento?

Es exactamente el patrón AI Agent con un tool que es otro workflow. En n8n: creas un sub-workflow que contiene la llamada al segundo LLM, lo expones como herramienta del agente. El agente, en su bucle, puede decidir invocarlo. Es muy potente pero también más complejo de depurar; déjalo para cuando domines los patrones más simples.

#### Orquestación de varios LLMs en workflows

- n8n AI · Tutorial completo. Documentación oficial de n8n específica para construir agentes y multi-agentes con el AI Agent node. docs.n8n.io/advanced-ai
- Anthropic · How to use Claude with tools. Documentación oficial sobre function calling y tool use en Claude. docs.anthropic.com/en/docs/build-with-claude/tool-use
- OpenAI · Function calling guide. Documentación oficial sobre tool use en GPT-4o y modelos posteriores. platform.openai.com/docs/guides/function-calling
- Awesome LLM Apps · Multi-agent section. Recopilación abierta de ejemplos multi-agente, muchos implementables con low-code. github.com/Shubhamsaboo/awesome-llm-apps

Fin lección 4.2 · Sigue lección 4.3

## Memoria y estado entre agentes

El paso de stateless a stateful. Memoria conversacional dentro de una ejecución, persistencia entre ejecuciones, vector stores para memoria semántica, y cómo elegir el tipo de memoria adecuado para cada caso.

#### Al final de esta lección sabrás:

- Distinguir memoria short-term (dentro de una ejecución) y long-term (entre ejecuciones).
- Configurar memoria conversacional en n8n con Window Buffer Memory.
- Persistir estado entre ejecuciones usando bases de datos (Postgres, Redis) o Data Stores de Make.
- Conocer los vector stores y cuándo conviene usarlos para memoria semántica.
- Implementar un chatbot que recuerde conversaciones anteriores en producción.

Sin memoria · cada ejecución es una isla

Por defecto, los workflows que hemos construido son stateless: cada ejecución empieza de cero, sin saber qué pasó en ejecuciones anteriores. Esto es perfectamente adecuado para muchos casos: un clasificador de tickets no necesita recordar los anteriores; un workflow que procesa un email no necesita saber qué emails vinieron antes.

Pero hay casos donde el estado importa críticamente:

- Chatbots conversacionales. El usuario espera que el bot recuerde el contexto previo de la conversación.
- Agentes con seguimiento. Un agente comercial debería saber «este cliente ya pidió esto antes».
- Workflows con human-in-the-loop. Una propuesta espera aprobación humana durante horas o días; durante ese tiempo, el estado debe estar guardado.
- Procesos largos. Análisis que ejecutan en varias fases con días de diferencia entre ellas.

Memoria short-term · dentro de una ejecución

El caso más simple es la memoria conversacional dentro de un único workflow. Si tu workflow recibe varios mensajes consecutivos del mismo usuario y quieres que el LLM los vea todos como una conversación coherente.

En n8n, esto se hace conectando un nodo Memory al AI Agent. Tipos disponibles:

- Window Buffer Memory. Guarda los últimos N mensajes (configurable, típicamente 5-10). Si la conversación supera el buffer, descarta los más antiguos. Sencillo, suficiente para la mayoría de chatbots cortos.
- Buffer Memory. Guarda todo el historial sin descartar. Solo viable para conversaciones cortas porque el coste en tokens crece linealmente con cada turno.
- Summary Buffer Memory. Cuando el buffer crece, llama a un LLM extra para resumir los mensajes antiguos. Conserva «contexto» histórico sin gastar tokens proporcionales. Más caro por ejecución pero permite conversaciones más largas.

#### Cómo n8n sabe a qué conversación pertenece cada mensaje

Para que el agente recuerde una conversación entre llamadas distintas al webhook, n8n necesita identificar qué llamadas pertenecen a la misma conversación. Esto se hace con un session_id: un identificador único por usuario o por conversación. Cuando un mensaje llega al webhook, extraes ese ID (de un campo del request, de un parámetro de Telegram, de un cookie, etc.) y lo pasas al nodo Memory. Mensajes con el mismo session_id se acumulan en la misma memoria; mensajes con session_id distinto son conversaciones independientes.

Memoria long-term · persistencia entre ejecuciones

Para que la memoria sobreviva a reinicios del workflow (o del propio n8n), necesitas un backend persistente. Opciones según madurez del proyecto:

- Postgres Memory (n8n). Usa una base de datos Postgres para guardar el historial. Si tu n8n ya usa Postgres (recomendado en producción), reutiliza la misma base. Si no, levanta otro contenedor Postgres con docker-compose junto a n8n. Es la opción más común y mejor balanceada.
- Redis Memory (n8n). Para conversaciones que requieren latencia mínima. Redis es una base de datos en memoria, rapidísima. Útil si tu chatbot recibe muchísimos mensajes por minuto.
- Make Data Stores. La opción Make. Funcional para casos sencillos. Limitado en tamaño en el plan Free.
- Bases de datos personalizadas. Para casos avanzados puedes guardar la memoria en cualquier base de datos (MongoDB, Supabase, Airtable, Notion) accediendo vía sus nodos. Más flexible pero más complejo de mantener.

#### Diseño de un caso real end-to-end

Trigger · Telegram Trigger escucha mensajes nuevos a tu bot.

Edit Fields (Set). Extrae el chat_id del usuario (será el session_id) y el texto del mensaje.

AI Agent. Configurado con:

- Chat Model: Anthropic Chat Model (Claude Haiku, rápido y barato).
- Memory: Postgres Chat Memory. Configurada con la URL de tu Postgres. session_id = chat_id de Telegram.
- System message: «Eres un asistente personal del usuario. Recuerda lo que te ha contado en mensajes anteriores y úsalo para responder con personalización. Tono cercano pero profesional.»

Telegram · Send Message. Envía la respuesta del agente al chat_id correspondiente.

Resultado: un chatbot que recuerda lo que le has contado en mensajes anteriores incluso si pasan días entre uno y otro. Mantén la memoria razonable: configurar Window Buffer en 20-30 mensajes suele bastar; más allá empieza a crecer el coste sin beneficio claro.

Vector stores · memoria semántica

Hay un tipo de memoria distinto que merece capítulo aparte: la memoria semántica vía vector stores. La idea: en vez de guardar mensajes literales, guardas embeddings (representaciones numéricas) de cada texto. Cuando llega una nueva pregunta, buscas los embeddings más similares semánticamente y los pasas al LLM como contexto.

Casos donde brilla:

- Chatbot que consulta una base de conocimiento grande (documentación interna, base de FAQs, artículos de blog).
- Recuperación de fragmentos relevantes de conversaciones pasadas («cuando hablamos del proyecto X»).
- Sistemas de búsqueda inteligente en lugar de búsqueda por palabras clave.

Opciones de vector stores gratuitas o con tier gratuito:

- Qdrant. Open-source, self-hosteable con un contenedor Docker más en tu docker-compose. n8n tiene nodo nativo. La opción recomendada para empezar self-hosted.
- pgvector. Extensión de Postgres. Si ya usas Postgres para tu n8n, añadirle pgvector te da vector store gratis sin nueva infraestructura.
- Pinecone. SaaS. Tier gratuito generoso (un índice, 100K vectores). Útil si no quieres gestionar infra.
- Supabase. SaaS con tier gratuito. Postgres + pgvector + auth + storage. Versátil.

El flujo típico con vector store: (1) Cargas tu corpus (documentos, FAQs, historial) una sola vez en el vector store, generando embeddings con un modelo de embeddings (OpenAI text-embedding-3-small es el más barato, ~0.02 USD por millón de tokens). (2) Cuando llega una pregunta, generas su embedding. (3) Buscas los N documentos más similares en el vector store. (4) Pasas esos documentos al LLM como contexto. (5) El LLM responde basándose en ellos.

Esta técnica se llama RAG (Retrieval-Augmented Generation) y es el patrón más usado para construir chatbots de empresa sobre documentación interna. Lo introducimos aquí porque combina naturalmente con multi-agente; un curso entero podría dedicarse a RAG en profundidad y queda fuera del alcance de este módulo.

#### Ejercicio 4.3 · añadir memoria a tu workflow

Convierte uno de tus workflows anteriores en uno con memoria persistente.

1. Opción A · convertir el workflow del ejercicio 4.2 añadiendo un AI Agent con memory: cada vez que llega una URL, además de procesarla, el agente recuerda las URLs procesadas anteriormente y puede responder preguntas sobre ellas («¿qué noticias de tecnología procesamos esta semana?»).
2. Opción B · construir un chatbot simple con memoria. Webhook que recibe mensajes con un campo user_id y un campo mensaje. AI Agent con Window Buffer Memory de 10 mensajes, session_id = user_id. Devuelve la respuesta. Prueba enviando varios mensajes consecutivos y verifica que el bot recuerda contexto previo.
3. Levanta una Postgres en tu docker-compose (junto a n8n) o usa Supabase free tier si prefieres no añadir contenedores. Configura el Postgres Memory del AI Agent.
4. Manda 5-7 mensajes consecutivos al mismo session_id, comprueba que la memoria funciona (el bot recuerda lo dicho hace varios mensajes).
5. Manda mensajes con session_id distinto y verifica que son conversaciones independientes (el bot no mezcla memorias).
6. Para n8n con `docker compose down`, vuelve a levantarlo con `up -d`, manda un mensaje a una sesión anterior, y comprueba que la memoria persistió.
7. Bonus avanzado: añade Qdrant a tu docker-compose y construye un sistema de RAG: carga 3-4 documentos largos (PDFs, artículos), genera embeddings, y haz que el chatbot consulte el vector store para responder preguntas con citas a los documentos.

No subestimes la complejidad de la primera vez que añades una base de datos al workflow. Si todo el setup de Postgres + memory te lleva 2-3 horas, es normal. Una vez configurado una vez, replicarlo en otros workflows toma minutos.

¿Cuánta memoria es suficiente para un chatbot?

Depende del caso. Para asistentes conversacionales tipo soporte (preguntas y respuestas dentro de una sesión), 10-20 mensajes en Window Buffer suele bastar. Para asistentes personales con relación a largo plazo (el bot recuerda preferencias del usuario que dijiste hace semanas), conviene combinar Window Buffer corto (últimos 10) + RAG sobre historial completo para «buscar» mensajes pasados relevantes.

¿Es seguro guardar conversaciones de usuarios en mi base de datos?

Depende del contenido y la regulación que apliques. Para chatbots empresariales en Europa, los mensajes pueden ser dato personal según GDPR. Buenas prácticas: minimizar lo que guardas, cifrado en reposo, política clara de retención (borrar memorias antiguas tras X días), aviso al usuario de que sus conversaciones se almacenan. Si dudas, consulta con un DPO.

¿Cómo escalo si tengo miles de usuarios con conversaciones largas?

Tres pasos. (1) Usa Window Buffer pequeño + Summary para que el coste por mensaje no crezca. (2) Mueve la memoria a Redis si necesitas baja latencia, o a Postgres con índices apropiados si necesitas volumen. (3) Considera memoria expirada (borrar conversaciones inactivas tras X días). Para volúmenes muy grandes (millones de usuarios), probablemente rebases las capacidades de n8n y necesites código a medida.

¿RAG y memoria conversacional son lo mismo?

No. Memoria conversacional guarda los mensajes recientes del propio usuario y se los pasa al LLM como contexto inmediato. RAG busca en una base de conocimiento externa (documentos, base de datos) fragmentos relevantes a la pregunta actual. Lo más sólido en producción combina las dos: el LLM ve la conversación reciente Y los fragmentos relevantes de la base de conocimiento.

#### Memoria, estado y RAG en workflows low-code

- n8n Memory nodes documentation. Documentación oficial de los nodos Memory: Window Buffer, Postgres, Redis. docs.n8n.io/advanced-ai/langchain/langchain-memory
- Qdrant Documentation. Vector store open-source self-hosteable. Guía oficial completa. qdrant.tech/documentation
- OpenAI Embeddings guide. Documentación oficial sobre cómo generar embeddings para RAG con tarifas detalladas. platform.openai.com/docs/guides/embeddings
- Awesome RAG. Lista open-source en GitHub con técnicas, papers y herramientas de RAG. github.com/frutik/Awesome-RAG

Fin lección 4.3 · Sigue lección 4.4 · Proyecto final

## Caso final · agente comercial multi-paso

El proyecto integrador del módulo: un agente comercial real que recibe consultas, las clasifica, busca en CRM, redacta respuesta personalizada, espera aprobación humana vía Slack, envía y registra. Combina los cuatro sub-módulos.

#### Al final de esta lección habrás:

- Construido un sistema multi-agente real que combina webhook, varios LLMs, búsqueda en CRM, human-in-the-loop y envío automatizado.
- Aplicado el patrón orquestador + trabajadores en un caso profesional.
- Manejado timeouts y casos de fallback en flujos con esperas humanas.
- Pieza demostrable para tu portfolio profesional como AI Engineer.

El caso · agente comercial inteligente

Construyes un sistema que ataca un caso concreto que cualquier empresa con departamento comercial reconoce: responder a consultas de leads de forma rápida y personalizada sin saturar a los comerciales. El flujo ideal:

1. Llega una consulta de un lead (por email, formulario web, Telegram, lo que sea).
2. Un primer agente clasifica la intención: demo, precio, soporte, partnerships, otros.
3. Busca al lead en el CRM (o en Notion, o en una Google Sheet con la lista de clientes). Si existe, recupera su histórico.
4. Un segundo agente redacta un borrador de respuesta personalizado considerando la consulta, el histórico y el tipo de cliente.
5. El borrador se envía al equipo comercial vía Slack para aprobación o edición.
6. Cuando un comercial aprueba (o edita y luego aprueba), la respuesta se manda al lead.
7. Todo el intercambio se registra en CRM con timestamp y comercial responsable.

Es un caso donde se ve claramente el valor de combinar varios agentes (clasificación + redacción) con lookup en datos externos (CRM) y con human-in-the-loop (aprobación comercial). En producción real, este tipo de sistema ahorra horas semanales al equipo comercial manteniendo calidad.

Arquitectura del workflow

El workflow tiene siete bloques principales:

- Bloque 1 · Webhook trigger. Recibe la consulta del lead. Puede venir de un formulario web (POST con email, nombre, mensaje), de Gmail Trigger (email entrante) o de Telegram (mensaje al bot comercial). Por simplicidad y portabilidad en este ejercicio: webhook genérico.
- Bloque 2 · Clasificador (LLM 1). Anthropic Haiku o Gemini Flash. Recibe el mensaje del lead y devuelve JSON: categoria (demo/precio/soporte/partnerships/otros), urgencia (alta/media/baja), idioma del mensaje.
- Bloque 3 · Lookup en CRM. Busca al lead por email en tu base (Notion DB / Google Sheet / Airtable / Postgres). Si no existe, lo crea como nuevo lead. Si existe, recupera: empresa, último contacto, último deal, comercial asignado.
- Bloque 4 · Redactor (LLM 2). Claude Sonnet o GPT-4o. Recibe: mensaje original, clasificación del bloque 2, datos del lead del bloque 3. Devuelve borrador de respuesta personalizado en el idioma detectado.
- Bloque 5 · Slack · enviar para aprobación. Posteo en canal del equipo comercial con: el mensaje original, los datos del CRM, el borrador propuesto, y dos botones (Aprobar / Editar). Esto requiere un workflow secundario que escuche la respuesta del Slack.
- Bloque 6 · Esperar y enviar. Cuando llega la aprobación (vía un segundo webhook desde Slack o nodo Wait), el workflow continúa y envía el email al lead. Si pasa demasiado tiempo sin respuesta (24h), notifica escalamiento.
- Bloque 7 · Registrar en CRM. Crea entrada en el CRM con: timestamp, lead, consulta, clasificación, respuesta enviada, comercial responsable, estado.

#### Esperar respuesta humana en un workflow

En n8n hay dos enfoques para el patrón aprobación humana:

Enfoque A · Wait node con webhook. El workflow se «duerme» en un nodo Wait esperando un webhook concreto. Cuando el comercial aprueba en Slack, Slack envía un webhook al endpoint específico y el workflow continúa. Limpio pero requiere coordinar Slack con el endpoint.

Enfoque B · dos workflows distintos. Workflow 1 procesa la consulta y posta en Slack. Workflow 2 escucha los clics de aprobación y, al recibirlos, recupera el contexto (de un Postgres o Data Store) y termina el envío. Más nodos pero más robusto frente a reinicios.

Para producción, el enfoque B es más resiliente: si el workflow se reinicia mientras espera, el enfoque A pierde el estado; el B no.

Ejemplo · workflow del proyecto final detallado

#### Diseño paso a paso (versión enfoque B, con dos workflows)

WORKFLOW 1 · «Procesar consulta de lead»

1. Webhook: POST /lead-consulta. Body: `{ "email": "...", "nombre": "...", "mensaje": "..." }`.

2. Anthropic Chat Model (Haiku): clasifica el mensaje. Output JSON con categoria, urgencia, idioma.

3. Postgres · Execute Query (o nodo de Notion/Airtable): busca lead por email. Si no existe, lo crea.

4. Anthropic Chat Model (Sonnet): redacta borrador combinando todo el contexto.

5. Postgres · Insert: guarda en tabla «pending_approvals» con id único, estado «pending», borrador, datos del lead, datos del comercial asignado, timestamp.

6. Slack · Send Message with buttons: mensaje en canal #ventas-aprobaciones con:

📩 Nueva consulta de María García ([email protected]) Categoría: demo · Urgencia: alta Histórico: 3 visitas previas, último contacto hace 2 semanas Borrador propuesto: "Hola María, gracias por interesarte en una demo..." [✓ Aprobar] [✏️ Editar] [🚫 Descartar]

Los botones de Slack apuntan al webhook del Workflow 2 incluyendo el id del pending_approval como parámetro.

WORKFLOW 2 · «Procesar aprobación»

1. Webhook: POST /lead-aprobacion. Body de Slack con la acción del comercial y el id.

2. Postgres · Select: recupera el pending_approval por id.

3. Switch: tres rutas según botón pulsado.

 - Ruta «Aprobar» → Gmail Send con el borrador al lead. Postgres Update: estado = «enviado».

 - Ruta «Editar» → Slack Open Modal con el texto editable. Tras edición, manda el editado.

 - Ruta «Descartar» → Postgres Update: estado = «descartado». Notifica al comercial supervisor.

4. Postgres Insert en tabla «crm_history»: registro completo del intercambio.

5. Slack reply: confirma al canal que la respuesta se ha procesado.

WORKFLOW 3 (opcional) · «Recordatorio de aprobaciones pendientes». Schedule cada 4 horas. Postgres Select de pending_approvals con estado «pending» y timestamp > 24h. Slack: «⚠️ 3 aprobaciones llevan más de 24h pendientes». Esto evita que peticiones queden colgadas.

Cómo manejar fallos y casos límite

Un sistema en producción tiene que aguantar lo que pasa cuando algo no va como esperabas:

- El LLM devuelve JSON malformado. Activa response_format JSON en OpenAI o usa structured outputs. Para Claude, sé muy estricto en el system prompt.
- El lead no está en CRM y no se puede crear automáticamente. Configura una ruta de fallback: si lookup falla, manda a aprobación con datos solo del email recibido.
- El comercial no aprueba en 24h. El workflow 3 que mencionamos resuelve esto.
- Slack está caído. Reintentos automáticos en el nodo Slack + Error Trigger que escale el problema a otro canal de emergencia o a Telegram.
- El lead manda 5 mensajes seguidos. Detecta duplicados antes del workflow completo: si ya hay un pending_approval activo para ese email, no creas otro, solo añades el nuevo mensaje al hilo.

#### Ejercicio 4.4 · proyecto final integrador

Tiempo estimado · 2 horas · Es el proyecto final del módulo

Construye el agente comercial completo en tu n8n self-hosted. Es el ejercicio más ambicioso del módulo y el más cercano a un proyecto profesional real.

1. Adapta el caso si lo necesitas. No hace falta que sea «agente comercial» literal. Puede ser: «agente de soporte de primer nivel», «agente de scheduling para una clínica», «agente que tritura emails y prepara respuestas para tu propia bandeja». Lo importante es el patrón completo.
2. Configura tu base de datos. Postgres en docker-compose junto al n8n self-hosted del SM3, o Notion/Airtable si prefieres una opción gestionada. Crea tablas/databases necesarias: leads (o contactos), pending_approvals, history.
3. Construye Workflow 1 · procesar consulta. Webhook + clasificador LLM + lookup en BD + redactor LLM + insert en pending_approvals + post a Slack con botones.
4. Construye Workflow 2 · procesar aprobación. Webhook que recibe el clic de Slack + select de pending_approval + switch según acción + envío + update + history.
5. Construye Workflow 3 (opcional) · recordatorio. Schedule cada 4-6h. Select de pending_approvals viejos. Notificación.
6. Prueba el flujo completo end-to-end: 

1. Manda una consulta de prueba al webhook 1.
2. Verifica que llega a Slack con borrador adecuado.
3. Pulsa aprobar.
4. Verifica que llega el email al receptor.
5. Verifica que se ha registrado en la tabla history.
7. Documenta el proyecto. README con: descripción del caso, arquitectura (diagrama), tecnologías usadas, instrucciones de despliegue, casos de uso, limitaciones conocidas. Sube todo a tu repositorio personal de GitHub (sin claves, claro). Esto es lo que enseñas en entrevistas técnicas como AI Engineer.
8. Graba un vídeo de 3-5 minutos mostrando el sistema en acción. Manda una consulta, enseña Slack, aprueba, enseña el resultado. Sube a YouTube no listado. Pega el link en tu LinkedIn. Esto vale más que cualquier titulación para conseguir tu primer puesto de AI Engineer.

Si dos horas no son suficientes para el sistema completo, prioriza Workflow 1 y Workflow 2 (sin recordatorio). El recordatorio es valor añadido, los dos primeros son el core. Cuando funcionen, vuelves al recordatorio y a bonus.

¿Cómo mido si el sistema funciona en producción real?

Tres métricas iniciales. (1) Tasa de aprobación: % de borradores aprobados sin edición. Si está alto (>70%), el clasificador y redactor van bien. Si bajo, hay que mejorar prompts. (2) Tiempo medio de aprobación: lo que tarda un comercial en revisar. Si crece, posiblemente el equipo necesita más capacidad. (3) Tasa de respuesta del lead: % de leads que responden tras recibir el email. Si baja, los borradores no están persuadiendo.

¿Qué pasa si el LLM se equivoca y propone una respuesta inadecuada?

Por eso existe el human-in-the-loop: el comercial revisa antes de enviar. Es la red de seguridad principal. Adicionalmente, en el redactor puedes incluir un revisor (un segundo LLM con prompt crítico) que verifique antes de mandar a aprobación. Y en última instancia, el sistema puede aprender de las ediciones humanas: guarda los pares borrador-versión-final y úsalo para iterar el prompt del redactor periódicamente.

¿Cómo escala este sistema a varios miles de leads al mes?

Postgres maneja sin problema cientos de miles de registros. n8n self-hosted en un VPS de 4 GB RAM procesa varios cientos de ejecuciones por hora sin sudar. El bottleneck suele ser el equipo humano que aprueba: si los comerciales no dan abasto, conviene segmentar (auto-aprobar respuestas a consultas «categoría: precio» bajo cierta plantilla, y dejar revisión humana solo para casos más complejos).

¿Qué hago tras terminar este módulo? ¿Cómo sigo aprendiendo?

Tres caminos. (1) Profundiza en LangGraph o CrewAI si quieres ir a multi-agente en código, te darán control adicional. (2) Especialízate en un vertical (legal, salud, fintech) construyendo sistemas adaptados a un sector. (3) Empieza a vender automatizaciones como freelance: encuentra una pyme con procesos manuales obvios, ofrece auditoría gratuita y luego implementación. Los AI Engineers que aprenden estos patrones encuentran trabajo rápido en agencias de automation o en proyectos freelance bien pagados.

#### Casos reales y siguientes pasos

- n8n AI Templates. Galería de workflows de IA pre-construidos por la comunidad, muchos con patrones multi-agente. Importables con un clic. n8n.io/workflows/?categories=AI
- Anthropic · Cookbook. Recetas oficiales de Anthropic con casos prácticos de multi-agente y human-in-the-loop. github.com/anthropics/anthropic-cookbook
- LangGraph. Framework de LangChain para multi-agente en código Python. Cuando te quedes corto con low-code. langchain-ai.github.io/langgraph
- Awesome LLM Apps · Production examples. Sección de casos en producción real, muchos open-source que puedes leer. github.com/Shubhamsaboo/awesome-llm-apps

## Lo que ya sabes hacer

40 horas, 4 sub-módulos, 13 lecciones y 13 ejercicios después, has pasado de no haber tocado un workflow en tu vida a tener un sistema multi-agente real corriendo en tu propio servidor con dominio propio y HTTPS automático. Has aprendido n8n cloud y self-hosted, Make con sus routers y aggregators, Docker desde cero, despliegue en VPS y conexión de varios LLMs colaborando con memoria persistente. Esto no es un curso teórico: es una pila técnica completa de las que se buscan ahora mismo en el mercado laboral de AI Engineering.

El portfolio que has construido incluye un workflow webhook + LLM end-to-end, un clasificador inteligente en Make, una instancia self-hosted en VPS con HTTPS, y un agente comercial multi-paso con human-in-the-loop. Cada uno de ellos vale como muestra en entrevistas. Súbelos a GitHub (workflows como JSON, instrucciones en README), publica los más impactantes en LinkedIn con un vídeo corto de demostración y respalda tu candidatura con piezas reales, no certificados.

Para profundizar más allá del módulo: si quieres ir hacia agentes en código, salta a LangGraph o CrewAI; el entendimiento que has construido en low-code traduce bien. Si quieres especializarte en un vertical (legal, salud, fintech, e-commerce), busca un proceso manual obvio en una pyme de ese sector y propón automatizarlo. Si quieres freelance, ofrece auditorías gratuitas de procesos: 90% de las pymes tienen al menos un flujo manual obvio que podrías automatizar en una semana cobrando 1.000-3.000 €.

Una última nota. La automatización con IA está al inicio de su curva. Los profesionales que dominan estas herramientas hoy van a ser indispensables en muchísimos puestos en los próximos años. No porque la IA «sustituya» a nadie, sino porque las empresas que combinen procesos humanos con automatización inteligente van a operar con ventaja sobre las que no. Tú ya tienes esa combinación. Sigue construyendo.

## Índice completo

Guía de aprendizaje autoguiado para el Módulo 3 del Bootcamp en AI Engineering. 40 horas en 4 sub-módulos y 13 lecciones, cada una con teoría, ejemplos y ejercicio práctico. Software gratuito o trial en todas las herramientas.

1. — Portada Automatización con n8n & Make 2 min
2. 00Índice rápido Mapa visual de los cuatro sub-módulos 5 min
3. 00.1 Cómo usar esta guía Estructura, cuentas gratuitas, plan de estudio 10 min

1. SM1 Apertura del sub-módulo Resumen y orientación 3 min
2. 1.1 Automatización low-code y por qué importa Conceptos, panorama, mapeo de flujos~2,5 h
3. 1.2 Primer workflow en n8n cloud Cuenta, dashboard, triggers, primer flujo real~3,5 h
4. 1.3 Webhooks y nodos avanzados Webhook trigger, expresiones, código, LLM end-to-end~4 h

1. SM2 Apertura del sub-módulo Resumen y orientación 3 min
2. 2.1 Make vs n8n · panorama y primer escenario Cuándo cada uno, plan Free, Gmail+Sheets~3 h
3. 2.2 Routers, filtros y aggregators Lógica condicional, iteración, Data Stores~3,5 h
4. 2.3 Conectando IA con Make · OpenAI, Claude, Gemini Módulo oficial, HTTP, clasificador empresarial~3,5 h

1. SM3 Apertura del sub-módulo Resumen y orientación 3 min
2. 3.1 Docker básico · contenedores en 90 minutos Imágenes, volúmenes, compose, primer servicio~3 h
3. 3.2 n8n local con Docker · paso a paso docker-compose, persistencia, migración cloud→local~3,5 h
4. 3.3 Despliegue en VPS · Hetzner, DigitalOcean Oracle Free, SSH, Caddy, HTTPS, backups~3,5 h

Sub-módulo 4 · Multi-agent workflows low-code · 10 h

1. SM4 Apertura del sub-módulo Resumen y orientación 3 min
2. 4.1 Qué es un multi-agent system Patrones, riesgos, diseño en papel~2 h
3. 4.2 Conectar varios LLMs en un workflow AI Agent node, serie y paralelo, mezcla de proveedores~2,5 h
4. 4.3 Memoria y estado entre agentes Short-term, long-term, vector stores, RAG~2,5 h
5. 4.4 Caso final · agente comercial multi-paso Proyecto integrador con human-in-the-loop~3 h

Cierre

1. — Cierre del módulo Lo que ya sabes hacer · siguientes pasos 5 min