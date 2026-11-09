# Módulo 2: Prompting Profesional, APIs y Tokens

**Cuatro sub-módulos, catorce lecciones, un proyecto final**. Este módulo se imparte tras el módulo de introducción y antes de los bloques de RAG, agentes y despliegue. Cuarenta horas distribuidas en trece sesiones de tres horas a diario, agrupadas en cuatro sub-módulos que se corresponden con los cuatro epígrafes oficiales del programa: **prompting**, **APIs**, **multimodalidad** y **tokens, costes, latencia y rate limits**. Cada sub-módulo cierra con un mini-proyecto integrador que se hereda al siguiente.

Esta guía está pensada para usarse exactamente igual que la del módulo de introducción: revisar la sesión la tarde anterior, llegar a clase con los materiales preparados, consultar la tabla de tiempos durante la franja teórica, y apoyarse en las notas pedagógicas y FAQs cuando aparezcan los puntos críticos del oficio.

---



## Filosofía pedagógica

Ubicación del módulo en el bootcamp, gestión del aula técnica y reparto de tiempos.

### Preparación previa

- Entorno Python.
- SDKs.
- API keys.
- Créditos iniciales.
- Gestión segura de secretos.

---



## Prompting profesional

De la prompt informal del módulo de introducción al prompt como pieza de ingeniería: zero-shot, few-shot, Chain-of-Thought, Self-consistency y ReAct.

### Anatomía del prompt profesional

Del «di lo que quieres» al prompt diseñado: roles, contexto, formato, restricciones y patrones anti-fallo. Primer contacto con la API en la franja práctica.

#### Lo que el alumno se lleva de hoy

Al final de la sesión 01, el alumno debe ser capaz de:

- Construir prompts profesionales capa a capa (rol, contexto, formato, restricciones, ejemplos).
- Entender la estructura de mensajes: system, user, assistant.
- Hacer su primera llamada a una API de LLM con validación básica.

---



### Cómo se da este módulo

El módulo 2 es el primer módulo realmente técnico del bootcamp. El alumno llega con vocabulario y cuentas activas, pero no ha tocado código de Python apuntando a una API de LLM en su vida. Tu trabajo es llevarlo en cuarenta horas de no haber llamado a ningún modelo a tener su propio pequeño Swiss-army knife de prompts, llamadas y arquitecturas comparables a las que se ven en producción.

### Qué viene antes y qué viene después

- **Antes de este módulo:** módulo de introducción (12 h, conceptos, vocabulario, cuentas) y un módulo de fundamentos de Python (variables, funciones, requests, manejo de errores). Sin esos dos pre-requisitos esta guía no funciona; verifícalo en la sesión 01 antes de avanzar.
- **Después de este módulo:** RAG y bases de datos vectoriales, donde se aplica todo lo que aquí se introduce sobre prompts y APIs a un caso concreto. Conviene que en la sesión 13 cierres anticipando esa continuidad: el módulo 2 no es un destino, es la base para todo lo demás.

El módulo 2 desplaza el equilibrio hacia la práctica respecto al módulo de introducción. La teoría sin código no se asienta en una disciplina técnica. La franja teórica se trocea en bloques cortos (10-15 min) intercalados con demos de live coding, no en una explicación monolítica.

### Los tres síntomas que indican que vas mal

1. **Pantallas congeladas en la última diapositiva durante la franja práctica:** alguien no ha podido instalar algo y ha desconectado. Pasea cada 5 min hasta que las pantallas vuelvan a tener código en movimiento.
2. **Una sola persona dominando todas las preguntas:** el resto se está apagando. Devuelve preguntas al aula («¿qué cree alguien más?») antes de responder.
3. **Errores que no salen:** el alumno copia y pega tu código y todo funciona a la primera. Mala señal: no está leyendo. Cambia un nombre de variable o un parámetro a propósito antes de pegar.

El profesor debe llegar al primer día con:

- Un repositorio GitHub del módulo (donde subirá las soluciones de referencia tras cada sesión).
- Las tres cuentas con API keys activas y créditos suficientes para demos.
- Un canal de Slack o Discord del módulo para que los alumnos compartan errores.
- Un documento vivo de «gotchas» que se va alimentando a lo largo del módulo.

---



## Entorno, API keys y créditos

El alumno entra al módulo 2 con Python instalado del módulo de fundamentos. Aquí se monta el entorno específico de LLMs y se generan las claves de las tres plataformas.

### El stack de trabajo del módulo

Todo el módulo se desarrolla sobre el mismo entorno virtual de Python. Verifica el día 1 que cada alumno tiene un entorno aislado y los tres SDKs instalados. Es la única forma de que los errores que aparezcan sean contenido del módulo y no problemas de instalación.

#### «Module not found» pese a haber instalado

Pasa todos los años: el alumno instala los SDKs en el Python del sistema en lugar de en el entorno virtual. El síntoma es ejecutar `pip install openai`, ver «successfully installed» y al importar recibir `ModuleNotFoundError`. Diagnóstico de 30 segundos: pídele que ejecute `which python` (Mac/Linux) o `where python` (Windows). Si no apunta a la ruta del `.venv`, no ha activado el entorno. Es contenido del módulo de fundamentos pero conviene repasarlo aquí.

### Las tres claves que activan el módulo

El alumno necesita una API key por cada uno de los tres proveedores. Las tres se generan online en menos de 5 minutos cada una. El profesor debe entender el modelo de créditos de cada plataforma para anticipar problemas de cuota.

El tema de los créditos hay que resolverlo antes del día 1:

- Hablar con coordinación académica con dos semanas de antelación: ¿la academia paga los créditos o los pone el alumno? Si los paga la academia, conviene generar una organización en cada plataforma e invitar a los alumnos. Si los paga el alumno, dejar claro en la comunicación previa que necesitan cargar ~15 $ totales repartidos entre las tres plataformas.
- Ningún alumno debe llegar al día 1 sin esto resuelto.

Anthropic tiene además un programa educativo (Anthropic for Education) que puede dar créditos a centros formativos. Vale la pena la gestión.

### Gestión segura de secretos

Las API keys son contraseñas con dinero detrás. Una key filtrada en GitHub puede generar facturas de miles de dólares en horas. El módulo entero se hace con archivos `.env` y `python-dotenv`, nunca hardcodeando claves en el código.

Enseñar qué pasa cuando una key se filtra:

- Cinco minutos bien invertidos al inicio de la sesión 01: cuenta una historia real (hay decenas documentadas) de un desarrollador que subió su key a un repo público, alguien la encontró por scraping en menos de una hora y le generó una factura de 5.000 $. GitHub detecta las keys conocidas y las invalida automáticamente, pero hay tipos de keys que no detecta.
- El miedo razonable es un buen profesor en este tema.



### Cinco casillas obligatorias al terminar la sesión 01

- Setup técnico verificado (versiones, SDKs, entorno virtual).
- `.env` creado y cargado sin errores de autenticación.
- Primera llamada a la API exitosa con respuesta parseada.
- Comprensión de la estructura de mensajes (system, user, assistant).
- Prompt profesional mínimo construido con rol, contexto y formato.

---



### Cómo dar la franja teórica (15 min que evitan 3 horas de problemas)



#### Setup técnico (3 min)

Pide tres comandos al inicio:

```bash
python --version
pip show openai
python -c "from openai import OpenAI; OpenAI()"
```

Si el último da error de autenticación, falta el `.env`. Si da `ModuleNotFoundError`, el venv no está activo.

Resuelve esto AHORA, no esperes a la práctica.

#### La estructura de la conversación (20 min)

