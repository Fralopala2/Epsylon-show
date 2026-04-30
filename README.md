<p align="center">
  <img src="./assets/banner.png" alt="Epsylon Banner" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/Status-Complete-green?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-red?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/Billing-Paddle-00aeef?style=for-the-badge" alt="Billing">
  <img src="https://img.shields.io/badge/Built%20with-Tauri%20%2B%20Next.js%2016-24c8db?style=for-the-badge" alt="Built with">
</p>

---

# 🛸 Epsylon

**Epsylon** es el asistente definitivo impulsado por IA diseñado para revolucionar tu carrera profesional. Combina la potencia de la automatización en la búsqueda de empleo con la asistencia inteligente en tiempo real durante entrevistas técnicas, todo en una aplicación de escritorio discreta y potente.

---

## 🚀 Características Principales

### 🎤 Interview Copilot (Asistencia en Tiempo Real)
*   **Cursor Virtual:** Al activarlo desde Ajustes, el cursor real del sistema queda oculto en capturas de pantalla y grabaciones. Un cursor SVG renderizado en el frontend sigue el movimiento real del ratón, mostrando una posición que puede diferir de la real.
*   **Click-through Mode (Ghost):** En modo fantasma, el teleprompter mantiene click-through para no robar foco/clics durante la entrevista.
*   **Navegación de bloques en Ghost sin click:** Las sugerencias del teleprompter pueden recorrerse con hotkeys globales `←/→` incluso cuando la ventana está en click-through.
*   **Camuflaje de proceso en Windows:** Además del camuflaje de título en modo stealth (`"System Host Process"`), el build aplica metadatos Win32 (`FileDescription`, `ProductName`) al `.exe` para reducir exposición visual en Task Manager. Se aplica sobre el binario release de Tauri y sobre los `.exe` copiados a `release/local|cloud`.
*   **Detección de Plataforma:** Reconocimiento automático de Zoom, Teams y Google Meet para optimizar el contexto. 
*   **Teleprompter Remoto:** Visor con scroll automático sincronizado y controlable remotamente desde la ventana principal.
*   **Teleprompter visible en capturas (Windows):** Nuevo check en `Ajustes` para permitir o bloquear la aparición del teleprompter en screenshots/grabaciones de pantalla.
*   **Hotkeys Globales Configurables en UI:** Edita los atajos desde `Ajustes`, se aplican al instante sin rebuild y quedan persistidos para próximos arranques.
*   **Personalización del Copiloto (Inyección avanzada de contexto):** textarea en `Copiloto` que añade “background personal” (criterios, estilo, resumen propio) que el backend mezcla con los hits de KB/roles antes de generar sugerencias.
*   **Hotkeys de audio robustas:** Fallback de ejecución directa desde Tauri para captura/chunks incluso si el bus de eventos del renderer no responde.
*   **UI 100% en Español:** Etiquetas, mensajes, botones y estados unificados en un único idioma. 

### 🔍 Job Search Engine (Búsqueda Automatizada)
*   **Crawlers Multi-Fuente:** Rastreo en LinkedIn, Infojobs, WeWorkRemotely, DjangoJobs, Adzuna, TheirStack y más.
*   **Diagnóstico de Crawlers en tiempo real:** Tras cada búsqueda, la UI muestra un badge por fuente indicando cuántas ofertas encontró, si está mal configurada (⚠) o si falló (✗).
*   **Filtros Avanzados:** Filtra por salario, experiencia, ubicación y modalidad remota. El filtro de ubicación reconoce aliases internacionales (España↔Spain, Alemania↔Germany, etc.).
*   **Hasta 200 resultados por búsqueda:** Límite ampliado para aprovechar al máximo todas las fuentes activas simultáneamente.
*   **Gestión de Candidaturas:** Tracking local en SQLite (`Guardado`, `Aplicado`, `Entrevista`, `Rechazado`).
*   **Auto-Apply & Outreach:** Generación automática de cartas de presentación y correos de seguimiento personalizados.
*   **Carta de Presentación por Oferta:** Selección explícita de oferta guardada antes de generar la carta.
*   **Nota sobre fuentes:** Indeed y Glassdoor bloquean scraping público sin API key oficial. Las fuentes más fiables sin coste son LinkedIn, WeWorkRemotely, DjangoJobs y Adzuna (requiere key gratuita).

