# Módulo 6: IA Multimodal · Voz, Visión y Generación

**Cuatro sub-módulos, catorce lecciones, un proyecto final.** Este módulo cierra la vertiente técnica del bootcamp aplicando IA a las tres modalidades que dominan las aplicaciones actuales: audio (voz), imagen (visión y generación) y su integración multimodal. Priorizamos herramientas open-source para que domines el stack por dentro, no solo APIs cerradas.

## Índice de sub-módulos

| Sub-módulo | Contenido |
|---|---|
| **SM0 · Setup del módulo** | GPU, cuentas, entornos Python, HuggingFace, LiveKit, verificación. |
| **SM1 · Voice agents** | Whisper para ASR, Piper/XTTS/ElevenLabs para TTS, LiveKit para tiempo real. |
| **SM2 · Computer Vision** | LLMs multimodales, CV clásico con YOLO y MediaPipe, OCR de documentos con Docling. |
| **SM3 · Generación de imagen** | Modelos de difusión, Stable Diffusion, FLUX.1, ControlNet, IP-Adapter, LoRA. |
| **SM4 · Apps multimodales** | Arquitecturas end-to-end, agente que ve/escucha/habla, deployment, proyecto final. |
| **Especificación completa** | Requisitos, rúbrica, formato de entrega, plantilla del README. |

---

## Preparación del entorno · GPU es el elefante

Este módulo requiere GPU para inferencia local de modelos abiertos (Whisper large, Stable Diffusion, FLUX). Si no dispones de GPU adecuada, tienes alternativas (Colab, Modal, Replicate) pero debes decidir antes de la primera sesión para no perder tiempo.

> **Coste estimado:** Rango: 5-30 USD según tu perfil.
>
> **Recomendación:** Configura límites de gasto duros en OpenAI y Anthropic desde el día 1. Los agentes multimodales consumen tokens más rápido que agentes de texto puro.

Organiza tu trabajo del módulo desde el día 1.

---

## SM1 · Del archivo de audio a la conversación en vivo

Aprenderás cómo funcionan realmente los sistemas de reconocimiento de voz (ASR) y síntesis (TTS), qué herramientas open-source usar en cada situación, y culminarás construyendo un voice agent completo en tiempo real con LiveKit sobre WebRTC.

### Speech-to-text: Whisper y sus derivados

Un sistema de reconocimiento automático de voz (ASR, Automatic Speech Recognition) convierte audio en texto. Los sistemas modernos, desde 2022, se basan en arquitecturas **encoder-decoder Transformer**. El encoder procesa una representación del audio (típicamente log-mel spectrogram) y el decoder genera el texto de forma autoregresiva, token a token, como un LLM.

Whisper, publicado por OpenAI en septiembre de 2022 como modelo **open-source con pesos abiertos**, cambió el mercado: por primera vez había un ASR de calidad casi comercial disponible sin restricciones, entrenado en 680.000 horas de audio multilingüe.

El paquete `faster-whisper` reimplementa Whisper usando **CTranslate2** (motor de inferencia optimizado). Ofrece la misma calidad que el Whisper original de OpenAI pero **4-5 veces más rápido**, con menor consumo de memoria. Es lo que usarás por defecto en el módulo.

#### Diarización y Streaming

Whisper no distingue hablantes. Si tienes una grabación con dos o más personas, todo se transcribe como un flujo. Para separar por hablante necesitas **diarización**: WhisperX integra Whisper con `pyannote` para hacerlo.

**Whisper NO es streaming por defecto.** Whisper procesa audio en chunks de 30 segundos. Para una conversación en tiempo real necesitas trucos: partir el audio en trozos más pequeños con VAD, mantener buffer overlapping, y aceptar que la latencia de un Whisper local ronda 500-1500ms.

Para latencia realmente baja (<200ms) en tiempo real, las opciones son:

1. `whisper-streaming` (proyecto abierto que hace trucos avanzados).
2. Servicios comerciales optimizados como **Deepgram Nova** o AssemblyAI streaming (free tiers generosos, latencia sub-300ms).

