# Módulo 8: LLMOps, Seguridad y Compliance

**Cuatro sub-módulos · ~40 horas aproximadas.** Este es el módulo que cierra el bootcamp y marca la diferencia. Vas a aprender a **operar** sistemas IA en producción: medir si funcionan bien, protegerlos de fallos y abusos, mantenerlos observables, y cumplir con la regulación europea (**AI Act**, **GDPR**) que ya aplica. Al terminar, tu proyecto del M7 habrá evolucionado de "demo que funciona" a "producto desplegable con documentación de compliance".

## Índice de sub-módulos

| Sub-módulo | Contenido |
|---|---|
| **SM0 · Setup del módulo** | Docker ya instalado, Ollama, cuentas gratuitas de LangFuse y MLflow. |
| **SM1 · Evaluación de sistemas LLM** | Datasets de eval, LLM-as-judge, LangFuse open-source, MLflow. |
| **SM2 · Guardrails, alucinaciones y seguridad** | Mitigar alucinaciones, Guardrails AI, defensa de prompt injection. |
| **SM3 · Despliegue LLMOps** | Ollama local, Docker Compose completo, cloud gratuito. |
| **SM4 · Compliance · AI Act y GDPR** | Clasificar tu sistema, DPIA, model cards, proyecto final. |
| **Proyecto Final del M8** | Extender el proyecto M7 con observabilidad, guardrails y compliance. |

> **Prerrequisitos · sin M7 no hay M8:** Este módulo construye sobre el proyecto del M7. Si no lo terminaste, dedica los primeros días a cerrarlo. Todo el valor del M8 viene de aplicar observabilidad, guardrails y compliance a un backend real que ya tienes funcionando.

---

## SM1 · Si no puedes medirlo, no puedes mejorarlo

El 90% de proyectos LLM entran en producción sin evaluación sistemática. Nadie sabe si el prompt nuevo mejora o empeora, las regresiones silenciosas pasan desapercibidas, el equipo se guía por anécdotas. Vas a cambiar esa mentalidad: datasets de evaluación, LLM-as-judge, tracing, versionado de prompts.

### Métricas, datasets, LLM-as-judge

Imagina que cambias el prompt del sistema para arreglar un caso concreto. ¿Cómo sabes que no has roto 5 casos que antes funcionaban? Sin dataset de evaluación, no lo sabes. Esperas a que un usuario se queje. Es exactamente como un backend sin tests: funciona hoy, nadie sabe por cuánto tiempo.

Hay dos tipos de evaluación complementarios:

1. **Offline**: Con dataset fijo antes de deploy.
2. **Online**: Métricas sobre tráfico real post-deploy.

Las dos son necesarias.

#### Sesgos conocidos del LLM-as-judge

- **Position bias**: Prefiere la primera opción en comparaciones.
- **Verbosity bias**: Prefiere respuestas largas.
- **Self-preference**: Favorece outputs de su misma familia.

Mitiga con escalas discretas (1-5), aleatorización de orden, y evaluando con un modelo distinto al evaluado.

#### Ejercicio 1.1 · Tu primer dataset de eval

Crea un dataset pequeño (ej. 20-50 ejemplos) con inputs esperados y criterios de éxito. Implementa un script que use un LLM como juez para puntuar las respuestas.

### Tracing y evaluación en una plataforma

Un **trace** captura toda la cadena de un request: prompts enviados al LLM, respuestas, llamadas a herramientas, latencias, tokens, coste. Sin tracing es imposible debuggear un agente que falla. Un sistema con 5 llamadas a LLM encadenadas tiene 5 puntos de fallo invisibles si no instrumentas.

> Analogía: tracing es a LLMOps lo que logs estructurados son al backend. No es opcional.

Al importar `langfuse.openai` en vez de `openai`, cada llamada queda instrumentada automáticamente: prompt, respuesta, modelo, latencia, tokens, coste USD estimado. Lo mismo existe para Anthropic, LangChain, LlamaIndex, Haystack.

Beneficios:

- Equipo de producto edita prompts sin tocar código.
- Vuelves a una versión anterior en 1 click si rompes algo.
- Comparas métricas entre versiones automáticamente.

#### Ejercicio 1.2 · Instrumenta tu M7