### 💳 Control de Costes API (portal TheirStack)
*   **Integración TheirStack en Modo Ahorro:** Activación manual desde UI para evitar consumo accidental.
*   **Tope por Consulta:** Máximo 5 resultados por búsqueda en TheirStack.
*   **Tope Diario Persistente:** Límite diario configurable de créditos TheirStack (por defecto: 20/día).
*   **Ventana Temporal Acotada:** Búsquedas TheirStack con antigüedad máxima configurable (`posted_at_max_age_days`).

### 💳 Billing y Membresías (Paddle)
*   **Modelo de Prueba (Trial) de 3 días:** Integración nativa de pruebas gratuitas en planes PRO y PREMIUM. El acceso se activa instantáneamente tras iniciar el trial en Paddle.
*   **Paddle Checkout v2:** Flujo de pago moderno integrado en la web (`apps/web`) utilizando el hook `usePaddle` y Price IDs específicos para cada plan.
*   **IDs de Producto (Paddle):** 
    *   PRO: `pri_01************`
    *   PREMIUM: `pri_01************`
    *   LIFETIME: `pri_01************`
*   **Webhook Endurecido:** Verificación de firma HMAC-SHA256 para cada evento de Paddle, garantizando que los datos de suscripción provienen únicamente del proveedor oficial.
*   **Idempotencia de Eventos:** Validación de `eventId` para evitar procesamientos duplicados de transacciones.
*   **Persistencia de Suscripción:** Mapeo completo de estados de Paddle (`trialing`, `active`, `past_due`, `canceled`) en la base de datos interna.
*   **Control de Descargas:** El backend bloquea el acceso al ejecutable si el usuario no tiene una suscripción válida (activa o en periodo de prueba).

### 🔐 Seguridad e Infraestructura
*   **Auth lista para cloud:** Registro, login, `me`, refresh token rotatorio y logout verificados contra la API desplegada.
*   **Superuser Bypass (Dev/Personal):** Sistema de acceso total mediante la variable de entorno `SUPERUSER_EMAILS`. Los emails listados obtienen rol `admin` y suscripción Premium automática.
*   **Infra free-tier validada:** Deploy operativo sobre Render + Neon + Upstash con smoke tests reales de health, auth y billing.

### 🌐 Landing Web Premium (Next.js)
*   **Carrusel Continuo de Portales de Empleo (Crawler Logos):** Un carrusel dinámico e infinito que muestra logos vectoriales de las fuentes más populares (LinkedIn, Infojobs, Indeed, etc.) con sus colores de marca originales.
*   **Consentimiento de Cookies Inteligente:** Banner de privacidad no intrusivo persistido mediante almacenamiento local (`localStorage`) para cumplimiento normativo óptimo.
*   **Rich Aesthetics (Diseño Inmersivo):** Transición fluida entre secciones sin cortes duros, iluminaciones ambientales con orbes difusos en tonos azul/índigo, y un diseño visualmente unificado.
*   **Cards de Contenido y Tablas Premium:** Tablas de comparación con bordes suavizados (`rounded-3xl`), resplandor trasero dinámico (`glow backdrop`) y tarjetas modulares de soporte con colores de contraste balanceados.
*   **Internacionalización & UX:** Traducción total al español y enrutado SPA optimizado mediante componentes `<Link>` nativos.
*   **Auth con Clerk Personalizado:** Registro e inicio de sesión integrados con Clerk. Interfaz de usuario adaptada a modo oscuro (menús y popovers con visibilidad corregida).
*   **Landing enfocada a Conversión:** Sección de precios actualizada con los límites reales (50 Auto-Applies en Pro, Ilimitado en Premium) y llamada a la acción directa para el Trial de 3 días.
*   **Logo e Identidad:** Restauración y preservación del logo original de Epsylon en toda la plataforma.

