Source URL: https://neoland.es/data026/dk421/modulo-04-ai-eng.html
Title: Módulo 4 · RAG y Bases Vectoriales · Bootcamp en AI Engineering · Neoland

Bootcamp en AI Engineering · Neoland

Módulo 4 · Guía del alumno

# RAG & _Bases Vectoriales_

Construir sistemas Retrieval-Augmented Generation que conectan IA con información privada de empresa. De embeddings y similitud semántica a Agentic RAG, pasando por bases vectoriales, hybrid search, reranking y CRAG. 40 horas para llegar al estado del arte real de los chatbots empresariales.

40 horas de aprendizaje 4 sub-módulos · 14 lecciones Python · Jupyter · APIs reales ChromaDB · Qdrant · Pinecone free Proyecto final integrador 

NEOLAND www.neoland.es BOOTCAMP AI ENGINEERING · MÓDULO 4 Guía del alumno 

00Índice rápido

## Del primer embedding a tu propio _RAG empresarial_

Este módulo te lleva desde entender qué es un embedding y por qué la búsqueda semántica funciona, hasta construir un sistema RAG completo con técnicas del estado del arte (hybrid search, reranking, CRAG, Self-RAG, Agentic RAG) sobre tu propia base de documentos privados. Es la pieza técnica más sofisticada del bootcamp y la más demandada por el mercado en 2026.

El módulo se desarrolla principalmente en **Python con Jupyter notebooks**: usarás librerías open-source maduras (LangChain, LlamaIndex, sentence-transformers, ChromaDB, Qdrant, RAGAS) y APIs comerciales en sus planes gratuitos o trial (Pinecone, Cohere Rerank, OpenAI embeddings con coste por uso muy bajo). Al terminar, podrás construir el corazón técnico de cualquier asistente empresarial sobre documentación privada.

SUB-MÓDULO 1 · 10 h

#### Embeddings y similitud semántica

Qué son los embeddings, modelos disponibles (OpenAI, sentence-transformers, Cohere, BGE), métricas de similitud y primer buscador semántico.

SUB-MÓDULO 2 · 10 h

#### Bases vectoriales

ChromaDB local, Qdrant self-hosted con Docker, Pinecone serverless free tier. Criterios para elegir según caso.

SUB-MÓDULO 3 · 10 h

#### RAG · de naive a avanzado

Pipeline RAG básico con LangChain, hybrid search con BM25, reranking con cross-encoders y Corrective RAG.

SUB-MÓDULO 4 · 10 h

#### Agentic RAG, Self-RAG, evaluación

Agentes que deciden cuándo recuperar, auto-evaluación de relevancia, métricas RAGAS y proyecto final integrador.

00.1Cómo usar esta guía

## Aprender RAG construyendo, no _solo leyendo_

Cada lección sigue el patrón **concepto + ejemplos + ejercicio práctico**. El concepto te da el modelo mental, los ejemplos muestran código real ejecutable que puedes copiar y probar, y el ejercicio te obliga a aplicarlo en tu propio entorno. Sin completar los ejercicios, leer la guía no te enseña RAG; con ellos completados, llegas al proyecto final con autonomía técnica real.

Prerrequisitos del módulo 

#### Lo que se asume que ya sabes

**Python intermedio**: trabajar con listas, diccionarios, comprensiones, funciones, gestionar entornos virtuales con venv o conda, instalar paquetes con pip. No hace falta saber programación orientada a objetos avanzada.

**APIs de LLMs del Módulo 2**: llamar a OpenAI, Anthropic o Google desde Python, manejar respuestas JSON, gestionar API keys con variables de entorno.

**Jupyter notebooks o un IDE** (VSCode, Cursor). Recomendado: Jupyter para los ejercicios exploratorios, VSCode para el proyecto final.

**Docker básico del Módulo 3**: levantar contenedores con docker-compose. Lo usarás en SM2 para Qdrant.

Si vienes flojo en alguno de estos, hay tiempo de refrescar antes del primer día. Los enlaces de cada sección incluyen recursos para repasar.

Software del módulo · todo gratis o trial generoso 

#### Lo que vas a usar y cómo va el coste

**Open-source completamente gratis**: ChromaDB (vector DB local), Qdrant (vector DB self-hosted o cloud free 1 GB), sentence-transformers (modelos de embeddings open-source de HuggingFace), LangChain, LlamaIndex, Haystack (frameworks RAG), RAGAS y DeepEval (evaluación), bge-reranker (reranking), pgvector (extensión Postgres).

**SaaS con plan gratuito o trial**: Pinecone (serverless free con 2 GB de almacenamiento sin caducar), Cohere (free tier con 1000 calls/mes a Rerank), Voyage AI (200M tokens gratis para embeddings), Jina AI (1M tokens gratis), Tavily Search API (1000 búsquedas gratis al mes para CRAG).

**Con coste por uso muy bajo**: OpenAI embeddings (text-embedding-3-small cuesta 0,02 USD por millón de tokens · todo el módulo te costará menos de 1 USD), Anthropic Claude (para generation), Google Gemini con tier gratuito Flash generoso.

El módulo completo se puede hacer gastando menos de 5 USD totales si gestionas bien. Las opciones de pago se mencionan como referencia pero no son el camino principal.

Setup recomendado del entorno 

#### Antes de la primera lección

Crea un entorno virtual nuevo dedicado al módulo:

`python -m venv venv-rag` · activa con `source venv-rag/bin/activate` (Mac/Linux) o `venv-rag\Scripts\activate` (Windows).

Instala las dependencias base (las específicas las irás añadiendo según el sub-módulo):

`pip install jupyter python-dotenv openai anthropic sentence-transformers chromadb langchain langchain-community`

Crea un archivo `.env` en la raíz de tu proyecto con tus API keys. Nunca lo subas a GitHub. Añade `.env` al `.gitignore`.

Filosofía de aprendizaje 

#### RAG se aprende rompiendo cosas

La mayoría de tutoriales de RAG enseñan el «happy path»: documentos limpios, queries claras, respuestas perfectas. La realidad de RAG en producción es muy distinta: documentos PDF con formato roto, queries ambiguas, retrieval que devuelve lo irrelevante, hallucinations del LLM final. Este módulo enfatiza los _casos difíciles_: lo que falla, por qué falla y cómo se diagnostica.

Por eso los ejercicios usan datasets variados (Wikipedia, PDFs reales, documentación técnica) y no solo casos idílicos. Cuando algo no te funcione a la primera, no es error tuyo: es la realidad de construir sistemas RAG. La habilidad clave que vas a desarrollar es **diagnosticar dónde falla un pipeline RAG**, no solo construirlo cuando todo va bien.

SUB-MÓDULO 1· 10 horas · 3 lecciones

## Embeddings y _similitud semántica_

El fundamento de todo lo que viene después. Qué son los embeddings, qué modelos hay y cómo elegir entre ellos, cómo se mide la similitud entre vectores y cómo construir un buscador semántico desde cero antes de tocar bases vectoriales reales.

10 horas totales 3 lecciones 3 ejercicios prácticos Python + sentence-transformers + OpenAI 

LECCIÓN 1.1· \~2,5 horas · Sub-módulo 1

## Qué son los embeddings y por qué _importan_

El concepto de embedding como vector que captura significado. Espacios vectoriales semánticos, propiedades geométricas, modelo mental visual y por qué los embeddings son la base de todo sistema RAG moderno.

Lectura · 50 min Ejemplos · 30 min Ejercicio · 70 min 

1.1.1De las palabras a los vectores

#### Al final de esta lección sabrás:

* Explicar qué es un embedding y por qué transforma el problema de «entender texto» en uno de geometría.
* Distinguir embeddings densos (semánticos) de representaciones sparse (TF-IDF, BM25) y cuándo usar cada uno.
* Comprender la noción de espacio vectorial semántico y las propiedades que se pueden explotar (similitud, analogías, clustering).
* Identificar los tres casos de uso fundamentales: búsqueda semántica, clasificación zero-shot, deduplicación.
* Conectar el concepto de embedding con todo el pipeline RAG que verás durante el módulo.

La idea central · convertir significado en geometría

Un **embedding** es una representación numérica de un fragmento de texto (una palabra, una frase, un párrafo o un documento completo) en forma de un vector de números reales, típicamente de entre 384 y 3072 dimensiones. La magia no está en el vector en sí, sino en una propiedad que aprenden los modelos modernos: _textos con significado parecido producen vectores cercanos en el espacio_.

Esto convierte un problema lingüístico difícil («¿qué significa esto?») en un problema geométrico fácil («¿cuál es el vector más cercano a este otro?»). El gran salto conceptual del RAG es que **la búsqueda por significado se reduce a calcular distancias entre puntos en un espacio de alta dimensión**.

Antes de la era de los embeddings densos, la búsqueda en texto se hacía con técnicas _sparse_: TF-IDF y BM25 contaban palabras exactas y las ponderaban estadísticamente. Funcionan bien cuando la query y el documento comparten términos literales (busca «inteligencia artificial» y encuentras documentos con la frase «inteligencia artificial»), pero fallan ante sinónimos, paráfrasis o conceptos relacionados (busca «redes neuronales» y no encuentras un texto que solo habla de «deep learning»).

Los embeddings densos resuelven precisamente eso. Si entrenas un modelo con millones de pares de textos que son semánticamente equivalentes, el modelo aprende a poner cerca en el espacio cosas como «coche» y «automóvil», «París» y «la capital de Francia», o «cómo configurar SSH» y «conectarme por terminal a un servidor remoto».

Sparse vs dense · cuándo cada uno 

#### No es elegir; es saber combinar

**Representaciones sparse** (TF-IDF, BM25): vectores de la longitud del vocabulario completo (decenas de miles de dimensiones), casi todas las posiciones a cero excepto las palabras presentes. Son _léxicas_: capturan qué palabras concretas aparecen. Funcionan increíblemente bien para términos técnicos exactos, números de modelo, acrónimos o IDs.

**Embeddings densos**: vectores de 384-3072 dimensiones con valores reales en todas las posiciones. Son _semánticos_: capturan el significado más allá de las palabras exactas. Brillan en queries naturales («¿cómo arreglo mi router?») y en sinónimos.

En sistemas RAG serios, los dos se combinan en **hybrid search** (lo verás en SM3): BM25 captura las menciones literales exactas, embeddings densos capturan el significado, y se combinan para obtener lo mejor de ambos mundos. Naive RAG con solo embeddings densos pierde precisión en queries con términos específicos; entender por qué desde el primer día evita errores comunes.

Propiedades geométricas explotables

Los embeddings de modelos modernos tienen propiedades que vamos a usar constantemente en el módulo:

* **Similitud por proximidad**. Cuanto más cerca están dos vectores en el espacio, más relacionados están sus significados. Esto se mide normalmente con _similitud coseno_, que devuelve un número entre -1 (opuestos) y 1 (idénticos en dirección). En la práctica, valores típicos entre textos relacionados están entre 0,5 y 0,9.
* **Clustering natural**. Si embeddings un corpus de noticias, los textos de deportes forman un cluster, los de política otro, los de tecnología otro. Esto se usa para clasificación zero-shot y para descubrimiento de temas.
* **Operaciones algebraicas con significado**. En algunos modelos clásicos (Word2Vec, GloVe), _vector(rey) - vector(hombre) + vector(mujer) ≈ vector(reina)_. En modelos modernos esta propiedad es más sutil pero sigue existiendo conceptualmente, y se aprovecha en técnicas como HyDE.
* **Normalización**. Muchos modelos producen vectores ya normalizados (norma 1). Cuando los vectores están normalizados, la similitud coseno y el producto escalar dan el mismo resultado, lo cual simplifica mucho los cálculos.

Ejemplo · embedding de frases en código 

#### Primer contacto con sentence-transformers

Antes de meternos en modelos comerciales, vamos a ver el ejemplo más simple posible usando un modelo open-source que corre en tu portátil sin necesidad de API keys.

from sentence\_transformers import SentenceTransformer import numpy as np # Modelo multilingüe ligero, 384 dimensiones, funciona en CPU model = SentenceTransformer('paraphrase-multilingual-MiniLM-L12-v2') frases = \[ "El gato duerme en el sofá", "Un felino descansa sobre el mueble", "Madrid es la capital de España", "La capital española es Madrid", "Las redes neuronales aprenden patrones", \] # Genera los embeddings (una matriz: una fila por frase) embeddings = model.encode(frases) print(embeddings.shape) # (5, 384) # Similitud coseno entre los pares from sentence\_transformers.util import cos\_sim print(cos\_sim(embeddings\[0\], embeddings\[1\])) # gato/felino \~ 0.85 print(cos\_sim(embeddings\[2\], embeddings\[3\])) # Madrid/España \~ 0.95 print(cos\_sim(embeddings\[0\], embeddings\[4\])) # gato/redes \~ 0.10

Tres observaciones importantes de este ejemplo. Primero, las frases sobre el mismo concepto (gato/felino) están cerca sin compartir prácticamente palabras: el modelo entiende sinónimos. Segundo, las dos formulaciones sobre Madrid están muy cerca: el modelo entiende paráfrasis. Tercero, frases sobre temas distintos están lejos: el modelo no se confunde con palabras que casualmente compartan letras.

El modelo concreto que hemos usado (`paraphrase-multilingual-MiniLM-L12-v2`) pesa unos 130 MB, corre en CPU en milisegundos, soporta más de 50 idiomas y es completamente gratuito y open-source. Para muchos casos de uso en español es perfectamente adecuado.

Los tres casos de uso fundamentales

Los embeddings son útiles más allá de RAG. Es importante que tengas el mapa mental de los tres patrones principales antes de profundizar en cualquiera de ellos:

* **Búsqueda semántica**. Tienes un corpus de documentos y una query del usuario. Embedeas todo, buscas el documento cuyo embedding es más cercano al embedding de la query. Es el corazón del RAG.
* **Clasificación zero-shot**. Tienes un texto y varias categorías candidatas. Embedeas el texto y las descripciones de cada categoría, asignas el texto a la categoría cuyo embedding está más cerca. Permite clasificar sin entrenar un modelo específico.
* **Deduplicación y clustering**. Tienes muchos textos y quieres detectar duplicados semánticos (no solo exactos) o agrupar por tema. Embedeas todo y aplicas clustering (k-means, HDBSCAN) sobre los vectores.

En este módulo nos vamos a centrar en la búsqueda semántica porque es la base de RAG, pero el ejercicio de esta lección incluye un experimento de clasificación para que veas la versatilidad del concepto.

Dimensiones · más no siempre es mejor 

#### El trade-off de dimensionalidad

Los embeddings comerciales modernos tienen entre 384 y 3072 dimensiones. Intuitivamente uno pensaría que más dimensiones es mejor porque hay más capacidad de representación. La realidad es más matizada:

**Más dimensiones** \= mayor capacidad expresiva, mejor desempeño en tareas complejas, pero también mayor coste de almacenamiento (un vector de 3072 dimensiones float32 ocupa 12 KB; mil millones de vectores ocuparían 12 TB), mayor coste de cálculo de similitud y, sorprendentemente, no siempre mejor calidad en queries simples.

**Menos dimensiones** \= más rápido, más barato de almacenar, suficiente para muchísimos casos. Para colecciones de hasta unos cientos de miles de documentos, modelos de 384-768 dimensiones suelen ser ideales.

OpenAI introdujo en 2024 los _Matryoshka embeddings_ con text-embedding-3-large/small: puedes truncar el vector a menos dimensiones (256, 512, 1024) sin perder demasiada calidad. Es una técnica útil cuando quieres flexibilidad.

#### Ejercicio 1.1 · primer buscador semántico

Tiempo estimado · 60-70 minutos 

Vas a construir un buscador semántico mínimo sobre un corpus pequeño usando solo Python y sentence-transformers, sin base vectorial todavía. El objetivo no es construir algo escalable: es internalizar qué hace exactamente un embedding.

1. **Crea un Jupyter notebook nuevo** en tu directorio del módulo. Instala las dependencias si aún no las tienes: `pip install sentence-transformers numpy`.
2. **Reúne un corpus de unas 20-30 frases** sobre 3 o 4 temas distintos. Pueden ser de tu propio interés: descripciones de películas, fragmentos de libros, noticias breves, lo que sea. La clave: que haya variedad temática.
3. **Carga un modelo de embeddings**. Para empezar, usa `paraphrase-multilingual-MiniLM-L12-v2` si tu corpus está en español o es multilingüe. Si está en inglés puro, prueba también `all-MiniLM-L6-v2`.
4. **Calcula los embeddings de todo el corpus** con `model.encode(corpus)`. Almacena la matriz resultante.
5. **Implementa una función de búsqueda** que reciba una query en texto, calcule su embedding, compute similitud coseno con todo el corpus y devuelva los top-K resultados ordenados por similitud descendente.
6. **Prueba con queries variadas**:  
   * Una query que use palabras exactas presentes en alguna frase del corpus.  
   * Una query que use sinónimos pero no palabras exactas.  
   * Una query que pregunte por concepto sin mencionar términos directos.  
   * Una query en otro idioma que el corpus (si usas modelo multilingüe).  
   * Una query sobre un tema que no esté en el corpus (¿qué resultados devuelve?).
7. **Reflexiona sobre los resultados**: ¿en qué casos funciona bien?, ¿en cuáles no?, ¿qué pasa con la query sobre tema inexistente?
8. **Bonus 1 · clasificación zero-shot**: define 4-5 categorías como frases descriptivas («texto sobre tecnología», «texto sobre deportes», etc.), embedéalas, y para cada frase de tu corpus asigna la categoría cuya descripción tenga el embedding más cercano. Compara con tu intuición sobre cómo deberían clasificarse.
9. **Bonus 2 · visualización**: usa `sklearn.manifold.TSNE` o `umap-learn` para reducir los embeddings a 2D y plotearlos con matplotlib. Observa visualmente cómo los textos del mismo tema se agrupan.

Guarda este notebook bien: lo vas a reutilizar en lecciones posteriores como banco de pruebas. La habilidad clave que estás desarrollando aquí no es escribir 30 líneas de código, es desarrollar _intuición sobre cuándo los embeddings funcionan y cuándo no_. Esa intuición es la que separa a alguien que copia tutoriales de alguien que construye sistemas RAG sólidos.

Preguntas frecuentes 

¿Por qué sentence-transformers en vez de directamente OpenAI desde la primera lección?

Por tres razones. Primero, pedagógica: queremos que veas que «hacer embeddings» no es magia propietaria sino algo que puedes correr en tu portátil con modelos open-source en segundos. Segundo, económica: te ahorra créditos de OpenAI para cuando los necesites en serio. Tercero, profesional: en producción real, muchos sistemas RAG usan modelos open-source self-hosted para evitar el lock-in y los costes a escala. En la siguiente lección compararemos sentence-transformers con OpenAI y otros proveedores comerciales.

¿Los embeddings funcionan igual en español que en inglés?

Depende fuertemente del modelo. Los modelos entrenados solo en inglés (la mayoría de los SOTA en benchmarks como MTEB) funcionan mal o muy mal en español. Los modelos multilingües específicos (_paraphrase-multilingual-\*_, _BGE-M3_, OpenAI text-embedding-3, Cohere embed-multilingual-v3, Jina-v3) funcionan bien en español pero suelen tener algo menos de calidad que sus equivalentes monolingües en inglés. Es importante elegir un modelo apropiado para tu idioma; lo veremos a fondo en L1.2.

¿Cuánto texto puedo embedear de una vez? ¿Hay un límite?

Sí, cada modelo tiene un límite de tokens de entrada (entre 256 y 8192 tokens según modelo). Texto que excede el límite es truncado. Esto importa muchísimo en RAG: si tus documentos son largos, no puedes embedear cada documento entero. Tienes que _chunkearlos_ en fragmentos del tamaño adecuado. Lo veremos en detalle en SM3 cuando construyamos el primer pipeline RAG.

¿Cómo se entrenan estos modelos? ¿Necesito entender la teoría profunda?

Para usar embeddings y construir RAG no necesitas entender el entrenamiento. Los modelos se entrenan típicamente con técnicas de contrastive learning sobre pares de textos similares (positivos) y disimilares (negativos): el modelo aprende a acercar los positivos y alejar los negativos en el espacio. Si te interesa profundizar, los papers de _Sentence-BERT_ (Reimers & Gurevych, 2019) y _SimCSE_ son las referencias. Pero ningún rol de AI Engineer junior necesita esto: necesita saber elegir modelo, evaluar resultados y construir el pipeline.

Recursos para profundizar 

#### Embeddings · teoría y práctica

* **SBERT · documentación oficial de sentence-transformers**. La referencia para la librería que vas a usar todo el módulo. Tiene tutoriales paso a paso y un selector de modelos por tarea. sbert.net
* **MTEB Leaderboard**. Benchmark abierto de Hugging Face donde se comparan todos los modelos de embeddings en muchas tareas e idiomas. Imprescindible para decidir qué modelo usar en cada caso. huggingface.co/spaces/mteb/leaderboard
* **Sentence-BERT paper**. Si quieres el porqué teórico detrás de los modelos modernos. Lectura técnica recomendable, no obligatoria. arxiv.org/abs/1908.10084
* **The Illustrated Word2Vec**. Para visualizar el concepto de embedding desde sus orígenes en 2013\. Explicación gráfica de Jay Alammar. jalammar.github.io/illustrated-word2vec

Fin lección 1.1 · Sigue lección 1.2

LECCIÓN 1.2· \~3,5 horas · Sub-módulo 1

## Modelos de embeddings · _panorama y elección_

Comparativa de modelos disponibles en 2026\. OpenAI text-embedding-3, Cohere embed-multilingual-v3, sentence-transformers, BGE-M3, Jina-v3, Voyage. Cuándo open-source vs API, dimensionalidad, multilingüismo y MTEB benchmark.

Lectura · 60 min Ejemplos · 50 min Ejercicio · 100 min 

1.2.1El panorama real de modelos en 2026

#### Al final de esta lección sabrás:

* Identificar los principales modelos de embeddings disponibles y sus características clave.
* Decidir entre modelos open-source y APIs comerciales según caso, coste y constraints de privacidad.
* Leer el MTEB Leaderboard con criterio y elegir un modelo basándote en las tareas que te importan.
* Generar embeddings con OpenAI, Cohere y sentence-transformers y comparar resultados sobre el mismo corpus.
* Argumentar técnicamente por qué elegiste un modelo para tu proyecto final.

Las dos familias · open-source vs APIs comerciales

Los modelos de embeddings se dividen en dos familias con trade-offs claros:

**Open-source · self-hosted**. Los descargas, los corres tú en tu máquina o servidor. Sin coste por uso, sin enviar datos a terceros, sin dependencia de uptime de un proveedor. A cambio: gestionas la infraestructura, los modelos top requieren GPU para volumen serio, y los mejores modelos open-source suelen ir un escalón por debajo de los mejores propietarios en benchmarks. La familia incluye sentence-transformers, BGE, Jina (versiones open), GTE de Alibaba, E5 de Microsoft, Nomic Embed.

**APIs comerciales**. Llamas a un endpoint, pagas por tokens. Sin gestión de infraestructura, los modelos suelen estar entre los mejores del MTEB, escala automática. A cambio: dependes del proveedor, tus datos salen a su API, coste por uso (aunque sea muy bajo). La familia incluye OpenAI text-embedding-3-small/large, Cohere embed-v3, Voyage AI, Jina AI Embeddings (versión API), Google Vertex.

En la práctica profesional, la elección depende de tres factores: **privacidad de los datos** (¿pueden salir a un tercero?), **volumen previsto** (¿millones de embeddings al mes o miles?) y **presupuesto de infraestructura** (¿tienes GPU disponible?). Empresas con datos sensibles o gran volumen tienden a self-hosted; startups y casos de uso medio van con APIs comerciales por simplicidad.

Los modelos principales · panorama a fecha de 2026

| Modelo                                   | Tipo        | Dim              | Multilingüe                   | Coste                                      | Cuándo elegirlo                                                                        |
| ---------------------------------------- | ----------- | ---------------- | ----------------------------- | ------------------------------------------ | -------------------------------------------------------------------------------------- |
| text-embedding-3-small (OpenAI)          | API         | 1536 (truncable) | Sí, \~100 idiomas             | 0,02 USD/M tokens                          | Default razonable para la mayoría de casos. Barato y bueno.                            |
| text-embedding-3-large (OpenAI)          | API         | 3072 (truncable) | Sí, \~100 idiomas             | 0,13 USD/M tokens                          | Cuando la calidad de retrieval crítica justifica 6x más coste.                         |
| embed-multilingual-v3 (Cohere)           | API         | 1024             | Sí, 100+ idiomas              | 0,10 USD/M tokens (free tier 100 reqs/min) | Multilingüe sólido, alternativa a OpenAI con free tier generoso.                       |
| voyage-3 (Voyage AI)                     | API         | 1024             | Limitado                      | 0,06 USD/M tokens (200M gratis)            | Top en benchmarks recientes; ofrece versión especializada para código (voyage-code-3). |
| jina-embeddings-v3 (Jina AI)             | API + open  | 1024 (truncable) | Sí, 89 idiomas                | 1M tokens gratis                           | Tarea-specific con LoRA adapters; bueno para multilingüe.                              |
| BGE-M3 (BAAI)                            | Open-source | 1024             | Sí, 100+ idiomas              | Gratis (self-hosted)                       | El open-source multilingüe más sólido. Soporta dense, sparse y multi-vector.           |
| all-MiniLM-L6-v2 (sentence-transformers) | Open-source | 384              | Limitado (inglés mayoritario) | Gratis                                     | El clásico ligero. Corre en CPU. Suficiente para muchos casos en inglés.               |
| paraphrase-multilingual-MiniLM-L12-v2    | Open-source | 384              | Sí, 50+ idiomas               | Gratis                                     | Multilingüe ligero. Default para empezar sin coste en español.                         |
| multilingual-e5-large (Microsoft)        | Open-source | 1024             | Sí, 100 idiomas               | Gratis (requiere GPU)                      | Alta calidad multilingüe. Necesita GPU para producción.                                |
| nomic-embed-text-v1.5                    | Open-source | 768 (truncable)  | Limitado                      | Gratis                                     | Open-source con Matryoshka, contexto largo de 8192 tokens.                             |

Este panorama cambia rápidamente. Antes de elegir definitivamente para un proyecto real, conviene revisar el MTEB Leaderboard porque las posiciones cambian cada pocos meses.

Cómo leer el MTEB Leaderboard 

#### El estándar de comparación de embeddings

El **Massive Text Embedding Benchmark (MTEB)** es el benchmark de referencia que mantiene Hugging Face. Compara modelos en docenas de tareas: clasificación, clustering, retrieval, reranking, STS (similarity), summarization. El leaderboard es público en _huggingface.co/spaces/mteb/leaderboard_.

Tres consejos prácticos al leerlo. **Uno**: no mires solo el «Average» global; filtra por la tarea que te importa (para RAG, mira «Retrieval»). **Dos**: filtra por idioma si tu caso no es solo inglés (hay sub-leaderboards multilingüe, MTEB-fr, MTEB-zh, etc.). **Tres**: ten en cuenta el tamaño del modelo: un modelo top con 7B parámetros (bge-multilingual-gemma2) requiere infraestructura que un modelo de 100M no.

Para el módulo y para muchos casos profesionales, los modelos entre las posiciones 10-30 del leaderboard suelen ser _más prácticos_ que los top-3, porque los top-3 a veces son enormes y caros de operar mientras la diferencia de calidad es marginal.

Generar embeddings con tres proveedores · ejemplos paralelos

Ejemplo · OpenAI text-embedding-3-small 

#### El default razonable

OpenAI ofrece dos modelos en su familia 3 (la familia anterior, ada-002, está deprecada). text-embedding-3-small es la opción default por su balance coste-calidad excepcional.

from openai import OpenAI import os from dotenv import load\_dotenv load\_dotenv() client = OpenAI(api\_key=os.getenv("OPENAI\_API\_KEY")) textos = \[ "La inteligencia artificial generativa transforma la productividad.", "Las redes neuronales aprenden representaciones jerárquicas.", "El gato persa duerme dieciocho horas al día.", \] # Batch de hasta 2048 elementos por llamada response = client.embeddings.create( model="text-embedding-3-small", input=textos, # encoding\_format="float" por defecto # dimensions=512 # opcional: truncar a menos dimensiones ) embeddings = \[item.embedding for item in response.data\] print(len(embeddings)) # 3 print(len(embeddings\[0\])) # 1536 (o el valor de dimensions= si lo pones)

Notas prácticas. El parámetro `dimensions=` permite truncar el vector (Matryoshka) a 256, 512 o 1024 sin perder demasiada calidad y reduciendo el coste de almacenamiento. Los embeddings de OpenAI vienen **ya normalizados** (norma 1), así que producto escalar = similitud coseno. El precio en 2026 es 0,02 USD por millón de tokens en small y 0,13 USD/M en large.

Ejemplo · Cohere embed-multilingual-v3 

#### Alternativa multilingüe sólida con free tier generoso

Cohere ofrece una API limpia con free tier de 100 calls/min al modelo embed-multilingual-v3, suficiente para experimentar y prototipar sin coste alguno.

import cohere import os from dotenv import load\_dotenv load\_dotenv() co = cohere.Client(api\_key=os.getenv("COHERE\_API\_KEY")) textos = \[ "La inteligencia artificial generativa transforma la productividad.", "Generative AI is changing how we work.", "Le chat dort sur le canapé.", \] # Importante: Cohere requiere especificar input\_type response = co.embed( texts=textos, model="embed-multilingual-v3.0", input\_type="search\_document", # o "search\_query", "classification", "clustering" embedding\_types=\["float"\], ) embeddings = response.embeddings.float print(len(embeddings\[0\])) # 1024

Característica importante de Cohere: distingue entre **document embeddings** y **query embeddings**. Cuando indexas documentos usas `input_type="search_document"`; cuando embedeas una query del usuario usas `"search_query"`. Esto asimetría está pensada para mejorar el retrieval. Si no lo respetas, los resultados son peores. OpenAI no requiere esta distinción.

Ejemplo · BGE-M3 open-source 

#### El estándar open-source multilingüe en 2026

BGE-M3 de BAAI es uno de los modelos open-source multilingües más usados en producción. Soporta los tres modos (dense, sparse, multi-vector) en un solo modelo, lo cual es muy útil para hybrid search.