Integra LangFuse en tu proyecto del M7 para visualizar traces y costes.

### Tracking de experimentos y gestión de modelos

Arranca el servidor con:

```bash
mlflow server --host 0.0.0.0 --port 5000
```

La UI permite comparar runs lado a lado: dos prompts, cuatro métricas, un gráfico. Es exactamente lo que falta cuando iteras prompts a ojo.

#### Ejercicio 1.3 · MLflow para versionar evals

Usa MLflow para registrar diferentes versiones de tus prompts y sus resultados de evaluación.

---

## SM2 · Defensa en profundidad · cuando el LLM falla, el sistema no

Un LLM libre produce basura ocasional (alucinaciones), filtra PII sin filtro, obedece inyecciones de prompts, y da respuestas tóxicas si se le pide bien. Los guardrails son la red que convierte un modelo probabilístico en un producto de forma determinista aceptable.

### Qué son, por qué ocurren, cómo reducirlas

Una alucinación es un output que suena plausible pero es factualmente incorrecto o no respaldado por los datos del input. La causa raíz: los LLMs son modelos probabilísticos de secuencias de tokens. No tienen concepto de "verdad". Generan la continuación más plausible dado el contexto, no la correcta.

No hay forma de eliminar completamente las alucinaciones; sí hay formas de reducirlas y detectarlas.

#### Ejercicio 2.1 · Detectar y mitigar alucinaciones

Implementa técnicas como RAG estricto, citas obligatorias o auto-consistencia para reducir alucinaciones en tu proyecto.

### Capas de protección antes y después del LLM

Nunca confíes en un único control. Capas:

- Validación de input.
- Prompt engineering.
- Modelo.
- Validación de output.
- Revisión humana si aplica.

Cada capa reduce la probabilidad de fallo; ninguna aislada es suficiente. Trade-off: más capas = más latencia + más coste. Elige con criterio.

Diferente filosofía: defines flujos conversacionales con un DSL propio (Colang). Permite guardrails de alto nivel: "si el usuario pide consejo médico específico → responde con disclaimer y sugiere profesional". Más potente para control conversacional complejo; curva más empinada. Para apps empresariales regulados (banca, salud) es el estándar emergente.

OpenAI structured outputs (y Anthropic tool use) garantizan respuestas conformes a Pydantic schema. Es el guardrail más barato y efectivo: deberías usarlo siempre que la respuesta tenga estructura.

#### Ejercicio 2.2 · 3 guardrails en tu M7

Implementa tres tipos de guardrails distintos (ej. validación de formato, detección de contenido sensible, restricción de tema).

### La nueva frontera de seguridad