### 🧠 Inteligencia Avanzada
*   **OCR Inteligente con Auto-Sugerencia:** Soporte mixto `spa+eng` con carga de imágenes o pegado directo desde el portapapeles. Al detectar texto, el sistema dispara automáticamente la generación de sugerencias IA.
*   **TTS (Text-To-Speech):** Escucha las sugerencias de la IA a través de tus auriculares.
*   **Memoria de Entrevista por Rol y Nivel:** Base general común + memoria específica para Backend, Java, Spring Boot, Full Stack y niveles Mid / Mid-Adv.
*   **Base de Conocimiento Local (PDF/TXT):** Ingesta, búsqueda, listado, reindexado y borrado de documentos desde la app.
*   **Pestaña dedicada de KB:** La gestión de la base de conocimiento vive en una pestaña/sección separada (`Base de conocimiento`) con una interfaz optimizada que incluye filtrado en tiempo real y una vista compacta basada en tablas para documentos y resultados.
*   **Trazabilidad de contexto:** Las sugerencias pueden devolver `knowledgeHits` para ver qué fragmentos KB se usaron.
*   **Wizard BYOK de OpenRouter en Ajustes:** El usuario puede crear cuenta, generar su API key, verificarla y guardarla desde un flujo guiado de 3 pasos.
*   **Clave del usuario como preferente:** Si el usuario guarda su OpenRouter API key, se usa por defecto en sugerencias, cover letters y follow-up emails; si no existe, el backend usa la clave base del sistema.
*   **Analíticas:** Visualiza tu progreso con dashboards de búsqueda y éxito en entrevistas.

### ⚡ Rendimiento y Operación
*   **Arquitectura Modular:** Componentes críticos como el `TeleprompterView`, `useDiscreetMode` y utilidades de procesamiento han sido extraídos de la vista principal para mejorar la mantenibilidad y el rendimiento del renderizado.
*   **Compresión HTTP:** API Fastify con compresión global para respuestas grandes.
*   **Carga Diferida de OCR:** `tesseract.js` se carga solo cuando se usa OCR (mejor arranque de API).
*   **Índices en Persistencia Local:** SQLite para jobs + SQLite FTS5 para chunks KB + índice Q/A dedicado para recuperación más precisa.
*   **Análisis de Bundle Desktop:** Script para inspeccionar tamaño y composición del bundle de renderer.
*   **Observabilidad:** Logs estructurados ultra-rápidos con `pino` y visualización legible en desarrollo con `pino-pretty`.
*   **Documentación Interactiva:** Endpoints del backend auto-documentados vía Swagger UI (`/docs`).
*   **CI/CD Automatizado:** Pipeline en GitHub Actions configurado para compilar y publicar releases (Tauri y Backend) de forma inteligente (bajo demanda o por tags) ahorrando minutos de ejecución.

---

## 🖼️ Infografia del Proyecto

<details>
  <summary>Ver infografia del proyecto</summary>
  <br />
  <p align="center">
    <img src="./assets/infografia.png" alt="Infografia del proyecto Epsylon" width="100%">
  </p>
</details>

---

## 🛠️ Stack Tecnológico

Epsylon está construido sobre una arquitectura moderna, escalable y robusta:

| Capa | Tecnologías |
| :--- | :--- |
| **Desktop App** | Tauri, React, TypeScript, Vite |
| **Backend API** | Node.js, Fastify, Zod |
| **Persistencia** | SQLite (jobs + KB FTS5 + KB Q/A), PostgreSQL (objetivo/infra), Redis (cache opcional) |
| **IA / ML** | Groq (STT), OpenAI (GPT/Whisper/TTS fallback), Anthropic (Claude), Google (Gemini + Cloud TTS), OpenRouter, Tesseract.js, pdf-parse |
| **Tooling** | NPM Workspaces, Docker, GitHub Actions, Vitest, React Testing Library, Swagger |
| **Web pública** | Next.js (App Router), Clerk (Auth), Paddle (Billing), Vercel |