En pizarra dibuja una tabla de tres filas: system, user, assistant. Explica que una llamada a la API no es «un prompt»; es una lista de mensajes con roles.

El system prompt dirige el comportamiento general. Los user prompts son las intervenciones del usuario. Los assistant prompts son lo que el modelo ha dicho antes (en conversaciones multi-turno).

Muestra en código:

```python
messages = [
    {"role": "system", "content": "Eres un asistente comercial profesional."},
    {"role": "user", "content": "Hola, necesito ayuda con un ticket."},
    {"role": "assistant", "content": "¡Claro! Déjame leerlo y ver en qué puedo ayudarte."},
    {"role": "user", "content": "El cliente dice que no puede pagar en la fecha acordada."}
]
response = client.chat.completions.create(messages=messages, model="gpt-4o-mini")
```

Insiste: nada en el system es invisible. El modelo lo lee igual que el user. La diferencia es que conceptualmente fija el «contrato de servicio» y el modelo le da más peso para reglas estables.

#### Construye un prompt en vivo (25 min)

Prepara un caso de uso real (sugerido: «un asistente que redacta correos comerciales de seguimiento») y constrúyelo en vivo en pantalla, capa a capa:

- Empieza con solo tarea. Ejecuta. Lee la respuesta mediocre.
- Añade rol. Ejecuta.
- Añade contexto. Ejecuta.
- Sigue con formato, restricciones, ejemplos.

Cada capa mejora visiblemente la respuesta. Al final tienes un prompt profesional construido por adición, no por nacimiento, y el aula ha visto el porqué de cada parte.

#### Aprender de los errores ajenos (20 min)

Muestra cinco prompts mal diseñados y sus resultados. Los cinco anti-patterns:

- Prompt descriptivo sin restricciones.
- Prompt contradictorio entre roles y contexto.
- Prompt con formato ambiguo.
- Prompt sin ejemplos y con instrucciones vagas.
- Prompt que pide algo que el modelo no puede hacer.

Pregunta al aula: «¿Qué haríais mejor en cada caso?». Usa sus respuestas para reforzar los seis componentes de un prompt profesional.

Cierre con la máxima del oficio:

> «Si tú no entenderías el prompt como humano sin contexto adicional, el modelo tampoco».



#### El momento «funciona de verdad» (10 min)

Live coding en pantalla compartida. Estos diez minutos son críticos: el alumno pasa de «la API es una idea abstracta» a «mira, esto responde». Escribe el código sin pegar, comentando cada línea:

```python
import openai
from dotenv import load_dotenv

load_dotenv()
client = openai.OpenAI()

prompt = (
    "Eres un asistente comercial. Redacta un correo de seguimiento para un cliente "
    "que ha pedido una demo hace 3 días y no ha respondido."
)

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role": "user", "content": prompt}]
)

print(response.choices[0].message.content)
```

Ejecuta. Cuando aparezca la respuesta en el terminal, espera tres segundos antes de hablar. Que se asienten. Después, abre `response` entero (con `print(response)`) y enseña la estructura completa: `choices[0].finish_reason`, `usage.prompt_tokens`, `usage.completion_tokens`. Eso engancha con la sesión 12.

### Cómo conducir la práctica



#### Setup (3 min)

Proyecta los cinco prompts mal diseñados. Pásales el archivo por chat. Indica que cada uno debe reescribir los cinco aplicando los seis componentes y ejecutarlos en la API.

#### Ejecución (27 min)

Pasa entre mesas. Mira sus reescrituras. Los errores típicos:

- Añaden rol pero olvidan formato.
- Añaden contexto pero el rol contradice el contexto.
- Añaden ejemplos pero los ejemplos no siguen la estructura que piden de salida.

Corrige en vivo, micro-coaching individual.

#### Puesta en común (5 min)

Pide a un voluntario que lea una reescritura buena. Comenta qué ha hecho bien. No leas las cinco; bastará con una o dos.

---



## Sesión 02: Zero-shot, Few-shot y salida estructurada

Aprendizaje en contexto: cuándo dar ejemplos y cuándo no, cómo elegirlos, y cómo forzar salidas JSON validables que se puedan procesar en código.

### Lo que el alumno se lleva de hoy

Al final de la sesión 02, el alumno debe ser capaz de:

- Decidir cuándo usar zero-shot vs few-shot según la tarea.
- Construir prompts few-shot con ejemplos eficaces.
- Usar structured outputs nativos para validar la salida con Pydantic.
- Medir accuracy y latencia de diferentes configuraciones.



### Cómo dar la franja teórica



#### Demo del salto cuantitativo (25 min)

El concepto «in-context learning» es uno de los grandes descubrimientos del campo. Que el modelo aprenda de tres ejemplos en el prompt sin que haya nada que «reentrenar» es contraintuitivo.

Para enseñarlo, haz una demo cuantitativa:

- Toma 20 frases sobre productos (10 positivas, 10 negativas, mezcladas).
- Primero clasifícalas con zero-shot («clasifica el sentimiento»).
- Anota accuracy en pizarra (suele rondar 70-80 %).
- Después añade 3 ejemplos al prompt (uno positivo, uno negativo, uno ambiguo resuelto).
- Reclasifica. Accuracy sube a 90-95 %.

El aula ve el salto. Esta demo de 5 min vale por 30 de teoría.

#### La calidad importa más que la cantidad (15 min)

Tres reglas para elegir ejemplos few-shot:

- **Cantidad:** La curva de utilidad satura entre 3 y 8 ejemplos para la mayoría de tareas. Más allá de 10 rara vez se gana algo, y el coste y la latencia suben.
- **Variedad:** Incluye ejemplos de casos límite, no solo casos «bonitos».
- **Claridad:** Si el ejemplo es ambiguo, el modelo se confunde.

La verdadera mejora viene de elegir mejor, no de añadir más.

#### La diferencia es real (25 min)

Conviene que entiendan los tres niveles de salida:

- **Texto libre:** Flexibilidad máxima, pero difícil de procesar en código.
- **Texto estructurado:** JSON, YAML, etc. Más fácil de parsear.
- **Structured outputs nativo:** El modelo genera automáticamente un schema (Pydantic) y la respuesta es un objeto. Sin validación post-hoc.

La regla profesional: siempre que el modelo lo soporte, structured outputs nativo. Es la diferencia entre código que funciona en demo y código que sobrevive en producción.

#### El patrón a fijar (15 min)

Escribe este patrón en vivo y deja que el alumno lo copie en su notebook:

```python
from typing import Optional
from pydantic import BaseModel


class Cliente(BaseModel):
    nombre: str
    email: str
    prioridad: Optional[str] = None
    activo: bool = True


def extraer_cliente(texto: str, modelo="gpt-4o-mini") -> Cliente:
    response = client.chat.completions.create(
        model=modelo,
        messages=[
            {
                "role": "system",
                "content": (
                    "Extrae los datos del cliente del siguiente texto. "
                    "Responde en JSON con el schema: Cliente."
                )
            },
            {"role": "user", "content": texto}
        ],
        response_format={"type": "json_object"}
    )

    raw = response.choices[0].message.content
    return Cliente.model_validate_json(raw)
```

Insiste en lo que pasa cuando un campo no existe en el texto (queda `None` gracias a `Optional[str]` y el modelo respeta la opcionalidad). Este patrón —Pydantic + parse— va a aparecer en el resto del módulo.

### Cómo conducir la práctica



#### Setup (3 min)

Reparte el CSV de 30 emails (15 spam, 15 no spam) y el notebook base. La consigna: empezar con prompt zero-shot, medir accuracy, ir añadiendo ejemplos uno a uno y registrar la curva en una tabla.

#### Ejecución (30 min)

