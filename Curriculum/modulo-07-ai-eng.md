# Módulo 7: Backend, Infraestructura y Producción

**Cuatro sub-módulos · ~40 horas aproximadas.** Este módulo cambia tu mentalidad: pasas de **construir prototipos que funcionan en un notebook** a **construir servicios que funcionan para usuarios reales**. Vas a montar APIs tipadas y rápidas, bases de datos, colas para trabajos pesados, autenticación, seguridad, y frontends. Al terminar tendrás un producto backend real desplegado con URL pública.

## Índice de sub-módulos

| Sub-módulo | Contenido |
|---|---|
| **SM0 · Setup del módulo** | Python, Docker, Node, PostgreSQL local, cuentas cloud, Supabase. |
| **SM1 · FastAPI + async + background jobs** | Bases del framework, streaming para LLMs, tareas en cola. |
| **SM2 · PostgreSQL + Vector DBs + Supabase** | Modelo de datos, pgvector, RAG en Postgres, Supabase como BaaS. |
| **SM3 · Frontends: Streamlit + Next.js** | Prototipos rápidos con Streamlit, productos con Next.js App Router. |
| **SM4 · Auth, seguridad, deployment** | OAuth2/JWT, CORS, rate limiting, deployment, proyecto final. |
| **Proyecto Final** | Backend integrador desplegado con URL pública y defensa oral. |

---

## Preparación del entorno · este módulo tiene muchas piezas

Este módulo introduce el mayor número de herramientas nuevas simultáneamente: **Node.js, PostgreSQL, Docker, Supabase, Redis y colas**. Dedicar el tiempo al setup ahora te ahorra **3-4 horas de fricción** distribuidas por el módulo.

- **Coste:** Módulo con el menor coste de APIs de IA porque el foco es la infra, no la generación. La mayor parte se puede cubrir con free tiers.
  - Gastos mínimos: OpenAI residual (2-3 USD para embeddings y ejemplos).
  - Railway Starter (opcional, 5 USD/mes) si quieres despliegue permanente.
- **Regla de oro:** Si todos los comandos ejecutan sin error, estás listo. Si falla alguno, dedícale tiempo antes de la primera sesión de FastAPI; empezar el módulo con un setup roto es la principal causa de frustración.

---

## SM1 · De un notebook a una API en producción

De un notebook que llama a un LLM a una API en producción. FastAPI se ha convertido en el estándar de facto para servir modelos y aplicaciones LLM. Vas a construir los cimientos: definir endpoints tipados con Pydantic, aprovechar async para I/O pesado, streamear respuestas para UX moderna, y encolar trabajos que tardan más de un request-response.

### Async, dependency injection, routers

Flask nació en 2010 con modelo síncrono (WSGI). FastAPI nació en 2018 con async nativo (ASGI). La diferencia importa mucho para IA: llamar a un LLM es una operación de red de varios segundos. En Flask síncrono, un worker queda bloqueado esperando. En FastAPI async, un solo worker atiende cientos de conexiones concurrentes esperando I/O.

Otras ventajas:

- Validación automática con Pydantic (sin tener que escribir `if isinstance` por todos lados).
- Documentación OpenAPI/Swagger generada automáticamente en `/docs`.
- Dependency injection integrado.

**El coste:** curva async más pronunciada, menos librerías legacy que en Flask, y tienes que pensar en concurrencia.

Arranca con:

```bash
uvicorn app.main:app --reload --port 8000
```

Y abre `http://localhost:8000/docs`. Ya tienes una UI de pruebas gratis. Prueba el endpoint desde el propio Swagger antes de escribir cualquier cliente.

#### Con Pydantic

Con Pydantic no necesitas escribir 30 líneas de validación imperativa: describes el shape de tus datos y la validación es gratis. Este ejemplo ya está protegiendo contra el usuario que envía prompt vacío, temperatura absurda, o intento básico de prompt injection.

#### Dependencies composables

Las dependencies son composables. Puedes anidar unas dentro de otras: `get_current_user` → `get_api_key` → `get_organization`. FastAPI resuelve el grafo de dependencias automáticamente. Compara con Flask, donde tendrías decoradores manuales o `@before_request` global.

#### Ejercicio 1.1 · Tu primera API

Monta una API FastAPI con validación de autenticación básica.

- Prueba desde `/docs`: sin header falla con 401, con header correcto responde.
- Enseña un curl equivalente en el README.

### Streaming: SSE, StreamingResponse, WebSockets