En el SM1 usarás Deepgram para la parte de tiempo real y Whisper local para batch y comparativas. En producción, la decisión depende del presupuesto y del requisito de latencia.

*Lecturas obligatorias de esta lección.*

### Text-to-speech: Piper, XTTS, Kokoro, ElevenLabs

Un sistema TTS moderno tiene tres piezas:

1. **Análisis lingüístico** del texto (normalización, división en fonemas).
2. **Modelo acústico** que predice espectrograma mel a partir de fonemas y prosodia deseada.
3. **Vocoder** que convierte espectrograma en forma de onda de audio.

Los sistemas end-to-end modernos (VITS, StyleTTS 2, F5-TTS) integran las tres piezas.

- **Piper**: Un TTS neuronal basado en VITS optimizado para inferencia en CPU. Extremadamente rápido, huella pequeña, soporta más de 30 idiomas. Ideal para asistentes locales, dispositivos edge, o cuando la latencia importa más que la calidad emocional. Licencia MIT.
- **XTTS-v2 (Coqui)**: Permite clonar una voz a partir de solo 6 segundos de audio de referencia. Multilingüe (17 idiomas incluyendo español), calidad muy alta. La empresa Coqui cerró en 2024 pero el modelo sigue accesible en HuggingFace.
- **Kokoro-82M (finales de 2024)**: Un TTS reciente basado en StyleTTS 2, con licencia Apache 2.0 (uso comercial libre). Calidad sorprendente para su tamaño reducido (82M parámetros). Buena opción cuando necesitas TTS abierto y comercialmente utilizable sin licencias restrictivas como CPML de XTTS.
- **ElevenLabs**: Calidad y prosodia superior al open-source actual. Free tier de 10.000 caracteres/mes. Precio: ~5 USD/mes plan Starter. Justifica su coste cuando la calidad emocional es crítica (audiobooks, personajes de juego, anuncios).

*Lecturas obligatorias de esta lección.*

### Voice agent completo: ASR + LLM + TTS orquestado

Un voice agent une cuatro componentes en un pipeline con streaming. La suma de latencias de cada componente debe estar por debajo de ~800ms para una conversación que se sienta natural. Superar 1500ms se percibe incómodo.

**WebRTC** es el estándar web para audio/video peer-to-peer con baja latencia. Atraviesa NATs, negocia códecs (Opus para audio), maneja pérdida de paquetes. Es lo que usan Zoom, Meet, Discord por debajo.

**LiveKit** es una SFU (Selective Forwarding Unit) open-source que encapsula la complejidad de WebRTC. Incluye **Agents SDK**, un framework en Python para conectar un backend (con tu LLM, ASR, TTS) a una sala WebRTC como si fuera un participante más. Puedes usar LiveKit Cloud (free tier suficiente para el módulo) o self-hosted. LiveKit ofrece un Agents Playground web donde puedes conectarte a la sala y hablar con tu agente sin escribir frontend. Perfecto para desarrollo. Cuando quieras integrar en tu propia app, LiveKit tiene SDKs para React, iOS, Android.

#### Cómo distribuir el presupuesto de ~800ms

- **VAD (~50-100ms)**: Rápido, casi gratis.
- **ASR streaming (~150-300ms)**: Deepgram Nova-2 muy rápido; Whisper local añade 500ms+ por chunk.
- **LLM (~300-500ms)**: Usa modelos rápidos (gpt-4o-mini, Claude Haiku). El TTFT (time to first token) importa más que el total.
- **TTS streaming (~150-300ms al primer chunk)**: ElevenLabs turbo v2.5 o Cartesia. Piper local es más rápido pero menos natural.

> **Truco pro:** Streaming del LLM al TTS palabra a palabra reduce percepción de latencia porque el agente empieza a hablar antes de terminar de pensar.

*Lecturas obligatorias de esta lección.*

### Práctica del SM1 · Tres ejercicios progresivos