El alumno construye un pequeño bucle que clasifica los 30 emails y compara con la etiqueta real. La tabla a rellenar tiene tres columnas:

- Nº ejemplos en few-shot.
- Accuracy.
- Latencia media.

Cada uno hace al menos 5 iteraciones (0, 1, 3, 5, 8 ejemplos).

#### Puesta en común (7 min)

Recoge tres curvas distintas del aula. Discutid juntos:

- ¿Dónde está el codo?
- ¿Hay sobre-ajuste cuando se añaden demasiados?
- ¿Qué ejemplos hacían más diferencia?



### La curva del codo en prompting

Esta dinámica enseña intuición visual sobre el rendimiento marginal de los ejemplos. Después del ejercicio, vuelve a la pizarra y dibuja la curva típica:

- Zero-shot: accuracy moderada.
- Salto grande entre 0 y 3 ejemplos.
- Mejora marginal entre 3 y 8.
- Plana o ligeramente peor a partir de 10.

Esa curva la van a internalizar y guiará todas sus decisiones de few-shot del bootcamp.

---



## Sesión 03: Chain-of-Thought, Self-consistency y ReAct

Técnicas avanzadas para que el modelo razone explícitamente, agregue varias trayectorias y combine razonamiento con acción. Cierre del sub-módulo de prompting.

### Lo que el alumno se lleva de hoy

Al final de la sesión 03, el alumno debe ser capaz de:

- Usar CoT para mejorar la precisión en tareas de razonamiento.
- Implementar Self-consistency como técnica de votación.
- Entender el patrón ReAct (Reason + Act) para agentes.
- Comparar coste vs ganancia de cada técnica.

---



### Cómo dar la franja teórica



#### Demo del «aha» (25 min)

El demo perfecto para CoT es un problema de palabras donde el modelo falla sin CoT y acierta con CoT.

Ejemplo: «Roger tiene 5 pelotas de tenis. Compra 2 latas más, cada una con 3 pelotas. ¿Cuántas tiene ahora?»

- Sin CoT, modelos pequeños fallan aproximadamente 1 de cada 3 veces.
- Con CoT explícito («Razona paso a paso antes de responder»), aciertan casi siempre.

Provoca el fallo en vivo: ejecuta varias veces hasta que falle, después añade «Let's think step by step» y vuelve a ejecutar. La diferencia es palpable.

Explica el porqué intuitivo:

El modelo no tiene «pensamiento interno», solo genera tokens. Forzarle a generar pasos intermedios es darle una memoria de trabajo expandida. Con razonamiento implícito (sin CoT) los pasos pasan por capas neuronales una sola vez; con CoT explícito cada paso recibe atención completa de las capas siguientes.

#### El cambio de paradigma de 2024-2025 (15 min)

Aclara que los modelos de razonamiento (o1, o3, Claude con Extended Thinking, DeepSeek-R1) ya hacen CoT internamente, en una fase de «pensamiento» que no ves pero que paga tokens. Esto cambia el oficio:

> **Regla:**
>
> - CoT explícito para modelos clásicos en tareas de razonamiento.
> - Modelo de razonamiento nativo cuando la tarea lo requiere y el coste lo permite.
> - Ninguno de los dos para tareas simples.



#### El truco de la mayoría (15 min)

Concepto sencillo: ejecuta el mismo prompt N veces con temperatura > 0, recoge las N respuestas, elige la respuesta que aparece más veces (votación por mayoría). Funciona especialmente bien cuando el problema tiene una respuesta numérica o categórica única.

**Coste vs ganancia:**

- Si pasas de N=1 a N=5, multiplicas el coste por 5 para una mejora típica del 5-15 % en accuracy.
- Vale la pena en tareas críticas (clasificación médica, decisiones automatizadas con valor económico).
- No vale la pena en tareas tolerantes a error (generación de texto creativo, brainstorming).



#### La base de los agentes (25 min)

ReAct (Reason + Act) es el patrón fundamental de los agentes modernos.

Pizarra: dibuja el bucle:

```text
Thought: ¿Qué debería hacer?
Action: llamar herramienta X
Observation: resultado de X
Thought: ¿Ahora qué?
Action: llamar herramienta Y
Observation: resultado de Y
...
```

Insiste en dos cosas:

- Cada turno es una llamada nueva a la API. No es magia, es código en bucle.
- Hay que poner un guard de seguridad (máximo N iteraciones) o el modelo puede entrar en loop infinito y vaciarte la cuenta.



#### Provoca el bug del loop (15 min)

Implementa en vivo un ReAct minimal con un bucle `while not finished and iterations < 10`.

- Hazlo sin el guard al principio.
- Lánzalo.
- Cuando entre en loop (puede pasar con prompts mal diseñados), pulsa Ctrl+C dramáticamente, abre tu consola de OpenAI en pantalla y muestra que has gastado 50 céntimos en 30 segundos.
- Después añades el guard y reejecutas.

Este teatro vale más que cualquier diapositiva de «sed cuidadosos».

---



### Cómo conducir la práctica



#### Setup (3 min)

Reparte 10 problemas de palabras (sumas, restas, productos con varios pasos). Indica que deben resolver cada uno con tres estrategias:

- Zero-shot directo.
- CoT explícito.
- Self-consistency con N=5.

Mantener una tabla con accuracy y coste estimado de cada estrategia.

#### Ejecución (35 min)

El alumno escribe tres funciones: `solve_zero_shot()`, `solve_cot()`, `solve_self_consistency(n=5)`. Pasa cada problema por las tres, anota resultados.

Al final, calcula la tabla resumen. Lo más interesante: comparar coste vs ganancia.

#### Puesta en común (7 min)

Recoge resultados. Esperable:

- Zero-shot ~60-70 % accuracy.
- CoT ~85-90 %.
- Self-consistency ~92-95 %.

Coste: zero-shot 1x, CoT 1.5-2x (más tokens de salida), Self-consistency 5x.

> **Conclusión profesional:** CoT casi siempre vale la pena; Self-consistency solo cuando el problema es crítico.



#### Setup (5 min)

Reparte el notebook base con dos tools dummy ya implementadas: `calculator(expression: str)` y `search_database(query: str)` que busca en una lista hardcodeada de empleados. Esqueleto del bucle incompleto.

La tarea: completar el bucle y probarlo con preguntas como «¿Cuánto cobra María Pérez al año?», «¿Es Juan Gómez el empleado mejor pagado?».

#### Ejecución (20 min)

El alumno completa el bucle:

- Parsear la decisión del modelo.
- Ejecutar la tool.
- Devolver la observación.
- Continuar.

Hazte presente: los puntos donde se atascan son normalmente el parsing de la salida del modelo (cuando elige tool sin formato consistente) y la construcción del siguiente prompt con la observación añadida.

#### Puesta en común (5 min)

Pide a un alumno que ejecute su agente en pantalla con una pregunta nueva improvisada. Mira el aula durante el «Thought - Action - Observation - Thought». Es uno de los momentos que más cambian la percepción del alumno: «ah, los agentes son esto».

---



## Síntesis antes de las APIs

En el cierre, repasa la jerarquía aprendida en las 3 sesiones:

1. Prompt profesional (roles, contexto, formato).
2. Zero-shot vs few-shot.
3. Structured outputs nativos.
4. CoT y Self-consistency.
5. ReAct para agentes.

Anuncia el sub-módulo 2 con honestidad:

> «Hasta ahora todo OpenAI. Mañana entramos en serio en las tres APIs (Anthropic y Google añadidas). Vais a ver que el 80 % es común y el 20 % son diferencias importantes que conviene dominar».

---