Latencia percibida vs latencia real. Un chat que empieza a mostrar tokens en 300ms y tarda 8s en terminar se siente rápido. Uno que espera 8s en silencio antes de mostrar todo se siente roto, aunque tarde lo mismo. ChatGPT popularizó la expectativa; sin streaming, tu interfaz parece antigua.

- **`StreamingResponse`** toma un async generator y envía cada `yield` como un chunk HTTP conforme está listo. El cliente lo lee con `response.iter_text()` en Python o `ReadableStream` en el navegador.
- **SSE (Server-Sent Events)** tiene formato estructurado (`event:`, `data:`), reconexión automática, y funciona sobre HTTP normal (no requiere upgrade a WebSocket, atraviesa proxies sin problemas). Es la elección natural para chat LLM.

#### Ejercicio 1.2 · Chat con streaming

Implementa un endpoint que use `StreamingResponse` para devolver tokens de LLM uno a uno.

### BackgroundTasks, ARQ, Celery + Redis

Regla de oro: si el trabajo tarda más que el timeout HTTP del cliente (típicamente 30s), no puede vivir en un request. Casos claros en IA: generación de imagen (5-30s), transcripción de audio largo, batch de embeddings, fine-tuning, procesar PDFs grandes.

El patrón siempre es el mismo:

1. Cliente pide → API encola trabajo y devuelve `job_id`.
2. Cliente hace polling o recibe notificación cuando termina.

**BackgroundTasks:** Sirve para fire-and-forget de segundos: logs, notificaciones, invalidar cache. Sus límites: mismo proceso, sin persistencia, sin reintentos. Si el server cae después del return, la tarea se pierde.

**Redis + Workers:** La API es un proceso. El worker es otro proceso. Redis es la cola de mensajes entre ambos. Ambos leen del mismo Redis. Escalas horizontalmente añadiendo más workers. Los workers reintentar tareas si fallan. Diseña tus tareas para que ejecutar dos veces produzca el mismo resultado. Usa `job_id` como clave en la operación: si el resultado ya existe, no lo repitas.

#### Ejercicio 1.3 · Cola de generación

Implementa un endpoint que encole una tarea larga en Redis y devuelva un `job_id`. Crea un worker separado que procese la cola.

---

## SM2 · La capa de datos: relacional, vectorial, gestionada

Ninguna aplicación seria vive sin persistencia. Vas a cubrir PostgreSQL como base sólida, pgvector como extensión que convierte Postgres en vector DB, alternativas dedicadas (Qdrant, Chroma), y Supabase como BaaS que ahorra 80% del trabajo de infra para prototipos y muchos productos reales.

### PostgreSQL

Modelo, sesiones async, migraciones ACID, transacciones, triggers, JSON nativo, y una lista larguísima de extensiones (pgvector para embeddings, PostGIS para geo, TimescaleDB para series temporales, pg_trgm para búsqueda textual). Escala vertical impresionante: instancias de 32 vCPU sirven aplicaciones de millones de usuarios. Para el 95% de aplicaciones que vas a construir, Postgres es la elección correcta y por defecto.

Usa la imagen `pgvector/pgvector` desde el principio para ahorrar reinstalar más tarde. El volume persiste datos entre reinicios; sin él pierdes todo al hacer `docker compose down`. Verifica con `psql -h localhost -U postgres -d ai_backend`.

### SQLAlchemy y N+1

El `selectinload` evita el problema clásico N+1: sin él, listar 20 conversations y acceder a sus messages hace 21 queries (1 + 20). Con él, se hacen 2 queries totales.

#### Ejercicio 2.1 · Persistir conversaciones

Configura Docker con PostgreSQL y pgvector. Crea un modelo SQLAlchemy para guardar conversaciones de chat.

### RAG en producción · elegir bien la base vectorial

Los embeddings son vectores de dimensión N (1536 para `text-embedding-3-small` de OpenAI, 384-768 para modelos open-source como bge o e5). Búsqueda semántica = encontrar los K vectores más cercanos a un query vector. La métrica más común para embeddings es la cosine similarity.

Complejidad: búsqueda exacta es O(N), lineal en el número de vectores. Para millones de vectores necesitas índices aproximados: HNSW (Hierarchical Navigable Small Worlds) es el estándar actual.

### Comparativa de Vector DBs

- **pgvector:** Si tu app ya usa Postgres, pgvector significa un solo servicio de base de datos. Sin sincronización entre DBs, sin dos backups, sin dos conexiones que gestionar. Para el 80% de aplicaciones RAG hasta 10 millones de documentos, pgvector es la elección racional.
- **Qdrant:** Escrito en Rust, muy rápido, filtros complejos combinables con búsqueda vectorial, cluster nativo. Elección natural cuando pasas de decenas de millones de vectores, o cuando quieres separar preocupaciones (Postgres para relacional, Qdrant para vectorial).
- **Chroma:** Diseñado como "SQLite para vectores": embebido, cero configuración. Ideal para POCs y notebooks. Escala limitada: no está pensado para producción a millones de vectores. Elección típica cuando prototipas rápido y ya migrarás.

