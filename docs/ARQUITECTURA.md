# Arquitectura tecnica — Epsylon

Epsylon es un monorepo Node.js con tres piezas principales que se comunican de forma clara y desacoplada.

---

## Estructura del monorepo

```text
Epsylon/
├── apps/
│   ├── api/         → endpoints, logica de negocio, crawlers, IA
│   └── desktop/     → UI React + shell de escritorio Tauri
└── packages/
    └── shared/      → tipos, esquemas Zod y contratos compartidos
```

---

## Flujo general del sistema

```mermaid
flowchart TD
    UI["🖥️ apps/desktop\nTauri + React + TypeScript"]

    subgraph API ["⚙️ apps/api — Fastify + TypeScript"]
        direction TB
        COPILOT["Interview Copilot\nSTT · Sugerencias LLM · RAG"]
        JOBS["Job Search Engine\nCrawlers · Tracking · Export"]
    end

    SHARED["📦 packages/shared\nTipos · Esquemas Zod · Contratos"]

    subgraph INFRA ["🐳 Infraestructura local — Docker Compose"]
        SQLITE["SQLite\nJobs · KB · Q&A"]
        PG["PostgreSQL\nPersistencia principal"]
        REDIS["Redis\nCache · Sesiones"]
    end

    subgraph EXTERNAL ["☁️ Servicios externos"]
        LLM["LLMs\nOpenAI · Gemini · OpenRouter"]
        STT["STT\nGroq · Whisper"]
        SOURCES["Fuentes de empleo\nLinkedIn · Indeed · Infojobs · +"]
    end

    UI -->|HTTP / IPC| COPILOT
    UI -->|HTTP / IPC| JOBS
    SHARED -.->|tipos compartidos| UI
    SHARED -.->|tipos compartidos| API
    COPILOT --> LLM
    COPILOT --> STT
    COPILOT --> SQLITE
    JOBS --> SOURCES
    JOBS --> SQLITE
    API --> PG
    API --> REDIS
```

---

## Interview copilot — flujo detallado

```mermaid
sequenceDiagram
    actor Usuario
    participant Desktop as Desktop (Tauri)
    participant API as API (Fastify)
    participant STT as STT (Groq / Whisper)
    participant LLM as LLM (Gemini / OpenAI)
    participant KB as Base de conocimiento (SQLite FTS5)

    Usuario->>Desktop: habla durante la entrevista
    Desktop->>API: audio chunk
    API->>STT: transcripcion
    STT-->>API: texto transcrito
    API->>KB: busqueda semantica (RAG)
    KB-->>API: contexto relevante
    API->>LLM: prompt + contexto
    LLM-->>API: sugerencia
    API-->>Desktop: sugerencia renderizada
    Desktop-->>Usuario: teleprompter / overlay
```

---

## Job search engine — flujo detallado

```mermaid
flowchart LR
    TRIGGER["Busqueda iniciada\npor el usuario"]
    CRAWLERS["Crawlers multi-fuente\nLinkedIn · Indeed · Infojobs\nRemoteOK · Adzuna · +"]
    FILTER["Filtrado\nsalario · ubicacion\nexperiencia · modalidad"]
    SQLITE[("SQLite\njobs.sqlite3")]
    TRACKER["Tracker de candidaturas\nGuardado → Aplicado\nEntrevista → Rechazado"]
    COVER["Generacion de carta\nde presentacion (LLM)"]

    TRIGGER --> CRAWLERS
    CRAWLERS --> FILTER
    FILTER --> SQLITE
    SQLITE --> TRACKER
    SQLITE --> COVER
```

---

## Infraestructura local

Docker Compose levanta tres servicios:

| Servicio | Tecnologia | Proposito |
| :--- | :--- | :--- |
| `api` | Node.js | Logica de negocio y endpoints |
| `postgres` | PostgreSQL | Persistencia principal |
| `redis` | Redis | Cache y sesiones |

La persistencia de jobs y la base de conocimiento se gestionan en SQLite directamente en `apps/api/data/`.

---

## Observabilidad

```mermaid
flowchart LR
    subgraph API
        FASTIFY_LOG["Logger Fastify"]
        UNHANDLED["unhandledRejection\nuncaughtException"]
    end

    subgraph Desktop
        FILE_LOG["desktop.log\nen appData"]
        GLOBAL_ERR["Captura global\nmain process + renderer"]
    end

    FASTIFY_LOG --> ARCHIVO["📄 Logs en disco"]
    UNHANDLED --> ARCHIVO
    FILE_LOG --> ARCHIVO
    GLOBAL_ERR --> ARCHIVO
```

---

## CI/CD

El pipeline de GitHub Actions ejecuta en cada push:

```mermaid
flowchart LR
    A["npm ci"] --> B["lint"] --> C["type-check"] --> D["test"]
```

---

## Proximos pasos arquitectonicos

- **Anti-bot:** definir estrategia de endurecimiento para los conectores de empleo
- **Multiusuario:** migrar tracking de jobs al esquema principal de PostgreSQL
- **Telemetria:** calidad de resultados por fuente de empleo
- **Release Tauri:** firmado de binarios, sistema de actualizaciones y observabilidad en produccion