## APIs de LLMs en producción

Una sesión de fundamentos comunes y una sesión dedicada a cada uno de los tres proveedores líderes: **OpenAI**, **Anthropic** y **Google**. Mismas tareas, tres APIs.

---



## Sesión 04: Anatomía de una API de LLM

Lo común a las tres: autenticación, parámetros, streaming, errores y reintentos. La sesión que evita repetir conceptos en las tres APIs.

### Lo que el alumno se lleva de hoy

Al final de la sesión 04, el alumno debe ser capaz de:

- Hacer llamadas HTTP crudas y con SDK.
- Entender parámetros clave (temperature, max_tokens, stop).
- Implementar streaming con retry.
- Usar exponential backoff ante errores 429 y de conexión.



### Cómo dar la franja teórica



#### Mostrar la request cruda primero (20 min)

Antes de usar SDKs, muestra la llamada HTTP cruda. Esto desmitifica las APIs y permite que el alumno entienda que el SDK es solo una conveniencia:

```http
POST https://api.openai.com/v1/chat/completions
Authorization: Bearer sk-...
Content-Type: application/json

{
  "model": "gpt-4o-mini",
  "messages": [{"role": "user", "content": "Hola"}],
  "temperature": 0.7,
  "max_tokens": 100
}
```

Ejecuta en vivo. Cuando aparezca el JSON de respuesta, lee en voz alta cada campo.

Después di: «El SDK de OpenAI hace exactamente esto, pero te ahorra escribir la URL, parsear el JSON y manejar la auth. Es Python amigable encima de HTTP. Punto».

#### La demo de temperatura (25 min)

Para temperature, haz una demo cuantitativa:

- Pasa "Escribe una frase sobre el mar" con `temperature=0` tres veces (las tres respuestas serán casi idénticas).
- Luego con `temperature=1.5` tres veces (creativas, dispares, alguna rara).

El concepto queda fijado para siempre.

Sobre `max_tokens`: aclara que limita la SALIDA, no la entrada. Si lo pones a 50, el modelo te corta a 50 tokens incluso a mitad de frase. Es tu mecanismo de seguridad para no dispararte costes en outputs largos inesperados.

Sobre `stop`: secuencias que, si el modelo las genera, hacen que pare. Útil para formatos como «Pregunta: ... Respuesta:» donde quieres que el modelo pare antes de empezar una segunda pregunta.

#### Demo del «typewriter effect» (15 min)

Muestra lado a lado:

- La misma llamada con `stream=False` (tarda 4-5 segundos en silencio y aparece todo de golpe).
- Con `stream=True` (empieza a escupir tokens en 200 ms y va completándose).

Pregunta al aula:

> «¿Qué experiencia es mejor para un chatbot?»

Respuesta unánime: el streaming.

**Trade-off honesto:**

- Streaming complica el código (procesar chunks, manejar errores a mitad de stream).
- Dificulta cosas como structured outputs (no puedes validar JSON parcial).

**Regla del oficio:**

- Streaming para UX conversacional.
- Sin streaming para pipelines internos donde solo importa el resultado final.

---



#### Provocar el 429 en vivo (20 min)

Esto es teatro útil. Prepara ANTES de clase un script que lance ~100 llamadas concurrentes a un modelo con rate limit bajo (gpt-4o nivel free, o tu cuenta de demos).

Guion en pantalla:

1. Lanza el script.
2. A los pocos segundos empiezan a aparecer errores 429 "Rate limit exceeded".
3. Lee el error en voz alta. No lo escondas.
4. Explica: en producción esto pasa todo el rato. Sin retry, tu app cae cada vez que hay un pico.
5. Escribe en pizarra el patrón de exponential backoff (cinco líneas):
  ```python
   import time, random

   def call_with_retry(fn, max_retries=5):
       for attempt in range(max_retries):
           try:
               return fn()
           except RateLimitError:
               sleep = (2 ** attempt) + random.uniform(0, 1)  # jitter
               time.sleep(sleep)
       raise Exception("Agotados los reintentos")
  ```

Insiste: CINCO LÍNEAS defienden contra el 90 % de los problemas operativos. Todo cliente API que llegue a producción debe llevar retry.

### Cómo conducir la práctica



#### Ejercicio A · SDK vs HTTP crudo

- Tarea: implementar la MISMA llamada a OpenAI de dos formas:
  1. Con el SDK `openai`.
  2. Con `requests.post` a la URL HTTP directa.
- Comparar el código resultante y el response.
- Beneficio pedagógico: DESMITIFICAR EL SDK. Cuando vean lo poco que añade, sabrán que pueden cambiar de proveedor sin miedo.



#### Ejercicio B · stream_with_retry

- Tarea: construir una función `stream_with_retry(messages, model)` que:
  - Llame al modelo con streaming.
  - Capture `RateLimitError` y `APIConnectionError`.
  - Aplique exponential backoff.
  - Devuelva el texto completo concatenado.
- Probar provocando errores deliberadamente (muchas requests en paralelo o forzando timeouts cortos).

> **Nota — El alumno avanzado quiere usar asyncio**
>
> Para concurrencia adecuada en producción se usa `asyncio` + `httpx` + el cliente async del SDK. Si alguien quiere ir por ahí, ofrécele código de ejemplo en privado al final de la sesión, pero NO lo metas en el ejercicio común. La concurrencia async pertenece a un módulo posterior; aquí basta con retry síncrono.

---



## Sesión 05: OpenAI API en profundidad

Chat Completions vs Responses API, modelos disponibles, function calling, structured outputs y patrones de uso típicos.

### Cómo dar la franja teórica — Los puntos críticos de OpenAI



#### Distinción clara y honesta (15 min)

- Chat Completions: API histórica (2023+), muy madura y bien documentada.
- Responses API (2024+): nueva, unificada; integra mejor tools, streaming y structured outputs, y mantiene estado entre llamadas.
- Diferencia clave: Responses tiene **STATEFUL CONVERSATIONS** (pasas un `previous_response_id` en vez de reenviar todo el historial).
- Recomendación operativa: PARA EMPEZAR Y PARA CASI TODO, Chat Completions sigue siendo perfecta. Si en producción los historiales son muy largos y reenviarlos cada vez es caro, migrar a Responses. En el bootcamp usamos Chat Completions; menciona Responses pero no te detengas.



#### Cuándo elegir cuál (15 min)

Tabla mental que debes dejar fijada (modelos por tiers: pequeño/rápido → medio → premium/razonamiento).

**Regla del oficio:** EMPIEZA SIEMPRE POR EL MODELO MÁS PEQUEÑO Y BARATO. SUBE SOLO SI LA CALIDAD NO ES ACEPTABLE. Es uno de los puntos donde más dinero se desperdicia en producción.

#### El patrón completo (40 min combinados)

Pizarra: dibuja el flujo de function calling:

```text
usuario → modelo (decide tool) → TU código ejecuta la tool → observación vuelve
al modelo → respuesta final.
```

Después, live coding del ciclo completo.

Insiste: EL MODELO NO EJECUTA LA FUNCIÓN; te dice cuál llamar y con qué argumentos. La ejecución la haces TÚ. Es uno de los puntos que más se confunde.

### Cómo conducir la práctica



#### Ejercicio A · Agente con tools

- Tres tools dummy sobre una lista en memoria:
  - `list_events()`
  - `create_event(title, date)`
  - `delete_event(id)`
- El alumno construye un asistente que mantiene conversación y usa las tools cuando hacen falta. **GUARD DE ITERACIONES OBLIGATORIO.**
- 30 min trabajo + 15 min puesta en común con demos de 2 alumnos.