1. Construye una pipeline que dado un archivo de audio con dos o más hablantes en español, devuelva un JSON estructurado con la transcripción diarizada.
2. Genera el mismo texto de referencia (5 frases variadas: pregunta con signo, exclamación, número «trescientos cuarenta y dos», nombre propio poco común, palabra técnica en inglés como «streaming») con 3 sistemas TTS distintos.
3. Construye un voice agent en LiveKit para un caso de uso concreto de tu elección. Sugerencias: recepcionista de restaurante, tutor de un tema técnico, asistente de compras, atención inicial en clínica dental.

---

## SM2 · Aplicaciones que ven

Dos aproximaciones que se complementan: LLMs multimodales (GPT-4o, Claude, Qwen2-VL) para tareas cognitivas de alto nivel, y CV clásico (YOLO, MediaPipe, OpenCV) para tareas específicas donde los LLMs no compiten en latencia ni precisión. Cierras con OCR moderno de documentos usando Docling.

### Cuando el LLM ve: GPT-4o, Claude, y alternativas open-source

Un LLM multimodal moderno tiene un encoder visual (típicamente basado en CLIP o similar) que convierte la imagen en una secuencia de tokens visuales. Estos tokens se proyectan al espacio de embeddings del LLM y se procesan junto con los tokens de texto. El decoder genera la respuesta atendiendo tanto a texto como a imagen.

Combinar vision + Pydantic te da una capacidad muy demandada en producción: extraer datos estructurados de imágenes de forma robusta. Facturas, tickets, formularios, DNIs, etiquetas de producto.

#### Qwen2-VL, LLaVA, Pixtral, Molmo

Qwen2-VL (Alibaba, Apache 2.0) es la mejor opción abierta actualmente. Versiones 2B, 7B y 72B. La 7B corre en 12-16 GB VRAM con calidad competitiva contra GPT-4o-mini en muchas tareas.

Justifica open-source cuando:

1. Privacidad crítica (datos que no pueden salir de tus servidores).
2. Escala masiva donde el coste por imagen del API es prohibitivo.
3. Fine-tuning necesario para dominio específico.
4. Deployment en edge.

En el resto de casos, las APIs comerciales suelen dar mejor calidad por menos ingeniería. Este es un juicio de coste/valor, no ideológico.

*Lecturas obligatorias de esta lección.*

### Cuando el LLM no basta: detección, tracking, pose en tiempo real

MediaPipe (Google) ofrece modelos optimizados para tareas específicas: pose estimation, face mesh, hand tracking, segmentación, gestos. Ligero (corre en CPU decente), rápido, gratuito, Apache 2.0.

OpenCV es la librería estándar para operaciones de imagen y video: lectura/escritura, transformaciones geométricas, filtros, morfología, detección de bordes, contornos, calibración de cámara. Es lo que rodea a cualquier pipeline moderno.

*Lecturas obligatorias de esta lección.*

### Convertir documentos en datos: Tesseract, PaddleOCR, Docling

Tesseract lleva funcionando desde los 2000. Extrae texto de imágenes limpias sin problema. El reto moderno son los documentos complejos: PDFs con múltiples columnas, tablas anidadas, fórmulas matemáticas, formularios con campos escritos a mano, gráficos. Es donde los avances recientes (Nougat, Donut, Docling) marcan la diferencia.

PaddleOCR (Baidu, Apache 2.0) combina detección de regiones de texto (DBNet) + reconocimiento (SVTR o similar) con soporte de tablas. Multi-idioma, muy buena calidad en documentos difíciles, ejecución local.

Docling (IBM, MIT, 2024) es un conversor de documentos complejos que preserva la estructura: divide páginas en regiones, detecta tablas y las extrae correctamente, identifica listas, títulos, fórmulas matemáticas, y devuelve markdown o JSON estructurado. En 2026 se está adoptando rápidamente en pipelines RAG serios como reemplazo de LlamaParse, Unstructured y muchas alternativas de pago.

#### Lo mejor de dos mundos

Para pipelines de producción sobre facturas, contratos o formularios complejos, la estrategia ganadora es combinar:

1. Docling extrae texto y preserva estructura.
2. Las regiones o campos ambiguos se envían a un LLM vision (GPT-4o o Claude) para interpretación semántica.
3. El output se valida con Pydantic.