---

## 📂 Estructura del Proyecto

```text
Epsylon/
├── apps/
│   ├── api/          # Backend Fastify & Core AI Logic
│   ├── desktop/      # Tauri App & React Frontend
│   └── web/          # Landing y auth web (Next.js, Clerk)
├── packages/
│   └── shared/       # Shared Types, Schemas & Contracts
├── docs/             # Technical Documentation & Guides
├── assets/           # Media & Brand Assets
├── vercel.json       # Vercel: preset Next.js (rootDirectory se define en el proyecto en Vercel)
└── docker-compose.yml # Local Infrastructure Setup
```

### Aplicación web (`apps/web`)

- **Stack:** Next.js 16, Clerk (`@clerk/nextjs`, localización `esES`), rutas `/sign-in`, `/sign-up`, área privada `/app`.
- **Edge:** autenticación con Clerk en [`apps/web/src/proxy.ts`](apps/web/src/proxy.ts) (convención **proxy** de Next.js 16; antes `middleware`).
- **Despliegue:** proyecto Vercel con **Root Directory** `apps/web`. Dominio de ejemplo: `epsylon.pacoal.dev` (DNS en el proveedor donde estén los NS del dominio).
- **Variables:** ver [`apps/web/.env.example`](apps/web/.env.example) y la guía detallada en [`apps/web/README.md`](apps/web/README.md).

---

## 🏁 Inicio Rápido

### Requisitos Previos
*   **Node.js 20+** e **npm 10+**
*   **Python 3.11+** (para herramientas locales)
*   **FFmpeg** (opcional, para STT local)

### Instalación
1.  **Clonar y preparar el entorno:**
    ```bash
    npm install
    npm run env:setup
    ```
2.  **Configurar credenciales:**
    Edita el archivo `.env` con tus API Keys y conectores de empleo.

    Variables mínimas recomendadas:
    ```env
    # IA
    OPENROUTER_API_KEY=...
    GROQ_API_KEY=...
    GROQ_STT_MODEL=whisper-large-v3-turbo
    OPENAI_API_KEY=...
    OPENAI_STT_API_KEY=... # opcional, si quieres separar clave de STT
    GOOGLE_CLOUD_TTS_API_KEY=... # opcional para mejorar TTS frente a FreeTTS
    GOOGLE_CLOUD_TTS_VOICE=es-ES-Standard-A # opcional

    # Adzuna
    ADZUNA_APP_ID=...
    ADZUNA_APP_KEY=...
    ADZUNA_COUNTRY=es

    # Infojobs
    INFOJOBS_CLIENT_ID=...
    INFOJOBS_CLIENT_SECRET=...

    # TheirStack (modo ahorro)
    THEIRSTACK_API_KEY=...
    THEIRSTACK_COUNTRY_CODE=ES
    THEIRSTACK_POSTED_MAX_AGE_DAYS=7
    THEIRSTACK_DAILY_CREDIT_LIMIT=20

    # OCR / LLM fallbacks (opcional para desarrollo)
    MOCK_OCR=false
    MOCK_OPENAI=false
    LLM_FALLBACK_TO_MOCK=false
    STT_FALLBACK_TO_MOCK=false
    LOCAL_STT_ENABLED=true
    LOCAL_STT_WHISPER_CPP_BIN=C:\tools\whisper.cpp\Release\whisper-cli.exe
    LOCAL_STT_WHISPER_CPP_MODEL=C:\tools\whisper.cpp\models\ggml-base.bin
    LOCAL_STT_FFMPEG_BIN=ffmpeg
    ```

### Base de conocimiento (KB) en runtime
- La KB se guarda localmente en `apps/api/data/kb.sqlite3` (SQLite + FTS5 + índice `kb_qa`).
- En el build de cloud (Docker), la carpeta `apps/api/data/` se incluye en la imagen para que los documentos indexados localmente estén disponibles en el despliegue inicial. El archivo `kb.sqlite3` está trackeado en Git expresamente para este propósito (`jobs.sqlite3` permanece ignorado por ser datos de usuario).
- Desde la UI puedes:
  - importar PDF/TXT,
  - consultar KB manualmente,
  - listar documentos indexados,
  - reindexar o eliminar documentos.