#### Ejercicio B · Structured outputs con anidamiento

- Schema Pydantic con anidamiento (factura tiene líneas; cada línea tiene producto y cantidad). Extraer 20 facturas y validar.
- Errores típicos: el modelo se inventa códigos de producto que no existen; formatea el total con coma en lugar de punto.
- Discusión: ¿se valida en Pydantic o se corrige el prompt?

---



## Sesión 06: Anthropic API en profundidad

Messages API, system top-level, tool use, prompt caching y extended thinking. Mismas tareas de la sesión 05, con las diferencias de Anthropic.

### Cómo dar la franja teórica — Las diferencias que importan



#### Tabla comparativa en pizarra (15 min)

Dos columnas: OpenAI | Anthropic. Una fila por diferencia (auth, system prompt, formato de messages, formato del tool definition, lectura del response, forma de devolver `tool_result`).

Mensaje: 80 % común; 20 % distinto pero importante de dominar. Quien entiende esta tabla lee cualquier código de cualquiera de las dos APIs sin sorpresa.

#### Cuándo usar cuál (15 min)

Misma jerarquía mental que con OpenAI. La regla empieza-pequeño-y-sube también aplica aquí.

#### Tool use, mismo patrón / formato propio (20 min)

Live coding del mismo asistente de la sesión 05, ahora con Anthropic. Que vean lado a lado lo que cambia y lo que se mantiene.

Pregunta al aula: «¿qué cambia y qué se mantiene?»

#### Prompt caching (20 min) — LA FEATURE QUE CAMBIA EL JUEGO EN PRODUCCIÓN

- Concepto: si reenvías el mismo system prompt o las mismas instrucciones largas en cada llamada, Anthropic puede cachearlas y solo cobra ~10 % por los tokens cacheados.
- Demo: misma llamada con un system prompt de 5 KB, primero sin cache (~$0.02 input) y luego con `cache_control` en ese bloque. La segunda cuesta una décima parte y baja la latencia.
- Es la feature por la que mucha gente elige Anthropic en producción.
- TRAMPA A EVITAR: la cache tiene TTL (típicamente 5 min). Si tu app llama esporádicamente cada hora, la cache no te ayuda. Es para apps con tráfico sostenido sobre el mismo contexto.



#### Extended thinking (10 min) — EL CoT INDUSTRIALIZADO

- Cómo se activa: `thinking={"type": "enabled", "budget_tokens": 10000}`.
- El modelo dedica esos tokens a pensar antes de responder. Se pagan pero no se ven (salvo que pidas explícitamente verlos).
- Cuándo usarlo: problemas complejos, debugging, razonamiento estructurado.
- Cuándo NO: clasificación, extracción, respuestas cortas (desperdicio de dinero y latencia).



### Cómo conducir la práctica



#### Ejercicio A · Porting del agente de tools

- Replicar el ejercicio 09 con Anthropic. Mismas tres tools, mismo objetivo.
- El alumno aprende PORTANDO: cambia el formato del tool definition (`input_schema`), la lectura del response (`content` como lista) y la forma de devolver el resultado (mensaje user con content de tipo `tool_result`).
- Comparación final: ¿coste similar? ¿calidad similar? ¿qué API te resultó más cómoda?



#### Ejercicio B · Prompt caching en acción

- Sobre un system prompt largo (5 KB, contenido de manual técnico que aportas), el alumno hace 10 preguntas relacionadas.
- Primera ronda SIN caching. Segunda ronda CON `cache_control` en el bloque del manual.
- Compara: tokens facturados (`usage.cache_creation_input_tokens` y `usage.cache_read_input_tokens`), latencia, coste total estimado.
- Conclusión del aula: ¿cuándo en la vida real has reenviado lo mismo 10 veces? Más a menudo de lo que parece.

> **Nota — «¿Cuál es mejor, OpenAI o Anthropic?»**
>
> Respuesta honesta: ninguna es siempre mejor. Ahora mismo Anthropic tiene mejor escritura larga y prompt caching más pulido; OpenAI tiene más madurez de ecosistema, modelos de razonamiento más establecidos y multimodalidad más completa. La elección depende del caso de uso y de la integración existente. Por eso aprendemos las dos. **NO TE CASES CON UN PROVEEDOR EN CLASE.**

---



## Sesión 07: Google Gemini API

SDK `google-genai`, contexto largo (1M-2M tokens), grounding con búsqueda y schema responses. Cierre del sub-módulo de APIs con comparativa de los tres.

### Cómo dar la franja teórica — Las fortalezas distintivas de Gemini



#### La consola más amigable de las tres (15 min)

- Google AI Studio (NO confundir con Vertex AI) es la consola de pruebas más amigable de los tres proveedores.
- Tour rápido en pantalla: chat directo, pestaña de prompts guardados, comparativa entre modelos, generación de código en varios lenguajes a partir del prompt.
- Excelente para que los alumnos prototipen antes de saltar al código.
- SDK: `google-genai` es la versión nueva (sustituye al antiguo `google-generativeai`). Pueden encontrarse docs con el SDK viejo. **ACLARA QUÉ VERSIÓN USAMOS.**



#### Contexto largo (20 min) — EL FEATURE DIFERENCIADOR

- 1M tokens en Flash, 2M en Pro. Para asimilar la cifra: 1M tokens ≈ 750.000 palabras ≈ la serie completa de Harry Potter (los 7 libros).
- Cambia el paradigma: en lugar de partir documentos y hacer RAG, metes el documento entero en el prompt en una sola llamada.
- Caveats honestos: saturar contexto sale caro; la calidad de detalle fino puede bajar.
- Regla del oficio: CONTEXTO LARGO PARA UNA LLAMADA PUNTUAL SOBRE UN DOCUMENTO; RAG PARA ACCESO REPETIDO Y SELECTIVO. Los dos conviven, no se excluyen.



#### Grounding con búsqueda (15 min)

- Activar grounding es añadir una tool del proveedor al prompt.
- Demo en vivo con una pregunta cuya respuesta es muy reciente. Compara con la misma pregunta a un modelo sin grounding: el primero da datos con fuentes verificables; el segundo o no sabe o alucina.
- Cuándo NO usar grounding: tareas internas con datos propios (ahí necesitas RAG).



#### Tabla mental para el alumno (10 min)

Antes de la práctica, deja en pizarra la tabla comparativa de los tres providers (fortaleza distintiva de cada uno). Esta tabla es la victoria pedagógica del sub-módulo 2. Si el alumno la entiende y la usa, ha aprendido a elegir como un ingeniero.

### Cómo conducir la práctica



#### Ejercicio A · Documento entero en contexto

- Aporta un PDF de 80-100 páginas (dominio público: sentencia judicial, paper, libro técnico de Project Gutenberg).
- El alumno lo carga como contenido, hace 10 preguntas que requieren entender partes distintas, y mide qué tal responde Gemini.
- Discusión: ¿qué preguntas responde excelentemente y cuáles flojea?
- Intuición: muy bueno en preguntas GLOBALES (resúmenes, temas principales); menos preciso en datos enterrados muy específicos.



#### Ejercicio B · Mini-proyecto integrador del sub-módulo 2

- Extraer información estructurada (Pydantic) de 5 textos comerciales largos y razonar sobre ellos.
- Ejecutar lo mismo en los TRES providers con el mismo prompt y rellenar tabla comparativa: latencia, tokens facturados, coste estimado, calidad subjetiva (1-5), facilidad del SDK.
- Cada alumno escribe una frase: «Si tuviera que llevar esto a producción, elegiría X porque...». La pluralidad de respuestas es la prueba de que han formado criterio.

---