Consigues precisión, robustez y coste controlado.

*Lecturas obligatorias de esta lección.*

### Práctica del SM2 · Tres ejercicios de visión

*(Detalles específicos de los ejercicios disponibles en la plataforma).*

---

## SM3 · De ruido a imagen

Fundamentos de modelos de difusión (denoising iterativo, UNet, latent space) y práctica intensiva con el stack open-source: Stable Diffusion como caballo de batalla, FLUX.1 como estado del arte, y control condicional preciso con ControlNet, IP-Adapter y LoRA.

### Por qué el denoising iterativo genera imágenes fotorrealistas

Un modelo de difusión aprende a invertir un proceso de destrucción. Imagina que tomas una imagen y le añades ruido gaussiano en pasos sucesivos hasta que solo hay ruido puro. Ese es el forward process. Ahora entrena una red neuronal a hacer lo opuesto: partir del ruido y quitarlo paso a paso hasta llegar a una imagen coherente. Ese es el reverse process, y es lo que ejecutas cuando generas.

La red no aprende a generar la imagen directamente. Aprende a predecir el ruido presente en cada paso. Con eso, en inferencia, empiezas con ruido puro y en 20-50 pasos vas obteniendo predicciones de ruido que restas, hasta llegar a una imagen limpia.

Aplicar difusión directamente en píxeles (1024×1024×3 = ~3M dimensiones) es carísimo. La innovación clave de Stable Diffusion (Rombach et al. 2022): aplicar la difusión en un espacio latente comprimido por un VAE (Variational Autoencoder). Un latente típico es 128×128×4 = ~65K dimensiones, ~50 veces más compacto.

Durante inferencia, el modelo hace dos predicciones: una condicionada por el prompt y otra sin condición. La diferencia se amplifica por el `guidance_scale`. Valores típicos 5-9. Muy bajo (<3) genera imágenes poco fieles al prompt; muy alto (>15) satura y produce artefactos.

*Lecturas obligatorias de esta lección.*

### FLUX.1: estado del arte open-source (2024-2026)

FLUX.1 fue lanzado en agosto de 2024 por Black Forest Labs, fundada por parte del equipo core que hizo Stable Diffusion en Stability AI. Introduce dos innovaciones frente a SDXL:

1. Arquitectura de rectified flow transformers en lugar de UNet clásico.
2. Text encoders más potentes (T5-XXL + CLIP).

El resultado: mejor coherencia semántica, mejor generación de texto en imágenes, mejor calidad fotorrealista. FLUX.1 es grande (12B parámetros).

#### ComfyUI vs Código Python

ComfyUI es un editor visual de workflows para generación de imagen. En lugar de escribir código Python, conectas nodos: cargar modelo → cargar prompt → sampler → decodificador → guardar. Muy popular entre artistas técnicos. Su ecosistema de custom nodes es enorme.

¿Cuándo ComfyUI vs código Python?

- **ComfyUI**: Para experimentación visual, workflows complejos con muchos ControlNets encadenados, comunidad con workflows compartibles.
- **Código Python (Diffusers)**: Para integración en aplicaciones, automatización, servidores de inferencia, control programático.

#### Replicate y fal.ai

- **Replicate**: Pay-per-second de GPU. FLUX.1 [schnell] cuesta ~0,003 USD por imagen. FLUX.1 [dev] ~0,03 USD. SDXL ~0,003 USD. Free credits iniciales. API muy limpia.
- **fal.ai**: Optimizado para latencia baja. FLUX.1 [schnell] a <2 segundos por imagen. Precios similares. Streaming de imágenes disponible.

Ambos válidos para el módulo. Elige uno y quédate con él para consistencia.

### De «prompt y reza» a control preciso

Text-to-image con solo prompt te da coherencia semántica pero cero control sobre composición, pose, identidad o estilo específico. Los proyectos comerciales reales requieren más: mismo modelo en distintas prendas, misma habitación con distintos estilos, personaje consistente en varias escenas. Aquí entran ControlNet, IP-Adapter y LoRA.