Decisiones importantes: tamaño de chunk (400 tokens es compromiso razonable), overlap (para no cortar frases justo entre chunks), K en búsqueda (5 suficiente, 20 satura el contexto), reranker opcional (Cohere Rerank o modelos como bge-reranker mejoran precisión a coste de latencia).

#### Ejercicio 2.2 · RAG end-to-end

Implementa un pipeline completo: ingesta de texto, generación de embeddings, almacenamiento en pgvector, y búsqueda semántica.

### Auth + Postgres + Storage + RLS · Supabase

BaaS (Backend as a Service) open-source, self-hostable, licencia Apache 2.0. Ofrece sobre Postgres: API REST y GraphQL autogenerada desde tu schema, auth con JWT (email/password + OAuth providers), Storage tipo S3, Realtime (WebSockets), Edge Functions. Free tier generoso: 500MB Postgres, 1GB Storage, 50k usuarios auth.

Comparado con Firebase: Supabase usa Postgres real por debajo, no NoSQL propietario. Migras a Postgres gestionado (RDS, Cloud SQL) cuando quieras sin cambiar código.

Flujo completo: el frontend hace login con Supabase (email/password o OAuth Google/GitHub), recibe un JWT firmado. Ese JWT viaja en el header `Authorization: Bearer ...` a la API FastAPI. La API valida la firma con el secret Supabase y extrae el `user_id`.

#### Ejercicio 2.3 · Multi-tenant con Supabase

Implementa Row Level Security (RLS) para que cada usuario solo acceda a sus propios datos.

---

## SM3 · Dos frontends · uno para prototipar, otro para producto

Streamlit convierte un script Python en una app web funcional en 30 líneas: ideal para demos internas, dashboards y POCs. Next.js es el framework serio: React Server Components, App Router, streaming, despliegue de una app SaaS real. Construirás ambos y sabrás cuándo elegir cada uno.

### Streamlit: De script a app web en 30 líneas

Zero conocimiento de HTML/CSS/JS. Todo Python.

- **Costes:** menos control estético, arquitectura re-run confunde al principio, no apto para SaaS con miles de usuarios en producción.
- **Re-ejecución:** cada interacción del usuario re-ejecuta el script entero de arriba abajo. Es raro al principio, pero simplifica el modelo mental una vez que lo aceptas.
- **Estado persistente** en `st.session_state` (dict mágico).
- **Cache** con `@st.cache_data` para datos y `@st.cache_resource` para conexiones y modelos.
- **Deploy:** push del repo público a GitHub → conecta en share.streamlit.io → deploy automático. Secrets (API keys) desde el panel del proyecto.

Limitación: para apps privadas necesitas Streamlit en Snowflake o desplegar por tu cuenta con Docker en Railway/Fly.

### Next.js: React Server Components + Tailwind + shadcn/ui

App Router es el estándar desde Next.js 13. Todo el ecosistema moderno lo asume.

- **Server Components por defecto:** se renderizan en el server y no llegan JS al cliente.
- **Client Components** con `"use client"` al principio del archivo cuando necesites hooks, interactividad, event handlers.
- **Streaming SSR** con `<Suspense>`: partes de la página se envían al cliente conforme están listas.
- **Deploy:** conecta el repo GitHub a Vercel. Deploy automático a cada push. Preview deployments: cada PR genera una URL con esa versión.
- **Env vars:** las que empiezan por `NEXT_PUBLIC_` se exponen al cliente, el resto son solo server.

### Tipos compartidos

Cinco minutos de setup elimina una clase entera de bugs. Cambias un campo Pydantic en FastAPI, regeneras los tipos, y TypeScript te avisa dónde tienes que actualizar el frontend.

### Ejercicios

- **Ejercicio 3.1 · Playground de LLM:** prototipo rápido con Streamlit.
- **Ejercicio 3.2 · Landing + dashboard:** app seria con Next.js.
- **Ejercicio 3.3 · App integrada:** conecta el frontend con la API FastAPI.

---

## SM4 · Cerrar el ciclo · de local a producción con URL pública

Las piezas que separan un juguete de un producto real: autenticación robusta, capa de seguridad (CORS, rate limiting, secretos, OWASP), deployment reproducible con Docker, observabilidad mínima, y arranque del proyecto final integrador.