## Cierre del sub-módulo 2 — Lo que se llevan tras 4 sesiones de APIs (10 min)

**Síntesis explícita:** las APIs no son intercambiables, pero son *traducibles*. Quien domina una puede leer las otras con un par de horas.

Lo importante no es memorizar la sintaxis sino entender los **patrones comunes**, que son universales:

- `messages`
- `tools`
- structured outputs
- streaming
- retries

**Anuncio del sub-módulo 3: multimodalidad.** Hasta ahora todo texto-texto. Mañana entran imágenes, después audio, después documentos complejos. El bootcamp se vuelve mucho más visual.

---



## Sub-módulo 3 — Modelos multimodales

Hasta aquí texto-texto. A partir de ahora, imágenes, audio, vídeo y documentos. La frontera donde los LLMs dejan de ser «chatbots» para ser interfaces universales.

---



## Sesión 08 — Visión por LLM (3 h)

Enviar imágenes a los modelos multimodales: descripción, OCR, análisis de gráficos, comparación. Coste, calidad y limitaciones.

### Lo que el alumno se lleva de hoy

Al final de la sesión 08, el alumno debe ser capaz de: *(objetivos de aprendizaje)*

### Antes de entrar al aula

*(checklist de preparación)*

### Cómo dar la franja teórica



#### La idea es más simple de lo que parece (15 min)

Explicación intuitiva: el modelo divide la imagen en *patches* (cuadraditos de típicamente 14×14 píxeles), convierte cada patch en un vector que vive en el mismo espacio que los embeddings de texto, y los pasa al transformer como si fueran tokens más. Para el modelo, una imagen es **una secuencia de tokens visuales** que va antes (o intercalado) con tokens de texto. De ahí que pague por «tokens de imagen».

No te metas en arquitectura interna. La intuición de «la imagen se convierte en tokens y vive en el mismo prompt» basta para todo el sub-módulo.

#### URL vs base64 (15 min)

Tres maneras de meter una imagen. Regla práctica: usar `low` cuando solo necesitas el «gist» de la imagen (qué hay, descripción general); usar `high` cuando necesitas leer texto pequeño o detalles. La diferencia de coste es **5-20x**.

#### La factura sorprende (15 min)

Demo: muestra la consola del provider con el detalle de uso después de unas llamadas con imágenes. El alumno suele asumir que «una imagen es una imagen» y pesa lo mismo que una palabra. Cuando ve que una sola foto en `detail: high` son ~1.000 tokens (~el equivalente a 750 palabras), entiende por qué muchas apps no pueden permitirse procesar miles de fotos al día.

Estrategia de optimización que se introduce aquí (se profundiza en la sesión 12): cuando el caso lo permite, **redimensiona la imagen ANTES de mandarla**. Una imagen 4096×3072 redimensionada a 1024×768 ahorra mucho dinero y suele no perder calidad para tareas de descripción.

#### Mostrar los fallos en vivo (15 min)

Esta es una franja crítica del módulo. **Muestra una imagen donde el modelo falle.**

El mensaje pedagógico: *los modelos multimodales son herramientas, no sustitutos universales*. Cuando el caso es manuscrito, denso o con orden espacial complejo, OCR clásico + LLM textual puede ser mejor que LLM multimodal directo. Hay que medir.

#### El patrón estrella (10 min)

Este patrón es lo más útil de la sesión. Combina **visión + structured outputs** en un único pipeline. Que el alumno lo guarde como plantilla mental.

### Cómo conducir la práctica

- **Práctica A:** El alumno aplica el pipeline OCR + Pydantic sobre las 10 facturas. Mide accuracy contra el ground truth proporcionado (campo a campo). Reflexión: ¿qué campos fallan más? ¿hay correlación con calidad de imagen? ¿qué pasa si comparamos GPT-4o-mini vs GPT-4o? El alumno avanzado prueba la misma factura con `detail low` vs `high` y compara coste/calidad.
- **Práctica B:** Cada alumno coge 5 gráficos preparados, los pasa por los tres modelos pidiendo extracción estructurada (tipo, ejes, datos, tendencia). Rellena una tabla comparativa. Lo interesante: probablemente algunos modelos sean mejores en gráficos de líneas y otros en gráficos de barras o pie. La comparativa es parte del aprendizaje.

---



## Sesión 09 — Audio · transcripción y voz (3 h)

Whisper para ASR, TTS de OpenAI y ElevenLabs, APIs de conversación en tiempo real, y el pipeline clásico ASR → LLM → TTS.

### Lo que el alumno se lleva de hoy

Al final de la sesión 09, el alumno debe ser capaz de: *(objetivos de aprendizaje)*

### Cómo dar la franja teórica — El sub-módulo más sensorial



#### La calidad por idioma sorprende (20 min)

Whisper se entrenó con datos en muchísimos idiomas. La calidad en castellano es excelente; en inglés, casi perfecta; en lenguas minoritarias (gallego, catalán, vasco) sigue siendo sorprendentemente buena. Demo en vivo en castellano y en alguna lengua co-oficial.

Modelos disponibles: `whisper-1` (original) y `gpt-4o-transcribe` (nueva generación, mejor en ruido y multilingüe). En el bootcamp usamos el más reciente.

Limitaciones: el archivo no puede pesar más de 25 MB (más o menos 25 minutos de audio comprimido). Para audios largos, hay que partir en chunks y unir transcripciones. Trampa: si cortas a mitad de palabra, la transcripción se rompe. Solución: cortar en silencios con `pydub`.

#### Audio lado a lado (20 min)

Demo perfecta: misma frase generada con voz de OpenAI («alloy» o «nova») y con voz de ElevenLabs (default). Reproduce las dos en altavoces. El aula vota cuál suena mejor. Casi siempre ElevenLabs gana en calidad emocional. Pero OpenAI gana en precio (~10x más barato) y latencia. Por eso conviven en producción: ElevenLabs para audiolibros, narración premium; OpenAI para asistentes y notificaciones.

Honestidad ética: las voces clonadas de ElevenLabs son tan buenas que generan problemas de identidad y desinformación. Comenta brevemente las implicaciones: clonar voz sin consentimiento es éticamente cuestionable y legalmente delicado en algunos países.

#### El cambio de paradigma (20 min)

Pizarra: dibuja dos pipelines en paralelo (clásico ASR → LLM → TTS vs. API Realtime).

Realtime es lo que hace que aplicaciones tipo «hablar con el modelo» se sientan naturales. Trade-off: el modelo Realtime es más caro y la API es más compleja (websockets, manejo de eventos, interrumpibilidad). Para batch processing (transcripción de reuniones, podcasts), el pipeline clásico sigue ganando.

#### Algo que ejecutar y oír (10 min)

Tres llamadas, 20 líneas. Ejecuta en vivo. Que se oiga el `output.mp3` por altavoz. Es el momento «funciona de verdad» de esta sesión.

### Cómo conducir la práctica

- **Práctica A:** Sobre el dataset de 5 audios de reunión corta, el alumno transcribe con Whisper y pasa cada transcripción al LLM con un prompt que pide estructura: temas tratados, decisiones, action items. Salida con Pydantic. Reflexión: ¿qué pasa con los audios con ruido? ¿el LLM pone palabras que Whisper no transcribió bien? Conexión con sesiones anteriores.
- **Práctica B:** El ejercicio más visceral del sub-módulo 3. El alumno completa el esqueleto: cargar audio del micro (o de archivo si no hay micrófono), pasarlo por el pipeline, reproducir la respuesta. 5 turnos de conversación con memoria. Al final el alumno tiene un mini-asistente de voz funcional en su máquina. Es uno de los entregables más motivadores del módulo.