from FlagEmbedding import BGEM3FlagModel # Descarga el modelo la primera vez (\~2 GB); luego lo carga del cache model = BGEM3FlagModel('BAAI/bge-m3', use\_fp16=True) textos = \[ "La inteligencia artificial generativa transforma la productividad.", "Generative AI is changing how we work.", "Le chat dort sur le canapé.", \] # Devuelve dense + sparse + (opcionalmente) multi-vector output = model.encode( textos, return\_dense=True, return\_sparse=True, return\_colbert\_vecs=False, # multi-vector tipo ColBERT, costoso ) dense\_vectors = output\['dense\_vecs'\] # shape (3, 1024) sparse\_weights = output\['lexical\_weights'\] # dicts token\_id -> peso

BGE-M3 brilla porque te da **los dos tipos de representación a la vez**: dense para semántica y sparse para términos léxicos. Para hybrid search (lo verás en SM3) esto te ahorra coordinar dos modelos. Requiere \~4 GB de RAM y va más cómodo en GPU pero corre razonablemente en CPU para volúmenes pequeños.

Criterios prácticos para elegir un modelo

Cuando estés ante un proyecto real y tengas que decidir qué modelo usar, esta es una matriz de decisión que funciona:

* **Volumen pequeño (menos de 100K documentos), inglés, presupuesto cero**: `all-MiniLM-L6-v2` de sentence-transformers. Corre en CPU, es gratis, suficiente calidad para empezar.
* **Volumen pequeño, multilingüe, presupuesto cero**: `paraphrase-multilingual-MiniLM-L12-v2` para ligereza, o `BGE-M3` si tienes GPU disponible.
* **Volumen medio (cientos de miles), quieres API simple, presupuesto bajo**: `text-embedding-3-small` de OpenAI. Default razonable para la mayoría de proyectos.
* **Multilingüe con calidad alta, prefieres no OpenAI**: Cohere embed-multilingual-v3, Jina-v3, Voyage-3 (alguno tiene free tier generoso suficiente para empezar).
* **Datos confidenciales que no pueden salir**: cualquier modelo open-source self-hosted. BGE-M3 si quieres calidad alta y tienes GPU; sentence-transformers si vas justo de infra.
* **Casos especializados (código, dominio legal, médico)**: `voyage-code-3` para código, modelos fine-tuned específicos de dominio si existen en HuggingFace; en último caso, fine-tuning propio (avanzado, fuera del módulo).

Sobre dimensiones y Matryoshka 

#### Por qué cada vez más modelos las soportan

Matryoshka Representation Learning es una técnica de entrenamiento donde el modelo aprende a poner la información más importante en las primeras dimensiones del vector. La consecuencia práctica: **puedes truncar el vector a menos dimensiones sin perder mucha calidad**.

Ejemplo concreto con text-embedding-3-large (3072 dims nativas). Si truncas a 1024, pierdes alrededor del 3% de calidad en retrieval pero reduces el almacenamiento a un tercio. Si truncas a 256, pierdes alrededor del 10-15% pero el almacenamiento es 12 veces menor. Esta flexibilidad es muy útil cuando escalas a millones o miles de millones de vectores.

Modelos con soporte Matryoshka en 2026: OpenAI text-embedding-3-\*, Nomic Embed, Jina Embeddings v3, varios modelos recientes de la familia BGE. Si vas a escalar mucho, valora esta característica.

#### Ejercicio 1.2 · comparar tres modelos sobre el mismo corpus

Tiempo estimado · 90-100 minutos 

Vas a embedear el mismo corpus con tres modelos distintos (uno open-source local, uno API gratis, uno API barato) y comparar resultados. Este ejercicio es esencial: te da experiencia directa con las diferencias prácticas entre modelos que no se ven en benchmarks.

1. **Prepara las cuentas y claves**. Crea cuenta en OpenAI con saldo (1-2 USD bastan), en Cohere (free tier suficiente). Añade las claves al `.env`: `OPENAI_API_KEY` y `COHERE_API_KEY`.
2. **Instala dependencias**: `pip install openai cohere sentence-transformers numpy pandas`.
3. **Reúne un corpus más amplio** que en L1.1, idealmente 50-100 fragmentos cortos sobre varios temas. Sugerencia: descarga artículos cortos de Wikipedia o usa un dataset de Hugging Face como `datasets.load_dataset("ag_news", split="test[:100]")`.
4. **Para cada uno de los tres modelos**, genera embeddings de todo el corpus:  
   * Modelo 1 · `paraphrase-multilingual-MiniLM-L12-v2` (open-source, gratis, local).  
   * Modelo 2 · Cohere embed-multilingual-v3 (API gratis con free tier).  
   * Modelo 3 · OpenAI text-embedding-3-small (API barata).  
 Mide el tiempo que tarda cada uno y registra el tamaño del vector resultante.
5. **Diseña un set de 10 queries** que mezcle: queries con términos literales del corpus, queries con sinónimos, queries en otro idioma (si tu corpus es multilingüe), queries ambiguas.
6. **Para cada query y cada modelo**, obtén el top-5 de resultados ordenados por similitud coseno. Construye una tabla comparativa.
7. **Analiza divergencias**: ¿en qué queries los tres modelos coinciden?, ¿en cuáles divergen?, ¿qué modelo da el resultado que tu intuición humana considera mejor?
8. **Calcula el coste** aproximado de embedear 1 millón de documentos similares al tuyo con cada modelo. ¿Cuál es la diferencia entre Modelo 2 y Modelo 3 en USD?
9. **Bonus 1 · normalización**. Verifica si cada modelo devuelve vectores normalizados (norma euclidiana = 1). Para los que no lo estén, normalízalos manualmente con `v / np.linalg.norm(v)`. Compara resultados antes y después.
10. **Bonus 2 · medir calidad cuantitativa**. Si tu corpus tiene labels (por ejemplo ag\_news tiene categorías), implementa un experimento de clasificación zero-shot: ¿qué % de aciertos saca cada modelo?

El objetivo no es decidir cuál «gana». Es internalizar que _distintos modelos tienen distintas fortalezas_. Cuando ante un proyecto real digas «vamos a usar OpenAI», querrás poder justificar la elección sobre la base de pruebas concretas como esta, no por moda. Guarda este notebook: te servirá de referencia para futuras decisiones técnicas.

Preguntas frecuentes 

¿Es mejor un modelo más reciente que uno más antiguo?

En general sí pero no automáticamente. Los modelos nuevos suelen incorporar mejores técnicas de entrenamiento y datasets más grandes. Pero _algunos modelos antiguos están más probados en producción_, tienen ecosistema maduro (integraciones con vector DBs, papers de optimización) y son más predecibles. Para proyectos profesionales, suelo recomendar modelos con al menos 6 meses de uso comunitario, no los recién salidos.

¿Puedo cambiar de modelo en mitad de un proyecto?

Sí pero implica **reembedear todo el corpus**. Los embeddings de un modelo no son compatibles con los de otro: el espacio vectorial es completamente distinto. Si tienes 10 millones de documentos indexados con un modelo y quieres cambiar a otro, tienes que regenerar 10 millones de embeddings (con su coste). Por eso es importante elegir bien al principio. Algunos sistemas en producción mantienen dos índices en paralelo durante la migración.

¿Y los embeddings de imágenes? ¿Funcionan igual?

Conceptualmente sí, pero usan modelos distintos (CLIP, OpenCLIP, SigLIP). Hay modelos multimodales (CLIP) que embedean imagen y texto al mismo espacio, lo que permite buscar imágenes por texto. Cae fuera del alcance de este módulo, que se centra en texto. Para multimodal serio, considera _BGE-VL_ o _Voyage Multimodal-3_.

¿Es viable fine-tunear un modelo de embeddings para mi caso?

Sí, especialmente para dominios muy específicos (legal, médico, código en lenguaje propio). El fine-tuning requiere un dataset de pares de textos similares (positivos) y disimilares (negativos) del orden de varios miles. Sentence-transformers tiene utilidades para esto. Pero **antes de fine-tunear, prueba primero con buenos prompts y reranking**: muchas veces la mejora marginal de fine-tunear no compensa el esfuerzo si tu pipeline base no está optimizado.

Recursos para profundizar 

#### Comparación y elección de modelos

* **MTEB Leaderboard**. Benchmark continuamente actualizado. Filtra por tarea (Retrieval) y por idioma. huggingface.co/spaces/mteb/leaderboard
* **OpenAI Embeddings · Documentación oficial**. Especialmente la guía sobre Matryoshka dimensions. platform.openai.com/docs/guides/embeddings
* **Cohere Embeddings · Documentación oficial**. Importante: la distinción entre input\_type. docs.cohere.com/docs/embeddings
* **BGE-M3 paper y modelo**. Open-source de referencia en 2026\. Documentación en HuggingFace. huggingface.co/BAAI/bge-m3
* **Awesome Embeddings · GitHub**. Lista curada de modelos, papers y recursos sobre embeddings. github.com/topics/sentence-embeddings

Fin lección 1.2 · Sigue lección 1.3

LECCIÓN 1.3· \~4 horas · Sub-módulo 1

## Similitud semántica · _medidas y experimentos_

Similitud coseno, distancia euclidiana y producto escalar. Cuándo cada una. Normalización de vectores. Implementación de un buscador k-NN desde cero antes de pasar a bases vectoriales reales. Datasets para experimentar.

Lectura · 70 min Ejemplos · 40 min Ejercicio · 130 min 

1.3.1Medidas de similitud y búsqueda k-NN

#### Al final de esta lección sabrás:

* Explicar las tres medidas de similitud principales y cuándo dan resultados idénticos o distintos.
* Implementar búsqueda k-NN (k-nearest neighbors) sobre embeddings con NumPy puro.
* Entender por qué la búsqueda exacta no escala y dónde entran las técnicas aproximadas (ANN) que verás en SM2.
* Construir un buscador semántico sobre un corpus de varios miles de documentos como precalentamiento del módulo 2.
* Diagnosticar problemas básicos en un sistema de retrieval (queries que no encuentran nada, falsos positivos, etc.).

Las tres medidas principales

Cuando tienes dos vectores y quieres saber «cuánto se parecen», hay tres medidas que vas a ver una y otra vez en código RAG. Conviene entenderlas bien y saber elegir entre ellas.

**Similitud coseno**. Mide el coseno del ángulo entre dos vectores. Va de -1 (vectores opuestos) a 1 (mismo dirección). Es la medida más usada en RAG porque solo considera la _dirección_, ignorando la magnitud. Esto es deseable: un texto largo no debería ser «más similar» a algo solo por ser largo. Matemáticamente: `cos(u, v) = (u · v) / (||u|| * ||v||)`.

**Distancia euclidiana**. Mide la distancia «recta» entre dos puntos en el espacio. Valores van de 0 (idénticos) a infinito. Sensible a la magnitud de los vectores. Se usa menos en RAG pero es el default en algunas bases vectoriales (FAISS, ChromaDB por defecto).

**Producto escalar (dot product)**. Suma de los productos componente a componente. Va de -infinito a +infinito. Es la medida más rápida de calcular. Sensible tanto a dirección como magnitud.

El truco de la normalización 

#### Por qué importa para la elección

Aquí está el dato crucial que aclara todo: **si los vectores están normalizados (norma euclidiana = 1), la similitud coseno y el producto escalar dan el mismo resultado**. La razón es directa: si `||u|| = ||v|| = 1`, entonces `cos(u, v) = u · v`.

Adicionalmente, sobre vectores normalizados existe esta relación: `distancia_euclidiana² = 2 - 2 * coseno`. Es decir: rankear por coseno descendente equivale a rankear por euclidiana ascendente.

**Implicación práctica**: si tu modelo de embeddings devuelve vectores normalizados (OpenAI lo hace por defecto, sentence-transformers también con el parámetro _normalize\_embeddings=True_), las tres medidas te dan el mismo orden de resultados. Solo cambia el valor numérico, no el ranking. Elige producto escalar por velocidad.

Si tu modelo NO normaliza, normaliza tú: `v_norm = v / np.linalg.norm(v)`. Es una operación barata que tienes que hacer una sola vez por vector.

Ejemplo · implementación de las tres medidas 

#### Para verlas en vivo y comprobar la equivalencia

import numpy as np from sentence\_transformers import SentenceTransformer model = SentenceTransformer('all-MiniLM-L6-v2') # normalize\_embeddings=True devuelve vectores con norma 1 emb = model.encode(\[ "El gato duerme en el sofá", "El felino descansa en el mueble", "Las redes neuronales son potentes", \], normalize\_embeddings=True) a, b, c = emb\[0\], emb\[1\], emb\[2\] def coseno(u, v): return np.dot(u, v) / (np.linalg.norm(u) \* np.linalg.norm(v)) def dot(u, v): return np.dot(u, v) def euclid(u, v): return np.linalg.norm(u - v) # Con vectores normalizados, coseno == dot print(f"coseno(a, b) = {coseno(a, b):.4f}") # \~ 0.85 print(f"dot(a, b) = {dot(a, b):.4f}") # \~ 0.85 (igual) print(f"euclid(a, b) = {euclid(a, b):.4f}") # \~ 0.55 (relacionado pero distinto valor) print(f"coseno(a, c) = {coseno(a, c):.4f}") # \~ 0.10 print(f"euclid(a, c) = {euclid(a, c):.4f}") # \~ 1.34

Observa que coseno y dot dan exactamente el mismo número porque los vectores están normalizados. Si los vectores no estuvieran normalizados, dot daría un valor distinto y dependiente de la magnitud, lo cual es indeseable en RAG.

Búsqueda k-NN sobre un corpus · implementación desde cero

k-NN (k-nearest neighbors) significa: «dado un punto query, encuentra los k puntos más cercanos del corpus». Es la operación base del retrieval. La implementación naïve es directa con NumPy:

Ejemplo · k-NN con NumPy puro 

#### Buscador semántico mínimo, \~30 líneas