- En KB y en el flujo de empleo, las vistas de datos se muestran con tablas compactas (mejor densidad, navegación y estados de error/vacío).
- La UI separa el trabajo por secciones (layout desktop): navegación principal en `sidebar` y acciones globales en `toolbar` superior, con `Copiloto`, `Base de conocimiento`, `Ofertas`, `Ajustes`.
- Puedes abrir directamente la pestaña KB usando query params:
  - `?tab=knowledge`
  - `?focus=knowledge`
- Endpoints principales:
  - `POST /knowledge-base/ingest`
  - `POST /knowledge-base/search`
  - `GET /knowledge-base/documents`
  - `POST /knowledge-base/documents/:id/reindex`
  - `DELETE /knowledge-base/documents/:id`
- Al reindexar (`/knowledge-base/documents/:id/reindex`) se regeneran:
  - chunks de texto (`kb_chunks`, `kb_chunks_fts`)
  - pares pregunta/respuesta (`kb_qa`) para respuestas directas más estables.

### Sugerencias en tiempo real (LLM + KB)
- El endpoint `POST /interview/assistant/suggest` soporta dos modos:
  1. **Modo normal (`preferLlm=false`)**: intenta `kb-qa-direct` -> `kb-direct` / `kb-structured` -> `kb-fallback` -> contexto/memoria/LLM.
  2. **Modo priorizar LLM (`preferLlm=true`)**: intenta LLM primero, con fallback robusto (Gemini->OpenRouter en 429, fallback local y KB filtrado si el LLM no responde).
- En la UI del Copiloto existe el toggle:
  - `Priorizar LLM (evitar atajos KB/reglas)`.
- Si el proveedor es `openrouter`, el Desktop puede enviar la key del usuario en header `X-OpenRouter-Api-Key`; si no existe, el backend usa `OPENROUTER_API_KEY`.
- En `Ajustes`, el wizard BYOK permite:
  - abrir signup de OpenRouter,
  - abrir la sección de API keys,
  - verificar la clave con `POST /llm/openrouter/verify`,
  - guardarla localmente para usarla por defecto en el arranque.
- Se aplican guards de calidad para evitar respuestas mezcladas, truncadas o basura:
  - limpieza de artefactos PDF (`-- x of y --`, bullets repetidos),
  - filtro por intención (ej: evitar cruzar pregunta SQL relacional con respuesta NoSQL),
  - descarte de respuestas rotas o incompletas,
  - bloqueo explícito de frases boilerplate de KB (ej. títulos de documento).
- Timeouts de sugerencias:
  - **Frontend:** timeout defensivo de 45000 ms.
  - **Backend:** `SUGGESTIONS_TIMEOUT_LLM_MS` (por defecto 45000 ms cuando `preferLlm=true`), `SUGGESTIONS_TIMEOUT_MS` (modo normal).
- Manejo de errores de proveedor:
  - Si Gemini devuelve `429` (quota/rate-limit), reintento automático con OpenRouter.
  - Si falla el LLM, se intenta fallback local/KB antes de devolver error final.
- La UI muestra badge de fuente:
  - `[KB]` (`kb-direct`, `kb-structured`, `kb-fallback`, `kb-qa-direct`)
  - `[AI]` (LLM `openrouter:*`, `openai:*`, `gemini:*`)
  - `[?]` (fuente no clasificada)
  - `[CTX]` (contexto/memoria/reglas)
  - `[!]` (timeout/error/mock)

### Formato de salida de sugerencias (anti-caos)
- El prompt del asistente está restringido para respuestas de entrevista en vivo:
  - sin tablas,
  - sin markdown pesado,
  - sin bloques de coaching largos,
  - 3 a 5 bullets técnicos, breves y accionables.