### Identidad segura sin reinventar la rueda

Autenticación (quién eres) vs autorización (qué puedes hacer). Auth es la puerta de entrada; authz decide qué habitaciones abres dentro. Confundirlos lleva a bugs difíciles.

### Higiene de seguridad · lo mínimo no negociable

- **CORS (Cross-Origin Resource Sharing):** es una política del navegador, no una feature de seguridad del server. Sin CORS configurado, un navegador bloquea peticiones desde otra-web.com a tu API. Configurarlo mal abre agujeros.
  - Antipatrón: `allow_origins=["*"]` combinado con `allow_credentials=True`. FastAPI lo rechaza, pero es habitual encontrarlo mal en tutoriales.
- **Rate Limiting:** una API pública con LLM sin rate limit es una factura infinita esperando. En proyectos serios, backend Redis para que los límites se compartan entre instancias.

#### Ejercicios 4.1 + 4.2 · Endurece tu API

Implementa CORS correcto y rate limiting con Redis.

### De local a URL pública

- **`.dockerignore` imprescindible:** `__pycache__/`, `.env`, `.git/`, `venv/`, `.pytest_cache/`. Sin él estás incluyendo basura en la imagen y filtrando `.env`.
- **Recomendación para el proyecto final:** FastAPI + Postgres + Redis en Railway; Next.js en Vercel. Free tier cubre todo, deploy automático desde GitHub, URLs públicas limpias.
- **Integración con GitHub:** Railway y Vercel tienen integración nativa: no necesitas Action de deploy, el push a `main` dispara deploy automático. Los tests sí deben pasar por Actions antes.

#### Ejercicio 4.3 · Deploy en producción

Despliega tu API y frontend con URLs públicas funcionales.

---

## Proyecto Final · Backend integrador desplegado

### Elegir alcance realista

Explica tu idea al docente en 5 minutos. Se valida alcance realista, se sugieren simplificaciones, se aprueba el arranque. Este scoping temprano te ahorra días de trabajo en dirección equivocada.

### Cinco ejemplos válidos de proyecto

Elige el que más te motive; la motivación es el mejor combustible para las últimas 15 horas de proyecto.

#### Producto de estilo "API de embeddings o resúmenes"

- Con usuarios, planes (free/pro), y límite de uso por plan.
- Registro, panel donde ven consumo, botón upgrade (mock).
- Backend cuenta requests y bloquea cuando se supera.
- Ejemplo de dominio: resumen de artículos, análisis de sentimientos, moderación de contenido.

#### Servicio que otros desarrolladores consumirían

Por ejemplo, API de transcripción de audio, o de OCR + estructuración.

- Emisión de API keys, tracking por request, panel con logs y consumo.
- Billing puede ser mock (mostrar cuánto habría facturado sin cobrar realmente).

#### Agente con acceso a herramientas

Búsqueda web, calculadora, calendario, alguna API interna.

- Streaming de respuestas paso a paso, historial persistente por usuario, feedback thumbs up/down para métricas de calidad.

#### "Chat con tus documentos" para una organización ficticia

- Upload de PDFs, ingesta con chunking + embeddings, chat que responde citando fuentes.
- Multi-usuario con RLS: cada usuario o equipo ve solo sus documentos.

#### Sistema de moderación de contenido

- Usuarios reportan contenido y moderadores lo revisan.
- El LLM da una primera pasada (clasificación + explicación), moderadores humanos ratifican o revierten.
- Roles: user, moderator, admin. Dashboard con cola de casos pendientes.

### Evaluación y defensa

#### Rúbrica de evaluación · 6 dimensiones

*Nota: La rúbrica específica de las 6 dimensiones no está detallada en el texto, pero se evalúa la integración completa del stack.*

### Preguntas típicas del tribunal · prepáralas

La defensa evalúa comprensión, no solo funcionalidad. Un alumno con menos features pero que explica bien sus decisiones puntúa más alto que uno con muchas features incapaz de justificarlas.

### Backend de IA · lo que te llevas

Empezaste el módulo con la capacidad de escribir notebooks que llaman a un LLM. Sales con la capacidad de convertir eso en un servicio backend real:

- API tipada y validada.
- Base de datos relacional y vectorial.
- Colas para trabajos pesados.
- Autenticación segura.
- Higiene de seguridad.
- Frontend funcional.
- URL pública.

La distancia entre "he hecho una demo" y "he desplegado un producto" se ha cerrado. Ese salto es el que te separa de la mayoría de quienes solo han hecho tutoriales de IA.