> **Si el aula no tiene micrófono:** Algunos portátiles no tienen micrófono integrado funcional. Plan B: que graben con el móvil, lo transfieran al portátil y carguen el archivo desde disco. El pipeline funciona idéntico. No pierdas tiempo intentando configurar micrófonos en clase.

---



## Sesión 10 — Documentos y vídeo (3 h)

PDFs nativos en Claude y Gemini, vídeo en Gemini, workflows con múltiples documentos. Cierre del sub-módulo 3 con teaser de RAG.

### Lo que el alumno se lleva de hoy

Al final de la sesión 10, el alumno debe ser capaz de: *(objetivos de aprendizaje)*

### Cómo dar la franja teórica — Cuando el documento habla solo



#### La diferencia respecto a la sesión 08 (20 min)

En la sesión 08 vimos cómo mandar un PDF convertido a imágenes (página a página). En esta sesión vemos la alternativa moderna: Anthropic y Google permiten subir el PDF como tal y el modelo lo procesa directamente, accediendo a texto, layout y elementos visuales en un solo paso.

Ventajas: una sola llamada, mejor entendimiento del orden de lectura, menos código. Inconvenientes: el coste se calcula sumando todos los tokens del PDF entero (incluso los que no interesan), y para documentos muy largos puedes saturar el contexto rápido.

Regla: **PDFs de hasta ~50 páginas, nativo. PDFs gigantes o cuando solo te interesa una sección, RAG.**

#### El patrón base (15 min)

El modelo lee el PDF entero antes de responder. Que el alumno vea en `usage.input_tokens` lo que ha costado.

#### El caso de uso más impactante (20 min)

Gemini procesa vídeo de forma nativa. Subes un MP4, el modelo lo analiza frame a frame (muestreando, no realmente frame por frame) y puede responder preguntas sobre lo que ocurre, transcribir diálogos, identificar escenas, extraer momentos por timestamp.

Demo en vivo: sube el vídeo, pregunta «¿qué pasa entre el segundo 10 y el 20?». La respuesta sorprende.

Limitaciones honestas: vídeos largos (más de unos minutos) son caros y la calidad de detección puntual cae. El modelo muestrea frames, no ve cada uno. Para análisis frame-perfect (deportes, vigilancia precisa), modelos especializados.

#### El puente al próximo módulo (25 min)

Esta franja es importante: prepara el terreno para el módulo siguiente del bootcamp. Pizarra: dibuja una arquitectura RAG simple.

El concepto clave: **cuando los datos no caben en el contexto, no se manda todo, se manda lo relevante.** RAG es la solución cuando tienes miles de documentos o cuando necesitas búsqueda actualizable. No la cubrimos en este módulo: hay un módulo entero para ello.

### Cómo conducir la práctica

- **Práctica A:** El alumno elige uno de los tres PDFs proporcionados y construye un mini-sistema de Q&A con preguntas predefinidas y un prompt que pide citar páginas. Prueba Claude y Gemini sobre el mismo PDF. Compara: calidad de respuesta, capacidad de citar correctamente, latencia, coste. El paper académico es el caso más difícil (terminología técnica); el contrato suele dar las mejores respuestas (estructura clara).
- **Práctica B:** Sobre el vídeo proporcionado, extraer estructura: lista de escenas con timestamps, transcripción si hay diálogo, momentos clave, descripción de estilo visual. Salida JSON validada con Pydantic. Discusión: ¿qué tipo de preguntas responde Gemini mejor? Suelen ser las temporales (qué pasa antes/después) y las descriptivas. Suele fallar en preguntas que requieren conteo preciso o detección frame-perfect.

---



## Cierre del sub-módulo 3 — Lo que se llevan tras visión, audio y documentos

**Síntesis explícita:** los modelos modernos no son chatbots, son **interfaces universales**. Texto, imagen, audio y vídeo entran y salen por la misma puerta. Los patrones aprendidos en sub-módulos anteriores (structured outputs, tools, retry) aplican igual en multimodalidad.

El sub-módulo 4 cierra el módulo bajando a la ingeniería invisible que hace que todo esto funcione a escala.

---



## Sub-módulo 4 — Tokens, costes, latencia y rate limits

La ingeniería invisible. Lo que separa un prototipo que funciona en demo de una aplicación que sobrevive en producción.

---



## Sesión 11 — Tokens · contar y optimizar (3 h)

Qué es un token técnicamente, cómo se cuentan en cada modelo, estrategias de compresión y truncación. La unidad económica de los LLMs.

### Lo que el alumno se lleva de hoy

Al final de la sesión 11, el alumno debe ser capaz de: *(objetivos de aprendizaje)*

### Cómo dar la franja teórica — La unidad económica del bootcamp



#### La web del tokenizer es imbatible (20 min)

Abre `platform.openai.com/tokenizer` en pantalla. Pega frases y muéstrales cómo se trocean en colores. Ejemplos para que vean los patrones.

Concepto a fijar: **token ≠ palabra ≠ carácter**. Los tokens son la unidad estadística que el modelo aprendió.

#### El patrón básico (20 min)

Insiste: **contar tokens antes de mandar** es disciplina profesional básica. Te ahorra sustos en producción.

- Anthropic ofrece `client.messages.count_tokens(...)` que hace lo mismo para sus modelos.
- Google tiene `model.count_tokens(...)`.

Tres APIs, tres tokenizers, tres conteos distintos para la misma frase. Importante.

#### Por qué castellano es más caro (10 min)

Los tokenizers se entrenaron principalmente con inglés. Cualquier otro idioma es menos eficiente. Demo cuantitativa.

Implicación práctica: una app para usuarios hispanohablantes cuesta un **30-40 % más en tokens** que la equivalente en inglés. Cuando hagas presupuestos, no lo olvides.

#### Las tres técnicas que más sirven (20 min)

Demo: prompt de 3000 tokens convertido en 800 tokens con las tres técnicas. Misma respuesta del modelo. Ratio de compresión 4x. **Ese ratio es típico cuando se aplica con criterio.**

#### Cuando ya no cabe (15 min)

Tres estrategias en orden de complejidad creciente. Para el bootcamp basta con conocer las tres. La implementación detallada de hierarchical memory pertenece al módulo de agentes.

### Cómo conducir la práctica

- **Práctica A:** El alumno construye un módulo `count.py` con una función `count_tokens(text, provider, model)` que llama al tokenizer apropiado según el provider. Sobre un dataset de 50 textos (mezcla de castellano, inglés y código), mide tokens en cada provider y guarda un CSV. Discusión: ¿qué provider es más generoso? ¿en qué tipo de texto las diferencias son mayores?
- **Práctica B:** Sobre un prompt sistema de ~3000 tokens (instrucciones detalladas, ejemplos, formato), el alumno aplica las tres estrategias de compresión. Tras cada iteración, mide tokens y la accuracy sobre 5 casos de prueba (proporcionados con ground truth). El objetivo: bajar de 3000 a 1000 sin perder más de 5 puntos de accuracy. Es difícil. Probablemente solo lo consigan los alumnos avanzados. Para el resto, marcar el ratio que han conseguido es éxito suficiente.

---



## Sesión 12 — Costes y arquitectura económica (3 h)

Pricing de cada provider, input vs output, caché, Batch API y la matriz de decisión que separa apps rentables de las que no lo son.

### Lo que el alumno se lleva de hoy

Al final de la sesión 12, el alumno debe ser capaz de: *(objetivos de aprendizaje)*

### Cómo dar la franja teórica — La economía de los LLMs



#### Saber leer una tabla de precios (25 min)