- Además, hay post-procesado de salida:
  - limpieza de markdown/tablas aunque el modelo las devuelva,
  - recorte de longitud por bullet,
  - eliminación de ruido estructural tipo STAR/plantillas extensas.
- El teleprompter normaliza la salida en un formato legible:
  - `Pregunta detectada: ...`
  - `Respuestas sugeridas: ...`
  - bullets cortos y escaneables.
- Incluye mejoras de lectura en vivo:
  - **Modo corto** (`C`) para truncar y simplificar bloques largos.
  - **Navegación por bloques** (`N/P` y `←/→`) para mostrar una respuesta cada vez.
  - Protección anti-navegación vacía: los atajos de bloques solo actúan cuando hay sugerencias estructuradas navegables.

### STT provider chain (entrevista -> texto)
- La transcripcion de `POST /interview/stt/transcribe` usa ahora:
  1. **Groq STT** (`GROQ_API_KEY`, modelo por defecto `whisper-large-v3-turbo`),
  2. **Whisper local** (`LOCAL_STT_ENABLED=true` + binario/modelo local),
  3. **OpenAI Whisper** como respaldo (`OPENAI_STT_API_KEY` o `OPENAI_API_KEY`).
- Variables clave:
  - `GROQ_API_KEY`
  - `GROQ_STT_MODEL` (opcional)
  - `LOCAL_STT_ENABLED`, `LOCAL_STT_WHISPER_CPP_BIN`, `LOCAL_STT_WHISPER_CPP_MODEL`, `LOCAL_STT_FFMPEG_BIN`
  - `OPENAI_STT_API_KEY` (backup)
- En la respuesta JSON, el campo `model` indica el proveedor real usado (`groq:...`, `local-whisper-cpp` u OpenAI).
- Si actualizas credenciales en `.env`, recarga runtime sin reiniciar con `POST /system/reload-env`.

### Troubleshooting Job Search (crawlers)
- Si una fuente aparece como `⚠` en el diagnóstico: falta configurar su API key en las variables de entorno (local o Render).
- Si aparece `(0)` sin error: la fuente respondió pero no encontró resultados con los filtros actuales. Prueba sin salario mínimo o con ubicación más genérica.
- **Indeed y Glassdoor** bloquean scraping sin API key oficial — aparecerán siempre como `⚠ not_configured`.
- **RemoteOK** solo filtra por salario cuando el dato está declarado numéricamente en la oferta; con salario mínimo alto puede devolver pocos resultados.
- Si el backend está en cloud (Render) y las keys de job search no están configuradas allí, las fuentes fallarán aunque funcionen en local.

### Troubleshooting KB (PDF)
- Si al importar PDF aparece un error, la UI muestra ahora el detalle devuelto por la API (no solo mensaje genérico).
- Causas comunes:
  - PDF escaneado sin texto embebido (requiere OCR previo por páginas),
  - PDF protegido con contraseña,
  - archivo corrupto o sin contenido textual útil.

### Troubleshooting LLM (Gemini/OpenRouter)
- Si ves `[!] Fuente: timeout` de forma repetida:
  - usa `Priorizar LLM` activado para evitar respuestas KB no deseadas,
  - verifica latencia del proveedor (modelos free pueden tardar más),
  - prueba con otra familia/modelo en OpenRouter.
- Si Gemini falla con error de proveedor:
  - revisa `GEMINI_API_KEY` y cuotas del proyecto,
  - el backend intentará fallback a OpenRouter en `429`.
- Si cambias claves en `.env`:
  - usa `POST /system/reload-env` o el botón de recarga de entorno/API.

### TTS provider chain (fallback automatico)
- El endpoint `POST /interview/tts/speak` usa esta prioridad:
  1. **FreeTTS** (Google Translate TTS sin clave, ideal para uso basico),
  2. **Google Cloud TTS** (`GOOGLE_CLOUD_TTS_API_KEY`),
  3. **OpenAI TTS** (`OPENAI_STT_API_KEY` o `OPENAI_API_KEY`).