import numpy as np from sentence\_transformers import SentenceTransformer model = SentenceTransformer('paraphrase-multilingual-MiniLM-L12-v2') corpus = \[ "Madrid es la capital de España y la ciudad más poblada del país.", "El Real Madrid es uno de los clubes de fútbol más importantes.", "París es la capital de Francia, situada al norte del país.", "El Barcelona ganó la Liga Española en 2023.", "Roma es la capital de Italia y centro histórico del Imperio Romano.", "Berlín es la capital y ciudad más grande de Alemania.", "La torre Eiffel es el monumento más visitado de París.", "El Camp Nou es el estadio del FC Barcelona.", # ... añade más \] # Indexación: embedear todo el corpus una vez corpus\_embeddings = model.encode(corpus, normalize\_embeddings=True) # shape: (N, 384) donde N = len(corpus) def buscar(query: str, k: int = 3): # Embedea la query (vectores normalizados → dot product = coseno) q\_emb = model.encode(\[query\], normalize\_embeddings=True)\[0\] # Una sola multiplicación matricial calcula similitud con todo el corpus similitudes = corpus\_embeddings @ q\_emb # shape: (N,) # Indices ordenados de mayor a menor similitud top\_k\_idx = np.argsort(-similitudes)\[:k\] return \[(corpus\[i\], float(similitudes\[i\])) for i in top\_k\_idx\] # Pruebas for resultado, score in buscar("¿qué ciudad es la capital francesa?", k=3): print(f"{score:.3f} · {resultado}") # 0.78 · París es la capital de Francia... # 0.55 · La torre Eiffel es el monumento más visitado... # 0.40 · Madrid es la capital de España... for resultado, score in buscar("equipos de fútbol catalanes", k=2): print(f"{score:.3f} · {resultado}") # 0.65 · El Barcelona ganó la Liga... # 0.60 · El Camp Nou es el estadio del FC Barcelona

Tres cosas a notar. Primero, todo el «motor» son tres líneas: encode, multiplicación, argsort. Una base vectorial no hace conceptualmente más que esto; añade persistencia, escalabilidad e índices aproximados. Segundo, la query «equipos de fútbol catalanes» encuentra correctamente el Barcelona aunque la palabra «catalán» no aparece literalmente: el modelo capta la asociación geográfica. Tercero, los resultados van con score numérico para que puedas filtrar por umbral (por ejemplo, descartar resultados con score < 0.5).

¿Por qué necesitamos bases vectoriales si esto es tan simple?

El ejemplo anterior funciona perfecto para corpus de hasta unos miles de documentos. Empieza a tener problemas serios cuando crece:

* **Memoria**. Si tienes 10 millones de vectores de 1536 dimensiones float32, son _60 GB_ solo de los vectores. No caben en RAM de un portátil. Necesitas almacenamiento en disco con acceso eficiente.
* **Tiempo de búsqueda**. Cada query requiere calcular similitud con todo el corpus (búsqueda exhaustiva, complejidad O(N)). Con N = 10 millones cada query tarda segundos.
* **Inserciones y borrados dinámicos**. En el ejemplo, si añadimos un documento nuevo, tenemos que regenerar el array de embeddings. En producción quieres añadir y borrar documentos sin reconstruir todo.
* **Filtros con metadatos**. «Buscar documentos sobre Python publicados después de 2024»: necesitas combinar búsqueda semántica con filtros estructurados.
* **Concurrencia y persistencia**. Múltiples usuarios consultando a la vez sin corromper el índice.

Las bases vectoriales resuelven estos problemas con técnicas como **ANN (Approximate Nearest Neighbors)**: en lugar de buscar exactamente los k más cercanos (caro), buscan «casi los k más cercanos» con algoritmos como HNSW (Hierarchical Navigable Small World) o IVF (Inverted File Index). El compromiso: pierdes precisión del 1-5% pero ganas velocidad de 100-1000x.

En SM2 vamos a usar ChromaDB, Qdrant y Pinecone, que implementan HNSW por defecto. De momento, internalizar la base: **una vector database es esencialmente lo que has hecho a mano, pero a escala y con índices aproximados**.

Datasets gratuitos para experimentar 

#### Material útil para los ejercicios y el proyecto final

Cuando aprendes RAG es importante practicar sobre datasets variados, no solo sobre tres frases inventadas. Algunos datasets gratuitos útiles, accesibles vía `datasets.load_dataset()` de HuggingFace:

* **ag\_news**: 120.000 noticias clasificadas en 4 categorías (World, Sports, Business, Sci/Tech). Ideal para experimentos de búsqueda y clasificación.
* **squad o squad\_v2**: dataset de question-answering con pasajes de Wikipedia. Útil para evaluar retrieval (sabes qué pasaje contiene la respuesta).
* **wikipedia (subset español)**: snapshots de Wikipedia en español. Pesado pero realista. Filtra por temas concretos para casos manejables.
* **BEIR benchmark**: colección de datasets específicos para evaluar retrieval. SCIDOCS, FiQA, NQ. Útil cuando quieras evaluar tu pipeline con métricas estándar.
* **EUR-Lex**: documentos legales de la UE en varios idiomas, incluido español. Útil si te interesa el dominio legal.
* **Tu propio corpus**: para el proyecto final, recolectar PDFs reales (manuales, documentación interna de un proyecto open-source que conozcas, leyes) es lo más realista.

#### Ejercicio 1.3 · buscador semántico sobre Wikipedia

Tiempo estimado · 2-2,5 horas 

Vas a construir un buscador semántico sobre un corpus de varios miles de párrafos de Wikipedia, completamente desde cero con NumPy, sin base vectorial todavía. Es la antesala perfecta del SM2 y consolida los conceptos del SM1.

1. **Carga un subset de Wikipedia**. Usa `datasets.load_dataset("wikipedia", "20220301.es", split="train", streaming=True)` e itera tomando los primeros 5.000-10.000 artículos. Como alternativa más ligera, usa `datasets.load_dataset("ag_news", split="train[:5000]")` si prefieres inglés.
2. **Procesa el corpus**. Cada artículo de Wikipedia es largo; divídelo en párrafos. Para este ejercicio, tomamos cada párrafo como un documento independiente. Filtra los muy cortos (menos de 50 palabras) y los muy largos (más de 500 palabras).
3. **Elige tu modelo de embeddings**. Recomendado: `paraphrase-multilingual-MiniLM-L12-v2` para Wikipedia en español, o `all-MiniLM-L6-v2` si trabajas con AG News en inglés. Más adelante puedes probar también con text-embedding-3-small para comparar.
4. **Embedea todo el corpus**. Usa `batch_size=64` para no sobrecargar memoria. Guarda los embeddings y los textos en disco con `np.save` y un pickle (o un archivo JSON) para no tener que regenerarlos cada vez que reabras el notebook.
5. **Implementa la función _buscar(query, k)_** como en el ejemplo de la lección. Mide el tiempo que tarda una query sobre 10.000 documentos.
6. **Prueba con 15-20 queries variadas**. Tipos sugeridos:  
   * Preguntas factuales («¿quién fue Einstein?», «¿cuándo se descubrió la penicilina?»).  
   * Queries por concepto sin nombres propios («grandes científicos del siglo XX»).  
   * Queries ambiguas («Java» como isla, café o lenguaje).  
   * Queries en otro idioma del que está el corpus.  
   * Queries con jerga o sinónimos.
7. **Implementa un filtro por umbral**: que la función solo devuelva resultados con score > 0.4\. Observa qué pasa cuando la query no tiene buena respuesta en el corpus (¿devuelve resultados malos? ¿no devuelve nada?).
8. **Bonus 1 · medir tiempo a escala**. Mide tiempo de búsqueda con corpus de 1.000, 5.000, 10.000, 50.000 documentos. Gráfica la curva. ¿Cuándo empieza a ser inaceptable?
9. **Bonus 2 · híbrido manual**. Implementa una versión que combine los resultados de tu k-NN con una búsqueda BM25 simple (usa la librería `rank_bm25`). Reranke los resultados sumando un porcentaje de ambos scores. Compara queries que mejoran y queries que empeoran.
10. **Bonus 3 · cacheo de queries**. Implementa cache de embeddings de queries (un diccionario en memoria). Si la misma query se repite, no regeneras embedding. Mide el ahorro de tiempo en queries repetidas.

Este ejercicio es deliberadamente sin base vectorial. La lección no es construir un sistema escalable, sino entender lo que una base vectorial te abstrae cuando la uses en SM2\. Cuando en la siguiente lección levantes ChromaDB y veas que «inserta documentos», «busca por similitud», entenderás exactamente qué hace por debajo. Esa comprensión profunda te diferenciará del 80% de desarrolladores que usan vector DBs como cajas mágicas.

Preguntas frecuentes 

¿Es problema que coseno y producto escalar den lo mismo con vectores normalizados? ¿No estoy desperdiciando información?

No, al contrario. Es una propiedad útil que te permite usar la operación más eficiente (producto escalar) sin sacrificar nada. Las bases vectoriales aprovechan esto: muchas piden que normalices al insertar y por debajo solo computan dot products. Si tu modelo ya normaliza, no tienes que hacer nada explícito.

¿Cuándo coseno y euclidiana dan rankings distintos?

Sobre vectores no normalizados, sí dan rankings distintos. La euclidiana penaliza diferencias de magnitud, el coseno no. En la práctica de RAG, casi siempre quieres coseno (o equivalentemente, producto escalar sobre vectores normalizados) porque no queremos que la longitud del texto sesgue la similitud. La distancia euclidiana se usa más en otros contextos: clustering en espacios de features físicos, embeddings de imágenes en algunos casos.

¿Cómo evalúo si mi retrieval es bueno sin tener ground truth?

Sin ground truth, la evaluación es cualitativa: leer los resultados manualmente y juzgar si son relevantes. Es lo que estás haciendo en el ejercicio. Para evaluación cuantitativa rigurosa necesitas un dataset etiquetado (cada query con la lista de documentos relevantes) y métricas como Recall@K, MRR (Mean Reciprocal Rank) o NDCG. Lo veremos en L4.3 cuando entremos en evaluación con RAGAS. Para ahora, la evaluación cualitativa basta.

¿Por qué hablamos solo de k-NN exacta y no de aproximada?

Para construir intuición correcta. El k-NN exacto es el «techo de calidad»: lo que devolvería el sistema perfecto. Los ANN (HNSW, IVF) sacrifican un pequeño % de recall a cambio de mucha velocidad. Cuando uses ChromaDB en SM2 y veas que devuelve resultados ligeramente distintos al k-NN exacto, sabrás por qué. Las técnicas ANN están muy probadas y la pérdida típica es 1-5% de recall, normalmente aceptable. Ningún sistema RAG en producción a escala usa k-NN exacta.

Recursos para profundizar 

#### Similitud y k-NN

* **NumPy documentation**. Refresca operaciones vectoriales y matriciales si vas justo. numpy.org/doc
* **Sentence-Transformers · Semantic Search tutorial**. Tutorial oficial con código directamente aplicable a tu ejercicio. sbert.net/examples/applications/semantic-search
* **HNSW paper**. Si quieres entender qué hay debajo de las bases vectoriales modernas. Lectura técnica. arxiv.org/abs/1603.09320
* **Faiss · documentación de Meta**. Librería pura para búsqueda vectorial. Conocerla te da contexto sobre lo que hacen las DBs por encima. faiss.ai
* **HuggingFace Datasets**. Catálogo de datasets gratuitos para experimentar. huggingface.co/datasets

Fin del sub-módulo 1 · Sigue sub-módulo 2 · Bases vectoriales

SUB-MÓDULO 2· 10 horas · 3 lecciones

## Bases vectoriales · _Pinecone, Qdrant, ChromaDB_

De los embeddings sueltos a bases de datos diseñadas para almacenarlos a escala. ChromaDB local para prototipos, Qdrant self-hosted con Docker para producción, Pinecone serverless cloud para escala sin gestionar infraestructura. Cómo elegir según caso y cómo migrar entre ellas.

10 horas totales 3 lecciones 3 ejercicios prácticos Python · Docker · APIs cloud 

LECCIÓN 2.1· \~2,5 horas · Sub-módulo 2

## Panorama de bases vectoriales · _cuándo cada una_

Qué es una vector database y qué problema resuelve. Comparativa de las opciones principales en 2026 (ChromaDB, Qdrant, Pinecone, Weaviate, Milvus, pgvector). Criterios para decidir entre open-source self-hosted y SaaS gestionado.

Lectura · 50 min Ejemplos · 25 min Ejercicio · 75 min 

2.1.1El ecosistema y los criterios de elección

#### Al final de esta lección sabrás:

* Definir qué es una vector database y qué la distingue de una base de datos tradicional.
* Conocer los actores principales del ecosistema en 2026 con sus fortalezas y debilidades.
* Decidir entre self-hosted open-source y SaaS cloud según constraints del proyecto.
* Anticipar las trampas de escalabilidad y planificar para ellas desde el diseño inicial.
* Elegir con criterio entre ChromaDB, Qdrant y Pinecone para el resto del módulo.

Qué es exactamente una vector database

Una **vector database** es una base de datos especializada en almacenar embeddings y permitir búsqueda por similitud eficiente. Conceptualmente hace lo mismo que tu k-NN con NumPy del SM1, pero añade:

* **Persistencia**. Los embeddings se guardan en disco (no solo en RAM) y sobreviven a reinicios.
* **Índices ANN**. Algoritmos como HNSW que aceleran las búsquedas de O(N) a O(log N) aproximadamente, a cambio de un pequeño % de recall.
* **Metadatos y filtros**. Cada vector puede tener metadatos asociados (fecha, autor, categoría, lo que sea) y puedes filtrar por ellos en la búsqueda.
* **Inserciones y borrados dinámicos**. Añades documentos sin reconstruir el índice completo.
* **API consistente**. Una interfaz limpia para insertar, buscar, actualizar, borrar.
* **Concurrencia**. Múltiples clientes pueden leer y escribir simultáneamente.
* **A veces, full-text search híbrido**. Combinación con BM25 para hybrid search (lo verás en SM3).

Algunas bases vectoriales son **vector-first** (Pinecone, Qdrant, Weaviate, Milvus, ChromaDB) y otras son **añadidos a bases existentes** (pgvector para Postgres, Atlas Vector Search para MongoDB, Redis Stack, Elasticsearch dense\_vector). Cada enfoque tiene su lógica: las vector-first están optimizadas para esta carga; las extensiones aprovechan infraestructura existente y simplifican el stack.

El panorama de las principales · 2026

| Base vectorial | Tipo                | Licencia                          | Free tier                                                | Cuándo usarla                                                                            |
| -------------- | ------------------- | --------------------------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| ChromaDB       | Vector-first        | Apache 2.0 (open)                 | Self-hosted gratis · Chroma Cloud en beta                | Prototipos, scripts locales, casos pequeños-medianos sin necesidad de servidor dedicado. |
| Qdrant         | Vector-first        | Apache 2.0 (open)                 | Self-hosted gratis · Qdrant Cloud Free 1 GB para siempre | Producción seria self-hosted o SaaS, hybrid search nativo, filtros complejos.            |
| Pinecone       | Vector-first SaaS   | Propietario                       | Serverless Free hasta 2 GB de almacenamiento             | No querer gestionar infraestructura, escala sin esfuerzo, integración fácil.             |
| Weaviate       | Vector-first        | BSD-3 (open)                      | Self-hosted gratis · WCS Sandbox 14 días                 | Hybrid search, modelos integrados, esquemas tipo GraphQL.                                |
| Milvus         | Vector-first        | Apache 2.0 (open)                 | Self-hosted gratis · Zilliz Cloud Free 2 GB              | Escala masiva (miles de millones de vectores), arquitectura distribuida.                 |
| pgvector       | Extensión Postgres  | PostgreSQL License (open)         | Si ya usas Postgres, gratis                              | Stack con Postgres existente, datos relacionales + vectores en una sola base.            |
| Redis Stack    | Extensión Redis     | RSALv2/SSPLv1                     | Self-hosted · Redis Cloud Free 30 MB                     | Stack con Redis existente, latencia muy baja, vectores no muy grandes.                   |
| Elasticsearch  | Buscador + vectores | Elastic License (no OSS estricto) | Self-hosted · Elastic Cloud trial 14 días                | Combinación con texto y filtros complejos, equipos con Elasticsearch ya.                 |

El módulo se centra en **ChromaDB, Qdrant y Pinecone** porque cubren los tres patrones principales: ChromaDB para prototipos rápidos, Qdrant para producción self-hosted o cloud económico, Pinecone para producción cloud sin gestionar nada. Conocer estas tres bien te permite afrontar el 95% de los casos profesionales.

Self-hosted open-source vs SaaS 

#### El trade-off real más allá del marketing

**Self-hosted open-source** (Qdrant, ChromaDB, Weaviate, Milvus, pgvector). Sin coste de licencia, sin enviar datos a terceros, control total sobre versión y configuración. A cambio: gestionas tú backups, alta disponibilidad, escalado, monitoring. Para volúmenes pequeños-medios en una empresa con perfil técnico, es muy razonable. Para casos sensibles (legal, salud, defensa) es prácticamente obligado.

**SaaS gestionado** (Pinecone, Weaviate Cloud, Qdrant Cloud, Zilliz Cloud). Pagas por uso (almacenamiento + queries). No gestionas servidores ni alta disponibilidad. La escala es elástica: si pasas de 1M a 100M de vectores no necesitas reaprovisionar nada. A cambio: vendor lock-in moderado (los datos están en su cloud), coste predecible solo si tu uso lo es.

**La pregunta crítica**: ¿cuántos vectores prevés tener en 12 meses? Si menos de 1 millón, casi cualquier opción funciona. Entre 1 y 100 millones, hay que pensar bien. Más de 100 millones, SaaS gestionado o Milvus distribuido son las opciones realistas.

Trampas comunes que importan desde el principio

Hay algunas decisiones que parecen pequeñas al principio pero te muerden después. Conviene anticiparlas:

* **Dimensionalidad fija por colección**. Una vez creas un índice con vectores de 1536 dimensiones, no puedes meter vectores de 768\. Si cambias de modelo de embeddings, normalmente necesitas crear una nueva colección y reembedear todo.
* **Métrica de distancia fija por colección**. Igual: defines coseno, dot product o euclidiana al crear el índice. No se cambia sin reconstruir.
* **Coste de almacenamiento crece linealmente con el corpus**. 10 millones de vectores de 1536 dimensiones float32 son 60 GB. En Pinecone serverless, \~10 USD/mes. En self-hosted, espacio en disco. Planifícalo desde el principio.
* **Limit en metadatos por vector**. Pinecone limita a 40 KB de metadatos por vector. Si quieres guardar el texto completo dentro, no cabe. Lo normal es guardar el texto en otra base (Postgres, S3) y guardar solo un ID en los metadatos.
* **Diferencias en filtros**. No todas las DBs soportan los mismos operadores. Filtrar por «category in \[A, B, C\] and date > 2024» es trivial en Qdrant; en Pinecone hay restricciones más sutiles según el plan.
* **Operaciones a granel**. Algunas DBs son muy lentas insertando uno por uno y mucho más rápidas en batch (cientos o miles por llamada). Lo verás en los ejercicios.

Ejemplo · misma operación en las tres DBs 

#### Para que veas el patrón común

Las tres bases que vamos a usar tienen APIs muy parecidas conceptualmente. Aquí están las tres operaciones básicas (insertar, buscar) en cada una. Las verás en detalle en las próximas lecciones; mirarlas juntas ayuda a fijar el patrón.

\# --- ChromaDB --- import chromadb client = chromadb.PersistentClient(path="./chroma\_db") collection = client.get\_or\_create\_collection("documentos") collection.add( documents=\["texto 1", "texto 2"\], embeddings=\[\[0.1, 0.2, ...\], \[0.3, 0.4, ...\]\], metadatas=\[{"cat": "a"}, {"cat": "b"}\], ids=\["1", "2"\], ) results = collection.query(query\_embeddings=\[query\_vec\], n\_results=3) # --- Qdrant --- from qdrant\_client import QdrantClient from qdrant\_client.models import VectorParams, Distance, PointStruct client = QdrantClient(host="localhost", port=6333) client.create\_collection( "documentos", vectors\_config=VectorParams(size=1536, distance=Distance.COSINE), ) client.upsert("documentos", points=\[ PointStruct(id=1, vector=\[0.1, 0.2, ...\], payload={"text": "texto 1", "cat": "a"}), PointStruct(id=2, vector=\[0.3, 0.4, ...\], payload={"text": "texto 2", "cat": "b"}), \]) results = client.search("documentos", query\_vector=query\_vec, limit=3) # --- Pinecone --- from pinecone import Pinecone, ServerlessSpec pc = Pinecone(api\_key=os.getenv("PINECONE\_API\_KEY")) pc.create\_index( "documentos", dimension=1536, metric="cosine", spec=ServerlessSpec(cloud="aws", region="us-east-1"), ) index = pc.Index("documentos") index.upsert(vectors=\[ {"id": "1", "values": \[0.1, 0.2, ...\], "metadata": {"text": "texto 1", "cat": "a"}}, {"id": "2", "values": \[0.3, 0.4, ...\], "metadata": {"text": "texto 2", "cat": "b"}}, \]) results = index.query(vector=query\_vec, top\_k=3, include\_metadata=True)

Mismo patrón, distinto vocabulario. ChromaDB llama «collection» a lo que Qdrant también llama «collection» y Pinecone llama «index». ChromaDB separa documents y embeddings y metadatas; Qdrant y Pinecone los meten todos en «points» o «vectors». Una vez entiendes una, las otras dos las pillas en horas.

Criterios prácticos para tu proyecto final

Para el proyecto final del módulo (SM4), elegirás una de las tres como motor de retrieval. Esta es una guía para que decidas con criterio:

* **Elige ChromaDB si**: quieres todo local, no quieres levantar contenedores, vas a tener menos de 100K documentos, prefieres simplicidad sobre rendimiento, te basta con persistencia en archivo.
* **Elige Qdrant si**: quieres self-hosted en docker-compose junto a tu n8n del Módulo 3, vas a tener entre 100K y varios millones de documentos, necesitas hybrid search nativo o filtros complejos, quieres una opción que escale igual a producción seria sin migrar de tecnología.
* **Elige Pinecone si**: no quieres tocar infraestructura, quieres una API SaaS limpia, tu volumen va a estar dentro del free tier (2 GB), o si quieres familiarizarte con un SaaS que se usa mucho en la industria.

Mi recomendación pedagógica para el proyecto final: **Qdrant self-hosted en docker-compose**, integrándolo con la infraestructura n8n que ya levantaste en el M3\. Es lo más cercano a lo que verás en empresas reales con datos sensibles y volumen mediano.

#### Ejercicio 2.1 · matriz de decisión para tu caso

Tiempo estimado · 60-75 minutos 

Antes de tocar código, vas a tomar una decisión informada sobre qué base vectorial usar en tu proyecto final. La habilidad de elegir tecnología con criterio es tan valiosa como la de usarla.

1. **Define tu caso de uso del proyecto final** (puedes refinar después). Anota: tipo de documentos (PDFs, web, código, mezcla), volumen estimado (¿100, 10.000, 1 millón?), idioma, sensibilidad de datos, plan de despliegue (¿local, VPS personal, cloud?).
2. **Para cada una de las tres bases del módulo** (ChromaDB, Qdrant, Pinecone) responde:  
   * ¿Encaja en mi volumen previsto sin costes?  
   * ¿Soporta los filtros por metadatos que probablemente necesitaré?  
   * ¿Cumple los requisitos de privacidad de mis datos?  
   * ¿Cuánto tiempo me llevará tenerla funcionando con datos reales?  
   * ¿Qué riesgos veo a 12 meses si mi proyecto crece?
3. **Lee la documentación oficial** de cada una (URLs en Resources). No te pares en blog posts: ve directo a la documentación. Pásale al menos 15-20 minutos a cada una.
4. **Construye una matriz comparativa** en una hoja (Notion, papel, lo que sea). Filas: las tres DBs. Columnas: precio, dificultad de setup, calidad de docs, comunidad activa, integración con LangChain/LlamaIndex, hybrid search, soporte a tu idioma, sentirte cómodo operándola.
5. **Toma una decisión preliminar** y escríbela en una frase como compromiso: «Voy a usar X porque...». Tres razones máximo. Si tras los ejercicios de L2.2 y L2.3 cambias de opinión, perfecto, pero el ejercicio aquí es comprometerse con criterio.
6. **Bonus · revisión de seguridad**. Si decides Pinecone o cualquier SaaS, revisa su SOC 2 / GDPR / data residency. Si vas a self-hosted, ¿quién accederá al servidor?, ¿hay datos personales?, ¿necesitas cifrado en reposo?

Este ejercicio puede parecer «no-código» pero es exactamente lo que harás en tu primer mes como AI Engineer junior cuando te pidan elegir una vector DB. La capacidad de razonar sobre trade-offs vale más en entrevistas técnicas que demostrar 200 líneas de código. No te lo saltes.

Preguntas frecuentes 

¿Y si quiero usar pgvector para no añadir otra tecnología al stack?

Es una opción muy razonable y cada vez más popular. pgvector es una extensión de PostgreSQL que añade soporte para vectores y búsqueda con HNSW. Para casos pequeños-medianos (hasta varios millones de vectores) funciona perfectamente, y tener vectores y datos relacionales en la misma base simplifica mucho. No lo cubrimos en profundidad en el módulo por foco, pero si tu stack ya es Postgres, pgvector es una elección sensata. Los principios del módulo aplican igual.

¿Cuál es la diferencia real entre Pinecone serverless y Pinecone pod-based?

Pinecone tuvo durante años un modelo «pod-based» (pagas por capacidad reservada, fijo) que sigue existiendo. En 2024 lanzaron «serverless» (pagas por uso, escalable, free tier hasta 2 GB). Para nuevos proyectos casi siempre conviene serverless por economía y simplicidad. El plan free serverless es lo que vamos a usar en el módulo.

¿Cuándo conviene usar Milvus en lugar de Qdrant?

Milvus está optimizado para escala muy grande con arquitectura distribuida nativa. Si vas a tener cientos de millones o miles de millones de vectores y necesitas sharding, replicación, alta disponibilidad gestionada, Milvus tiene ventaja. Para casos hasta unos cuantos millones de vectores en una máquina, Qdrant es más simple y rápido de operar. La mayoría de proyectos no llegan al volumen donde Milvus se justifica.

¿Las APIs cambian mucho entre versiones?

Sí, especialmente en el ecosistema joven. Pinecone cambió su API drásticamente entre v2 y v3 en 2023\. ChromaDB ha evolucionado el cliente varias veces. Qdrant es más estable. **Recomendación práctica**: cuando uses un tutorial, comprueba la fecha. Tutoriales de 2022-2023 sobre Pinecone están desfasados. Los ejemplos de este módulo están actualizados a 2026 pero verifica con docs oficiales antes de copiar a tu proyecto.

Recursos para profundizar 

#### Documentación oficial de las tres bases

* **ChromaDB Documentation**. La referencia. docs.trychroma.com
* **Qdrant Documentation**. Muy completa, especialmente la sección de filtros complejos. qdrant.tech/documentation
* **Pinecone Documentation**. Importante: distingue entre serverless y pod-based. docs.pinecone.io
* **pgvector · GitHub**. Si te interesa la opción Postgres. github.com/pgvector/pgvector
* **VectorDB Comparison**. Comparativa abierta mantenida por la comunidad. github.com/erikbern/ann-benchmarks
* **Awesome Vector Search · GitHub**. Lista curada de recursos. github.com/currentslab/awesome-vector-search

Fin lección 2.1 · Sigue lección 2.2

LECCIÓN 2.2· \~3,5 horas · Sub-módulo 2

## ChromaDB local · _primera VDB en tu máquina_

Instalación, creación de colecciones, inserción en batch, query con filtros por metadatos y persistencia en disco. ChromaDB es la base vectorial más sencilla de empezar a usar y la ideal para prototipos rápidos y aprendizaje.

Lectura · 60 min Ejemplos · 30 min Ejercicio · 120 min 

2.2.1Indexar, buscar, filtrar con ChromaDB

#### Al final de esta lección sabrás:

* Instalar y configurar ChromaDB en modo persistente sin necesidad de servidor externo.
* Crear colecciones, insertar documentos en batch con sus embeddings y metadatos.
* Realizar búsquedas por similitud con filtros por metadatos (where).
* Gestionar el ciclo de vida: actualizar, borrar, listar y reindexar colecciones.
* Conectar ChromaDB con sentence-transformers como provider de embeddings integrado.

Por qué empezamos con ChromaDB

ChromaDB es probablemente la base vectorial más fácil de empezar a usar en Python. Tres motivos:

* **Cero infraestructura**. No requiere Docker ni un servidor separado. Corre embebida en tu proceso Python. Persiste en un directorio del disco.
* **Embeddings opcionales**. Puedes pasarle embeddings ya calculados, o dejarle que los calcule por ti con sentence-transformers (descarga el modelo automáticamente). Esto reduce líneas de código en prototipos.
* **API directa**. Métodos como `add`, `query`, `delete` hacen exactamente lo que esperas.

No es la opción más rápida ni la que escala a más vectores, pero como aprendizaje y prototipo es excepcional. Muchos proyectos pequeños-medianos en producción usan ChromaDB sin mayor problema.

Instalación y primer cliente

La instalación es directa:

Ejemplo · primer cliente persistente 

#### Crear, ver y borrar colecciones

pip install chromadb # En tu script o notebook: import chromadb # Cliente persistente: guarda en disco en ./chroma\_db client = chromadb.PersistentClient(path="./chroma\_db") # Crea o recupera una colección collection = client.get\_or\_create\_collection( name="documentos\_modulo\_4", metadata={"description": "Corpus de aprendizaje del Módulo 4"}, ) # Ver colecciones existentes print(client.list\_collections()) # Información de la colección print(collection.count()) # 0 al principio

Alternativas al PersistentClient: `chromadb.Client()` en memoria (se pierde al cerrar el proceso, útil para tests), `chromadb.HttpClient(host, port)` para conectar a un Chroma server remoto (modo cliente-servidor, más adecuado para producción con múltiples clientes). Para aprendizaje y este módulo, PersistentClient es perfecto.

Inserción en batch · el patrón correcto

ChromaDB acepta inserciones de documentos individuales, pero inserción en batch (cientos o miles a la vez) es muchísimo más eficiente. Patrón estándar:

Ejemplo · insertar con embeddings calculados aparte 

#### El patrón más usado en producción

from sentence\_transformers import SentenceTransformer import chromadb model = SentenceTransformer('paraphrase-multilingual-MiniLM-L12-v2') client = chromadb.PersistentClient(path="./chroma\_db") collection = client.get\_or\_create\_collection("noticias") documentos = \[ "El Real Madrid ha fichado a un nuevo entrenador para la próxima temporada.", "La Comisión Europea aprueba un nuevo plan de financiación para startups.", "Investigadores chinos publican un avance en computación cuántica.", "Las exportaciones españolas crecieron un 5% en el primer trimestre.", # ... añade muchos más \] # Calculamos embeddings en batch (mucho más rápido que uno a uno) embeddings = model.encode(documentos, normalize\_embeddings=True).tolist() # Metadatos: cualquier dict con tipos básicos (str, int, float, bool) metadatos = \[ {"categoria": "deporte", "fecha": "2026-05-10", "fuente": "marca"}, {"categoria": "economia", "fecha": "2026-05-11", "fuente": "elpais"}, {"categoria": "ciencia", "fecha": "2026-05-12", "fuente": "nature"}, {"categoria": "economia", "fecha": "2026-05-13", "fuente": "expansion"}, \] # IDs únicos por documento (string) ids = \[f"doc\_{i}" for i in range(len(documentos))\] collection.add( documents=documentos, embeddings=embeddings, metadatas=metadatos, ids=ids, ) print(collection.count()) # 4

Algunas reglas importantes. Los **IDs deben ser únicos**: si vuelves a llamar `add` con el mismo ID, ChromaDB lanza error; usa `upsert` en su lugar si quieres sobrescribir. Los **metadatos tienen tipos limitados**: string, int, float, bool, y listas de esos. No puedes guardar dicts anidados. Si necesitas estructuras complejas, serialízalas a JSON string.

Ejemplo · insertar dejando que ChromaDB calcule embeddings 

#### El atajo para prototipos rápidos

ChromaDB puede generar embeddings por ti usando sentence-transformers internamente. Útil si quieres reducir líneas de código, pero te quita control sobre qué modelo usa.

from chromadb.utils import embedding\_functions # Función de embedding integrada sentence\_transformer\_ef = embedding\_functions.SentenceTransformerEmbeddingFunction( model\_name="paraphrase-multilingual-MiniLM-L12-v2" ) collection = client.get\_or\_create\_collection( name="noticias\_auto", embedding\_function=sentence\_transformer\_ef, ) # Sin pasar embeddings: ChromaDB los calcula al insertar collection.add( documents=documentos, metadatas=metadatos, ids=ids, )

Hay también funciones de embedding integradas para OpenAI, Cohere, HuggingFace API, Google Gemini, etc. Documentación oficial las lista. **Recomendación profesional**: para producción, calcula tú los embeddings con control explícito; el atajo es útil para prototipos pero te quita visibilidad sobre coste y modelo.

Búsqueda con filtros por metadatos

La fuerza de las bases vectoriales modernas no es solo búsqueda semántica: es combinarla con filtros estructurados. «Busca documentos similares a esta query, pero solo los de categoría 'ciencia' publicados después del 2026-05-01».

Ejemplo · query con where clause 

#### Búsqueda semántica filtrada

query = "avances tecnológicos recientes" query\_embedding = model.encode(\[query\], normalize\_embeddings=True).tolist() # Query simple sin filtro results = collection.query( query\_embeddings=query\_embedding, n\_results=3, ) # Query con filtro por metadato (where clause) results\_filtrados = collection.query( query\_embeddings=query\_embedding, n\_results=3, where={"categoria": "ciencia"}, # solo categoría == ciencia ) # Filtros complejos con operadores results\_complejos = collection.query( query\_embeddings=query\_embedding, n\_results=5, where={ "$and": \[ {"categoria": {"$in": \["ciencia", "tecnologia"\]}}, {"fecha": {"$gte": "2026-05-01"}}, \] }, ) # La respuesta tiene estructura: # results\["documents"\] -> List\[List\[str\]\] (top-K por cada query) # results\["metadatas"\] -> List\[List\[dict\]\] # results\["distances"\] -> List\[List\[float\]\] # results\["ids"\] -> List\[List\[str\]\] for doc, meta, dist in zip(results\_filtrados\["documents"\]\[0\], results\_filtrados\["metadatas"\]\[0\], results\_filtrados\["distances"\]\[0\]): print(f"\[{dist:.3f}\] {meta\['categoria'\]} · {doc}")

Operadores disponibles en where: `$eq` (default si pasas valor directo), `$ne`, `$gt`, `$gte`, `$lt`, `$lte`, `$in`, `$nin`. Y composiciones lógicas `$and`, `$or`. También `where_document` permite filtrar por contenido del documento literal (full-text). La sintaxis es muy parecida a MongoDB.

Nota sobre las distancias: ChromaDB usa por defecto distancia L2 (euclidiana al cuadrado). Si quieres coseno, especifícalo al crear la colección: `metadata={"hnsw:space": "cosine"}`. Para vectores normalizados como los nuestros, los rankings son equivalentes pero los valores numéricos cambian.

Ciclo de vida · actualizar, borrar, reindexar

Operaciones que vas a necesitar en cualquier proyecto real:

Ejemplo · operaciones de mantenimiento 

#### Update, delete, get

\# Recuperar documentos por ID items = collection.get(ids=\["doc\_0", "doc\_1"\]) print(items\["documents"\]) # Recuperar todos los documentos con un filtro todos\_deporte = collection.get(where={"categoria": "deporte"}) # Actualizar metadatos o documentos de IDs existentes collection.update( ids=\["doc\_0"\], metadatas=\[{"categoria": "deporte", "fecha": "2026-05-10", "fuente": "as", "verificado": True}\], ) # Upsert: actualiza si existe, crea si no collection.upsert( ids=\["doc\_99"\], documents=\["Texto nuevo"\], embeddings=\[model.encode(\["Texto nuevo"\], normalize\_embeddings=True)\[0\].tolist()\], metadatas=\[{"categoria": "test"}\], ) # Borrar por ID collection.delete(ids=\["doc\_99"\]) # Borrar por filtro collection.delete(where={"categoria": "test"}) # Borrar colección completa # client.delete\_collection("noticias")

Persistencia y backups 

#### Qué pasa con tus datos

Con `PersistentClient(path="./chroma_db")`, ChromaDB crea una carpeta con archivos SQLite y los vectores en disco. Esta carpeta es tu base entera: **cópiala** y tienes backup completo. Restaurarla es copiarla a otra máquina y abrir cliente apuntando ahí.

Limitaciones a conocer. ChromaDB persistente no está pensada para acceso concurrente desde múltiples procesos (varios scripts a la vez intentando escribir). Si necesitas multi-cliente, usa Chroma Server (`chroma run --path ./chroma_db`) y conecta con HttpClient. Para producción seria con concurrencia alta, conviene Qdrant.

El tamaño en disco crece linealmente con el corpus. Como referencia: 100.000 vectores de 1536 dimensiones float32 ocupan unos 600 MB + índices HNSW. Planifica espacio.

#### Ejercicio 2.2 · primer índice persistente sobre tu propio corpus

Tiempo estimado · 100-120 minutos 

Vas a migrar lo que hiciste en SM1 con NumPy a ChromaDB. Mismo corpus de Wikipedia (o similar), pero ahora con persistencia, metadatos y filtros.

1. **Instala las dependencias**: `pip install chromadb sentence-transformers datasets`.
2. **Carga el corpus**. Reutiliza el corpus de Wikipedia o AG News del ejercicio 1.3\. Si no lo tienes, descarga un subset: `datasets.load_dataset("ag_news", split="train[:5000]")`.
3. **Decide tu schema de metadatos**. Para cada documento, qué metadatos vas a guardar. Sugerencias: _categoria_ (si el dataset tiene labels), _fecha_ (asigna fechas dummy si no hay), _longitud_ (chars), _idioma_, _fuente_. Tener metadatos variados te permite practicar filtros más adelante.
4. **Crea la colección persistente** con métrica coseno. Inserta todos los documentos en batches de 500 (no de uno en uno; medir la diferencia te dará intuición).
5. **Implementa una función de búsqueda con filtros opcionales**:  
   * `buscar(query, k=5)`  
   * `buscar_por_categoria(query, categoria, k=5)`  
   * `buscar_recientes(query, desde_fecha, k=5)`
6. **Prueba con queries reales**. Verifica que los filtros funcionan: que al filtrar por categoría no aparecen documentos de otras categorías.
7. **Compara con tu k-NN de NumPy del SM1**. ¿Los resultados son los mismos? ¿Cuánto más rápido es ChromaDB en queries? ¿Y en cargar la colección al inicio?
8. **Operaciones de mantenimiento**: implementa funciones para añadir un documento nuevo, actualizar la categoría de un documento por ID, y borrar todos los documentos de una categoría concreta.
9. **Persistencia en práctica**: cierra Python, abre un notebook nuevo, abre la misma colección y verifica que todo sigue ahí. Esto te da intuición sobre persistencia real.
10. **Bonus 1 · embeddings de OpenAI**. Crea una segunda colección con embeddings de text-embedding-3-small en vez de sentence-transformers. Compara calidad de resultados con las mismas queries. Mide el coste en USD de embedear el corpus.
11. **Bonus 2 · benchmark de inserción**. Mide el tiempo de insertar 5.000 documentos: uno a uno vs batch de 100 vs batch de 1.000\. La diferencia será radical. Aprende qué tamaño de batch es óptimo en tu máquina.
12. **Bonus 3 · uso de espacio**. Mide cuánto ocupa la carpeta `./chroma_db` tras insertar todo. Extrapola: si tuvieras 1 millón de documentos, ¿cuánto ocuparía?

Si tu portátil es modesto, no insertes más de 10.000 documentos en este ejercicio. ChromaDB es eficiente pero el cálculo de embeddings con sentence-transformers en CPU para corpus grande es lento. Para 50.000+ documentos conviene tener GPU o usar OpenAI embeddings (más rápido vía API). Guarda este notebook bien: será la base sobre la que construirás el primer pipeline RAG completo en SM3.

Preguntas frecuentes 

¿Puedo usar ChromaDB en producción o es solo para prototipos?

Para casos pequeños-medianos (decenas a cientos de miles de documentos, uso interno de equipo, no muchos clientes concurrentes) es perfectamente viable en producción. Para escala mayor o concurrencia alta, conviene Qdrant o Pinecone. Muchos proyectos reales empiezan con ChromaDB y migran a Qdrant cuando crecen, lo cual está bien porque la lógica es muy similar.

¿Cómo elijo entre pasar embeddings yo o dejar que ChromaDB los calcule?

Calcular tú es lo profesional: te da control sobre qué modelo se usa, batch sizes, optimización, posibilidad de usar GPU dedicada, y permite cachear/reutilizar embeddings en otros sistemas. Dejar que ChromaDB los calcule es atajo pedagógico cómodo. Para el módulo: calcula tú en los ejercicios principales, usa el atajo solo cuando estés prototipando rapido.

¿Hay diferencia entre HNSW de ChromaDB y de otras DBs?

Conceptualmente no, pero los parámetros expuestos varían. ChromaDB usa hnswlib por debajo y te permite configurar parámetros como _hnsw:M_ (conectividad del grafo), _hnsw:construction\_ef_ (calidad del índice durante construcción), _hnsw:search\_ef_ (calidad en búsqueda). Para corpus de hasta cientos de miles, los defaults suelen estar bien. Para volúmenes mayores conviene tunearlos: aumentar M (16-64) mejora calidad a costa de RAM.

¿Y si quiero versionar el índice? ¿Cómo gestiono cambios?

ChromaDB no tiene versionado nativo. Patrones habituales: nombrar colecciones con timestamp («docs\_2026\_05»), tener colecciones paralelas (vieja + nueva) durante migraciones, copiar la carpeta como snapshot. Para versionado serio en producción, conviene gestionar fuera (Git para metadata, snapshots de carpeta para backup). Hay herramientas más avanzadas (LakeFS, DVC) pero quedan fuera del módulo.

Recursos para profundizar 

#### ChromaDB en detalle

* **ChromaDB Documentation**. La referencia oficial. Lee especialmente la sección de Embeddings y Querying. docs.trychroma.com
* **ChromaDB · GitHub**. Examples directory con casos prácticos. github.com/chroma-core/chroma
* **Chroma Cookbook · ejemplos comunidad**. cookbook.chromadb.dev
* **hnswlib · GitHub**. La librería HNSW que usa ChromaDB por debajo. github.com/nmslib/hnswlib

Fin lección 2.2 · Sigue lección 2.3

LECCIÓN 2.3· \~4 horas · Sub-módulo 2

## Qdrant self-hosted + Pinecone cloud · _nivel producción_

Levantar Qdrant en docker-compose junto a tu n8n del Módulo 3\. Pinecone serverless free tier con su API. Comparativa práctica de las tres bases con el mismo corpus. Migración entre ellas. Hybrid search nativo en Qdrant.

Lectura · 65 min Ejemplos · 45 min Ejercicio · 130 min 

2.3.1Qdrant y Pinecone en práctica

#### Al final de esta lección sabrás:

* Levantar Qdrant self-hosted con docker-compose y operarlo desde Python.
* Crear una cuenta Pinecone Serverless free y trabajar con su API en la versión actual.
* Comparar las tres bases (ChromaDB, Qdrant, Pinecone) sobre el mismo corpus y queries.
* Migrar embeddings y metadatos entre bases sin perder información.
* Aprovechar características avanzadas de Qdrant: filtros complejos, payload indexing, sparse vectors.

Qdrant self-hosted con Docker

Qdrant se levanta con un único contenedor Docker. Si tienes tu stack del Módulo 3 con docker-compose corriendo, añadirle Qdrant es trivial. Es la base vectorial más cercana en filosofía a lo que se ve en producción seria.

Ejemplo · docker-compose.yml con Qdrant 

#### Levantar Qdrant como servicio

\# docker-compose.yml services: qdrant: image: qdrant/qdrant:latest container\_name: qdrant restart: unless-stopped ports: - "6333:6333" # API REST - "6334:6334" # gRPC volumes: - ./qdrant\_storage:/qdrant/storage environment: - QDRANT\_\_SERVICE\_\_API\_KEY=${QDRANT\_API\_KEY:-} # opcional pero recomendado # Levantar: # docker compose up -d qdrant # Verificar que está activo: # curl http://localhost:6333/ → {"title":"qdrant - vector search engine", ...} # Dashboard web (muy útil para inspeccionar tu base): # http://localhost:6333/dashboard

Notas. El puerto 6333 es REST, el 6334 gRPC (más rápido para volúmenes altos). El volumen `./qdrant_storage` persiste todos los datos: cópialo y tienes backup. La API key es opcional en local pero **obligatoria en producción**: sin ella, cualquiera con acceso a la red puede leer y escribir tu base. El dashboard web en /dashboard es excelente para inspeccionar tus colecciones, hacer queries de prueba y debug.

Ejemplo · cliente Python con Qdrant 

#### Crear colección, insertar, buscar

pip install qdrant-client from qdrant\_client import QdrantClient from qdrant\_client.models import ( VectorParams, Distance, PointStruct, Filter, FieldCondition, MatchValue, Range ) from sentence\_transformers import SentenceTransformer model = SentenceTransformer('paraphrase-multilingual-MiniLM-L12-v2') # Cliente apuntando al Qdrant local client = QdrantClient(host="localhost", port=6333) # Si necesitas auth: QdrantClient(host=..., port=..., api\_key="...") COLLECTION = "noticias" DIM = 384 # dimensiones del modelo # Crear la colección si no existe if not client.collection\_exists(COLLECTION): client.create\_collection( collection\_name=COLLECTION, vectors\_config=VectorParams(size=DIM, distance=Distance.COSINE), ) # Documentos a insertar documentos = \[ {"id": 1, "texto": "El Real Madrid ha fichado a un nuevo entrenador.", "categoria": "deporte", "fecha": "2026-05-10"}, {"id": 2, "texto": "La Comisión Europea aprueba financiación para startups.", "categoria": "economia", "fecha": "2026-05-11"}, {"id": 3, "texto": "Investigadores publican avance en computación cuántica.", "categoria": "ciencia", "fecha": "2026-05-12"}, \] # Generar embeddings textos = \[d\["texto"\] for d in documentos\] embeddings = model.encode(textos, normalize\_embeddings=True) # Insertar puntos (vector + payload con todo lo que quieras guardar) points = \[ PointStruct( id=d\["id"\], vector=emb.tolist(), payload={"texto": d\["texto"\], "categoria": d\["categoria"\], "fecha": d\["fecha"\]}, ) for d, emb in zip(documentos, embeddings) \] client.upsert(collection\_name=COLLECTION, points=points) # Búsqueda simple query = "novedades en investigación científica" q\_emb = model.encode(\[query\], normalize\_embeddings=True)\[0\].tolist() results = client.search( collection\_name=COLLECTION, query\_vector=q\_emb, limit=3, ) for r in results: print(f"\[{r.score:.3f}\] {r.payload\['categoria'\]} · {r.payload\['texto'\]}") # Búsqueda con filtros complejos results\_filtered = client.search( collection\_name=COLLECTION, query\_vector=q\_emb, limit=3, query\_filter=Filter( must=\[ FieldCondition(key="categoria", match=MatchValue(value="ciencia")), FieldCondition(key="fecha", range=Range(gte="2026-05-01")), \] ), )

Diferencias con ChromaDB. En Qdrant, el «point» contiene id + vector + payload (los metadatos). No hay distinción entre «documents» y «metadatas»: todo va en payload. Los filtros se construyen con objetos tipados (Filter, FieldCondition) en vez de dicts; un poco más verboso pero más seguro tipo-fuerte. Soporta filtros con must/should/must\_not (equivalentes lógicos AND/OR/NOT) y muchos operadores: match, range, geo, full-text. La API es más rica para casos complejos.

Payload indexing en Qdrant 

#### El truco para filtros eficientes a escala

Cuando filtras por un campo del payload (categoría, fecha, etc.) sobre una colección grande, Qdrant escanea todos los puntos del HNSW que matchean. Esto puede ser lento. La solución es indexar el campo:

`client.create_payload_index(collection_name=COLLECTION, field_name="categoria", field_schema="keyword")`

Tipos de schema: _keyword_ (string discreto), _integer_, _float_, _geo_, _text_ (full-text con tokenización). Indexar el campo lo hace mucho más rápido para filtros. **Indexa siempre los campos por los que vas a filtrar frecuentemente**; no indexes campos que solo lees pero no filtras (cuesta espacio sin beneficio).

Pinecone Serverless · cloud sin gestionar nada

Pinecone es la opción cloud-first. Te registras en pinecone.io, creas una cuenta gratuita y obtienes API key. Free tier (Serverless): hasta 2 GB de almacenamiento, 5 índices serverless. Suficiente para corpus de varios millones de vectores pequeños o cientos de miles de vectores de OpenAI text-embedding-3-large.

Ejemplo · Pinecone serverless desde Python 

#### API actual (versión >= 5)

pip install pinecone-client from pinecone import Pinecone, ServerlessSpec import os from dotenv import load\_dotenv load\_dotenv() pc = Pinecone(api\_key=os.getenv("PINECONE\_API\_KEY")) INDEX\_NAME = "noticias-mod4" DIM = 384 # Crear índice serverless si no existe existing = \[idx.name for idx in pc.list\_indexes()\] if INDEX\_NAME not in existing: pc.create\_index( name=INDEX\_NAME, dimension=DIM, metric="cosine", spec=ServerlessSpec(cloud="aws", region="us-east-1"), ) # Conectar al índice index = pc.Index(INDEX\_NAME) # Insertar vectores (formato dict) from sentence\_transformers import SentenceTransformer model = SentenceTransformer('paraphrase-multilingual-MiniLM-L12-v2') documentos = \[ {"id": "doc\_1", "texto": "El Real Madrid ha fichado...", "categoria": "deporte"}, {"id": "doc\_2", "texto": "La Comisión Europea aprueba...", "categoria": "economia"}, {"id": "doc\_3", "texto": "Avance en computación cuántica...", "categoria": "ciencia"}, \] vectors\_to\_upsert = \[\] for d in documentos: emb = model.encode(d\["texto"\], normalize\_embeddings=True).tolist() vectors\_to\_upsert.append({ "id": d\["id"\], "values": emb, "metadata": {"texto": d\["texto"\], "categoria": d\["categoria"\]}, }) index.upsert(vectors=vectors\_to\_upsert) # Query query = "novedades científicas" q\_emb = model.encode(query, normalize\_embeddings=True).tolist() results = index.query( vector=q\_emb, top\_k=3, include\_metadata=True, filter={"categoria": {"$in": \["ciencia", "tecnologia"\]}}, ) for match in results.matches: print(f"\[{match.score:.3f}\] {match.metadata\['categoria'\]} · {match.metadata\['texto'\]}")

Particularidades de Pinecone. Los IDs son strings (no integers). El metadata tiene tipos limitados (string, number, boolean, list-of-strings). No puedes guardar nested dicts. **Importante**: tras un upsert, Pinecone necesita unos segundos para que el dato sea consultable; en tests inmediatos esto te confunde si esperas consistencia inmediata. Para queries de prueba post-upsert, espera 2-3 segundos.

Pinecone tiene una característica única útil: **namespaces**. Dentro de un mismo índice, puedes particionar en namespaces lógicos: `index.upsert(vectors=[...], namespace="cliente_A")` y luego `index.query(vector=..., namespace="cliente_A")`. Perfecto para multi-tenant: cada cliente tiene su propio namespace en un solo índice, ahorras coste y aíslas datos.

Migración entre bases · cuando cambias de tecnología

A veces necesitas migrar: empezaste con ChromaDB en prototipo, ahora vas a producción con Qdrant. La buena noticia: como todas almacenan vectores + payload + ID, migrar es directo si tienes los vectores. La mala: si solo guardaste textos y reembedeas, vuelves a generar todos los embeddings con coste asociado.

Ejemplo · migración ChromaDB → Qdrant 

#### Exportar e importar sin recalcular embeddings

\# 1\. Exportar desde ChromaDB import chromadb chroma\_client = chromadb.PersistentClient(path="./chroma\_db") collection = chroma\_client.get\_collection("noticias") # get(include=\["embeddings", "documents", "metadatas"\]) trae todo data = collection.get(include=\["embeddings", "documents", "metadatas"\]) ids = data\["ids"\] embeddings = data\["embeddings"\] documents = data\["documents"\] metadatas = data\["metadatas"\] # 2\. Importar a Qdrant from qdrant\_client import QdrantClient from qdrant\_client.models import VectorParams, Distance, PointStruct q\_client = QdrantClient(host="localhost", port=6333) COLLECTION = "noticias\_qdrant" if not q\_client.collection\_exists(COLLECTION): q\_client.create\_collection( collection\_name=COLLECTION, vectors\_config=VectorParams(size=len(embeddings\[0\]), distance=Distance.COSINE), ) # Construir puntos. IDs en Qdrant deben ser int o UUID string points = \[ PointStruct( id=i, # usamos índice numérico vector=emb, payload={"original\_id": orig\_id, "texto": doc, \*\*meta}, ) for i, (orig\_id, emb, doc, meta) in enumerate(zip(ids, embeddings, documents, metadatas)) \] # Insertar en batches de 100 for i in range(0, len(points), 100): q\_client.upsert(collection\_name=COLLECTION, points=points\[i:i+100\]) print(f"Migrados {len(points)} documentos a Qdrant")

Patrón aplicable también a Pinecone (con la diferencia de que Pinecone IDs son strings y el formato es dict). Si necesitas hacer esto en producción con millones de vectores, conviene paralelizar la inserción (varios workers insertando en batches simultáneos) y monitorizar progreso.

Sparse vectors y hybrid search en Qdrant 

#### Preludio del SM3

Qdrant soporta nativamente vectores sparse (BM25 o similares) además de los dense (embeddings). Esto permite implementar hybrid search en una sola base sin necesidad de coordinar dos sistemas. En SM3 cuando entremos en hybrid search a fondo, usaremos esta capacidad.

Para crear una colección que admite ambos tipos: `vectors_config={"dense": VectorParams(size=384, distance=Distance.COSINE)}, sparse_vectors_config={"sparse": SparseVectorParams()}`. Por ahora basta saber que existe; lo usaremos a fondo en L3.2.

#### Ejercicio 2.3 · indexar el mismo corpus en las tres y comparar

Tiempo estimado · 2-2,5 horas 

Vas a montar el mismo corpus en ChromaDB, Qdrant y Pinecone. La meta: ver con tus propias manos las diferencias prácticas entre las tres opciones y consolidar criterio para tu proyecto final.

1. **Levanta Qdrant en docker-compose**. Si tienes el stack del M3, añade el servicio Qdrant. Verifica que `curl localhost:6333/` responde y que el dashboard funciona en `localhost:6333/dashboard`.
2. **Crea cuenta en Pinecone** (pinecone.io). Genera una API key. Crea un índice serverless con dimensión 384 (si usas sentence-transformers) o 1536 (si usas OpenAI). Métrica coseno.
3. **Recupera tu corpus indexado en ChromaDB** del ejercicio 2.2\. Es tu fuente de datos para este ejercicio.
4. **Migra el corpus a Qdrant** siguiendo el patrón de migración del ejemplo. Verifica que el conteo es correcto.
5. **Migra el corpus a Pinecone**. Inserta en batches de 100\. Espera 5 segundos antes de hacer queries (consistencia eventual).
6. **Implementa una función unificada de búsqueda**: `buscar(query, db, k=5)` donde _db_ es uno de {"chroma", "qdrant", "pinecone"}. Devuelve lista normalizada de resultados.
7. **Construye una tabla comparativa** con 10-15 queries representativas. Para cada query y cada DB, anota: tiempo de respuesta (ms), top-1 resultado, top-3 IDs. Observa coincidencias y divergencias.
8. **Medir tiempos de inserción**. Para cada DB, inserta los mismos 1.000 documentos midiendo el tiempo total. Compara.
9. **Medir uso de espacio**. Mide cuánto ocupa la carpeta de ChromaDB, la de Qdrant en docker. Pinecone te lo dice en su dashboard.
10. **Filtros con metadatos · prueba en las tres**:  
   * Filtrar por categoría única.  
   * Filtrar por categoría in \[A, B, C\].  
   * Filtrar por categoría = X AND fecha >= Y.  
 ¿Funcionan todos en las tres? ¿Hay sintaxis incompatibles?
11. **Bonus 1 · payload indexing en Qdrant**. Crea índices sobre los campos por los que filtras. Mide diferencia de tiempo en queries filtradas con y sin índice. Sobre 5.000 documentos el efecto se nota; sobre 50.000 es muy claro.
12. **Bonus 2 · Pinecone namespaces**. Divide tu corpus en 2 namespaces lógicos (por ejemplo, los pares y los impares por ID). Comprueba que queries en un namespace no devuelven nada del otro.
13. **Bonus 3 · concurrencia**. Lanza 100 queries en paralelo desde varios threads. ¿Qué DB aguanta mejor?

Toma notas detalladas durante este ejercicio. Cuando termines, escribe una página: «mi base vectorial para el proyecto final es X porque...». La decisión que tomes aquí va a guiar el resto del módulo. No hay opción «mejor en abstracto»; hay «mejor para tu caso», y este ejercicio te da los datos para razonarlo. Si dudas, recuerda mi recomendación pedagógica: Qdrant self-hosted en docker-compose es la opción más cercana a producción profesional.

Preguntas frecuentes 

¿Cuánto tarda Pinecone en estar realmente disponible tras un upsert?

Pinecone es eventually consistent. En la práctica, los datos están consultables en 1-10 segundos tras el upsert. Si haces query inmediatamente después de upsert y no ves los datos, espera y reintenta. En producción, esto importa si tu sistema necesita consistencia fuerte (no es lo común en RAG; con segundos de delay normalmente está bien).

¿Cuál es la mejor opción para empezar a aprender?

ChromaDB. Cero infraestructura, te concentras en los conceptos. Una vez dominas ChromaDB, pasarte a Qdrant es cuestión de horas porque la lógica es la misma. Pinecone también es fácil pero tiene la fricción de la cuenta cloud y los segundos de consistencia eventual que confunden cuando aprendes.

¿Y si quiero usar Qdrant cloud en lugar de self-hosted?

Qdrant Cloud tiene un free tier de 1 GB siempre gratis (1 cluster con 1 nodo). Es excelente para prototipos en cloud sin gestionar infra. La diferencia con Pinecone: Qdrant cloud te da más control, mejores filtros, hybrid search. Pinecone es más simple. Ambos son válidos; Qdrant me parece técnicamente superior para casos avanzados.

¿Cómo gestiono las claves API de Pinecone en proyectos compartidos?

Igual que cualquier secret. Variables de entorno via .env (con .env en .gitignore), o gestor de secretos (Doppler, Infisical, AWS Secrets Manager). Nunca commits en el repo. Pinecone permite crear múltiples API keys con scope diferenciado por proyecto, lo cual es útil para revocar una sin tocar las demás.

Recursos para profundizar 

#### Qdrant y Pinecone

* **Qdrant Documentation**. Excelente. Lee especialmente la sección Concepts (vectors, points, payload, filters) y la de Optimization para tuning. qdrant.tech/documentation
* **Qdrant · GitHub examples**. Casos prácticos y benchmarks. github.com/qdrant/qdrant
* **Pinecone Documentation**. Lee Serverless quickstart si vas con esa opción. docs.pinecone.io
* **Pinecone · Learning Center**. Tutoriales y casos. pinecone.io/learn
* **ANN-Benchmarks · GitHub**. Comparativas técnicas y reproducibles de bases vectoriales y algoritmos. github.com/erikbern/ann-benchmarks

Fin del sub-módulo 2 · Sigue sub-módulo 3 · RAG de naive a avanzado

SUB-MÓDULO 3· 10 horas · 4 lecciones

## RAG · _de naive a avanzado_

Del primer pipeline RAG end-to-end con LangChain y LlamaIndex hasta técnicas del estado del arte. Hybrid search combinando BM25 con embeddings densos, reranking con cross-encoders para mejorar precisión final y Corrective RAG con fallback a búsqueda web cuando el retrieval interno falla.

10 horas totales 4 lecciones 4 ejercicios prácticos Python · LangChain · Cohere · Tavily 

LECCIÓN 3.1· \~3 horas · Sub-módulo 3

## Naive RAG · _primer pipeline end-to-end_

Construir un pipeline RAG completo desde cero. Carga de PDFs, chunking con estrategias (fixed-size, recursive, semantic), embedding, almacenamiento en vector DB, retrieval, augmentation y generation. Implementación con LangChain y LlamaIndex sobre tu propio corpus.

Lectura · 60 min Ejemplos · 40 min Ejercicio · 80 min 

3.1.1El pipeline RAG y sus piezas

#### Al final de esta lección sabrás:

* Explicar las cinco etapas del pipeline RAG canónico y qué hace cada una.
* Cargar documentos en distintos formatos (PDF, txt, HTML, Markdown) con loaders maduros.
* Aplicar estrategias de chunking apropiadas según tipo de documento y caso de uso.
* Construir un pipeline RAG completo con LangChain LCEL o LlamaIndex sobre tu propio corpus.
* Diagnosticar los tres puntos de fallo más comunes: chunks malos, retrieval irrelevante, hallucinations del LLM.

El pipeline canónico · cinco etapas

Cualquier sistema RAG, por simple o sofisticado que sea, sigue conceptualmente las mismas cinco etapas. Conviene tenerlas claras antes de tocar código, porque cada técnica avanzada que veremos (hybrid search, reranking, CRAG, Agentic RAG) interviene en una etapa concreta:

1. **Ingesta y carga**. Leer los documentos fuente desde su formato original (PDF, DOCX, HTML, Markdown, bases de datos). Extraer el texto manteniendo estructura útil (títulos, secciones).
2. **Chunking**. Dividir los documentos en fragmentos del tamaño adecuado para embedear. Cada chunk debe ser autocontenido conceptualmente.
3. **Embedding e indexación**. Calcular el embedding de cada chunk y almacenarlo en una base vectorial con sus metadatos (documento de origen, página, sección).
4. **Retrieval**. Dada una query del usuario, embedearla y recuperar los top-K chunks más similares.
5. **Augmentation y generation**. Construir un prompt al LLM que incluye la query original más los chunks recuperados como contexto. El LLM genera una respuesta apoyada en ese contexto.

La versión **naive RAG** implementa cada etapa de la forma más directa posible. Es lo que vas a construir en esta lección. Funciona razonablemente bien para muchos casos sencillos. Las siguientes lecciones del SM3 y todo el SM4 son refinamientos de este esquema: añadir BM25 al retrieval (L3.2), reordenar resultados (L3.3), evaluar la calidad del retrieval (L3.4), hacer el sistema agéntico (SM4).

Etapa 1 · ingesta y carga de documentos

La calidad final de un RAG depende muchísimo de cómo extraes el texto de los formatos originales. Un PDF mal parseado (con texto desordenado, tablas convertidas a líneas inconexas, encabezados duplicados) condena al sistema desde el principio.

Ejemplo · cargar PDFs con varios loaders 

#### Tres opciones según calidad y dependencias

pip install pypdf pdfplumber unstructured langchain-community # Opción 1 · pypdf · simple, ligero, suficiente para PDFs limpios from langchain\_community.document\_loaders import PyPDFLoader loader = PyPDFLoader("manual.pdf") docs = loader.load() # lista de Document, uno por página print(docs\[0\].page\_content\[:200\]) print(docs\[0\].metadata) # {'source': 'manual.pdf', 'page': 0} # Opción 2 · pdfplumber · mejor en tablas y formato from langchain\_community.document\_loaders import PDFPlumberLoader loader = PDFPlumberLoader("manual.pdf") docs = loader.load() # Opción 3 · unstructured · el más robusto, detecta secciones, tablas, listas from langchain\_community.document\_loaders import UnstructuredPDFLoader loader = UnstructuredPDFLoader("manual.pdf", mode="elements") docs = loader.load() # Cada element es un párrafo, título, tabla, etc. con su tipo en metadata

Recomendación práctica. Para PDFs sencillos (texto plano sin tablas complejas), `pypdf` es suficiente. Para PDFs con tablas, formularios o estructura compleja, `unstructured` es la opción más robusta aunque requiere dependencias pesadas (Tesseract para OCR, pandoc para algunos formatos). **Para PDFs escaneados que solo tienen imágenes**, necesitas OCR: `unstructured` con `strategy="ocr_only"` usa Tesseract internamente. Hay alternativas modernas como `Marker` o `Docling` de IBM que dan mejor calidad pero son más pesadas.

LangChain Community tiene loaders para casi cualquier formato: `TextLoader`, `CSVLoader`, `UnstructuredMarkdownLoader`, `WebBaseLoader` (URLs), `NotionDirectoryLoader`, `ConfluenceLoader`, etc. Antes de implementar tu propio parser, busca si existe uno en LangChain o LlamaIndex.

Etapa 2 · chunking · la decisión más importante

El chunking es donde más se gana o se pierde calidad en RAG. Un mal chunking destruye la coherencia semántica: si partes una explicación por la mitad, ningún chunk contiene la respuesta completa. Un chunking demasiado grande mete ruido: el embedding diluye la información relevante en mucho contexto irrelevante.

Las estrategias principales, de más simple a más sofisticada:

* **Fixed-size chunking**. Divide en chunks de N caracteres o N tokens con overlap. Simple, predecible, rápido. No respeta estructura del texto.
* **Recursive character splitting**. Intenta dividir primero por párrafos (`\n\n`), si los párrafos son muy largos por líneas (`\n`), luego por frases, luego por palabras. Respeta más la estructura. Es el default razonable.
* **Document-specific**. Para markdown, divide por headers (## ###). Para código, por funciones o clases. Para HTML, por etiquetas semánticas. LangChain tiene splitters específicos.
* **Semantic chunking**. Divide en función de cambios semánticos detectados por embeddings. Más caro de computar pero suele dar mejor resultado.

Ejemplo · recursive splitting 

#### La estrategia que cubre el 80% de casos

from langchain\_text\_splitters import RecursiveCharacterTextSplitter splitter = RecursiveCharacterTextSplitter( chunk\_size=500, # caracteres por chunk chunk\_overlap=80, # solapamiento entre chunks separators=\["\\n\\n", "\\n", ". ", " ", ""\], # orden de preferencia length\_function=len, ) chunks = splitter.split\_documents(docs) print(f"Documentos: {len(docs)}, chunks resultantes: {len(chunks)}") print(chunks\[0\].page\_content) print(chunks\[0\].metadata) # mantiene source, page, etc.

Parámetros clave. El **chunk\_size** óptimo depende del modelo de embeddings y del caso: para documentación técnica densa, 300-500 caracteres suele ir bien. Para texto narrativo, 800-1.500\. El **overlap** (10-20% del chunk\_size) reduce el problema de información cortada en frontera de chunks. Los **separators** definen el orden de corte; con los defaults, LangChain intenta primero dividir por párrafos y solo baja a niveles más finos si los párrafos exceden el chunk\_size.

Ejemplo · semantic chunking 

#### Cuando el contenido es muy heterogéneo

from langchain\_experimental.text\_splitter import SemanticChunker from langchain\_openai import OpenAIEmbeddings # Usa embeddings para detectar puntos donde el tema cambia text\_splitter = SemanticChunker( OpenAIEmbeddings(model="text-embedding-3-small"), breakpoint\_threshold\_type="percentile", # o "standard\_deviation", "interquartile" breakpoint\_threshold\_amount=95, ) chunks = text\_splitter.create\_documents(\[texto\_largo\])

Coste: \~1.5x más embeddings que recursive (uno por frase del documento original para detectar cortes). Beneficio: chunks naturalmente cohesivos. Vale la pena para corpus de calidad alta donde el coste de embeddings es despreciable comparado con la mejora de retrieval.

El problema del contexto perdido 

#### Por qué los chunks aislados a veces fallan

Un chunk típico es un párrafo de 500 caracteres. Pero un párrafo de la página 50 de un manual a menudo se refiere a algo definido en la página 5 («como se vio en el capítulo anterior, este parámetro...»). Aislado, el chunk pierde contexto.

Soluciones que la comunidad ha desarrollado:

* **Parent-child retrieval**. Embedeas chunks pequeños (para precisión) pero recuperas chunks padre más grandes (para contexto). LangChain tiene `ParentDocumentRetriever`.
* **Contextual retrieval** (técnica popularizada por Anthropic en 2024). A cada chunk se le añade un breve resumen de contexto del documento generado por un LLM barato (Haiku o Flash). El embedding captura tanto el chunk como su contexto.
* **Late chunking** (de Jina). Embedeas el documento entero primero (con modelos de contexto largo) y luego haces pooling sobre rangos de tokens.

En esta lección usaremos recursive splitting simple. En el proyecto final del SM4 podrás experimentar con estas técnicas avanzadas si tu caso lo pide.

Etapas 3-5 · indexación, retrieval, generation con LangChain

Una vez tienes los chunks, las etapas restantes son las que ya conoces de SM1 y SM2: embedear los chunks, almacenarlos en una vector DB, recuperar los más similares a la query y generar respuesta con un LLM. LangChain las orquesta con su sintaxis LCEL (LangChain Expression Language).

Ejemplo · pipeline RAG completo end-to-end 

#### Cargar PDF · chunkear · indexar · responder

pip install langchain langchain-openai langchain-chroma pypdf from langchain\_community.document\_loaders import PyPDFLoader from langchain\_text\_splitters import RecursiveCharacterTextSplitter from langchain\_openai import OpenAIEmbeddings, ChatOpenAI from langchain\_chroma import Chroma from langchain\_core.prompts import ChatPromptTemplate from langchain\_core.runnables import RunnablePassthrough from langchain\_core.output\_parsers import StrOutputParser # 1\. Cargar loader = PyPDFLoader("manual.pdf") docs = loader.load() # 2\. Chunkear splitter = RecursiveCharacterTextSplitter(chunk\_size=500, chunk\_overlap=80) chunks = splitter.split\_documents(docs) # 3\. Indexar embeddings = OpenAIEmbeddings(model="text-embedding-3-small") vectorstore = Chroma.from\_documents( documents=chunks, embedding=embeddings, persist\_directory="./chroma\_rag", ) retriever = vectorstore.as\_retriever(search\_kwargs={"k": 4}) # 4 y 5\. Cadena RAG con LCEL prompt = ChatPromptTemplate.from\_template("""Eres un asistente experto. Responde la pregunta del usuario basándote ÚNICAMENTE en el contexto proporcionado. Si la respuesta no está en el contexto, di que no tienes esa información. Contexto: {context} Pregunta: {question} Respuesta:""") llm = ChatOpenAI(model="gpt-4o-mini", temperature=0) def format\_docs(docs): return "\\n\\n".join(d.page\_content for d in docs) rag\_chain = ( {"context": retriever | format\_docs, "question": RunnablePassthrough()} | prompt | llm | StrOutputParser() ) # Usar print(rag\_chain.invoke("¿Cuáles son los requisitos del sistema?"))

Esto es un pipeline RAG funcional completo en 30 líneas. Funciona. No es ideal: el chunking es básico, el retrieval es solo dense (sin BM25), no hay reranking, no hay manejo de errores. Pero responde queries sobre un PDF con un LLM. Las siguientes lecciones añaden capas de calidad sobre este esqueleto.

Ejemplo · la misma pipeline con LlamaIndex 

#### Alternativa más concisa orientada a RAG

pip install llama-index llama-index-embeddings-openai llama-index-llms-openai llama-index-vector-stores-chroma from llama\_index.core import VectorStoreIndex, SimpleDirectoryReader, Settings, StorageContext from llama\_index.embeddings.openai import OpenAIEmbedding from llama\_index.llms.openai import OpenAI from llama\_index.vector\_stores.chroma import ChromaVectorStore import chromadb # Configuración global Settings.embed\_model = OpenAIEmbedding(model="text-embedding-3-small") Settings.llm = OpenAI(model="gpt-4o-mini", temperature=0) Settings.chunk\_size = 500 Settings.chunk\_overlap = 80 # 1\. Cargar (lee todo el directorio) documents = SimpleDirectoryReader("./docs").load\_data() # 2\. Crear índice (chunkea, embedea, indexa) chroma\_client = chromadb.PersistentClient(path="./chroma\_llamaindex") chroma\_collection = chroma\_client.get\_or\_create\_collection("rag\_docs") vector\_store = ChromaVectorStore(chroma\_collection=chroma\_collection) storage\_context = StorageContext.from\_defaults(vector\_store=vector\_store) index = VectorStoreIndex.from\_documents(documents, storage\_context=storage\_context) # 3\. Query query\_engine = index.as\_query\_engine(similarity\_top\_k=4) response = query\_engine.query("¿Cuáles son los requisitos del sistema?") print(response) print(response.source\_nodes) # los chunks usados, útil para debug

LlamaIndex tiene sintaxis más concisa para RAG porque está más enfocada al caso (LangChain es más general). En la práctica profesional, ambas se usan. LangChain tiene más integraciones generales (chains, agentes, herramientas); LlamaIndex tiene mejor experiencia específicamente para RAG (parsers, reranking integrado, evaluación). Conoce las dos.

Los tres puntos de fallo del naive RAG

Cuando tu naive RAG no funciona bien, el problema suele estar en uno de tres lugares. Saber identificar dónde está el fallo es la habilidad clave para mejorar el sistema:

* **Chunks malos**. Verifica los chunks generados directamente. ¿Son coherentes? ¿Información relevante quedó partida entre dos chunks? ¿Hay chunks de basura (encabezados repetidos, numeración, footers)? Síntoma: el LLM responde mal porque el chunk recuperado está incompleto o roto.
* **Retrieval irrelevante**. Mira qué chunks devuelve el retriever para una query mal respondida. Si los chunks no contienen la respuesta, el problema es de retrieval (modelo de embeddings débil, falta hybrid search, query muy ambigua). Síntoma: el LLM responde «no tengo esa información» o inventa porque el contexto no incluye la respuesta.
* **Generation con hallucinations**. Los chunks correctos están ahí pero el LLM ignora el contexto o lo malinterpreta. Síntoma: el LLM dice algo que contradice lo que dice el contexto recuperado, o añade información inventada.

El método de diagnóstico es siempre el mismo: **imprime los chunks recuperados** antes de pasar al LLM y léelos tú mismo. Si la respuesta está en los chunks y el LLM responde mal, problema de generation (mejorar prompt, modelo más potente). Si la respuesta no está en los chunks, problema de retrieval (mejorar chunking, embeddings, añadir hybrid search). Si los chunks están rotos, problema de ingesta o chunking.

#### Ejercicio 3.1 · primer pipeline RAG sobre PDFs propios

Tiempo estimado · 75-90 minutos 

Vas a construir tu primer pipeline RAG funcional sobre PDFs reales. Elige el dominio que te interese: documentación técnica de un proyecto open-source, leyes en BOE, manuales de un producto, artículos académicos. La calidad final del proyecto del SM4 dependerá en parte de la calidad del corpus que elijas aquí.

1. **Elige y reúne 5-10 PDFs** sobre un tema cohesivo. Sugerencias: manuales de Python o de algún framework, documentación de Qdrant o ChromaDB exportada, leyes españolas en PDF del BOE, capítulos abiertos de libros técnicos. Total: entre 100 y 500 páginas.
2. **Setup del entorno**: `pip install langchain langchain-openai langchain-chroma langchain-community pypdf python-dotenv`. Configura tu OpenAI API key en `.env`.
3. **Implementa la ingesta**. Carga los PDFs con PyPDFLoader. Imprime los primeros 500 caracteres de varias páginas para verificar que el texto se extrae correctamente. **Si ves texto desordenado o caracteres raros**, prueba con PDFPlumberLoader o UnstructuredPDFLoader.
4. **Aplica chunking**. RecursiveCharacterTextSplitter con chunk\_size=500 y overlap=80 como punto de partida. Imprime 3-4 chunks aleatorios y léelos. ¿Son autocontenidos? ¿Tiene sentido leerlos aislados? Si no, ajusta chunk\_size o usa otro splitter.
5. **Indexa en ChromaDB** con embeddings de OpenAI text-embedding-3-small. Para 500 páginas con chunking de 500 chars, esperaríamos del orden de 5.000-10.000 chunks. Coste estimado de embeddings: menos de 0,10 USD.
6. **Construye la cadena RAG** con LCEL siguiendo el patrón del ejemplo. Usa gpt-4o-mini como LLM (barato y suficiente).
7. **Prueba con 8-10 queries reales** sobre tu corpus:  
   * Queries factuales con respuesta clara en los documentos.  
   * Queries que requieren combinar información de varios sitios.  
   * Queries con jerga del dominio.  
   * Queries cuya respuesta NO está en el corpus (¿el sistema lo reconoce o inventa?).  
   * Queries con typos o formulación inusual.
8. **Para cada query mal respondida, diagnostica**. Imprime los chunks recuperados. ¿Está la respuesta ahí? Aplica el método de los tres puntos de fallo descrito en la lección.
9. **Bonus 1 · variantes de chunking**. Repite el experimento con chunk\_size=300 y chunk\_size=1.000\. ¿Mejoran o empeoran los resultados? Toma notas: encontrar el chunk\_size óptimo para tu corpus es un ejercicio de calibración real.
10. **Bonus 2 · prueba con LlamaIndex**. Implementa el mismo pipeline con LlamaIndex sobre el mismo corpus. Compara la experiencia de desarrollo y los resultados.
11. **Bonus 3 · prompt engineering**. Mejora el prompt del LLM para que cite las fuentes (página, sección) en su respuesta. Esto se hace metiendo los metadatos en el contexto formateado e instruyendo al LLM a referenciarlos.

Guarda este pipeline limpio en un módulo Python reutilizable. En las siguientes lecciones (hybrid, reranking, CRAG) iremos sustituyendo piezas concretas (el retriever, el generador) sin reescribir todo. Una arquitectura limpia desde el principio te ahorra horas. Para queries que respondan mal, no te frustres: es lo normal del naive RAG. Las siguientes lecciones existen precisamente para resolver esos casos.

Preguntas frecuentes 

¿LangChain o LlamaIndex? ¿Cuál aprender más a fondo?

Ambos. Tienen filosofías distintas. LangChain es más general (chains, agentes, tools, RAG) y se usa también para casos no-RAG. LlamaIndex está más especializado en RAG con primitivas más maduras (parsers, reranking, sub-question query engines). Para tu primer proyecto, elige el que te resulte más cómodo; ambos hacen lo que necesitas. En entornos profesionales, vas a encontrar los dos según el equipo.

¿Hace falta usar un framework? ¿Puedo hacer RAG sin LangChain?

Absolutamente. RAG es conceptualmente simple: el SM1 y SM2 te dan todas las piezas. Puedes implementarlo con cliente Python directo de OpenAI/Anthropic + cliente Qdrant/ChromaDB en menos de 100 líneas. Los frameworks aportan integraciones listas y abstracciones útiles cuando el sistema crece, pero también añaden dependencias y complejidad. Conoce los frameworks **pero no los uses por reflejo**: para casos simples, código directo es más mantenible.

¿Cuál es el chunk\_size óptimo en general?

No existe «el óptimo» universal. Depende del modelo de embeddings (los modelos modernos como text-embedding-3 manejan hasta 8.192 tokens; los antiguos como ada-002 también), del tipo de contenido (técnico denso vs narrativo) y del LLM final (que tiene su propio contexto). Como punto de partida razonable: 500-800 caracteres para documentación técnica, 1.000-1.500 para texto general. Calibra con tu corpus probando varias opciones y midiendo calidad de respuestas.

¿Por qué le digo al LLM «basándote ÚNICAMENTE en el contexto»?

Para reducir hallucinations. Sin esa instrucción, el LLM tiende a complementar con conocimiento general («se sabe que también...»), mezclando lo del corpus con lo aprendido en su entrenamiento. En RAG empresarial generalmente quieres separar claramente «lo que dicen tus documentos» de «lo que sabe el LLM». La instrucción de groundedness es esencial. Modelos modernos (Claude, GPT-4 reciente) la respetan bastante bien; modelos más débiles pueden ignorarla.

Recursos para profundizar 

#### RAG · pipelines y frameworks

* **LangChain Documentation · RAG**. Tutorial oficial actualizado. Lee especialmente Build a Retrieval Augmented Generation (RAG) App. python.langchain.com/docs/tutorials/rag
* **LlamaIndex Documentation**. La sección High-Level Concepts y Building a RAG Pipeline. docs.llamaindex.ai
* **Anthropic · Contextual Retrieval**. Técnica para mejorar chunks con contexto añadido. Recomendable. anthropic.com/news/contextual-retrieval
* **Unstructured · GitHub**. La librería más robusta para parseo de documentos heterogéneos. github.com/Unstructured-IO/unstructured
* **Awesome RAG**. Lista curada de papers, frameworks y tutoriales sobre RAG. github.com/run-llama/awesome-llamaindex

Fin lección 3.1 · Sigue lección 3.2

LECCIÓN 3.2· \~3 horas · Sub-módulo 3

## Hybrid search · _BM25 + dense embeddings_

Combinar búsqueda léxica (BM25) con búsqueda semántica (embeddings densos) para capturar tanto coincidencias exactas como significado. Reciprocal Rank Fusion para fusionar resultados. Implementación con Qdrant nativo y con LangChain EnsembleRetriever.

Lectura · 55 min Ejemplos · 45 min Ejercicio · 80 min 

3.2.1Sparse + dense · lo mejor de los dos mundos

#### Al final de esta lección sabrás:

* Explicar por qué hybrid search supera consistentemente a búsqueda solo semántica o solo BM25.
* Implementar BM25 con la librería `rank_bm25` y combinarlo con embeddings densos.
* Aplicar Reciprocal Rank Fusion (RRF) para fusionar resultados de dos retrievers.
* Construir hybrid search nativo en Qdrant aprovechando vectores sparse y dense en una sola colección.
* Identificar qué tipos de query mejoran con hybrid y cuáles se quedan igual.

Por qué hybrid search funciona mejor

Lo viste en SM1: BM25 (sparse, léxico) y embeddings densos capturan cosas distintas. BM25 captura coincidencias exactas de términos, especialmente útil para nombres propios, acrónimos, números de modelo, IDs, jerga técnica. Embeddings densos capturan significado, paráfrasis, sinónimos, conceptos relacionados.

La realidad de las queries de usuarios es que **algunas son léxicas y otras son semánticas, y a menudo son mixtas**. «Configurar SSH en Ubuntu 24.04» tiene componente léxica fuerte («SSH», «Ubuntu 24.04») y componente semántica («configurar»). Un retriever solo-dense puede perder el documento exacto que menciona «Ubuntu 24.04» si sus términos están sumergidos en un párrafo largo. Un retriever solo-BM25 puede perder un documento que dice «activar acceso remoto» sin usar «SSH». Hybrid recupera ambos y los combina.

Las cifras de benchmarks como BEIR son consistentes: hybrid search supera al mejor de los dos individuales en casi todos los datasets. La mejora típica es del 5-15% en métricas de retrieval. Es la mejora más rentable que puedes hacer sobre un naive RAG.

BM25 · la fórmula que vence el test del tiempo 

#### Por qué sigue siendo el baseline a 50 años

BM25 (Best Match 25) es una mejora de TF-IDF publicada en los años 90 por Robertson y otros en el contexto de Okapi BM25\. Calcula un score de relevancia de un documento para una query basándose en frecuencia de términos, longitud del documento (normalización para evitar que documentos largos saquen ventaja) y rareza global de los términos en el corpus (IDF).

Tres puntos clave para entenderla: **premia coincidencias exactas** entre query y documento; **penaliza documentos demasiado largos** que matchean por casualidad; **premia términos raros** sobre términos comunes («que», «el», «de» pesan poco). Esto la hace excepcionalmente robusta en queries con términos específicos.

Hoy 2026, BM25 sigue siendo el baseline contra el que se miden todos los retrievers neuronales. En muchos datasets de dominio especializado, BM25 supera a embeddings modernos. Ningún sistema RAG en producción serio prescinde de BM25.

Implementación práctica · BM25 con rank\_bm25

La librería `rank_bm25` implementa BM25 en Python con interfaz mínima. Para corpus pequeños y medianos (hasta cientos de miles de documentos) es suficiente.

Ejemplo · BM25 standalone 

#### Para entender la mecánica

pip install rank\_bm25 nltk from rank\_bm25 import BM25Okapi import nltk from nltk.tokenize import word\_tokenize nltk.download('punkt\_tab') corpus = \[ "Configurar SSH en Ubuntu 24.04 requiere instalar openssh-server.", "El acceso remoto al servidor se puede activar con el protocolo SSH.", "Python es un lenguaje de programación de alto nivel.", "Docker permite ejecutar aplicaciones en contenedores aislados.", "Ubuntu es una distribución Linux popular para servidores.", \] # Tokenizar el corpus (BM25 trabaja a nivel de tokens) tokenized\_corpus = \[word\_tokenize(doc.lower()) for doc in corpus\] bm25 = BM25Okapi(tokenized\_corpus) # Query query = "cómo activar SSH" tokenized\_query = word\_tokenize(query.lower()) # Scores BM25 para cada documento scores = bm25.get\_scores(tokenized\_query) print(scores) # array con un score por documento # Top-3 top\_n = bm25.get\_top\_n(tokenized\_query, corpus, n=3) for doc in top\_n: print(doc) # Configurar SSH en Ubuntu 24.04... # El acceso remoto al servidor... # Ubuntu es una distribución Linux...

Notas. Para español y otros idiomas no-ingleses conviene tokenizar adecuadamente: `word_tokenize(doc, language='spanish')` o usar spaCy para lematización. La **lematización** (reducir «corriendo», «corrió», «corre» a «correr») mejora notablemente BM25 porque hace match léxico tolerante a flexiones. Para producción seria con español, considera usar spaCy + un lematizador.

Combinar BM25 con embeddings · Reciprocal Rank Fusion

Una vez tienes dos rankings (uno de BM25, otro de dense), necesitas combinarlos. Los scores no son directamente comparables (BM25 da valores absolutos sin techo; coseno va de -1 a 1). Las dos técnicas principales para combinar:

* **Suma ponderada de scores normalizados**. Normalizas cada ranking (min-max o softmax) y haces `final = α * dense + (1-α) * bm25`. Requiere calibrar α. Sensible a outliers de score.
* **Reciprocal Rank Fusion (RRF)**. Ignora los scores; usa solo el ranking. Para cada documento d que aparece en al menos uno de los rankings: `RRF(d) = Σ 1 / (k + rank_i(d))` donde k es una constante (típicamente 60) y rank\_i es la posición de d en el ranking i. Documentos que aparecen alto en ambos rankings reciben score alto.

RRF es la opción más popular porque no necesita calibrar pesos y es robusta a las diferencias de escala entre rankings. Es lo que usan Elasticsearch, Qdrant nativamente y la mayoría de papers académicos cuando combinan.

Ejemplo · RRF implementado a mano 

#### 30 líneas explican la mecánica

def reciprocal\_rank\_fusion(rankings, k=60): """ rankings: lista de listas. Cada lista es un ranking de doc\_ids del más relevante al menos relevante. Retorna: dict {doc\_id: score\_rrf}. """ scores = {} for ranking in rankings: for rank, doc\_id in enumerate(ranking, start=1): scores\[doc\_id\] = scores.get(doc\_id, 0) + 1.0 / (k + rank) return dict(sorted(scores.items(), key=lambda x: -x\[1\])) # Ejemplo de uso bm25\_ranking = \["doc\_2", "doc\_5", "doc\_1", "doc\_7"\] # top-4 por BM25 dense\_ranking = \["doc\_5", "doc\_3", "doc\_2", "doc\_8"\] # top-4 por dense fused = reciprocal\_rank\_fusion(\[bm25\_ranking, dense\_ranking\]) print(fused) # doc\_5 (aparece 2º y 1º) -> score alto # doc\_2 (aparece 1º y 3º) -> score alto # doc\_3 (solo en dense, 2º) -> score medio # etc.

El parámetro k (60 por defecto, recomendación de la literatura original) controla cuánto pesan las posiciones bajas. Con k más pequeño, los primeros puestos dominan; con k más grande, los rankings se aplanan. 60 funciona muy bien en la práctica.

Hybrid search en LangChain · EnsembleRetriever

LangChain tiene una abstracción lista para hybrid: `EnsembleRetriever` combina varios retrievers con pesos (suma ponderada por defecto, pero también acepta RRF).

Ejemplo · EnsembleRetriever en LangChain 

#### Hybrid sobre tu corpus indexado

pip install langchain langchain-community rank\_bm25 from langchain\_community.retrievers import BM25Retriever from langchain.retrievers import EnsembleRetriever from langchain\_chroma import Chroma from langchain\_openai import OpenAIEmbeddings # 1\. Retriever dense (lo que ya tenías en L3.1) embeddings = OpenAIEmbeddings(model="text-embedding-3-small") vectorstore = Chroma( persist\_directory="./chroma\_rag", embedding\_function=embeddings, ) dense\_retriever = vectorstore.as\_retriever(search\_kwargs={"k": 10}) # 2\. Retriever BM25 sobre los mismos documentos # BM25Retriever espera tener los documentos en memoria # Recupéralos del vectorstore o de tu corpus original all\_docs = vectorstore.get() # devuelve dict con documents, metadatas, ids documents\_for\_bm25 = \[ Document(page\_content=doc, metadata=meta) for doc, meta in zip(all\_docs\["documents"\], all\_docs\["metadatas"\]) \] bm25\_retriever = BM25Retriever.from\_documents(documents\_for\_bm25) bm25\_retriever.k = 10 # 3\. Ensemble · pesos 0.5 / 0.5 como punto de partida ensemble = EnsembleRetriever( retrievers=\[bm25\_retriever, dense\_retriever\], weights=\[0.5, 0.5\], # c=60 # parámetro RRF si usas search\_type="rrf" ) # Usar igual que cualquier retriever docs\_recuperados = ensemble.invoke("configurar acceso SSH en Ubuntu 24.04") for d in docs\_recuperados\[:5\]: print(d.page\_content\[:150\])

Para usar RRF de forma explícita: en versiones recientes de LangChain hay `EnsembleRetriever` con opciones para RRF, o puedes implementarlo manualmente combinando los dos rankings con tu propia función RRF. La diferencia práctica con pesos es marginal en muchos casos; experimenta con ambos.

Hybrid search nativo en Qdrant

Qdrant soporta hybrid search nativamente. Una sola colección puede tener vectores dense y sparse, y la query usa los dos a la vez con RRF aplicado por la base. Esta es la opción más limpia para producción.

Ejemplo · hybrid search nativo en Qdrant 

#### Sparse + dense en una colección

pip install qdrant-client\[fastembed\] fastembed from qdrant\_client import QdrantClient from qdrant\_client.models import ( VectorParams, SparseVectorParams, Distance, PointStruct, SparseVector, Fusion, FusionQuery, Prefetch, NamedVector, ) from fastembed import TextEmbedding, SparseTextEmbedding # Modelos: uno dense y uno sparse. FastEmbed los descarga automáticamente dense\_model = TextEmbedding(model\_name="BAAI/bge-small-en-v1.5") sparse\_model = SparseTextEmbedding(model\_name="prithivida/Splade\_PP\_en\_v1") client = QdrantClient(host="localhost", port=6333) COLLECTION = "hybrid\_docs" # Crear colección que admite ambos tipos de vector client.create\_collection( collection\_name=COLLECTION, vectors\_config={"dense": VectorParams(size=384, distance=Distance.COSINE)}, sparse\_vectors\_config={"sparse": SparseVectorParams()}, ) # Insertar (cada punto tiene un dense + un sparse) documentos = \["texto 1", "texto 2", "texto 3", ...\] dense\_embs = list(dense\_model.embed(documentos)) sparse\_embs = list(sparse\_model.embed(documentos)) points = \[\] for i, (doc, d\_emb, s\_emb) in enumerate(zip(documentos, dense\_embs, sparse\_embs)): points.append(PointStruct( id=i, vector={ "dense": d\_emb.tolist(), "sparse": SparseVector(indices=s\_emb.indices.tolist(), values=s\_emb.values.tolist()), }, payload={"texto": doc}, )) client.upsert(collection\_name=COLLECTION, points=points) # Query hybrid: usa los dos vectores y fusiona con RRF query\_text = "configurar acceso SSH en Ubuntu" q\_dense = list(dense\_model.embed(\[query\_text\]))\[0\] q\_sparse = list(sparse\_model.embed(\[query\_text\]))\[0\] results = client.query\_points( collection\_name=COLLECTION, prefetch=\[ Prefetch(query=q\_dense.tolist(), using="dense", limit=20), Prefetch(query=SparseVector( indices=q\_sparse.indices.tolist(), values=q\_sparse.values.tolist(), ), using="sparse", limit=20), \], query=FusionQuery(fusion=Fusion.RRF), limit=5, ) for r in results.points: print(f"\[{r.score:.3f}\] {r.payload\['texto'\]}")

El truco: el método `query_points` con `prefetch` trae los top-20 de cada vector tipo y los fusiona con RRF para devolverte el top-5 final. Todo en una sola llamada a la base. Para producción con hybrid search, Qdrant es probablemente la opción más limpia y eficiente.

Cuándo hybrid mejora y cuándo no 

#### El honest assessment

Hybrid no es magia. Mejora consistentemente pero no en todos los casos. Patrones:

* **Mejora claramente**: corpus con muchos términos específicos (técnico, legal, médico), queries con nombres propios o acrónimos, datasets en idiomas donde los embeddings tienen menor calidad, sistemas donde los usuarios buscan por código o identificadores.
* **Mejora poco**: corpus narrativo general (ficción, noticias largas) con queries semánticas, datasets pequeños donde la diferencia entre rankings es marginal.
* **Puede empeorar puntualmente**: queries muy semánticas (paráfrasis con cero palabras compartidas) donde BM25 mete ruido. Patrón típico: BM25 hace match con un documento que comparte una palabra común pero no es relevante.

Recomendación: implementa hybrid, mide con tus queries reales (no con benchmarks generales), ajusta pesos o desactiva BM25 si para tu caso degrada. La medición es la regla de oro.

#### Ejercicio 3.2 · añadir hybrid search a tu pipeline

Tiempo estimado · 75-90 minutos 

Vas a evolucionar tu pipeline RAG de L3.1 para incorporar hybrid search. Compararás resultados de las tres versiones (solo dense, solo BM25, hybrid) sobre el mismo corpus y queries.

1. **Recupera tu pipeline de L3.1**. Asegúrate de que sigue funcional con tu corpus de PDFs indexado en ChromaDB.
2. **Implementa BM25 retriever paralelo**. Carga los mismos chunks (puedes leerlos desde ChromaDB con `get()` o desde tu ingesta original). Crea un `BM25Retriever`. Verifica que devuelve resultados razonables sobre una query con términos específicos.
3. **Combina con EnsembleRetriever**. Pesos 0.5/0.5 como punto de partida. Sustituye tu retriever dense en la cadena RAG por el ensemble.
4. **Diseña un set de queries de evaluación** que mezcle:  
   * 5 queries con términos específicos (nombres propios, acrónimos, números, código).  
   * 5 queries semánticas (paráfrasis, conceptos relacionados).  
   * 5 queries mixtas (con algo de ambas).
5. **Tabula resultados**. Para cada query, anota los top-5 IDs recuperados por dense-only, BM25-only y hybrid. Marca cuáles consideras correctos manualmente.
6. **Calcula Recall@5 simple**. Si para cada query sabes el chunk correcto («ground truth»), Recall@5 = % de queries donde el chunk correcto aparece en top-5\. Compara las tres configuraciones.
7. **Ajusta los pesos del ensemble**. Prueba 0.3/0.7, 0.7/0.3\. ¿Qué configuración da mejores resultados en tu corpus?
8. **Implementa RRF manualmente**. Combina los rankings sin usar EnsembleRetriever, con tu propia función RRF. Verifica que da resultados similares.
9. **Bonus 1 · hybrid nativo en Qdrant**. Migra tu corpus a Qdrant siguiendo el ejemplo de hybrid nativo. Compara latencia y calidad con la implementación de LangChain.
10. **Bonus 2 · BM25 con lematización española**. Si tu corpus es en español, usa spaCy para lematizar antes de indexar BM25\. `pip install spacy` y `python -m spacy download es_core_news_sm`. ¿Mejora el matching?
11. **Bonus 3 · análisis cualitativo**. Identifica 3 queries donde hybrid claramente mejora sobre dense, 3 donde es similar y 3 donde dense puro funciona mejor. Reflexiona sobre el patrón.

El objetivo de este ejercicio no es solo activar hybrid: es desarrollar criterio sobre cuándo aporta y cuándo no. En entrevistas técnicas para puestos de AI Engineer junior, una respuesta como «implementé hybrid search y aporta un 12% de mejora en Recall@5 para queries con jerga técnica» te diferencia radicalmente de «usé RAG de LangChain». Mide. Anota. Aprende a defender tus decisiones técnicas con datos.

Preguntas frecuentes 

¿BM25 funciona bien en español?

Funciona pero rinde mejor con lematización y filtrado de stopwords. Los defaults de rank\_bm25 no lematizan ni quitan stopwords; si no lo configuras, palabras como «el», «la», «de» pesan menos por su IDF natural pero siguen apareciendo en tokenización. Para producción seria con español, usa spaCy: tokeniza, lematiza, opcionalmente filtra stopwords, y pasa esos tokens a BM25Okapi. La mejora frente a tokenización ingenua es notable.

¿Cuál es la diferencia entre SPLADE y BM25 sparse?

BM25 es un algoritmo determinista que cuenta términos. SPLADE (Sparse Lexical and Expansion Model) es un modelo neuronal que aprende sparse vectors donde cada dimensión corresponde a un token del vocabulario del modelo. SPLADE aprende a «expandir» queries añadiendo términos relacionados (mejor que BM25) sin perder la naturaleza sparse. En benchmarks suele superar a BM25 puro. Es lo que usa el ejemplo de Qdrant con FastEmbed. Para producción seria, SPLADE es opción más moderna; BM25 sigue siendo baseline robusto.

¿Hybrid search aumenta mucho la latencia?

No significativamente si se implementa bien. En Qdrant nativo, las dos búsquedas se hacen en paralelo dentro de la base; la latencia añadida es del 10-30% sobre dense puro. En implementaciones con EnsembleRetriever de LangChain, BM25 sobre corpus grande puede ser lento si está en memoria sin índices; conviene precalcular el índice BM25 una vez al levantar el servicio. Para corpus de millones de documentos, conviene Qdrant nativo o Elasticsearch.

¿Vale la pena hybrid si ya tengo reranking en SM3.3?

Sí, son complementarios. Hybrid mejora el recall del top-K inicial (mete más documentos relevantes en la primera selección). Reranking mejora la precisión del top final (reordena lo que ya tienes). Lo ideal es: hybrid recupera top-50, reranker reduce a top-5\. Cada técnica aporta en una capa distinta del pipeline.

Recursos para profundizar 

#### Hybrid search · teoría y práctica

* **BM25 · paper original de Robertson**. La referencia fundacional. en.wikipedia.org/wiki/Okapi\_BM25
* **rank\_bm25 · GitHub**. Librería que vas a usar. github.com/dorianbrown/rank\_bm25
* **Reciprocal Rank Fusion · paper original**. Cormack et al. 2009\. plg.uwaterloo.ca/\~gvcormac/cormacksigir09-rrf.pdf
* **Qdrant · Hybrid Search**. Documentación oficial con ejemplos. qdrant.tech/articles/hybrid-search
* **SPLADE · paper de Formal et al.**. Si te interesa profundizar en sparse neuronal. arxiv.org/abs/2107.05720
* **FastEmbed · GitHub**. Librería ligera para sparse + dense embeddings. github.com/qdrant/fastembed

Fin lección 3.2 · Sigue lección 3.3

LECCIÓN 3.3· \~2 horas · Sub-módulo 3

## Reranking · _cross-encoders al rescate_

El problema del top-K por similitud y por qué los primeros resultados no siempre son los más relevantes. Bi-encoders vs cross-encoders. Cohere Rerank API con free tier. Alternativas open-source con bge-reranker y Jina Reranker. El patrón retrieval-then-rerank en dos etapas.

Lectura · 40 min Ejemplos · 30 min Ejercicio · 50 min 

3.3.1Reranking como segunda etapa de calidad

#### Al final de esta lección sabrás:

* Explicar la diferencia entre bi-encoder (retrieval) y cross-encoder (reranking).
* Aplicar Cohere Rerank API (free tier) sobre tus resultados de retrieval.
* Usar bge-reranker o Jina Reranker como alternativas open-source self-hosted.
* Construir el patrón retrieval-then-rerank en dos etapas, midiendo la mejora en precisión final.
* Decidir cuándo el coste extra de reranking se justifica para tu caso.

El problema · los top-K por similitud no son los más relevantes

Embeddings densos son rápidos: precalculas embeddings del corpus una sola vez y la búsqueda es un producto matricial. Pero tienen una limitación importante: cada documento se embedea de forma independiente, sin conocer la query. El modelo de embeddings tiene que «adivinar» qué aspectos del texto serán importantes en queries futuras, comprimiendo todo en un vector único.

Esto introduce ruido. Dos documentos pueden tener embeddings similares por temas comunes («ambos hablan de Python») aunque solo uno responde realmente a la query («cómo decorar funciones en Python»). En el top-5 de un retriever solo-dense, es habitual ver 1-2 documentos perfectamente relevantes mezclados con 2-3 que comparten tema pero no responden.

El reranking ataca exactamente este problema: **tras la primera recuperación rápida del top-K (digamos K=50), aplica un modelo más caro y más preciso que mira query y documento juntos, y reordena para que los top-3 finales sean realmente los más relevantes**. Pierdes algunos milisegundos pero ganas precisión final notable.

Bi-encoder vs cross-encoder 

#### La diferencia técnica que importa

**Bi-encoder** (modelo de embeddings, como text-embedding-3-small): produce un vector por cada texto. Query y documento se procesan por separado. La similitud entre ellos es producto escalar. Velocidad: muy rápida (puedes precomputar embeddings del corpus). Precisión: limitada porque comprimes información en un vector único.

**Cross-encoder** (modelo de reranking, como bge-reranker-v2-m3): recibe query y documento como input conjunto («\[CLS\] query \[SEP\] documento \[SEP\]») y produce un único score de relevancia. No produce embeddings reutilizables. Velocidad: 10-100x más lento que bi-encoder porque cada par query-documento requiere una pasada del modelo. Precisión: mucho mejor porque el modelo «ve» query y documento simultáneamente y puede atender a las relaciones específicas entre ellos.

Por eso el patrón es **retrieve-then-rerank**: bi-encoder rápido recupera muchos candidatos (top-50), cross-encoder lento pero preciso reordena los 50 para dar el top-5 final. Lo mejor de los dos mundos: velocidad razonable + precisión alta.

Cohere Rerank · la opción más simple

Cohere ofrece Rerank como API gestionada. El modelo `rerank-multilingual-v3.0` es robusto en muchos idiomas incluido español. El free tier es generoso: 1.000 calls/mes, suficiente para experimentar y prototipos serios.

Ejemplo · Cohere Rerank en pipeline 

#### Reranking en una llamada

pip install cohere import cohere import os from dotenv import load\_dotenv load\_dotenv() co = cohere.Client(api\_key=os.getenv("COHERE\_API\_KEY")) query = "configurar acceso SSH en Ubuntu 24.04" # Documentos candidatos · habitualmente vienen de tu retriever (top-50) candidatos = \[ "Ubuntu 24.04 introduce nuevas funciones de seguridad.", "Para activar SSH en Ubuntu, instala openssh-server con apt.", "Python es un lenguaje de alto nivel ampliamente usado.", "El servicio SSH en Ubuntu 24.04 viene desactivado por defecto.", "Configurar el firewall ufw para permitir SSH es esencial.", "Linux tiene muchas distribuciones populares.", # ... hasta 50 candidatos típicamente \] response = co.rerank( model="rerank-multilingual-v3.0", query=query, documents=candidatos, top\_n=3, # devuelve solo los 3 mejores reordenados ) for r in response.results: print(f"\[{r.relevance\_score:.3f}\] idx={r.index} · {candidatos\[r.index\]\[:80\]}") # \[0.94\] idx=1 · Para activar SSH en Ubuntu, instala openssh-server... # \[0.89\] idx=3 · El servicio SSH en Ubuntu 24.04 viene desactivado... # \[0.71\] idx=4 · Configurar el firewall ufw para permitir SSH...

Notas. El `relevance_score` es un valor entre 0 y 1, calibrado a probabilidad de relevancia (no escala arbitraria como BM25). Esto permite filtrar por umbral: descarta documentos con score < 0.3, por ejemplo. La API acepta hasta 1.000 documentos por request en Cohere v3, suficiente para casi cualquier caso. Cada call cuenta como una en el free tier.

Alternativas open-source · bge-reranker y Jina Reranker

Si prefieres no depender de Cohere o necesitas self-hosting, hay opciones open-source excelentes:

* **bge-reranker-v2-m3 (BAAI)**. Multilingüe, soporta más de 100 idiomas incluido español. \~568M parámetros. Calidad comparable a Cohere Rerank. Apache 2.0.
* **bge-reranker-large**. Variante grande monolingüe inglés. Top en benchmarks BEIR. \~560M parámetros.
* **jina-reranker-v2-base-multilingual**. Más ligero (\~280M parámetros). Buen balance velocidad/calidad. Apache 2.0.
* **ms-marco-MiniLM-L-12-v2**. Cross-encoder muy ligero (\~33M params). Para queries rápidas con calidad aceptable.

Ejemplo · bge-reranker-v2-m3 local 

#### Reranking sin enviar datos fuera

pip install FlagEmbedding from FlagEmbedding import FlagReranker # Carga el modelo (descarga \~2 GB la primera vez) reranker = FlagReranker('BAAI/bge-reranker-v2-m3', use\_fp16=True) query = "configurar acceso SSH en Ubuntu 24.04" candidatos = \[ "Ubuntu 24.04 introduce nuevas funciones de seguridad.", "Para activar SSH en Ubuntu, instala openssh-server con apt.", # ... \] # Crea pares (query, doc) y obtiene scores pares = \[\[query, doc\] for doc in candidatos\] scores = reranker.compute\_score(pares, normalize=True) # entre 0 y 1 # Reordena ranked = sorted(zip(candidatos, scores), key=lambda x: -x\[1\]) for doc, score in ranked\[:3\]: print(f"\[{score:.3f}\] {doc\[:80\]}")

Notas. La primera ejecución descarga el modelo y lleva varios minutos. Luego, en GPU procesa 50 pares en menos de 1 segundo; en CPU son varios segundos. Para producción con volumen alto, GPU es prácticamente obligatorio. Para corpus pequeños y volumen bajo, CPU funciona. Para cualquier modelo de HuggingFace, comprueba si tiene versión cuantizada (int8, gguf) que reduce mucho los requisitos de hardware.

Ejemplo · sentence-transformers CrossEncoder 

#### Alternativa con la librería que ya conoces

from sentence\_transformers import CrossEncoder # Cross-encoder más ligero, suficiente para muchos casos model = CrossEncoder('cross-encoder/ms-marco-MiniLM-L-12-v2', max\_length=512) query = "cómo activar SSH en Ubuntu" docs = \["doc1...", "doc2...", "doc3..."\] # Calcula scores para todos los pares query-doc scores = model.predict(\[(query, doc) for doc in docs\]) # scores: array de floats, valores absolutos (no calibrados como Cohere) # Reordena ranked\_docs = sorted(zip(docs, scores), key=lambda x: -x\[1\])

Esta opción es la más ligera (33M parámetros, corre fácilmente en CPU). Calidad menor que bge-reranker pero suficiente para muchos casos. Útil si estás en máquina sin GPU y quieres reranking sin coste de API.

El patrón completo · retrieve-then-rerank

Integrando reranking en tu pipeline:

Ejemplo · pipeline completo con reranking 

#### Hybrid retrieve top-50 → rerank top-5

def retrieve\_and\_rerank(query: str, k\_retrieval: int = 50, k\_final: int = 5): # 1\. Hybrid retrieval (de L3.2): trae 50 candidatos candidates = ensemble\_retriever.invoke(query)\[:k\_retrieval\] texts = \[d.page\_content for d in candidates\] # 2\. Rerank con Cohere response = co.rerank( model="rerank-multilingual-v3.0", query=query, documents=texts, top\_n=k\_final, ) # 3\. Devuelve los Documents originales reordenados reranked\_docs = \[candidates\[r.index\] for r in response.results\] return reranked\_docs # Sustituye en la cadena RAG el retriever por esta función def format\_docs(docs): return "\\n\\n".join(d.page\_content for d in docs) def rag\_with\_rerank(question: str) -> str: reranked = retrieve\_and\_rerank(question, k\_retrieval=50, k\_final=5) context = format\_docs(reranked) prompt\_text = prompt.format(context=context, question=question) return llm.invoke(prompt\_text).content print(rag\_with\_rerank("¿Cómo configuro SSH en Ubuntu 24.04?"))

El parámetro clave es **k\_retrieval=50**. Si tu retrieval inicial trae 10, el reranker tiene poco margen para mejorar. Si trae 100-200, el reranker compensa errores del retrieval inicial. El sweet spot está entre 30 y 100 candidatos según calidad de tu retrieval base. Mide.

Cuándo el reranking vale la pena · y cuándo no 

#### Trade-off real

El reranking añade latencia (típicamente 100-500 ms con Cohere API, 1-3 segundos con bge-reranker en CPU) y, si usas APIs, coste por uso. La pregunta es cuándo esa inversión devuelve mejoras notables.

**Vale claramente la pena**: corpus medianos-grandes donde el retriever inicial trae mucho ruido, queries con matices semánticos donde los embeddings densos solos pierden precisión, sistemas donde la respuesta del LLM es muy sensible a qué contexto se le pasa (presupuesto de tokens limitado y necesitas que los 5 contextos seleccionados sean los buenos).

**Aporta poco**: corpus muy pequeños (cientos de docs), queries muy específicas donde el retriever ya da el correcto en top-3, sistemas con muy alta sensibilidad a latencia (chatbots interactivos donde 500ms más se notan).

La regla de oro: implementa retrieve-only y retrieve-then-rerank, mide con queries reales, decide. Casi siempre el reranking aporta, pero cuánto exactamente y a qué coste depende de tu caso.

#### Ejercicio 3.3 · añadir reranking al pipeline

Tiempo estimado · 50-60 minutos 

Vas a añadir una etapa de reranking sobre el pipeline hybrid de L3.2\. Compararás precisión final con y sin reranking.

1. **Setup Cohere**. Si no tienes ya, regístrate en Cohere (cohere.com) y obtén una API key. Free tier suficiente. Añade al .env como `COHERE_API_KEY`.
2. **Construye `retrieve_and_rerank`** según el ejemplo, sobre tu corpus indexado en L3.2\. **k\_retrieval=30** como punto de partida, **k\_final=5**.
3. **Usa el mismo set de queries de evaluación** de L3.2.
4. **Para cada query, ejecuta tres versiones**:  
   * v1 · solo retrieval hybrid (top-5 directo).  
   * v2 · hybrid retrieve top-30 + Cohere Rerank top-5.  
   * v3 · hybrid retrieve top-30 + bge-reranker top-5 (si tienes recursos para ejecutarlo).
5. **Marca manualmente qué resultados son relevantes** en cada caso. Calcula Precision@5 (cuántos de los top-5 son realmente relevantes).
6. **Mide latencias**. Tiempo total de cada versión por query. ¿Cuánto añade Cohere Rerank? ¿Y bge-reranker en tu máquina?
7. **Construye pipeline RAG final**. Sustituye en tu cadena LCEL la función de retrieval por la versión con reranking. Prueba 5 queries de extremo a extremo (retrieval → rerank → generation). ¿La respuesta final es mejor?
8. **Bonus 1 · variar k\_retrieval**. Prueba k\_retrieval=10, 30, 50, 100\. ¿Cómo evoluciona la precisión? ¿Hay punto de rendimientos decrecientes?
9. **Bonus 2 · filtro por umbral**. Solo pasa al LLM los documentos cuyo score de reranking sea > 0.5\. Si menos de 2 documentos superan el umbral, considera que la query no es contestable. Implementa este caso en tu pipeline.
10. **Bonus 3 · análisis de coste**. Calcula el coste hipotético de reranking en Cohere si tu sistema procesara 10.000 queries/mes. Compara con el coste de embeddings y de LLM. ¿Cuál pesa más?

El reranking suele ser la mejora más vistosa en demos: queries que devuelven «basura» con solo retrieval responden mucho mejor tras añadirlo. Es una pieza que casi siempre vale la pena en proyectos serios. Cuando termines este ejercicio, tu pipeline RAG está en nivel profesional: hybrid + reranking es la arquitectura por defecto de la mayoría de sistemas RAG empresariales en 2026.

Preguntas frecuentes 

¿Hace falta GPU para usar bge-reranker?

Recomendable pero no obligatorio. En CPU procesa pares query-doc del orden de 100-500 ms cada uno; para top-50 son 5-25 segundos por query. Demasiado para producción interactiva. En GPU (incluso modestas T4) procesa 50 pares en menos de 1 segundo. Si vas a usar reranking open-source en producción seria, planifica GPU. Para prototipos y desarrollo, CPU es viable con paciencia.

¿Cohere Rerank es muy distinto a bge-reranker en calidad?

Muy similar en calidad para queries en idiomas mainstream. Cohere tiene la ventaja de ser API gestionada (cero infraestructura). bge-reranker tiene la ventaja de ser open-source (sin envío de datos, sin coste por uso a escala). En entornos sensibles a privacidad o con volumen muy alto, bge-reranker es la elección racional. En prototipos y volumen medio, Cohere es más cómodo. Otra alternativa interesante: Jina Reranker como API también tiene free tier y suele rendir muy bien.

¿Puedo combinar hybrid search con reranking en Qdrant nativamente?

Qdrant hace hybrid nativamente pero el reranking con cross-encoder lo aplicas tú a posteriori (Qdrant no integra cross-encoders, solo dense y sparse). El patrón habitual: Qdrant te devuelve top-50 con hybrid + RRF, tú aplicas reranking a esos 50 con Cohere o bge-reranker, te quedas con top-5\. Es la combinación más potente.

¿Y los rerankers basados en LLM general (GPT-4 como reranker)?

Existe y se llama «LLM-as-reranker» o RankGPT. Le pides a un LLM general que ordene una lista de documentos por relevancia. Calidad muy buena (los LLMs grandes son excelentes evaluando relevancia) pero coste y latencia muy altos: 50 documentos en contexto consume muchos tokens. Reservado para casos donde calidad importa más que coste. Para uso general, cross-encoder dedicado es 100x más eficiente con calidad comparable.

Recursos para profundizar 

#### Reranking · modelos y prácticas

* **Cohere Rerank · documentación**. docs.cohere.com/docs/rerank-overview
* **BGE Reranker · HuggingFace**. Tarjeta del modelo con ejemplos. huggingface.co/BAAI/bge-reranker-v2-m3
* **Jina Reranker · GitHub y blog**. huggingface.co/jinaai/jina-reranker-v2-base-multilingual
* **Sentence-Transformers · CrossEncoder docs**. Para usar cross-encoders con la librería que ya conoces. sbert.net/examples/applications/cross-encoder
* **RankGPT paper**. LLM-as-reranker para contexto. arxiv.org/abs/2304.09542

Fin lección 3.3 · Sigue lección 3.4

LECCIÓN 3.4· \~2 horas · Sub-módulo 3

## Corrective RAG (CRAG) · _fallback a búsqueda web_

El paper CRAG de Yan et al. 2024\. Evaluador de retrieval que clasifica resultados como Correct, Ambiguous o Incorrect. Fallback a búsqueda web con Tavily (free tier) cuando el corpus interno no tiene la respuesta. Implementación con LangGraph para el flujo condicional.

Lectura · 40 min Ejemplos · 30 min Ejercicio · 50 min 

3.4.1CRAG · cuando el retrieval falla, busca fuera

#### Al final de esta lección sabrás:

* Explicar la idea central del paper CRAG (Yan et al. 2024) y por qué resuelve un problema real.
* Implementar un evaluador de relevancia que clasifica retrieval como Correct, Ambiguous o Incorrect.
* Activar fallback a búsqueda web con Tavily Search API (free tier 1.000 búsquedas/mes).
* Construir el flujo condicional con LangGraph para tu primer sistema RAG con corrección.
* Identificar cuándo CRAG mejora un sistema RAG y cuándo añade complejidad sin retorno.

El problema que CRAG resuelve

Has construido un pipeline RAG con hybrid search y reranking. La calidad ha subido notablemente. Pero queda un problema fundamental: **¿qué pasa cuando la respuesta simplemente no está en tu corpus?**

Tres escenarios típicos:

* La pregunta es sobre un tema que tu corpus no cubre (preguntan por una novedad de 2026 y tus documentos son de 2024).
* La pregunta está sobre el límite de tu corpus (lo cubre parcialmente, los chunks recuperados están en la frontera de relevancia).
* La pregunta está mal formulada o es ambigua, y el retrieval trae documentos tangencialmente relacionados.

En todos ellos, naive RAG falla silenciosamente: pasa al LLM contexto irrelevante y el LLM o se inventa una respuesta (hallucinations) o dice «no tengo esa información» basándose en contexto inútil. CRAG ataca esto añadiendo una **etapa de evaluación del retrieval**: antes de generar la respuesta, juzga si los chunks recuperados son suficientes. Si lo son, sigue normal. Si no, activa fallback (búsqueda web, knowledge refinement, etc.).

El paper original · Yan et al. 2024 

#### «Corrective Retrieval Augmented Generation»

El paper de Shi-Qi Yan y otros, publicado en arXiv en enero 2024, propone tres elementos principales:

* **Retrieval Evaluator**. Un modelo (en el paper un T5 pequeño fine-tuned) que recibe la query y los documentos recuperados y predice la confianza de relevancia. Clasifica el retrieval en tres buckets:  
   * _Correct_: hay al menos un documento claramente relevante. Sigue el flujo normal de RAG.  
   * _Incorrect_: ningún documento es relevante. Activa búsqueda web y reemplaza el contexto.  
   * _Ambiguous_: hay documentos parcialmente relevantes pero ninguno claramente bueno. Combina el contexto recuperado con búsqueda web (knowledge refinement).
* **Knowledge Refinement**. Para mejorar los chunks recuperados, los descompone en sentencias («strips»), evalúa cada una y reconstruye un contexto refinado que mantiene solo las sentencias relevantes.
* **Web Search**. Cuando el retrieval interno es insuficiente, hace búsqueda web (en el paper, con DuckDuckGo) sobre una query reescrita por un LLM.

El paper reporta mejoras significativas en benchmarks como PopQA y Biography. En la práctica, implementaciones simplificadas de CRAG (sin fine-tunear el T5, usando un LLM general como evaluador) capturan la mayoría del beneficio.

Implementación práctica · evaluador con LLM

Para no fine-tunear un T5, lo más práctico es usar un LLM general (Haiku, Gemini Flash, GPT-4o-mini) como evaluador. Le pides que valore la relevancia de cada chunk respecto a la query con un prompt estructurado y un output JSON.

Ejemplo · evaluador de relevancia con LLM 

#### Clasificar el retrieval en Correct / Ambiguous / Incorrect

from langchain\_openai import ChatOpenAI from langchain\_core.prompts import ChatPromptTemplate from langchain\_core.pydantic\_v1 import BaseModel, Field from typing import Literal evaluator\_llm = ChatOpenAI(model="gpt-4o-mini", temperature=0) class RetrievalGrade(BaseModel): grade: Literal\["correct", "ambiguous", "incorrect"\] = Field( description="Calidad del retrieval para responder la pregunta" ) reason: str = Field(description="Breve justificación de la valoración") evaluator\_prompt = ChatPromptTemplate.from\_template("""Eres un evaluador estricto. Te dan una pregunta y los fragmentos de documentos recuperados para responderla. Tu tarea es valorar si los fragmentos son suficientes. - "correct": al menos un fragmento contiene información clara y directa para responder la pregunta. - "ambiguous": los fragmentos están relacionados con el tema pero la respuesta no es clara o falta información. - "incorrect": los fragmentos no son relevantes; no se puede responder con esta información. Pregunta: {question} Fragmentos: {context} Responde solo con tu valoración.""") evaluator = evaluator\_prompt | evaluator\_llm.with\_structured\_output(RetrievalGrade) # Uso result = evaluator.invoke({ "question": "¿Cómo configuro SSH en Ubuntu 24.04?", "context": "\\n\\n".join(\[d.page\_content for d in retrieved\_docs\]), }) print(result.grade) # "correct" / "ambiguous" / "incorrect" print(result.reason)

El truco está en el prompt: cuanto más estricto y específico, mejor decisión. Un evaluador laxo califica todo como «correct» y CRAG no aporta nada. Un evaluador muy estricto activa fallback demasiado y aumenta latencia. Iterar el prompt y validar con queries de prueba es esencial.

Búsqueda web como fallback · Tavily Search API

Tavily es un buscador especializado para LLMs con free tier de 1.000 búsquedas al mes. Devuelve resultados ya procesados en formato JSON limpio, sin ruido de SEO ni publicidad. Ideal para CRAG.

Alternativas: **DuckDuckGo** (sin API key, pero menos fiable y a veces rate-limited), **SerpAPI** o **Brave Search API** (más estables pero con planes de pago tras el free tier), **Exa** (Metaphor) si quieres búsqueda semántica.

Ejemplo · web search con Tavily 

#### Free tier, sin SEO, formato limpio

pip install tavily-python from tavily import TavilyClient import os from dotenv import load\_dotenv load\_dotenv() tavily = TavilyClient(api\_key=os.getenv("TAVILY\_API\_KEY")) # Búsqueda básica response = tavily.search( query="configurar SSH Ubuntu 24.04 mejores prácticas seguridad", search\_depth="basic", # "basic" (más rápido) o "advanced" (más profundo) max\_results=5, include\_answer=True, # Tavily genera un resumen automático ) print(response\["answer"\]) # resumen agregado for r in response\["results"\]: print(f"\\n{r\['title'\]}") print(r\["url"\]) print(r\["content"\]\[:200\]) # snippet ya extraído # Para CRAG: usar los snippets como contexto adicional/sustitutivo web\_contexts = \[r\["content"\] for r in response\["results"\]\]

Tavily incluye opcionalmente un _answer_ que es un resumen del LLM de Tavily sobre los resultados. Útil como pre-respuesta. Para CRAG conviene usar los `content` individuales como nuevos «chunks» que reemplazan o complementan el retrieval interno.

El flujo condicional · LangGraph para orquestar

CRAG no es un pipeline lineal: dependiendo del resultado del evaluador, el flujo se bifurca. Implementarlo con if/else en Python es viable pero feo. LangGraph (parte del ecosistema LangChain) está diseñado para grafos de estado donde nodos representan acciones y aristas condicionales representan decisiones. Es la herramienta natural para CRAG y para los patrones agénticos de SM4.

Ejemplo · CRAG simplificado con LangGraph 

#### Grafo con retrieval + evaluator + web search condicional

pip install langgraph from langgraph.graph import StateGraph, END from typing import TypedDict, List # Estado del grafo: las variables que viajan entre nodos class CRAGState(TypedDict): question: str documents: List\[str\] grade: str web\_results: List\[str\] final\_answer: str # --- Nodos --- def retrieve\_node(state: CRAGState): docs = ensemble\_retriever.invoke(state\["question"\]) return {"documents": \[d.page\_content for d in docs\]} def evaluate\_node(state: CRAGState): context = "\\n\\n".join(state\["documents"\]) result = evaluator.invoke({"question": state\["question"\], "context": context}) return {"grade": result.grade} def web\_search\_node(state: CRAGState): response = tavily.search(query=state\["question"\], max\_results=5) web\_contexts = \[r\["content"\] for r in response\["results"\]\] return {"web\_results": web\_contexts} def generate\_node(state: CRAGState): # Combinar fuentes según el grade if state\["grade"\] == "correct": context = "\\n\\n".join(state\["documents"\]) elif state\["grade"\] == "ambiguous": context = "\\n\\n".join(state\["documents"\] + state.get("web\_results", \[\])) else: # incorrect context = "\\n\\n".join(state.get("web\_results", \[\])) answer = llm.invoke(prompt.format( question=state\["question"\], context=context )).content return {"final\_answer": answer} # --- Arista condicional --- def decide\_next(state: CRAGState): if state\["grade"\] == "correct": return "generate" return "web\_search" # ambiguous o incorrect # --- Construir el grafo --- graph = StateGraph(CRAGState) graph.add\_node("retrieve", retrieve\_node) graph.add\_node("evaluate", evaluate\_node) graph.add\_node("web\_search", web\_search\_node) graph.add\_node("generate", generate\_node) graph.set\_entry\_point("retrieve") graph.add\_edge("retrieve", "evaluate") graph.add\_conditional\_edges("evaluate", decide\_next, { "generate": "generate", "web\_search": "web\_search", }) graph.add\_edge("web\_search", "generate") graph.add\_edge("generate", END) app = graph.compile() # Uso result = app.invoke({"question": "¿Qué es el modo Lockdown en macOS Sonoma?"}) print(result\["final\_answer"\]) print(f"Grade: {result\['grade'\]}")

El grafo tiene tres rutas posibles: retrieve → evaluate → generate (caso correct), o retrieve → evaluate → web\_search → generate (casos ambiguous e incorrect). LangGraph hace el orquestado limpio y trazable. Para sistemas más complejos del SM4 (Agentic RAG, Self-RAG), LangGraph es la herramienta natural.

CRAG vs solo RAG · honest assessment 

#### Cuándo realmente vale la complejidad

CRAG añade latencia (la evaluación es una llamada LLM extra, la web search más latencia) y coste (más llamadas a APIs). El beneficio depende del caso:

**Aporta claramente**: sistemas tipo asistente generalista donde los usuarios preguntan cosas que el corpus puede no cubrir (manual interno + preguntas tangenciales), chatbots de servicio al cliente donde queremos cubrir queries fuera del FAQ con info web, casos donde recency importa (info que cambia y tu corpus se queda atrás).

**Aporta poco**: sistemas RAG estrictamente sobre dominio cerrado donde las queries fuera del corpus deben rechazarse (chatbot legal sobre una jurisdicción concreta donde no quieres mezclar con info web sin verificar), sistemas con corpus muy completo donde el retrieval casi siempre acierta.

Mi recomendación: implementa CRAG, mide en queries reales (incluido casos donde la respuesta no está), y decide si el beneficio compensa. Para sistemas serios suele valer la pena al menos el evaluador (sin web search): clasificar retrieval como correct/ambiguous/incorrect te permite responder honestamente «no tengo esa información» en vez de inventar.

#### Ejercicio 3.4 · CRAG simplificado sobre tu pipeline

Tiempo estimado · 60-75 minutos 

Vas a integrar un evaluador de retrieval y opcionalmente fallback a búsqueda web sobre tu pipeline con hybrid + reranking.

1. **Setup Tavily**. Regístrate en tavily.com, genera API key. Añade al .env como `TAVILY_API_KEY`. Free tier 1.000 búsquedas/mes.
2. **Setup LangGraph**: `pip install langgraph`.
3. **Implementa el evaluador** según el ejemplo. Itera el prompt hasta que clasifique con criterio: prueba con queries donde sabes la respuesta está en el corpus (debería decir correct) y queries fuera del corpus (incorrect).
4. **Construye el grafo CRAG** con los cuatro nodos: retrieve, evaluate, web\_search, generate. Aristas condicionales según el grado.
5. **Diseña queries de prueba** en tres categorías:  
   * 5 queries cuya respuesta SÍ está en tu corpus.  
   * 5 queries cuya respuesta NO está en tu corpus pero es buscable en internet.  
   * 5 queries cuya respuesta está parcialmente (el corpus la cubre incompletamente).
6. **Ejecuta el pipeline CRAG con cada query**. Registra: grade del evaluador, si se activó web search, calidad final de la respuesta.
7. **Compara con el RAG normal de L3.3** sobre las mismas queries. ¿En qué casos CRAG mejora? ¿En cuáles añade complejidad sin ganancia?
8. **Identifica errores del evaluador**. ¿Hay queries donde dice correct cuando no debería, o viceversa? Ajusta el prompt del evaluador y reitera.
9. **Bonus 1 · query rewriting**. Antes de la web search, reescribe la query original con un LLM para que sea más adecuada para búsqueda web («¿cómo configuro X?» → «configurar X tutorial paso a paso»). Mide si mejora los resultados de Tavily.
10. **Bonus 2 · knowledge refinement**. Implementa el «strip filtering» del paper: descompón cada chunk en oraciones, evalúa la relevancia de cada una con un LLM ligero, recompon el contexto solo con las relevantes. Mide impacto en respuestas finales.
11. **Bonus 3 · medir coste y latencia**. Para cada query, anota cuántas llamadas LLM y APIs se hicieron. Calcula el coste total mensual hipotético si tu sistema procesara 5.000 queries/mes.

CRAG es el paso del RAG estático al RAG dinámico que se autocorrige. Tras este ejercicio, tu pipeline cubre prácticamente toda la práctica profesional de RAG en producción. El SM4 añade la capa agéntica encima: agentes que deciden cuándo recuperar, auto-evaluación de la respuesta generada, y proyecto final integrador. La curva ya está hecha; lo que queda es composición.

Preguntas frecuentes 

¿No es CRAG simplemente «si el retrieval falla, busca en Google»?

Conceptualmente sí, pero con dos sutilezas importantes. Primero, la evaluación: necesitas un evaluador fiable para detectar «retrieval falla», porque el RAG ingenuo siempre devuelve algo (top-K nunca está vacío). El valor está en distinguir «no tengo respuesta» vs «aquí está el documento correcto». Segundo, la integración: cuando hay info parcial en el corpus y parcial en web, la combinación inteligente es mejor que sustitución pura. El paper formaliza esto con la categoría ambiguous y knowledge refinement.

¿Y si no quiero que mi sistema consulte web search nunca? ¿Sirve CRAG?

Sí, sigue siendo útil. Sin web search, el evaluador te permite responder honestamente cuando no tienes la información. En vez de generar respuesta inventada o forzada con contexto irrelevante, tu sistema dice «no tengo información para responder esto». Para chatbots empresariales serios, esta honestidad es muy valiosa: prefieres que el bot no responda a que invente.

¿LangGraph reemplaza a LangChain o son complementarios?

Complementarios. LangChain provee los componentes (loaders, splitters, retrievers, LLMs, prompts). LangGraph provee la orquestación con grafos de estado. Para pipelines lineales basta LangChain LCEL; para flujos con decisiones, ciclos, agentes, LangGraph es la herramienta. Ambos están desarrollados por el mismo equipo y son interoperables.

¿Tavily es el único buscador para LLMs? ¿Qué alternativas open-source hay?

No es el único. Alternativas: **DuckDuckGo** (open-source vía _duckduckgo-search_, sin API key pero rate-limited), **Brave Search API** (free tier 2.000 búsquedas/mes), **Exa** (búsqueda semántica, free tier), **SearXNG** (meta-buscador self-hosted, agrega múltiples motores). Tavily destaca por estar diseñado específicamente para agentes LLM (formato JSON limpio, sin SEO, includes\_answer). Para producción seria, vale la pena comparar varios.

Recursos para profundizar 

#### CRAG y orquestación de RAG corregido

* **CRAG paper · Yan et al. 2024**. La referencia original. arxiv.org/abs/2401.15884
* **LangGraph Documentation**. Tutorial oficial con CRAG implementado. langchain-ai.github.io/langgraph
* **Tavily Documentation**. API y best practices. docs.tavily.com
* **LangChain · CRAG cookbook**. Notebook completo con LangGraph. github.com/langchain-ai/langgraph/blob/main/examples/rag/langgraph\_crag.ipynb
* **DuckDuckGo-search · GitHub**. Alternativa open-source a Tavily. github.com/deedy5/duckduckgo\_search

Fin del sub-módulo 3 · Sigue sub-módulo 4 · Agentic RAG, Self-RAG y proyecto final

SUB-MÓDULO 4· 10 horas · 4 lecciones

## Agentic RAG, Self-RAG, _evaluación y proyecto final_

El salto del pipeline lineal al sistema agéntico. Agentes que deciden cuándo y cómo recuperar. Self-RAG con auto-evaluación de relevancia y soporte. Evaluación con RAGAS y métricas estándar. Proyecto final integrador: chatbot empresarial sobre documentación privada con todo lo aprendido.

10 horas totales 4 lecciones Proyecto final integrador LangGraph · RAGAS · Tu propio dominio 

LECCIÓN 4.1· \~2,5 horas · Sub-módulo 4

## Agentic RAG · _agentes que deciden cuándo recuperar_

Del retrieval automático al retrieval como herramienta de un agente. Patrón ReAct con tools. Query decomposition para preguntas complejas. Multi-step reasoning. Construcción de un agente con varias herramientas (retrieval interno + búsqueda web + calculadora) en LangGraph.

Lectura · 55 min Ejemplos · 35 min Ejercicio · 60 min 

4.1.1Retrieval como herramienta de un agente

#### Al final de esta lección sabrás:

* Explicar la diferencia entre RAG estático (siempre recupera) y Agentic RAG (decide cuándo recuperar).
* Implementar el patrón ReAct: el LLM piensa, decide qué herramienta usar, observa el resultado y continúa.
* Construir un agente con múltiples herramientas (retrieval, web search, calculadora) en LangGraph.
* Aplicar query decomposition para preguntas complejas que requieren varios pasos.
* Reconocer cuándo Agentic RAG aporta valor frente a un pipeline estático.

El salto de pipeline a agente

Los pipelines RAG de SM3 son estáticos: la query entra, se ejecuta una secuencia fija (retrieve → rerank → generate), sale la respuesta. Funciona bien para preguntas simples sobre un único corpus. Falla en escenarios cada vez más comunes:

* **Preguntas que no necesitan retrieval**. «¿Cuánto es 17 × 23?»: el RAG estático recupera contexto irrelevante. El agente entiende que es cálculo y no recupera.
* **Preguntas con varios componentes**. «Compara la política de devolución de mi empresa con la mediana de las del sector»: requiere retrieval interno (política propia) más búsqueda externa (otras políticas) más cálculo (mediana).
* **Preguntas que requieren razonamiento sobre los chunks**. «¿Cuál es el cliente con mayor facturación de los mencionados en el informe Q3?»: el LLM necesita procesar varios chunks y razonar entre ellos.
* **Preguntas con herramientas externas**. «¿Qué hora es en Tokio ahora?», «¿Cotización actual de Tesla?», «¿Hay noticias hoy sobre X?»: requieren tools que no son retrieval ni embeddings.

La arquitectura agéntica resuelve esto: **el LLM es el orquestador** que decide en cada turno qué hacer. Tiene a su disposición un conjunto de herramientas (entre ellas, retrieval) y elige cuándo usar cada una. Es lo que Anthropic llama _agent_ en su post «Building Effective Agents»: un sistema donde el LLM dirige su propio proceso usando tools.

El patrón ReAct 

#### Reasoning + Acting · el ciclo agéntico

ReAct (Yao et al. 2022) es el patrón canónico: el LLM alterna entre **Thought** (razonamiento sobre qué hacer), **Action** (invocar una herramienta con parámetros) y **Observation** (recibir el resultado). El ciclo continúa hasta que el LLM decide que tiene suficiente para responder.

Un agente ReAct para RAG sobre documentación de Python podría procesar «¿Cómo se ordenan listas en Python y cuánto tarda?» así:

1. _Thought_: «La pregunta tiene dos partes. Primero busco cómo se ordenan listas en la documentación.»
2. _Action_: `retrieve("ordenar listas Python sort sorted")`.
3. _Observation_: chunks sobre `list.sort()` y `sorted()`.
4. _Thought_: «Ahora necesito la complejidad. Busco Timsort.»
5. _Action_: `retrieve("Timsort complexity algorithm")`.
6. _Observation_: chunks sobre Timsort, O(n log n).
7. _Thought_: «Tengo suficiente para responder.»
8. Final answer: explicación de los dos métodos + complejidad.

Los LLMs modernos (Claude 3.5/4, GPT-4o, Gemini 1.5+) soportan tool use nativamente: el modelo devuelve estructuralmente «usar tool X con params Y» y tú ejecutas, devolviendo el resultado. Esto es mucho más fiable que parsear texto libre del modelo.

Implementación · agente con retrieval como tool

Ejemplo · agente ReAct simple con LangGraph 

#### Retrieval + cálculo como tools

pip install langgraph langchain-anthropic from langchain\_core.tools import tool from langchain\_anthropic import ChatAnthropic from langgraph.prebuilt import create\_react\_agent # Define herramientas como funciones decoradas @tool def buscar\_en\_docs(query: str) -> str: """Busca información en la documentación interna de la empresa. Úsalo para preguntas sobre productos, políticas o procesos internos.""" docs = retrieve\_and\_rerank(query, k\_retrieval=20, k\_final=5) return "\\n\\n".join(\[d.page\_content for d in docs\]) @tool def buscar\_web(query: str) -> str: """Busca información en internet con Tavily. Úsalo para preguntas sobre eventos recientes, noticias o información no presente en docs internos.""" response = tavily.search(query=query, max\_results=5) return "\\n\\n".join(\[f"{r\['title'\]}: {r\['content'\]}" for r in response\["results"\]\]) @tool def calcular(expresion: str) -> str: """Evalúa una expresión matemática. Ej: '17 \* 23' o '(120 - 80) / 4'.""" try: # En producción usar una calculadora segura, no eval() import ast, operator as op ops = {ast.Add: op.add, ast.Sub: op.sub, ast.Mult: op.mul, ast.Div: op.truediv, ast.USub: op.neg, ast.Pow: op.pow} def \_eval(node): if isinstance(node, ast.Num): return node.n if isinstance(node, ast.BinOp): return ops\[type(node.op)\](\_eval(node.left), \_eval(node.right)) if isinstance(node, ast.UnaryOp): return ops\[type(node.op)\](\_eval(node.operand)) raise ValueError("Expresión no permitida") return str(\_eval(ast.parse(expresion, mode='eval').body)) except Exception as e: return f"Error: {e}" # Modelo con soporte de tool use model = ChatAnthropic(model="claude-3-5-sonnet-latest", temperature=0) # Sistema con instrucciones system\_prompt = """Eres un asistente útil que ayuda a empleados. Tienes herramientas: - buscar\_en\_docs: para info de productos, políticas o procesos internos. - buscar\_web: para eventos recientes, noticias, info externa. - calcular: para operaciones matemáticas. Antes de responder, piensa qué herramienta necesitas. Si la pregunta no requiere ninguna, responde directamente desde tu conocimiento. Cita siempre las fuentes cuando uses retrieval.""" agent = create\_react\_agent(model, tools=\[buscar\_en\_docs, buscar\_web, calcular\], state\_modifier=system\_prompt) # Uso result = agent.invoke({ "messages": \[("user", "¿Cuál es nuestra política de vacaciones para empleados con 5 años de antigüedad? Y si me corresponden 23 días, ¿cuántos serían en horas si la jornada es de 8h?")\] }) for msg in result\["messages"\]: print(f"{msg.type}: {msg.content\[:300\]}")

El agente ReAct prebuilt de LangGraph hace todo el ciclo automáticamente: el LLM elige tools, LangGraph las ejecuta, devuelve resultados al LLM, el LLM continúa hasta tener respuesta final. Para casos más complejos puedes construir el grafo a mano con StateGraph (control total) en lugar de usar el prebuilt.

Query decomposition · descomponer antes de ejecutar

Para queries complejas, una estrategia útil es **descomponer la pregunta en sub-preguntas antes de empezar**. Cada sub-pregunta se resuelve por separado, los resultados se combinan. Esto es especialmente útil cuando una pregunta toca varios documentos o temas:

Ejemplo · query decomposition explícita 

#### Descomponer · resolver · combinar

from langchain\_core.pydantic\_v1 import BaseModel, Field from typing import List class SubQuestions(BaseModel): questions: List\[str\] = Field(description="Lista de sub-preguntas independientes") decompose\_prompt = ChatPromptTemplate.from\_template("""Descompón la siguiente pregunta compleja en sub-preguntas más simples e independientes. Cada sub-pregunta debe poder responderse por separado. Si la pregunta ya es simple, devuelve la lista con esa única pregunta. Pregunta: {question} Devuelve solo la lista de sub-preguntas.""") decomposer = decompose\_prompt | model.with\_structured\_output(SubQuestions) def answer\_complex\_query(question: str) -> str: # 1\. Descomponer sub\_qs = decomposer.invoke({"question": question}).questions print(f"Sub-preguntas: {sub\_qs}") # 2\. Resolver cada sub-pregunta con RAG sub\_answers = \[\] for q in sub\_qs: docs = retrieve\_and\_rerank(q, k\_retrieval=10, k\_final=3) context = "\\n\\n".join(\[d.page\_content for d in docs\]) answer = llm.invoke(prompt.format(question=q, context=context)).content sub\_answers.append((q, answer)) # 3\. Combinar combined\_context = "\\n\\n".join(\[f"Q: {q}\\nR: {a}" for q, a in sub\_answers\]) final = llm.invoke(f"""Dada esta lista de preguntas y respuestas, sintetiza una respuesta única y coherente a la pregunta original. Pregunta original: {question} Información: {combined\_context} Respuesta final:""").content return final print(answer\_complex\_query( "¿Cuáles son las diferencias entre nuestra política de teletrabajo del 2023 y la actualizada de 2025, y qué cambios afectan a empleados con hijos?" ))

Variantes interesantes. **Sub-question Query Engine** de LlamaIndex hace esto nativamente. Para preguntas en grafo (pregunta B depende de respuesta a A), conviene un agente ReAct que vaya planeando dinámicamente. Para preguntas paralelas independientes, decomposition con resolución concurrente es la opción más eficiente.

Trade-offs del enfoque agéntico 

#### Cuándo aporta y cuándo es overkill

Agentic RAG es más flexible pero más costoso. Cada pregunta puede acabar haciendo 3-5 llamadas LLM en lugar de 1, con latencias y costes proporcionales. Antes de adoptarlo, valora:

**Aporta claramente**: sistema con muchos tipos de query muy distintos (algunas requieren cálculo, otras docs, otras búsqueda), preguntas complejas multi-paso recurrentes, casos donde se necesita razonamiento sobre los resultados (no solo «devolver» el contexto), asistentes con varias bases de conocimiento heterogéneas.

**Es overkill**: sistemas donde 95% de queries son simples retrieve-then-answer, escenarios con latencia crítica (chatbots conversacionales fluidos), proyectos con presupuesto muy ajustado donde cada llamada LLM extra duele.

Patrón híbrido común: clasifica la query primero («¿es simple o compleja?»). Si simple, RAG estático rápido. Si compleja, agente. Esta combinación da buena experiencia sin coste excesivo.

#### Ejercicio 4.1 · agente RAG con múltiples herramientas

Tiempo estimado · 60-75 minutos 

Vas a construir un agente que combina retrieval sobre tu corpus, búsqueda web y cálculo. Es la base para tu proyecto final del 4.4.

1. **Define al menos 3 tools**:  
   * Una para retrieval sobre tu corpus (la pipeline de L3.3 envuelta como tool).  
   * Una para web search con Tavily (de L3.4).  
   * Una a tu elección: calculadora, consulta de fechas/horas, listar archivos del corpus, etc.
2. **Implementa el agente** con `create_react_agent` de LangGraph. Usa Claude 3.5 Sonnet o GPT-4o como modelo (tool use fiable).
3. **Diseña system prompt** que oriente el uso de cada tool: cuándo usar cada una, importancia de citar fuentes, instrucción de no inventar.
4. **Diseña queries de prueba**:  
   * 3 que deberían usar solo retrieval interno.  
   * 3 que deberían usar solo web search.  
   * 2 que requieren combinar tools (interno + web, o interno + cálculo).  
   * 2 que no necesitan ninguna tool (saludos, preguntas generales).
5. **Para cada query, inspecciona los mensajes**. ¿Eligió bien las tools el agente? ¿Razonó correctamente?
6. **Mide latencia y nº de llamadas LLM** por query. Compara con tu pipeline estático de SM3.
7. **Identifica fallos**. Patrones comunes: el agente no usa retrieval cuando debería, hace muchas búsquedas redundantes, alucina en la respuesta final ignorando los resultados de tools.
8. **Refina el system prompt** iterativamente para corregir los fallos.
9. **Bonus 1 · query decomposition**. Añade un paso previo de decomposition para queries detectadas como complejas (con un clasificador inicial).
10. **Bonus 2 · multi-base**. Si tienes dos corpus distintos (manuales + FAQs + contratos), expón cada uno como tool separada. El agente elige cuál(es) consultar según la pregunta.
11. **Bonus 3 · streaming**. Configura el agente para streamear el proceso (thoughts, actions, observations) en vez de devolver solo la respuesta final. Útil para UI tipo «mostrar al usuario qué hace el bot».

El paso de pipeline a agente es conceptual: cambias de «yo controlo el flujo» a «el LLM controla el flujo». Esto da flexibilidad enorme pero requiere disciplina en system prompts y observabilidad. Sin trazas (logs) de qué hizo el agente en cada turno, los fallos son imposibles de diagnosticar. LangSmith (de LangChain, free tier) o herramientas open-source como Langfuse ayudan mucho aquí.

Preguntas frecuentes 

¿Agentic RAG es lo mismo que un agente?

Casi. Agentic RAG es la subcategoría de agentes donde retrieval es una herramienta (la más importante, normalmente). Un agente más general puede tener tools que no son retrieval (interactuar con APIs, ejecutar código, controlar un navegador). Conceptualmente la arquitectura es la misma; «Agentic RAG» enfatiza que el caso de uso es responder preguntas sobre conocimiento.

¿Qué modelos LLM son mejores para agentes?

Los que soportan tool use de forma fiable. Claude 3.5/4 Sonnet y Opus son excelentes en tool use, GPT-4o también, Gemini 1.5/2.0 Pro funciona pero a veces es menos disciplinado. Modelos open-source con tool use razonable: Llama 3.1/3.3 70B+, Mistral Large, Qwen 2.5 Coder/Instruct 32B+. Para tareas críticas, valida con tu caso específico: la calidad de tool use varía mucho por modelo.

¿Cuántas tools puedo darle a un agente?

En la práctica, modelos modernos manejan bien hasta 10-15 tools. Más de eso y el modelo empieza a confundirse o eligir mal. Si necesitas más, hay patrones como tool routing (un clasificador inicial decide qué subset de tools mostrar) o jerarquía (tool «consultar producto» que internamente decide entre varias APIs). Para empezar, 3-5 tools bien definidas funcionan mejor que 20 mal organizadas.

¿LangGraph para todo, o también CrewAI, AutoGen, etc.?

LangGraph es el más maduro para grafos de estado, pero hay alternativas: **CrewAI** (multi-agente con roles definidos), **AutoGen** (de Microsoft, conversaciones entre agentes), **Pydantic AI** (tipado fuerte sobre tools). Para tu primer agente, LangGraph es opción sólida y se integra con todo el ecosistema LangChain que ya conoces. Si tu sistema crece a multi-agente con varios «expertos» colaborando, valora CrewAI.

Recursos para profundizar 

#### Agentic RAG y patrones agénticos

* **Anthropic · Building Effective Agents**. Lectura imprescindible. Define con claridad qué es agente vs workflow. anthropic.com/research/building-effective-agents
* **ReAct paper · Yao et al. 2022**. El paper fundacional. arxiv.org/abs/2210.03629
* **LangGraph · documentación oficial**. Tutoriales y patrones. langchain-ai.github.io/langgraph
* **LlamaIndex · Agentic RAG guide**. Su perspectiva sobre el patrón. docs.llamaindex.ai/en/stable/use\_cases/agents
* **Awesome LLM Agents · GitHub**. Lista curada de papers, frameworks y proyectos. github.com/kaushikb11/awesome-llm-agents

Fin lección 4.1 · Sigue lección 4.2

LECCIÓN 4.2· \~2,5 horas · Sub-módulo 4

## Self-RAG · _auto-evaluación de retrieval y generación_

El paper Self-RAG de Asai et al. 2023\. Adaptive retrieval (el modelo decide cuándo recuperar), reflection tokens (IsRel, IsSup, IsUse) para evaluar relevancia, soporte factual y utilidad. Implementación práctica con prompting sobre LLMs generales sin fine-tuning.

Lectura · 50 min Ejemplos · 40 min Ejercicio · 60 min 

4.2.1Reflection tokens y adaptive retrieval

#### Al final de esta lección sabrás:

* Explicar las ideas centrales de Self-RAG y en qué se diferencia de CRAG.
* Implementar los conceptos clave (adaptive retrieval, evaluación de IsRel, IsSup, IsUse) con prompting sobre LLMs generales, sin fine-tuning.
* Construir un flujo Self-RAG simplificado con LangGraph.
* Comparar Self-RAG con CRAG y con Agentic RAG estructurado.
* Decidir cuándo cada enfoque encaja mejor en un proyecto real.

Las ideas centrales de Self-RAG

El paper de Asai et al. (NeurIPS 2023) propone un sistema RAG donde el propio LLM se autoevalúa en varios puntos. La idea central: en lugar de recuperar siempre y generar respuesta basada en lo recuperado, el modelo decide en cada paso si necesita recuperar, valora si los chunks recuperados son relevantes, y verifica si su propia respuesta está realmente apoyada por los chunks.

El paper introduce «reflection tokens» especiales que el modelo emite durante la generación:

* **\[Retrieve\]**. Decisión adaptativa: «¿necesito recuperar para responder esto?» Valores: _yes_, _no_, _continue_ (seguir generando con lo que ya tengo).
* **\[IsRel\]**. Relevancia del chunk recuperado: _relevant_ o _irrelevant_.
* **\[IsSup\]**. Soporte factual de la respuesta generada: _fully supported_, _partially supported_, _no support_.
* **\[IsUse\]**. Utilidad de la respuesta final, en escala 1-5.

En el paper original, el LLM se fine-tunea para emitir estos tokens de forma natural. En la práctica, la mayoría de implementaciones de la comunidad no hace fine-tuning: usa un LLM general (Claude, GPT) y le pide que evalúe cada paso con prompts dedicados. Pierdes algo de elegancia (más llamadas LLM en vez de un solo paso integrado) pero ganas portabilidad (cualquier modelo sirve) y simplicidad.

Self-RAG vs CRAG · diferencias clave 

#### Cuándo cada uno encaja mejor

Ambos añaden capas de auto-corrección sobre RAG estático, pero con énfasis distintos:

* **CRAG** evalúa principalmente el _retrieval_ y activa fallback a web search cuando falla. Su pieza estrella es la búsqueda externa como red de seguridad.
* **Self-RAG** evalúa retrieval y también la _respuesta generada_ (¿está apoyada por los chunks? ¿es útil?). Su pieza estrella es la verificación factual sobre el output, no solo el input.

Self-RAG es más completo conceptualmente: no solo «¿tengo información suficiente?» sino también «¿estoy usándola bien?». Es más complejo de implementar y más caro (varios LLM calls por query). CRAG es más simple y suele bastar para muchos casos.

En la práctica profesional moderna se ven combinaciones: CRAG para el fallback web, ideas de Self-RAG (verificación de soporte factual) para reducir hallucinations. No tienes que elegir uno; toma lo útil de cada uno según tu caso.

Adaptive retrieval · ¿realmente necesito recuperar?

Una de las ideas más útiles y portables de Self-RAG es el «adaptive retrieval»: antes de recuperar, evalúa si hace falta. Muchas queries no requieren contexto externo (saludos, preguntas generales, cálculos, queries que el LLM puede responder con su conocimiento de entrenamiento).

Ejemplo · clasificador adaptive de retrieval 

#### Decidir retrieve / no\_retrieve por query

from langchain\_core.pydantic\_v1 import BaseModel, Field from typing import Literal class AdaptiveDecision(BaseModel): decision: Literal\["retrieve", "no\_retrieve"\] = Field( description="Si la pregunta requiere recuperar información del corpus" ) reason: str = Field(description="Justificación breve") adaptive\_prompt = ChatPromptTemplate.from\_template("""Decide si esta pregunta requiere consultar la documentación interna o si puede responderse directamente sin retrieval. - "retrieve": la pregunta es sobre productos, políticas, procesos o cualquier información específica de la empresa. - "no\_retrieve": saludos, preguntas generales no específicas, cálculos puros, preguntas conversacionales sin requerir hechos concretos del corpus. Pregunta: {question}""") adaptive\_decider = adaptive\_prompt | model.with\_structured\_output(AdaptiveDecision) def smart\_answer(question: str): decision = adaptive\_decider.invoke({"question": question}) print(f"Decisión: {decision.decision} · {decision.reason}") if decision.decision == "no\_retrieve": # Responder directamente sin RAG return llm.invoke(question).content else: # RAG normal docs = retrieve\_and\_rerank(question, k\_retrieval=20, k\_final=5) context = "\\n\\n".join(\[d.page\_content for d in docs\]) return llm.invoke(prompt.format(question=question, context=context)).content print(smart\_answer("Hola, ¿cómo estás?")) # Decisión: no\_retrieve # "¡Hola! Estoy bien, ¿en qué puedo ayudarte?" print(smart\_answer("¿Cuál es nuestra política de gastos de viaje?")) # Decisión: retrieve # \[respuesta con info del corpus\]

Beneficio claro: queries que no necesitan retrieval no consumen embeddings ni mete contexto ruidoso al LLM. Beneficio sutil: el sistema responde más naturalmente a queries conversacionales («hola», «gracias», «explícame algo más») sin el sesgo de querer apoyarse en un corpus que no tiene esa información.

Verificación de soporte factual · IsSup

Tras generar una respuesta apoyada en chunks recuperados, ¿está realmente la respuesta soportada por esos chunks? Verificarlo permite detectar hallucinations.

Ejemplo · evaluador de soporte factual 

#### Verificar la respuesta contra el contexto

class SupportGrade(BaseModel): support: Literal\["fully\_supported", "partially\_supported", "not\_supported"\] = Field( description="Grado en que la respuesta está apoyada por el contexto" ) unsupported\_claims: List\[str\] = Field( description="Lista de afirmaciones de la respuesta no presentes en el contexto", default\_factory=list, ) support\_prompt = ChatPromptTemplate.from\_template("""Evalúa si esta respuesta está apoyada por el contexto proporcionado. - "fully\_supported": todas las afirmaciones de la respuesta están claramente en el contexto. - "partially\_supported": algunas están en el contexto, otras no. - "not\_supported": ninguna o muy pocas afirmaciones están en el contexto. Lista también las afirmaciones específicas de la respuesta que NO están en el contexto. Contexto: {context} Respuesta a evaluar: {answer}""") support\_evaluator = support\_prompt | model.with\_structured\_output(SupportGrade) # Uso tras una generación normal question = "¿Cuáles son los requisitos para acceso remoto?" docs = retrieve\_and\_rerank(question, k\_retrieval=20, k\_final=5) context = "\\n\\n".join(\[d.page\_content for d in docs\]) answer = llm.invoke(prompt.format(question=question, context=context)).content # Verificar soporte support\_result = support\_evaluator.invoke({"context": context, "answer": answer}) print(f"Soporte: {support\_result.support}") if support\_result.unsupported\_claims: print("Afirmaciones no soportadas:") for claim in support\_result.unsupported\_claims: print(f"- {claim}") # Decidir si confiar en la respuesta o regenerar if support\_result.support == "not\_supported": # Regenerar con un prompt más estricto, o devolver «no tengo info suficiente» pass

Esto es enormemente útil en escenarios serios (legal, médico, financiero) donde las hallucinations son inaceptables. Pagas con una llamada LLM extra por respuesta, pero ganas verificabilidad. Para mostrar al usuario, puedes incluso devolver «esta respuesta tiene _fully supported_ \= sí» como sello de confianza.

Self-RAG simplificado con LangGraph

Combinando los elementos anteriores, podemos construir un Self-RAG simplificado con tres evaluadores: adaptive (decidir si recuperar), relevance (evaluar chunks), support (verificar la respuesta).

Ejemplo · grafo Self-RAG simplificado 

#### Tres puntos de auto-evaluación

from langgraph.graph import StateGraph, END from typing import TypedDict, List, Optional class SelfRAGState(TypedDict): question: str needs\_retrieval: Optional\[bool\] documents: List\[str\] answer: str support: Optional\[str\] iterations: int def decide\_retrieval(state): decision = adaptive\_decider.invoke({"question": state\["question"\]}) return {"needs\_retrieval": decision.decision == "retrieve"} def retrieve\_step(state): if not state\["needs\_retrieval"\]: return {"documents": \[\]} docs = retrieve\_and\_rerank(state\["question"\], k\_retrieval=20, k\_final=5) # Filtramos chunks por relevancia individual (IsRel) relevant\_docs = \[\] for d in docs: is\_rel = evaluator.invoke({"question": state\["question"\], "context": d.page\_content}) if is\_rel.grade == "correct": relevant\_docs.append(d.page\_content) return {"documents": relevant\_docs} def generate\_step(state): if not state\["documents"\]: # Sin contexto · responder con conocimiento del modelo o pedir info answer = llm.invoke(state\["question"\]).content else: context = "\\n\\n".join(state\["documents"\]) answer = llm.invoke(prompt.format(question=state\["question"\], context=context)).content return {"answer": answer, "iterations": state\["iterations"\] + 1} def verify\_support(state): if not state\["documents"\]: return {"support": "no\_context"} context = "\\n\\n".join(state\["documents"\]) result = support\_evaluator.invoke({"context": context, "answer": state\["answer"\]}) return {"support": result.support} def should\_regenerate(state): # Si la respuesta no está soportada y tenemos contexto, regenerar (máx 2 intentos) if state\["support"\] == "not\_supported" and state\["iterations"\] < 2: return "generate" return "end" # Construir grafo graph = StateGraph(SelfRAGState) graph.add\_node("decide", decide\_retrieval) graph.add\_node("retrieve", retrieve\_step) graph.add\_node("generate", generate\_step) graph.add\_node("verify", verify\_support) graph.set\_entry\_point("decide") graph.add\_edge("decide", "retrieve") graph.add\_edge("retrieve", "generate") graph.add\_edge("generate", "verify") graph.add\_conditional\_edges("verify", should\_regenerate, { "generate": "generate", "end": END, }) self\_rag\_app = graph.compile() # Uso result = self\_rag\_app.invoke({"question": "¿Cómo solicito vacaciones?", "iterations": 0}) print(f"Respuesta: {result\['answer'\]}") print(f"Soporte: {result\['support'\]}")

Este sistema es una simplificación pedagógica del paper original. En producción, conviene ajustar: número máximo de iteraciones de regeneración (para no loopear infinitamente), forma de combinar el feedback de soporte en el siguiente intento (con un prompt distinto que indique qué falló), métricas para evaluar si el sistema mejora respecto a versiones más simples.

¿Vale la pena toda esta complejidad? 

#### El honest assessment de Self-RAG

Self-RAG es elegante y resuelve problemas reales pero cada query puede acabar requiriendo 4-6 llamadas LLM:

* 1 para adaptive decision.
* 5 para evaluar relevancia de cada chunk (si recuperamos 5).
* 1 para generar respuesta.
* 1 para verificar soporte.
* +1-2 para regenerar si no está soportada.

Coste: \~8 llamadas LLM por pregunta en lugar de 1\. Latencia: 5-15 segundos en lugar de 1-3\. Para chatbots interactivos, demasiado. Para casos donde calidad importa más que velocidad (asistentes técnicos donde una respuesta incorrecta tiene coste real), las cifras se justifican.

Patrones de uso pragmáticos. **Tier 1**: RAG simple con buen prompt («basado únicamente en el contexto...»). Para 80% de queries esto basta. **Tier 2**: aplicar verificación de soporte solo si la respuesta va a usarse en contexto crítico (la API key tiene un flag de criticidad). **Tier 3**: Self-RAG completo con regeneración solo en casos donde se requiera máxima fiabilidad.

#### Ejercicio 4.2 · Self-RAG simplificado sobre tu corpus

Tiempo estimado · 60-75 minutos 

Vas a implementar las ideas clave de Self-RAG sobre tu pipeline. No fine-tunes nada; usa LLMs generales como evaluadores.

1. **Implementa adaptive retrieval**. Construye el clasificador binario (retrieve / no\_retrieve) según el ejemplo. Prueba con 10 queries variadas (algunas requieren docs, otras no).
2. **Mide impacto del adaptive retrieval**. ¿Cuántas queries evitas hacer retrieval sin perder calidad de respuesta? Esto reduce coste y mejora UX.
3. **Implementa filtro de relevancia por chunk** (IsRel). Para cada chunk recuperado, un evaluador binario decide si es relevante. Solo los relevantes pasan al LLM final.
4. **Compara con tu hybrid+rerank de SM3**. ¿El filtro de relevancia mejora o se vuelve redundante con el reranker? Mide.
5. **Implementa verificación de soporte** (IsSup). Tras generar respuesta, evalúa si está soportada. Registra el grado de soporte para cada query.
6. **Implementa regeneración condicional**. Si soporte es _not\_supported_, regenera con un prompt más estricto que mencione las afirmaciones no soportadas detectadas.
7. **Construye el grafo Self-RAG con LangGraph** integrando los tres pasos.
8. **Diseña queries de evaluación** que mezclen:  
   * Queries con respuesta clara en el corpus.  
   * Queries que tu LLM responde tendiendo a alucinar (preguntas específicas tipo «¿cuántos clientes tiene la empresa?» donde el corpus tal vez no dice exactamente).  
   * Queries fuera del corpus.
9. **Mide**:  
   * Tasa de hallucinations detectadas (cuántas respuestas marcó como not\_supported).  
   * Latencia media y nº de llamadas LLM por query.  
   * Calidad subjetiva de respuestas finales.
10. **Bonus 1** · combinar con CRAG. Si soporte es bajo y tienes web search, activa fallback a Tavily. Es la combinación más robusta.
11. **Bonus 2** · UI de confianza. Para cada respuesta, devuelve un campo extra _confidence_ (high/medium/low) basado en el resultado de IsSup. Útil para que la UI muestre un indicador visual al usuario.

Self-RAG es la culminación de las técnicas de RAG corregido. Tras este ejercicio tienes prácticamente todas las herramientas del estado del arte 2026\. La siguiente lección entra en cómo medir cuantitativamente todo este sistema con RAGAS, y la última integra todo en el proyecto final.

Preguntas frecuentes 

¿Existe un modelo Self-RAG fine-tuned ya disponible?

Sí, el paper original publicó modelos Self-RAG-7B y Self-RAG-13B basados en Llama 2 (en HuggingFace como _selfrag/selfrag\_llama2\_7b_). Funcionan pero son de 2023 y los LLMs generales modernos (Claude 3.5/4, GPT-4o) con buen prompting suelen rendir mejor que esos modelos especializados. Para producción 2026, recomiendo el enfoque sin fine-tuning con un buen LLM general.

¿Qué modelo usar como evaluador para minimizar coste?

Para evaluadores (adaptive, relevance, support), modelos pequeños y baratos son suficientes: Claude Haiku 3.5, Gemini Flash, GPT-4o-mini. Las tareas de clasificación binaria o ternaria no requieren modelos grandes. Reserva el modelo grande para la generación final donde la calidad importa. Esto reduce el coste extra de Self-RAG significativamente.

¿Cómo evito que el verificador de soporte sea demasiado estricto?

Calibrando el prompt. Si tu evaluador rechaza el 90% de respuestas como «not\_supported», está demasiado estricto: probablemente penaliza respuestas válidas donde el LLM ha sintetizado o inferido razonablemente desde el contexto. Ajusta el prompt para distinguir «no presente literalmente» (puede ser válido) de «contradice o inventa» (eso sí es problema). Itera con casos reales.

¿Self-RAG resuelve definitivamente las hallucinations?

No, las reduce significativamente pero no las elimina. El verificador es a su vez un LLM falible: a veces certifica como «supported» una respuesta que en realidad no lo está. La capa de verificación atrapa muchas hallucinations pero no todas. Para escenarios donde 0% hallucinations es requisito, ningún sistema LLM puro lo garantiza; necesitas humano en el loop (HITL) o restricciones más fuertes (respuestas plantilla con campos del corpus rellenados).

Recursos para profundizar 

#### Self-RAG y auto-corrección

* **Self-RAG paper · Asai et al. 2023**. La referencia original. arxiv.org/abs/2310.11511
* **Self-RAG models · HuggingFace**. Modelos fine-tuned publicados por los autores. huggingface.co/selfrag
* **LangGraph · Self-RAG tutorial**. Notebook completo. langchain-ai.github.io/langgraph/tutorials/rag/langgraph\_self\_rag
* **LlamaIndex · Self-RAG pack**. Implementación pre-armada. llamahub.ai/l/llama\_packs-self\_rag

Fin lección 4.2 · Sigue lección 4.3

LECCIÓN 4.3· \~2 horas · Sub-módulo 4

## Evaluación de sistemas RAG · _RAGAS y métricas estándar_

Cómo medir cuantitativamente la calidad de un pipeline RAG. Métricas clave: faithfulness, answer\_relevancy, context\_precision, context\_recall. RAGAS como framework open-source de referencia. Generación de test sets sintéticos. DeepEval como alternativa. Ground truth en proyectos reales.

Lectura · 40 min Ejemplos · 30 min Ejercicio · 50 min 

4.3.1Medir calidad sin engañarse

#### Al final de esta lección sabrás:

* Explicar las cuatro métricas RAGAS fundamentales y qué dimensión de calidad mide cada una.
* Generar un test set sintético sobre tu corpus para evaluar tu pipeline.
* Ejecutar RAGAS sobre tu sistema RAG y leer los resultados con criterio.
* Conocer DeepEval como alternativa y elegir entre ambos.
* Diseñar un plan de evaluación realista que combine métricas automáticas con revisión humana.

Por qué evaluar es la pieza más infravalorada

Hasta ahora has construido sistemas RAG cada vez más sofisticados pero la pregunta clave es: **¿cómo sabes si la versión avanzada es realmente mejor que la naive?** Sin medición rigurosa, las decisiones técnicas se basan en impresiones («me parece que mejora») que están sesgadas por confirmation bias y por el ruido de probar 5 queries casuales.

Los equipos serios de AI Engineering miden todo el sistema con métricas reproducibles antes de promocionarlo a producción. Sin esa disciplina, optimizar RAG es a ciegas: cambias un parámetro, te parece que va mejor, despliegas, en producción resulta peor. La habilidad de evaluar bien diferencia a un junior bueno de uno excelente.

RAGAS · las cuatro métricas fundamentales

RAGAS (Retrieval-Augmented Generation Assessment) es el framework open-source más usado para evaluar pipelines RAG. Es Apache 2.0, mantenido por la comunidad y bien integrado con LangChain, LlamaIndex y Hugging Face Datasets. Define varias métricas; las cuatro fundamentales son:

* **Faithfulness**. Mide si la respuesta generada está apoyada por el contexto recuperado. ¿El LLM inventa? Valor entre 0 y 1\. Lo más cercano a 1 es ideal. Equivale conceptualmente al «IsSup» de Self-RAG.
* **Answer Relevancy**. Mide si la respuesta es relevante a la pregunta, independientemente de su corrección. Detecta respuestas vagas, evasivas o que cambian de tema.
* **Context Precision**. De los chunks recuperados, ¿qué proporción es realmente relevante para la pregunta? Mide ruido en el retrieval.
* **Context Recall**. De toda la información necesaria para responder, ¿qué proporción está en los chunks recuperados? Requiere ground truth (respuesta canónica). Mide qué información falta.

Las dos primeras (faithfulness, answer\_relevancy) se calculan solo con la query, la respuesta y el contexto. Las dos siguientes (context\_precision, context\_recall) requieren una respuesta de referencia (ground truth) para comparar. RAGAS usa un LLM como juez para todas ellas; por tanto, las métricas son aproximaciones útiles pero no perfectas.

Ejemplo · RAGAS sobre tu pipeline 

#### De query y answer a métricas cuantitativas

pip install ragas datasets from ragas import evaluate from ragas.metrics import faithfulness, answer\_relevancy, context\_precision, context\_recall from datasets import Dataset # Preparas un dataset con tus queries y la salida de tu pipeline data = { "question": \[ "¿Cómo configuro SSH en Ubuntu 24.04?", "¿Cuáles son los requisitos de RAM mínimos?", # ... \], "answer": \[ "Para configurar SSH en Ubuntu 24.04, primero instala openssh-server con sudo apt install openssh-server...", "El sistema requiere mínimo 4 GB de RAM, recomendado 8 GB para producción.", # ... \], "contexts": \[ \["chunk 1 sobre SSH...", "chunk 2 sobre Ubuntu...", "chunk 3..."\], \["chunk con requisitos hardware...", "chunk con specs..."\], # ... \], "ground\_truth": \[ "SSH se configura instalando openssh-server con apt, activando el servicio con systemctl enable ssh y configurando /etc/ssh/sshd\_config.", "Requisitos mínimos: 4 GB RAM, 20 GB disco. Recomendados: 8 GB RAM.", # ... \], } dataset = Dataset.from\_dict(data) # Evaluar (usa OpenAI por defecto como juez, configurable) results = evaluate( dataset, metrics=\[faithfulness, answer\_relevancy, context\_precision, context\_recall\], ) print(results) # {'faithfulness': 0.85, 'answer\_relevancy': 0.92, 'context\_precision': 0.78, 'context\_recall': 0.81} # Por query individual df = results.to\_pandas() print(df\[\["question", "faithfulness", "answer\_relevancy"\]\])

RAGAS usa por defecto GPT como LLM juez (configurable). Cada métrica implica llamadas al juez: evaluar 50 queries puede costar entre 0,10 y 0,50 USD según las métricas activas. Es asumible para iteraciones de mejora y mucho más barato que evaluación humana.

Generación de test sets sintéticos

Para evaluar necesitas un test set: una lista de (pregunta, respuesta de referencia) sobre tu corpus. Crearlo a mano es trabajoso. RAGAS incluye un generador automático que crea queries diversas y las respuestas canónicas a partir de tu corpus.

Ejemplo · generar test set sintético con RAGAS 

#### De PDFs a queries con ground truth

from ragas.testset import TestsetGenerator from langchain\_openai import ChatOpenAI, OpenAIEmbeddings # Tus documentos cargados con LangChain loader = PyPDFLoader("manual.pdf") docs = loader.load() # Modelos · uno generador y uno crítico generator\_llm = ChatOpenAI(model="gpt-4o-mini") critic\_llm = ChatOpenAI(model="gpt-4o") embeddings = OpenAIEmbeddings() generator = TestsetGenerator.from\_langchain( generator\_llm=generator\_llm, critic\_llm=critic\_llm, embeddings=embeddings, ) # Genera 30 ejemplos con distribución de tipos testset = generator.generate\_with\_langchain\_docs( docs, testset\_size=30, distributions={ "simple": 0.5, # preguntas factuales directas "reasoning": 0.25, # requieren razonamiento "multi\_context": 0.25 # requieren combinar chunks }, ) df = testset.to\_pandas() print(df\[\["question", "ground\_truth"\]\].head()) df.to\_csv("test\_set.csv", index=False)

El test set generado tiene queries variadas: algunas directas, otras que requieren razonar entre varios pasajes, otras multi-contexto. Para producción seria, conviene **revisar manualmente** el test set sintético: descartar preguntas mal formuladas, completar respuestas truncadas, añadir preguntas que sabes son importantes para tu caso.

DeepEval · alternativa más amplia

DeepEval es otro framework open-source de evaluación, más ambicioso que RAGAS. Cubre RAG pero también evaluación general de LLMs (bias, toxicity, hallucination, summarization quality, etc.). Es más completo pero también más complejo.

Cuándo cada uno: **RAGAS** si tu foco es RAG puro y quieres rápido. **DeepEval** si haces evaluación más allá de RAG (chatbots generales, summarization, multi-turno) o quieres integración con CI/CD (tests automatizados que fallan si las métricas bajan tras un cambio).

Limitaciones de LLM-as-judge 

#### Por qué las métricas RAGAS no son verdad absoluta

RAGAS y DeepEval usan LLMs como jueces. Esto implica:

* **Variabilidad**. La misma evaluación ejecutada dos veces puede dar valores ligeramente distintos. Para resultados estables, ejecuta varias veces y promedia.
* **Sesgos del modelo juez**. Si el juez es GPT-4 y el generador también, hay riesgo de auto-validación. Conviene usar un juez de proveedor distinto al modelo bajo evaluación (Claude juzgando GPT, por ejemplo).
* **Coste**. Cada métrica implica llamadas LLM. Evaluar 200 queries con 4 métricas son 800+ llamadas LLM.
* **Brittle prompts**. Las métricas dependen de prompts internos del framework. Versiones distintas dan resultados distintos sobre los mismos datos. Fija la versión.

A pesar de las limitaciones, RAGAS y similares son **extremadamente útiles** en la práctica: te dan señales cuantitativas con bajo esfuerzo. La regla es no tomar valores absolutos como verdad sino usarlos para _comparar configuraciones_ (versión A vs versión B sobre el mismo test set). En relativo, las métricas son muy fiables.

Plan de evaluación realista en un proyecto

Una rutina razonable para proyectos profesionales:

1. **Fase 0 · test set inicial**. Genera 50-100 ejemplos sintéticos con RAGAS. Revisa manualmente y depura.
2. **Fase 1 · baseline naive RAG**. Ejecuta sobre el test set. Anota las cuatro métricas como punto de partida.
3. **Fase 2 · iteraciones**. Por cada cambio significativo (cambio de chunking, modelo de embeddings, hybrid search, reranking, CRAG, agentic), re-ejecuta y compara con baseline. Mantén versionado: ¿qué configuración produjo qué métricas?
4. **Fase 3 · revisión humana**. Métricas automáticas no detectan todo. Revisa manualmente 20-30 respuestas aleatorias del último resultado. ¿Las métricas reflejan la calidad real?
5. **Fase 4 · test set en producción**. Una vez en producción, recoge queries reales de usuarios y úsalas para construir un test set «real» que complemente el sintético.

Anti-patrón típico: optimizar contra el test set sin revisar manualmente. Puedes acabar con un sistema que saca buenas métricas pero responde mal en queries reales que no parecen al test set. La revisión humana periódica es indispensable.

#### Ejercicio 4.3 · evaluar tu pipeline con RAGAS

Tiempo estimado · 60-75 minutos 

Vas a medir cuantitativamente la calidad de las distintas versiones de tu RAG (naive, hybrid+rerank, CRAG, Self-RAG) sobre un test set generado de tu propio corpus.

1. **Instala RAGAS**: `pip install ragas datasets`.
2. **Genera test set sintético** sobre tu corpus de PDFs (el del SM3) con TestsetGenerator. 30-50 ejemplos. Distribución 50% simple, 25% reasoning, 25% multi\_context.
3. **Revisa manualmente el test set** generado. Descarta ejemplos mal formulados o con ground\_truth incorrecta. Idealmente añade 5-10 ejemplos tuyos sobre queries que sabes son importantes.
4. **Ejecuta tu pipeline naive RAG (de L3.1)** sobre cada query del test set. Guarda question, answer y contexts (chunks recuperados).
5. **Calcula RAGAS sobre los resultados de naive**. Anota las 4 métricas como baseline.
6. **Repite con tu pipeline hybrid+rerank (L3.3)**. Compara con baseline. ¿Mejora? ¿En qué métricas?
7. **Repite con tu CRAG (L3.4)** y con tu Self-RAG (L4.2). Compara.
8. **Construye una tabla comparativa**. Filas: las versiones. Columnas: faithfulness, answer\_relevancy, context\_precision, context\_recall, latencia media, coste medio por query.
9. **Analiza las diferencias**. ¿Cuál es la mejor versión en métricas? ¿Y considerando coste? ¿Hay metric trade-offs (mejora una pero empeora otra)?
10. **Revisión manual**. Toma 10 queries al azar y compara las respuestas de naive vs Self-RAG. ¿La preferencia humana coincide con las métricas RAGAS?
11. **Bonus 1 · ablation study**. Pruebas isolando cambios: solo cambiar chunk\_size (300 vs 500 vs 800), solo cambiar modelo de embeddings (sentence-transformers vs OpenAI), solo activar reranking. ¿Qué pieza aporta más?
12. **Bonus 2 · medir coste real**. Para cada versión, suma el coste real en USD del test set (embeddings + llamadas LLM + Cohere + Tavily). Construye gráfico coste vs faithfulness y elige punto óptimo.

Documenta este ejercicio especialmente bien. Una tabla comparativa con métricas + coste + latencia para varias arquitecturas RAG es exactamente lo que cualquier empresa pediría al diseñar un sistema serio. Si en tu proyecto final del 4.4 puedes incluir este análisis, demuestras un nivel profesional muy por encima de la media. Esa capacidad de razonar sobre trade-offs medidos vale enormemente en entrevistas y en el día a día como AI Engineer.

Preguntas frecuentes 

¿Las métricas RAGAS son comparables entre proyectos?

Solo comparables entre sí dentro del mismo proyecto y test set. No tiene sentido decir «el RAG de la empresa X tiene 0,85 de faithfulness y el mío 0,82, luego el suyo es mejor». Los valores absolutos dependen del corpus, queries, juez LLM, versión de RAGAS. La comparación útil es siempre _relativa_ entre versiones del mismo proyecto.

¿Vale la pena evaluar si no tengo ground truth?

Sí, parcialmente. Faithfulness y answer\_relevancy no requieren ground truth. Te dan señal sobre alucinaciones y relevancia de la respuesta. Context\_recall y context\_precision sí necesitan ground truth. En proyectos donde no tienes respuestas canónicas, focaliza en las dos primeras y complementa con revisión humana sobre context.

¿Cómo evalúo continuamente en producción (no solo en desarrollo)?

Pattern habitual: logs de queries reales con sampling. Cada N queries (1 de cada 100), guardas la interacción y la pasas por evaluación offline. Combinado con feedback explícito de usuarios (👍/👎) y métricas operacionales (latencia, errores). Herramientas tipo Langfuse, LangSmith, Phoenix de Arize ayudan con observabilidad continua.

¿Hay alternativas no basadas en LLM-as-judge?

Algunas. Métricas clásicas como BLEU, ROUGE, METEOR comparan respuesta con ground truth por similitud léxica; rápidas y baratas pero malas para RAG porque penalizan paráfrasis correctas. Métricas de embedding (BERTScore) son mejores pero limitadas. Para retrieval puro hay métricas IR clásicas (Recall@K, MRR, NDCG) que no requieren LLM y son muy útiles si tienes ground truth de qué chunks son relevantes. La combinación recomendada: métricas IR para retrieval + RAGAS/LLM-judge para generation.

Recursos para profundizar 

#### Evaluación de RAG

* **RAGAS · documentación oficial**. La referencia principal. docs.ragas.io
* **RAGAS paper**. Es et al. 2023 con la fundamentación de las métricas. arxiv.org/abs/2309.15217
* **DeepEval · GitHub**. Framework alternativo con cobertura amplia. github.com/confident-ai/deepeval
* **BEIR Benchmark**. Datasets estándar para retrieval IR. github.com/beir-cellar/beir
* **LangFuse · open-source observability**. Evaluación continua en producción. langfuse.com
* **Arize Phoenix · open-source**. Observabilidad y evaluación para LLM apps. github.com/Arize-ai/phoenix

Fin lección 4.3 · Sigue lección 4.4 · Proyecto final

LECCIÓN 4.4· \~3 horas · Sub-módulo 4

## Proyecto final · _chatbot empresarial sobre documentación privada_

Integrar todo lo aprendido en un sistema completo: ingesta de PDFs propios, hybrid search con Qdrant, reranking con Cohere, opcional CRAG con Tavily, agente con LangGraph, generación con LLM y evaluación con RAGAS. Tu portfolio técnico real para el mercado.

Definición · 30 min Implementación · 120-150 min Evaluación y documentación · 30-45 min 

4.4.1Tu sistema RAG completo, end-to-end

#### Al final del proyecto habrás:

* Construido un chatbot empresarial funcional sobre tu propio corpus de documentación privada.
* Integrado todas las técnicas del módulo: embeddings, base vectorial, hybrid search, reranking y al menos una técnica avanzada (CRAG, Self-RAG o Agentic RAG).
* Evaluado cuantitativamente el sistema con RAGAS sobre un test set propio.
* Documentado el proyecto en un README profesional con arquitectura, decisiones técnicas y métricas.
* Grabado un vídeo demo de 60-90 segundos para tu LinkedIn y tu portfolio.

Arquitectura propuesta · adaptable a tu caso

La arquitectura recomendada para el proyecto final integra todas las piezas del módulo. Es exactamente el patrón que verás en empresas serias construyendo asistentes empresariales con IA:

1. **Capa de ingesta**. Carga de PDFs (o el formato de tu corpus) con loaders robustos (PyPDFLoader, UnstructuredPDFLoader). Chunking con RecursiveCharacterTextSplitter, chunk\_size calibrado para tu tipo de documento.
2. **Capa de embedding**. Modelo elegido con criterio: text-embedding-3-small de OpenAI (default razonable), Cohere embed-multilingual-v3 (free tier), sentence-transformers (open-source), o BGE-M3 (open-source multilingüe top).
3. **Capa de almacenamiento**. Qdrant self-hosted en docker-compose (recomendado) o ChromaDB persistente local (más simple) o Pinecone serverless free (cloud sin gestionar).
4. **Capa de retrieval**. Hybrid search (dense + BM25 sparse) con RRF. Top-50 candidatos iniciales.
5. **Capa de reranking**. Cohere Rerank free tier o bge-reranker open-source. Reducir a top-5.
6. **Capa de corrección (opcional pero recomendada)**. CRAG con evaluador LLM + fallback a Tavily, o Self-RAG con verificación de soporte, o Agentic con tools.
7. **Capa de generación**. LLM final (Claude 3.5 Sonnet, GPT-4o o Gemini Pro) con prompt que exige groundedness y cita fuentes.
8. **Capa de evaluación**. Test set de 30-50 queries con RAGAS. Faithfulness, answer\_relevancy, context\_precision, context\_recall.
9. **Capa de UI (opcional)**. Streamlit, Gradio o integración con n8n del Módulo 3 como interfaz Slack/Telegram/web.

Elegir el dominio del proyecto 

#### Qué corpus funciona y qué corpus no

La elección del dominio determina la calidad final más que cualquier decisión técnica. Algunos patrones de dominios que funcionan bien:

* **Documentación técnica de un proyecto open-source**. Toma docs de Qdrant, n8n, FastAPI, React o el framework que conozcas. 50-200 PDFs o páginas web. Corpus cohesivo, queries naturales para alguien que aprende esa tecnología.
* **Normativa o legislación específica**. Una sección concreta del BOE (LOPD, normativa fiscal de autónomos, ley de teletrabajo). Queries naturales de profesionales que necesitan consultar.
* **Manuales de producto**. Manuales técnicos de un dispositivo, software o vehículo. Queries de servicio técnico o soporte.
* **Documentación interna de una organización ficticia**. Genera con un LLM una empresa ficticia con sus políticas, procesos, productos. 30-50 docs. Realista y reproducible.
* **Papers académicos de un área**. 50-100 papers sobre un tema (RAG, embeddings, NLP). Queries de investigación.
* **Tu propio corpus profesional o personal**. Si tienes acceso a documentación real anonimizada, es el caso más interesante.

Dominios que dan problemas: corpus de menos de 30 documentos (RAG aporta poco), corpus mezclados de varios temas sin cohesión (retrieval pierde precisión), corpus con PDFs escaneados sin OCR previo (texto irrecuperable), corpus con queries que requieren matemáticas complejas (LLM falla, no es problema de RAG).

Pasos detallados del proyecto

Plantilla · estructura del proyecto 

#### Cómo organizar el repositorio

proyecto-rag-final/ ├── README.md # documentación principal ├── .env.example # plantilla de variables de entorno ├── .gitignore # incluye .env, chroma\_db/, qdrant\_storage/ ├── requirements.txt # dependencias Python ├── docker-compose.yml # si usas Qdrant self-hosted ├── data/ │ └── raw\_docs/ # PDFs originales (no commits si son privados) ├── src/ │ ├── ingest.py # carga, chunking, indexación │ ├── retrieval.py # hybrid + rerank │ ├── chains.py # cadena RAG con LangGraph o LCEL │ ├── evaluation.py # ejecución RAGAS │ └── ui.py # Streamlit/Gradio si aplica ├── notebooks/ │ ├── 01\_explore\_corpus.ipynb │ ├── 02\_build\_pipeline.ipynb │ └── 03\_evaluate.ipynb ├── tests/ │ └── test\_set.csv # test set generado con RAGAS └── docs/ ├── architecture.md # diagrama y decisiones └── results.md # métricas, comparativas, hallazgos

Esta estructura es la que se espera en proyectos profesionales. Cuando un reclutador o un líder técnico abra tu repo, encontrar README claro, separación de código vs notebooks vs documentación, requirements limpio y tests es la diferencia entre «portfolio amateur» y «portfolio profesional».

Ejemplo · esqueleto del archivo principal 

#### src/chains.py con LangGraph

""" Pipeline RAG completo: hybrid retrieval + rerank + CRAG simplificado + generation con Claude. Integra todo lo aprendido en el módulo 4\. """ from typing import TypedDict, List from langgraph.graph import StateGraph, END from langchain\_core.prompts import ChatPromptTemplate from langchain\_anthropic import ChatAnthropic from src.retrieval import hybrid\_retrieve, rerank from src.evaluation\_models import retrieval\_evaluator, web\_search llm = ChatAnthropic(model="claude-3-5-sonnet-latest", temperature=0) ANSWER\_PROMPT = ChatPromptTemplate.from\_template("""Eres un asistente experto sobre documentación interna. Responde la pregunta del usuario basándote ÚNICAMENTE en el contexto. Si la respuesta no está, di "No tengo información para responder esto en mi base de conocimiento". Cita siempre las fuentes (documento + página) entre paréntesis tras cada afirmación. Contexto: {context} Pregunta: {question} Respuesta:""") class RAGState(TypedDict): question: str documents: list grade: str web\_results: list answer: str def retrieve(state): docs = hybrid\_retrieve(state\["question"\], k=30) return {"documents": rerank(state\["question"\], docs, top\_n=5)} def evaluate(state): grade = retrieval\_evaluator(state\["question"\], state\["documents"\]) return {"grade": grade} def web\_fallback(state): return {"web\_results": web\_search(state\["question"\])} def generate(state): if state\["grade"\] == "correct": ctx = "\\n\\n".join(d.page\_content + f"\\n\[{d.metadata}\]" for d in state\["documents"\]) elif state\["grade"\] == "ambiguous": ctx = "\\n\\n".join(\[d.page\_content for d in state\["documents"\]\] + state\["web\_results"\]) else: ctx = "\\n\\n".join(state\["web\_results"\]) answer = llm.invoke(ANSWER\_PROMPT.format(question=state\["question"\], context=ctx)).content return {"answer": answer} def route(state): return "generate" if state\["grade"\] == "correct" else "web\_fallback" graph = StateGraph(RAGState) graph.add\_node("retrieve", retrieve) graph.add\_node("evaluate", evaluate) graph.add\_node("web\_fallback", web\_fallback) graph.add\_node("generate", generate) graph.set\_entry\_point("retrieve") graph.add\_edge("retrieve", "evaluate") graph.add\_conditional\_edges("evaluate", route, {"generate": "generate", "web\_fallback": "web\_fallback"}) graph.add\_edge("web\_fallback", "generate") graph.add\_edge("generate", END) rag\_app = graph.compile() def answer(question: str) -> dict: """Punto de entrada principal del sistema.""" return rag\_app.invoke({"question": question, "documents": \[\], "web\_results": \[\]})

Esto es código de producción real, no un toy example. Aísla concerns (ingesta en un módulo, retrieval en otro, chain en otro). Tipa estados. Compila el grafo una sola vez al import. Las decisiones de diseño aquí son las que separan código de aprendizaje de código profesional.

Criterios de calidad esperables

Para que el proyecto sirva como portfolio técnico defensible, estos son los criterios mínimos que debería cumplir:

* **Corpus real y suficiente**. Mínimo 50 documentos / 200 páginas. Idealmente 100-300 documentos. Si menos, el sistema no muestra el valor real de RAG.
* **Pipeline completo, no un toy**. Hybrid + rerank al mínimo. Idealmente con una técnica avanzada del SM4 (CRAG, Self-RAG o Agentic).
* **Test set propio con métricas**. 30-50 queries, ejecución RAGAS, tabla comparativa con al menos dos versiones (naive vs avanzada) mostrando el delta.
* **Decisiones documentadas**. Por qué elegiste cada componente. «Usé Qdrant en docker-compose porque \[razón\]; usé text-embedding-3-small porque \[razón\]; chunk\_size de 500 porque \[razón medida\]».
* **README profesional**. Problema, solución, arquitectura (con diagrama si es posible), tech stack, instrucciones de instalación reproducibles, métricas y limitaciones conocidas.
* **Código limpio y reproducible**. Cualquiera con tu .env.example debería poder clonar y levantar el sistema. requirements.txt fijado en versiones.
* **Vídeo demo**. 60-90 segundos. Muestra el sistema funcionando, 2-3 queries representativas, mención de las técnicas usadas.

#### Ejercicio 4.4 · proyecto final

Tiempo estimado · 3 horas en clase + tiempo personal 

El proyecto final integra todo el módulo. Esperado: 3 horas de trabajo guiado en clase + 6-10 horas de trabajo personal para llegar a calidad portfolio. Calidad antes que cantidad de features.

1. **Define tu dominio**. Elige uno de los tipos sugeridos. Justifica en una frase por qué te interesa.
2. **Recolecta el corpus**. 50-200 documentos cohesivos. Organízalos en `data/raw_docs/`. Si son privados, no los commits; incluye un dataset de prueba pequeño.
3. **Construye el pipeline base**. Reutiliza el código que has ido construyendo en los ejercicios anteriores. Refactoriza para que esté limpio (no en notebooks dispersos).
4. **Integra al menos una técnica avanzada del SM4**. CRAG con Tavily fallback, o Self-RAG con verificación de soporte, o agente con varias tools. Justifica la elección.
5. **Genera test set y mide**. RAGAS sobre tu corpus. Mínimo 30 queries. Tabla comparativa naive vs final.
6. **Documenta**. README profesional con todas las secciones mencionadas. Diagrama de arquitectura (puedes hacerlo con draw.io, Excalidraw, Mermaid).
7. **Despliega (opcional pero muy recomendable)**. Streamlit Cloud (gratis) o despliegue en el VPS del Módulo 3\. Si has hecho M3 con VPS, integra con un workflow n8n que envíe queries por Slack y reciba respuestas. Es el portafolio combinado más fuerte que puedes tener.
8. **Vídeo demo**. 60-90 segundos. Loom, OBS, lo que prefieras. Sube a YouTube unlisted y enlaza en el README.
9. **Publica**. Repo en GitHub, post en LinkedIn anunciando el proyecto con el vídeo, perfil de LinkedIn con el proyecto en «Featured».
10. **Bonus 1 · multi-base**. Si tu dominio lo justifica, expón el corpus en varias colecciones (manuales, FAQs, contratos) con un agente que elige cuál consultar.
11. **Bonus 2 · UI con feedback**. Streamlit/Gradio con 👍/👎 que loguea el feedback en un archivo para análisis posterior.
12. **Bonus 3 · observabilidad**. Integra LangFuse o Phoenix de Arize para tracing de cada query. Útil para debug y como demo de madurez técnica.

El proyecto final no se evalúa por cantidad de features. Se evalúa por calidad y por capacidad de defender técnicamente las decisiones. Un sistema con hybrid + rerank + CRAG bien explicado y bien medido vale más que uno con 10 técnicas mal integradas. Si vas justo de tiempo, prioriza siempre: **corpus real → pipeline base sólido → métricas → README → vídeo**. Las técnicas avanzadas son la guinda; la base es la tarta.

Preguntas frecuentes 

¿Qué dominio es el «más impresionante» para portfolio?

No hay uno mejor que otro: el que mejor sepas defender técnicamente y que demuestre encaje con el tipo de puesto que buscas. Si aplicas a una startup B2B SaaS, un asistente sobre documentación técnica conecta. Si aplicas a una consultora, un asistente legal o normativo conecta. Si aplicas a una agencia de IA, demostrar dominio del stack completo importa más que el dominio del corpus. Elige algo que puedas defender 10 minutos en entrevista con detalle técnico.

¿Cuánto tiempo de trabajo personal extra es razonable?

Para portfolio profesional: 6-12 horas tras las 3 de clase. Para portfolio sobresaliente con despliegue, UI cuidada y bonus completos: 15-25 horas. Más allá, suele ser perfeccionismo improductivo. La diferencia clave es el README y el vídeo: dos cosas que cuestan poco tiempo y multiplican el impacto.

¿Y si voy muy justo de tiempo y no llego a todo?

Prioriza por este orden: (1) corpus real con 50+ docs, (2) pipeline hybrid + rerank funcional, (3) test set con métricas RAGAS, (4) README claro, (5) vídeo demo. Si llegas a estos 5, tienes proyecto válido. Las técnicas avanzadas del SM4 son deseables pero opcionales; mejor un naive RAG completo bien medido que un Self-RAG roto a medio implementar.

¿Cómo presento el proyecto en entrevistas técnicas?

Estructura de 3 minutos: **contexto** (qué problema resuelve, qué dominio), **decisiones técnicas** (por qué Qdrant y no Pinecone, por qué este modelo de embeddings, por qué reranking), **resultados** (las métricas RAGAS y el delta vs baseline), **limitaciones** (qué no funciona, qué harías con más tiempo). La capacidad de hablar de limitaciones con honestidad pesa mucho: muestra criterio profesional.

Recursos para profundizar 

#### Despliegue, portfolio y siguientes pasos

* **Streamlit Cloud**. Despliegue gratuito de apps Python con UI. Ideal para demo de tu RAG. streamlit.io/cloud
* **Gradio**. Alternativa para crear UIs rápidas para LLM apps. gradio.app
* **LangChain Cookbooks**. Plantillas de proyectos completos. github.com/langchain-ai/langchain/tree/master/cookbook
* **LlamaIndex Examples**. Repositorio con casos reales avanzados. github.com/run-llama/llama\_index/tree/main/docs/examples
* **Awesome RAG Resources**. Lista curada de papers y proyectos. github.com/frutik/Awesome-RAG
* **Loom · grabación de vídeo**. Para tu vídeo demo. Free tier 25 vídeos. loom.com

Cierre del módulo 4

## Lo que ya _sabes hacer_

**Has llegado al estado del arte real de los sistemas RAG empresariales en 2026.** Sabes generar embeddings con varios proveedores, almacenarlos en bases vectoriales open-source o cloud según el caso, recuperar con hybrid search combinando semántica y léxica, reordenar con cross-encoders para precisión final, autocorregir con CRAG cuando el retrieval falla, verificar con Self-RAG que las respuestas estén apoyadas en el contexto, orquestar con agentes que deciden cuándo recuperar y, lo más importante, evaluar cuantitativamente cada decisión técnica con RAGAS. Esa combinación es exactamente el perfil que el mercado de AI Engineering pide.

**Portfolio para el mercado.** Si has hecho el proyecto final con calidad, tienes un repositorio público en GitHub que demuestra capacidad de construir el corazón técnico de cualquier asistente empresarial sobre documentación privada. El vídeo demo en LinkedIn convierte ese repositorio en visibilidad para recruiters. La capacidad de defender las decisiones técnicas con métricas concretas en entrevista te separa del 80% de candidatos junior que «hicieron un tutorial de RAG». Esa diferencia es la que cierra ofertas.

**Siguientes pasos naturales.** Tras este módulo, las direcciones de profundización lógicas son: _LangGraph avanzado_ para sistemas multi-agente reales (planning, replanning, multi-actor), _fine-tuning de embeddings_ para dominios muy específicos donde los modelos generales pierden calidad, _multimodal RAG_ integrando imágenes y tablas (especialmente útil para PDFs técnicos con diagramas), _GraphRAG_ (la propuesta de Microsoft con grafos de conocimiento sobre los chunks), y _RAG en producción_ con observabilidad, caching, evaluación continua, gestión de versiones del índice. Cada uno de estos es un módulo completo en sí mismo; los abordarás en módulos posteriores del bootcamp o en proyectos profesionales reales.

**El momento del mercado.** RAG es, junto con automation, la habilidad más demandada del perfil AI Engineer junior en 2026\. Empresas medianas y grandes están construyendo sus chatbots empresariales sobre documentación privada; consultoras están implementando proyectos en cliente; startups están construyendo SaaS verticales basados precisamente en este stack. Sales con las técnicas que esa demanda necesita y con la disciplina profesional para defenderlas. Aprovéchalo.

Módulo 4 · Guía del alumno

## Índice _completo_

Navegación rápida por el módulo. **40 horas distribuidas en 4 sub-módulos y 14 lecciones**: embeddings y similitud semántica, bases vectoriales, RAG de naive a avanzado, y finalmente Agentic RAG, Self-RAG, evaluación y proyecto final integrador.

Inicio

1. —PortadaRAG y Bases Vectoriales2 min
2. 00Índice rápidoMapa de los 4 sub-módulos5 min
3. 00.1Cómo usar esta guíaPrerrequisitos, software, setup, filosofía15 min

Sub-módulo 1 · Embeddings y similitud semántica

1. SM1Introducción al sub-módulo10 h · 3 lecciones5 min
2. 1.1Qué son los embeddingsVectores, espacios semánticos, casos de uso\~2,5 h
3. 1.2Modelos de embeddingsOpenAI, Cohere, sentence-transformers, BGE\~3,5 h
4. 1.3Similitud semánticaCoseno, euclidiana, k-NN desde cero\~4 h

Sub-módulo 2 · Bases vectoriales

1. SM2Introducción al sub-módulo10 h · 3 lecciones5 min
2. 2.1Panorama de bases vectorialesChromaDB, Qdrant, Pinecone, pgvector\~2,5 h
3. 2.2ChromaDB localPrimera VDB persistente con metadatos\~3,5 h
4. 2.3Qdrant + PineconeSelf-hosted con Docker y cloud free\~4 h

Sub-módulo 3 · RAG de naive a avanzado

1. SM3Introducción al sub-módulo10 h · 4 lecciones5 min
2. 3.1Naive RAGPrimer pipeline end-to-end con LangChain\~3 h
3. 3.2Hybrid searchBM25 + dense con RRF\~3 h
4. 3.3RerankingCross-encoders, Cohere Rerank, bge-reranker\~2 h
5. 3.4Corrective RAGEvaluator + fallback web con Tavily\~2 h

Sub-módulo 4 · Agentic RAG, Self-RAG y proyecto final

1. SM4Introducción al sub-módulo10 h · 4 lecciones5 min
2. 4.1Agentic RAGReAct, tools, query decomposition\~2,5 h
3. 4.2Self-RAGAdaptive retrieval, IsRel, IsSup\~2,5 h
4. 4.3Evaluación con RAGASFaithfulness, relevancy, precision, recall\~2 h
5. 4.4Proyecto finalChatbot empresarial integrador\~3 h

Cierre

1. —Cierre del móduloPortfolio y siguientes pasos5 min

× 

NEOLAND Módulo 4 · **RAG & Bases Vectoriales** 

ÍNDICE 

↑ 