- **ControlNet (Zhang et al. 2023)**: Añade una rama al UNet que acepta una imagen de condición estructural: bordes canny, mapa de profundidad, pose de personas (OpenPose), scribble, líneas de dibujo, segmentación semántica, normales de superficie, mlsd (líneas rectas para arquitectura), softedge (bordes suaves), tile (tiles para upscaling).
- **IP-Adapter (Ye et al. 2023)**: Te permite condicionar por imagen igual que por texto. Le pasas una imagen de referencia y el modelo genera respetando su estilo, colores o —con variantes «face»— la identidad facial de una persona.
- **LoRA (Low-Rank Adaptation, Hu et al. 2021)**: Es una técnica de fine-tuning que añade matrices de bajo rango a las capas de atención del modelo base, dejando los pesos originales congelados. Muy eficiente: entrenas ~1-10 MB de parámetros en lugar de todo el modelo (~2-12 GB). Usos típicos: adaptar el modelo a un personaje concreto, un estilo artístico, un producto, una marca visual. La comunidad publica miles de LoRAs en Civitai.

**Ejemplo: catálogo de moda**

Quieres el mismo modelo en 20 prendas distintas. Estrategia: usa un LoRA del modelo base y ControlNet/IP-Adapter para mantener la pose/identidad mientras cambias la ropa.

Resultado: 20 imágenes coherentes con el modelo en las prendas del catálogo. Es lo que están haciendo muchos e-commerce en 2026 para reducir costes de shoot fotográfico.

*Lecturas obligatorias de esta lección.*

### Práctica del SM3 · Tres ejercicios de generación

Elige uno de estos tres casos. Entrega: las 4 imágenes finales, la imagen de referencia, el código completo, y un README explicando decisiones técnicas y limitaciones.

---

## SM4 · Todo junto: aplicaciones que ven, escuchan, hablan y generan

Cierras el módulo integrando las tres modalidades en aplicaciones reales. Arquitecturas de referencia, integración práctica en un agente multimodal completo, patrones de deployment con GPU, y arranque del proyecto final individual.

### Patrones de diseño para sistemas multimodales

Estrategias para reducir latencia cuando incluyes visión:

1. Muestrear frames a 1 fps o menos.
2. Enviar solo frames tras cambio significativo (SSIM comparison).
3. Desacoplar el análisis visual del turno de voz (procesamiento asíncrono en paralelo).
4. Resumir frames antiguos a texto y descartar píxeles para no explotar contexto.

### Ejercicio guiado: Agente multimodal completo

Vas a extender un LiveKit Agent (como el del SM1) para que además de audio, procese frames de video de forma periódica y los use en el contexto de la conversación. Un ejemplo: tutor que ve tu pantalla mientras programas, o asistente de reparaciones que ve por tu cámara.

> **Enviar frames constantemente explota el contexto.** Si mandas un frame en cada turno del LLM, en 10 turnos llevas ~15.000-30.000 tokens de imágenes en el historial. Esto sube el coste y degrada la calidad (contexto excesivo).
>
> **Solución:** Solo envía el frame cuando la conversación lo requiere (patrón «tool que da acceso a visión bajo demanda»), y no lo dejes acumulándose en el histórico: úsalo en el turno y descarta.

### Del notebook al servicio en producción

**Voice agent con 100 usuarios activos/día · 5 min conversación media**

Si escalas 10x los usuarios: linealmente sube el coste de APIs (~2000-2500 USD/mes). Aquí empieza a compensar migrar componentes a self-hosted open-source.

---

## Proyecto Final del M6 · Todo lo que necesitas para completar y defender

Léela entera antes de decidir tu caso de uso. Los mejores proyectos empiezan por leer bien la especificación.

### Elegir bien el caso · determina el 40%

Algunas ideas de dominio recomendadas:

1. **Asistente visual para personas con baja visión**
   - App móvil o web que la persona activa por voz.
   - La cámara del dispositivo captura frames, GPT-4o vision los describe verbalmente.
   - Además, OCR con Docling para leer texto en documentos, carteles o pantallas.
   - TTS con Piper (local, sin latencia de red) para reproducir la descripción.