Lectura obligatoria antes de esta lección: [genai.owasp.org](https://genai.owasp.org).

Los 10 ítems:

- LLM01 Prompt Injection
- LLM02 Insecure Output Handling
- LLM03 Training Data Poisoning
- LLM04 Model DoS
- LLM05 Supply Chain
- LLM06 Sensitive Information Disclosure
- LLM07 Insecure Plugin Design
- LLM08 Excessive Agency
- LLM09 Overreliance
- LLM10 Model Theft

Mapea cada ítem a tu proyecto: ¿dónde está expuesto? ¿qué mitigación tienes?

Rebuff (Apache 2.0) combina enfoques: heurísticas, modelo clasificador, canary words. La canary word se inyecta en el system prompt; si aparece en el output, hubo extracción. No es infalible: ningún detector lo es. Es una capa más dentro de defensa en profundidad.

#### Ejercicio 2.3 · Red teaming de tu proyecto

Intenta romper tu propio sistema usando técnicas de prompt injection y observa cómo responden tus guardrails.

---

## SM3 · Operar modelos · locales, contenedores, cloud

Hasta ahora dependías siempre de APIs externas (OpenAI, Anthropic). Este sub-módulo abre la puerta a modelos propios: ejecutar Llama/Mistral/Qwen en local con Ollama, empaquetar todo el stack en contenedores reproducibles, y entender cuándo tiene sentido migrar partes del sistema a servidores propios.

### Llama, Mistral, Qwen, Gemma en tu máquina

Literalmente cambiando `base_url` funciona. Este es el momento del clic: entiendes que el "lock-in" con OpenAI es mucho menor de lo que parecía. Para muchos tasks, un modelo local decentemente afinado es más que suficiente.

#### Ejercicio 3.1 · Ollama en tu proyecto

Configura tu aplicación para poder alternar entre OpenAI y un modelo local vía Ollama.

### Un solo docker compose up para todo

Referencias disponibles en la plataforma.

#### Ejercicio 3.2 · Stack completo compose

Orquesta tu API, base de datos, Redis y servicios auxiliares en un único archivo `docker-compose.yml`.

### De local a URL pública · sin pagar

Más del 60% de empresas serias usan AWS, Azure o GCP. AWS lidera. Un profesional de IA que no haya tocado AWS parte en desventaja en entrevistas.

Objetivo pedagógico aquí: familiaridad, no maestría. 3,5h no te convierten en experto AWS; sí quitan el miedo a usarlo.

Para tu proyecto final del bootcamp, Railway (API) + Vercel (frontend) desde el M7 siguen siendo lo mejor. Si tu proyecto incluye modelo local pesado, Hetzner o Scaleway por precio. AWS lo haces para ponerlo en el CV y entender el ecosistema, no necesariamente para producir el proyecto final.

#### Ejercicio 3.3 · Deploy real con URL pública

Despliega tu stack actualizado en la nube elegida.

---

## SM4 · Normativa europea · no es opcional, ya aplica

El AI Act entró en vigor en agosto 2024 y se aplica progresivamente. GDPR lleva 7 años aplicando. Un ingeniero de IA en Europa que no entienda estas dos piezas trabaja con los ojos cerrados sobre lo que puede y no puede desplegar. Este sub-módulo lo desatasca y cierra el proyecto final.

### Categorías de riesgo y qué significan para el desarrollador

*(Consulta las referencias oficiales del módulo para la clasificación detallada de riesgo mínimo, limitado, alto y prohibido).*

#### Ejercicio 4.1 · Clasifica tu proyecto

Determina en qué categoría de riesgo cae tu sistema según el AI Act y documenta las implicaciones.

### Datos personales, DPIA, decisiones automatizadas

*(Consulta las referencias del módulo sobre GDPR y evaluaciones de impacto).*

#### Ejercicio 4.2 · DPIA mínima de tu proyecto

Realiza una Evaluación de Impacto en la Protección de Datos (DPIA) simplificada para tu sistema.

### Documentar en serio · no es paja, es obligatorio

Crear Model Cards y documentación técnica clara es requisito legal y profesional.

#### Ejercicio 4.3 · Documentar tu sistema

Genera la documentación de compliance y arquitectura necesaria.

---

## Proyecto Final del M8 · Convertir el proyecto M7 en producto responsable

No construyes proyecto nuevo. Extiendes el del M7 con todas las capacidades del M8. Al terminar, tu proyecto es defendible como "producto desplegable" y no solo como "demo que funciona".

### Añadir el "Ops" al proyecto M7 · entregables concretos

- Integración de LangFuse/MLflow.
- Implementación de guardrails.
- Docker Compose completo.
- Documentación de Compliance (AI Act/GDPR).

#### Rúbrica de evaluación · 6 dimensiones

*(La rúbrica evalúa la capacidad de justificar decisiones técnicas y regulatorias).*

### Preguntas típicas del tribunal · 12 que no pueden fallar

La defensa evalúa comprensión, no solo entregables. Un alumno que ha hecho menos pero sabe justificar sus decisiones puntúa más alto que uno con todas las entregas pero incapaz de explicarlas.

---

## Conclusión · LLMOps + AI Safety + AI Act completado

Al cerrar este módulo sales con competencias que la mayoría de "ingenieros de IA" del mercado europeo todavía no tienen: evaluar sistemáticamente, poner guardrails, operar en producción con contenedores y observabilidad, montar modelos locales cuando convenga, y hablar con criterio de AI Act y GDPR. Es la ventaja competitiva real del programa.

Lo que te hace valioso en el mercado es la combinación: construir + operar + cumplir.

Y con esto cierras el bootcamp. Durante 8 módulos has pasado de "nunca he tocado un LLM" (o similar) a tener un backend de IA desplegado, observable, seguro y conforme a la ley. Pocos profesionales en España tienen hoy ese perfil. Úsalo.