- Variables opcionales:
  - `GOOGLE_CLOUD_TTS_API_KEY`
  - `GOOGLE_CLOUD_TTS_VOICE` (ej: `es-ES-Standard-A`).
- Nota: FreeTTS prioriza latencia y coste cero; para textos largos o voces mas estables, configura Google Cloud TTS.

### Desarrollo
Lanza los servicios que necesites:
```bash
# Terminal 1: Backend
npm run dev:api

# Terminal 2: Frontend Desktop
npm run dev:desktop

# Opcional: aplicación web Next.js (landing + Clerk)
npm run dev:web
```

Si modificas variables de entorno en caliente, puedes recargarlas desde la app con el botón de recarga de entorno/API local.

### 🔐 Seguridad y Auth (Backend)
- **Rutas Protegidas:** Endpoints críticos (`/interview/*`, `/knowledge-base/*`, `/billing/subscription`) protegidos por un hook de autenticación global (`onRequest`).
- **Shared Secret Proxy:** Comunicación segura entre el frontend (Vercel) y el backend mediante `INTERNAL_API_SECRET`, permitiendo el paso de identidad de usuario de forma verificable.
- **CORS Allowlist:** Acceso restringido exclusivamente a dominios autorizados (`tauri.localhost`, `epsylon.app`, etc.).
- **Bypass de Seguridad en Tests:** Suite de pruebas configurada para operar en modo `test`, permitiendo validaciones automáticas de flujo completo sin dependencias externas de Auth.

### Despliegue inicial en internet (free tier)
- Guía paso a paso: `docs/DEPLOYMENT.md`
- Perfil recomendado:
  - Render (API)
  - Neon (PostgreSQL)
  - Upstash (Redis)
  - Paddle (membresías)
- Validación funcional ya realizada sobre entorno desplegado:
  - `GET /health` OK
  - `GET /auth/me` con validación de JWT OK
  - Webhook de Paddle verificado con firma HMAC OK
  - Flujo de Trial de 3 días validado de extremo a extremo.

### Variables de entorno en cloud (Render)
Para que todas las funcionalidades operen en cloud, configura estas variables en Render → Environment:
```env
# Obligatorias
NODE_ENV=production
PORT=4000
DATABASE_URL=<neon_url>
JWT_ACCESS_SECRET=<secreto_largo>

# IA
OPENROUTER_API_KEY=...
GROQ_API_KEY=...
OPENAI_API_KEY=...

# Job Search
ADZUNA_APP_ID=...
ADZUNA_APP_KEY=...
ADZUNA_COUNTRY=es
THEIRSTACK_API_KEY=...

# Paddle
PADDLE_WEBHOOK_SECRET=...
PADDLE_API_KEY=...
PADDLE_ENVIRONMENT=sandbox # o production

# Seguridad Interna
INTERNAL_API_SECRET=...
API_ALLOWED_ORIGINS=https://tauri.localhost,app://.,https://epsylon.app

# CORS
API_ALLOWED_ORIGINS=https://tauri.localhost,app://.
```
> Si una variable de job search (ej. `ADZUNA_APP_ID`) no está en Render, esa fuente aparecerá como `⚠ not_configured` en el diagnóstico de crawlers aunque funcione en local.

### Testing
El proyecto cuenta con suites de tests tanto para el frontend como para el backend. Para ejecutarlos:

```bash
# Backend (Tests de integración y unitarios)
npm run test --workspace @epsylon/api

# Frontend (Componentes de React y Custom Hooks mockeando Tauri)
npm run test --workspace @epsylon/desktop
```

### Build para Producción (Windows)
```bash
npm run build:phase3
```

Build directo del Desktop:
```bash
npm run build:win --workspace @epsylon/desktop
```

Builds recomendados por entorno:
```bash
# Desktop apuntando a API local (127.0.0.1:4000)
npm run build:win:local --workspace @epsylon/desktop

# Desktop apuntando a API cloud (Render)
npm run build:win:cloud --workspace @epsylon/desktop
```