2. **Inspección de defectos con voz**
   - Operario en línea de producción hace foto de una pieza y describe por voz lo que ve.
   - YOLO fine-tuneado detecta defectos comunes.
   - LLM vision analiza casos ambiguos.
   - TTS lee al operario el veredicto y la acción sugerida.
   - Todo el flujo hands-free y en menos de 5 segundos.

3. **Tutor de dibujo o caligrafía**
   - El alumno dibuja/escribe algo en papel, apunta con la webcam.
   - MediaPipe detecta trazos.
   - GPT-4o vision compara con el modelo objetivo.
   - Voice agent LiveKit da feedback en tiempo real.
   - Opcionalmente, genera con Stable Diffusion una versión corregida como ejemplo visual.

4. **Editor de podcast asistido**
   - Sube un episodio grabado.
   - WhisperX transcribe y diariza.
   - Un LLM analiza y sugiere: recortes, capítulos, silencios a eliminar, quotes destacables.
   - Genera con FLUX una miniatura para el episodio en base al contenido.
   - Genera con ElevenLabs las intro/outro personalizadas con la voz del podcaster (con su consentimiento).

5. **Asistente visual de shopping**
   - Cliente muestra por webcam un objeto (prenda, mueble, herramienta) y describe por voz lo que busca.
   - GPT-4o vision identifica lo mostrado.
   - LLM busca en catálogo (RAG).
   - Voice agent conversa.
   - Puede generar con Stable Diffusion + IP-Adapter previsualizaciones del producto en el contexto del cliente.

### Seis dimensiones que determinarán tu nota

*(La rúbrica evalúa la integración de las tres modalidades, la eficiencia del pipeline, la calidad de la interacción en tiempo real y la robustez del sistema).*

### Repositorio GitHub · Estructura obligatoria

### Prepara la defensa como si fuera una entrevista técnica

Mismo formato que el proyecto del M5: presentación breve, demo funcional, preguntas duras. Adaptado al perfil multimodal.

### Cómo transcurren tus 25 minutos

*(Presentación, Demo, Preguntas).*

---

## Conclusión · Cierras la vertiente técnica del bootcamp

Con este módulo terminas el bloque técnico del bootcamp. Tienes en las manos un stack completo para construir aplicaciones que ven, escuchan, hablan y generan:

- Whisper, LiveKit, GPT-4o vision, Docling, Diffusers, FLUX, ControlNet.

El conjunto de herramientas que los AI Engineers de 2026 usan en producto real, la mayoría de ellas open-source. Este era también el módulo más denso en herramientas y con mayor variabilidad de setup. Si has llegado hasta aquí con los ejercicios completados, tienes una base técnica muy sólida.

La generación de imagen y los voice agents son áreas donde el mercado laboral tiene demanda alta y donde muchos desarrolladores se quedan en el nivel superficial de «uso APIs comerciales»: tú ahora entiendes por dentro cómo funciona el stack, sabes cuándo justifica un servicio comercial y cuándo compensa self-host, y puedes tomar decisiones fundamentadas.

**Lo que sigue en tu trayectoria:**

1. Cerrar los dos proyectos finales (M5 Agentes y M6 Multimodal).
2. Publicarlos con calidad (READMEs pulidos, vídeos demo, LinkedIn).
3. Apoyarte en el equipo de carreras profesionales de Neoland para el proceso de búsqueda de empleo.

El bootcamp continúa hasta que consigas encaje profesional real.

> **Una nota sobre este material.** Todo el contenido de esta guía —estructura pedagógica, pseudocódigo ilustrativo, ejercicios, ejemplos de casos, rúbricas, guiones de defensa— es el resultado de iteración pedagógica sobre lo que funciona en formación intensiva. Es **propiedad intelectual exclusiva de Neoland School SL**. Te lo entregamos para tu formación; confiamos en que respetes su uso.

**Buena suerte con el proyecto y con la defensa.**