Pizarra con tres columnas (OpenAI, Anthropic, Google) y filas para los modelos comparables. Coste de input y de output por millón de tokens. Datos orientativos a 2026 (**cambian; verifica antes de impartir**).

Insiste: estos precios bajan periódicamente. Hace 2 años eran 10x más caros que hoy. La tendencia es a la baja, pero los modelos nuevos «top» siguen apareciendo en la zona alta y los maduros bajan.

#### Implicación práctica (10 min)

El output es **3-5x más caro** que el input. Razón técnica: cada token de output requiere una pasada por el modelo, mientras que el input se procesa en una sola pasada paralela.

Establece `max_tokens` conservador siempre. Es la defensa contra costes inesperados.

#### Pizarra con cuatro cuadrantes (20 min)

- Eje X: **complejidad de la tarea** (simple ↔ compleja).
- Eje Y: **tolerancia a error** (alta ↔ baja, p. ej. en medicina baja, en sugerencias de UI alta).

Cuatro cuadrantes.

#### El patrón estrella (15 min)

Idea: la mayoría de inputs en producción son «fáciles», unos pocos son «difíciles». No tiene sentido pagar el premium en todos.

Implementación real en producción: ahorro típico del **60-80 %** con caída marginal en calidad (porque el modelo barato cubre los casos donde es competente y solo el caro entra en los difíciles). Es uno de los patrones más infravalorados del oficio.

#### Cuándo aceptar 24h de espera (15 min)

Batch API: subes un JSONL con miles de requests, lo procesan en hasta 24h con **50 % de descuento**.

Ideal para: tareas diferibles. No aplica a: chatbots, asistentes en vivo, cualquier cosa con usuario esperando. Para todo lo demás, considera siempre Batch antes que síncrono.

### Cómo conducir la práctica

- **Práctica A:** Caso ficticio: asistente de soporte para una empresa SaaS con 5.000 usuarios activos mensuales, una media de 4 consultas/usuario/mes, longitud media 200 tokens de entrada + 400 de salida. ¿Cuánto cuesta al mes si lo hacemos con gpt-4o vs gpt-4o-mini vs Sonnet vs Haiku? El alumno rellena la calculadora de Excel y obtiene las cuatro cifras. Choque típico: el premium puede costar miles de dólares al mes mientras el eficiente cuesta cientos. Decisión clara para la mayoría de casos.
- **Práctica B:** Sobre el mismo caso, proponer una arquitectura optimizada. Sugerencias a explorar: cascada (clasificador Haiku, escalado a Sonnet en casos complejos), prompt caching (el system prompt común se cachea), Batch para reportes nocturnos, `max_tokens` conservador. Estimar el ahorro vs la solución «un solo modelo premium». Presentar a la clase en 1 minuto cada arquitectura. Discusión final: ¿qué arquitectura propuso mayor ahorro? ¿es viable mantenerla a largo plazo o aumenta complejidad de operación?

---



## Sesión 13 — Latencia y rate limits (3 h)

Time-to-first-token, tokens-per-second, streaming, errores 429, retry con exponential backoff, concurrencia y benchmarking. Cierre del módulo.

### Lo que el alumno se lleva de hoy

Al final de la sesión 13, el alumno debe ser capaz de: *(objetivos de aprendizaje)*

### Cómo dar la franja teórica — La ingeniería invisible



#### Las dos métricas que importan (20 min)

Pizarra: dibuja una línea de tiempo de una llamada. Marca **TTFT** (tiempo hasta el primer token) y **TPS** (velocidad de generación una vez empezada).

Por qué importa la distinción: para un chatbot, el TTFT alto se nota mucho aunque el TPS sea bueno (el usuario espera al primer token). Para generar un informe largo en background, el TPS importa más (cuántos minutos tarda en total).

Demo: ejecuta una misma pregunta en gpt-4o-mini y en Opus con thinking, midiendo ambas métricas y mostrándolas en pantalla. El delta sorprende.

#### La frustración más común en producción (20 min)

Tres tipos de límite. Los límites suben automáticamente con uso y antigüedad de cuenta. Hay tiers (1, 2, 3, 4, 5 en OpenAI) que se desbloquean al gastar X $ acumulado.

**Atención:** los rate limits pueden cambiar bruscamente cuando un modelo nuevo se lanza (los pasados se relajan, los nuevos arrancan apretados).

#### Refinamiento del patrón de la sesión 04 (15 min)

El retry simple de la sesión 04 funciona, pero cuando 100 clientes reciben 429 simultáneamente y todos reintentan al mismo tiempo, vuelven a chocar (*thundering herd*). Solución: **jitter** (ruido aleatorio en el wait). Patrón estándar con `tenacity`.

`tenacity` es la librería estándar en Python para retries. Casi todo el código de producción serio la usa. Es uno de los patches one-liner más rentables del oficio.

#### De 1 a N requests por segundo (15 min)

Patrón básico. El semáforo es la pieza clave: limita a 10 concurrentes simultáneos para respetar rate limits. Sin él, mandar 1000 peticiones a la vez te da un 429 inmediato.

#### Cómo medir bien (10 min)

Reglas para benchmarks honestos.

### Cómo conducir la última práctica

- **Práctica A:** Procesar 200 prompts cortos. Primera ronda: en secuencial con retry simple. Segunda ronda: con asyncio + semáforo + tenacity. Medir tiempo total. Reflexión cuantitativa: ¿cuántas veces más rápido? Típicamente entre **8x y 15x** dependiendo de concurrencia y latencias. Comentar trade-off: la concurrencia consume rate limit más rápido; hay que balancear paralelismo y prudencia.
- **Práctica B:** Cada alumno benchmarkea TTFT y TPS sobre los tres modelos eficientes (gpt-4o-mini, Haiku 4.5, Gemini 2.5 Flash) sobre los mismos 30 prompts. Rellena tabla con P50 y P95. Al final, defiende en una frase: *«Para una app de chat de soporte en tiempo real, elegiría X porque...»*. Es el cierre del módulo y del aprendizaje de criterio.

---



## Cómo terminar las 40 horas

Última franja del módulo. Tres minutos por sub-módulo recordando lo aprendido.

**Anuncio del siguiente módulo: RAG y bases de datos vectoriales.** Recoge dudas globales (5 min). Cierra con la idea fuerza:

> «Habéis pasado de no haber llamado a una API a poder construir aplicaciones reales sobre LLMs. El siguiente módulo os enseña a hacerlas inteligentes sobre vuestros propios datos. Enhorabuena por llegar hasta aquí.»

---



## Rúbrica de salida del módulo 2

Tras las 40 horas el alumno debe haber consolidado un conjunto concreto de capacidades. Esta rúbrica sirve para evaluar individualmente y para que el alumno se autoevalúe antes de entrar al módulo de RAG.

Si un alumno falla más de tres puntos, conviene apartar 30 minutos de tutoría antes de avanzar al siguiente módulo.

**Mini-proyecto de consolidación** (para alumnos que quieren afianzar antes del siguiente módulo):

> «Asistente que recibe el PDF de una factura escaneada, extrae los datos estructurados, los valida con Pydantic, los compara con un catálogo de productos en JSON y genera un informe de discrepancias.»

Aplica visión, structured outputs, tool use y manejo de errores. Es la prueba más completa de las 40 horas y deja al alumno con un entregable real que puede enseñar en una entrevista.

> **Nota final para el docente:** el módulo 2 es el primer momento en el que el alumno siente que está construyendo algo de verdad. Es también donde más se nota la diferencia entre quien ha hecho los ejercicios y quien ha copiado código sin entenderlo. Las preguntas individuales en los últimos 5 minutos de cada sesión son el mejor radar.