Después del build, los artefactos quedan organizados por entorno:
- `apps/desktop/release/local/` — build apuntando a API local
- `apps/desktop/release/cloud/` — build apuntando a API cloud (Render)
- Cada carpeta contiene el `.exe`, `.msi` y `Epsylon-dev.exe` (binario portable)

El script de copia detecta automáticamente el entorno según el comando usado y limpia la carpeta destino antes de copiar.
En Windows, durante la copia de artefactos también se aplican metadatos del ejecutable con `rcedit` (si está disponible en `%APPDATA%/npm/...` o en `EPSYLON_RCEDIT_PATH`).

#### Camuflaje Windows (detalle técnico)
- **Camuflaje runtime (stealth):** al activar stealth, el título visible de ventana se camufla como `System Host Process`.
- **Configuración desde UI (`Ajustes`):** ahora puedes editar y guardar directamente:
  - `Camuflaje Win32 (FileDescription)`
  - `Camuflaje Win32 (ProductName)`
  - Botón: `Guardar camuflaje Win32`
- **Camuflaje de metadatos del ejecutable (build):** el pipeline de `apps/desktop/scripts/copy-release-artifacts.mjs` ejecuta `rcedit` para fijar:
  - `FileDescription` (por defecto: `Corsair LightKeeper Center`)
  - `ProductName` (por defecto: `Corsair`)
- **Prioridad de valores en build:**
  1. Variables de entorno (`EPSYLON_WIN_FILE_DESCRIPTION`, `EPSYLON_WIN_PRODUCT_NAME`)
  2. Valores persistidos desde UI (`Ajustes`)
  3. Valores por defecto del proyecto
- **Variables opcionales de personalización:**
  - `EPSYLON_WIN_FILE_DESCRIPTION`
  - `EPSYLON_WIN_PRODUCT_NAME`
  - `EPSYLON_RCEDIT_PATH` (ruta explícita al binario `rcedit-x64.exe`)
- **Comportamiento seguro:** si `rcedit` no está disponible, el build no falla; solo omite el paso de metadatos y continúa.

Checklist de cutover completado: desktop shell unificado en Tauri.

### Releases automáticas (GitHub Actions)
El workflow `.github/workflows/release.yml` compila y publica automáticamente en GitHub Releases:

```bash
# Publicar una nueva versión
git tag v1.0.0
git push --tags
```

O lanzarlo manualmente desde GitHub → Actions → "Release Epsylon" → "Run workflow".

Requisito previo: añadir el secret `VITE_API_URL` en GitHub → Settings → Secrets and variables → Actions con el valor `https://epsylon-api.onrender.com`.

El workflow genera el build en Windows, crea la release como borrador y sube los artefactos `.exe` y `.msi` automáticamente.
```bash
npm run build:analyze --workspace @epsylon/desktop
```

Generación de icono Windows (`.ico`) desde `logo.png`:
```bash
npm run icons:generate --workspace @epsylon/desktop
```

---

## ⌨️ Atajos de Teclado (Hotkeys Globales)

Configurables desde la pestaña `Ajustes` (sin recompilar). Valores por defecto actuales:

*   `Ctrl/Cmd + Shift + T`: Toggle Teleprompter.
*   `Ctrl/Cmd + Shift + A`: Iniciar/Detener captura de micrófono.
*   `Ctrl/Cmd + Shift + R`: Toggle grabación de audio en chunks.
*   `Ctrl/Cmd + Shift + H`: Toggle Modo Stealth (Ocultar ventana + Tray + Camuflaje).
*   `← / →`: Retroceder/avanzar bloque de sugerencia en el teleprompter (global, también en Ghost con click-through).

Notas:
*   Los atajos se guardan en runtime y se reaplican al iniciar la app.
*   Si una combinación entra en conflicto con Windows/u otra app, puedes cambiarla desde UI y guardar.

---

## 📄 Licencia

Este proyecto está bajo la licencia **All Rights Reserved**.
Para consultas comerciales o permisos de uso, por favor contacta con: pacoaldev@gmail.com
