<p align="center">
  <img src="./assets/banner.png" alt="Epsylon Banner" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/Status-Complete-green?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-red?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/Built%20with-Tauri%20%2B%20React-24c8db?style=for-the-badge" alt="Built with">
</p>

---

> ⚠️ **Repo de escaparate** — Este repositorio contiene únicamente documentación visual y descripción del proyecto. El código fuente es privado.

---

# 🛸 Epsylon

**Epsylon** es el asistente definitivo impulsado por IA diseñado para revolucionar tu carrera profesional. Combina la potencia de la automatización en la búsqueda de empleo con la asistencia inteligente en tiempo real durante entrevistas.

> "No solo busques trabajo. Domina el proceso desde la primera búsqueda hasta el apretón de manos final."

---

## 🖼️ Demo

<p align="center">
  <img src="./assets/demo.gif" alt="Demo de Epsylon en accion" width="100%">
</p>

---

## 📸 Capturas de pantalla

<table>
  <tr>
    <td align="center">
      <img src="./assets/screenshot-copilot.png" alt="Interview Copilot" width="100%">
      <sub><b>El Copiloto — asistencia en tiempo real</b></sub>
    </td>
    <td align="center">
      <img src="./assets/screenshot-jobs.png" alt="Job Search Engine" width="100%">
      <sub><b>Modulo de Empleos — búsqueda automatizada</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="./assets/screenshot-kb.png" alt="Base de conocimiento" width="100%">
      <sub><b>Base de conocimientos — RAG local</b></sub>
    </td>
    <td align="center">
      <img src="./assets/screenshot-settings.png" alt="Ajustes y hotkeys" width="100%">
      <sub><b>Ajustes — hotkeys globales configurables</b></sub>
    </td>
  </tr>
</table>

---
<!-- SYNC:FEATURES:START -->
## 🚀 Características Principales

### 🎤 Interview Copilot (Asistencia en Tiempo Real)
*   **Transcripción Inteligente Mejorada:** Captura con Groq STT como proveedor principal, fallback local con whisper.cpp y respaldo OpenAI, con contexto reciente para mejorar continuidad en conversaciones.
*   **Chunks Optimizados para Voz Natural:** Grabación por fragmentos ajustada para mejorar tasa de acierto en primera transcripción.
*   **Sugerencias LLM Multi-Modelo (Gemini/OpenRouter/OpenAI):** Selección de proveedor desde UI con prioridad configurable al LLM.
*   **Recuperación Automática de Contexto (RAG local):** Antes de responder, el backend consulta la base de conocimiento y adjunta los fragmentos más relevantes al prompt.
*   **Pipeline híbrido robusto (LLM + KB):** Soporta modo `Priorizar LLM` para intentar respuesta generativa primero y degradar a fallback controlado si hay límites/timeout.
*   **Modo Stealth Avanzado (Ghost):** Interfaz ultra-discreta con opacidad ajustable, ocultación del icono en la barra de tareas y minimización al área de notificación (System Tray).
*   **Detección de Plataforma:** Reconocimiento automático de Zoom, Teams y Google Meet para optimizar el contexto.
*   **Teleprompter Remoto:** Visor con scroll automático sincronizado y controlable remotamente desde la ventana principal.
*   **Teleprompter visible en capturas (Windows):** Nuevo check en `Ajustes` para permitir o bloquear la aparición del teleprompter en screenshots/grabaciones de pantalla.
*   **Hotkeys Globales Configurables en UI:** Edita los atajos desde `Ajustes`, se aplican al instante sin rebuild y quedan persistidos para próximos arranques.
*   **Hotkeys de audio robustas:** Fallback de ejecución directa desde Tauri para captura/chunks incluso si el bus de eventos del renderer no responde.
*   **UI 100% en Español:** Etiquetas, mensajes, botones y estados unificados en un único idioma.

### 🔍 Job Search Engine (Búsqueda Automatizada)
*   **Crawlers Multi-Fuente:** Rastreo en LinkedIn, Infojobs, Indeed, Glassdoor, RemoteOK, Wellfound, Adzuna y más.
*   **Filtros Avanzados:** Filtra por salario, experiencia, ubicación y modalidad remota.
*   **Gestión de Candidaturas:** Tracking local en SQLite (`Guardado`, `Aplicado`, `Entrevista`, `Rechazado`).
*   **Auto-Apply & Outreach:** Generación automática de cartas de presentación y correos de seguimiento personalizados.
*   **Carta de Presentación por Oferta:** Selección explícita de oferta guardada antes de generar la carta.

### 💳 Control de Costes API (portal TheirStack)
*   **Integración TheirStack en Modo Ahorro:** Activación manual desde UI para evitar consumo accidental.
*   **Tope por Consulta:** Máximo 5 resultados por búsqueda en TheirStack.
*   **Tope Diario Persistente:** Límite diario configurable de créditos TheirStack (por defecto: 20/día).
*   **Ventana Temporal Acotada:** Búsquedas TheirStack con antigüedad máxima configurable (`posted_at_max_age_days`).

### 🔐 Auth, Billing y Membresías
*   **Auth lista para cloud:** Registro, login, `me`, refresh token rotatorio y logout verificados contra la API desplegada.
*   **Billing con Stripe funcional:** Planes `Pro`, `Premium` y `Lifetime` expuestos por API y conectados a Stripe Checkout.
*   **Webhook Stripe endurecido:** Verificación real de firma del webhook con `STRIPE_WEBHOOK_SECRET` para evitar activaciones falsas.
*   **Persistencia de suscripción:** Tras pago en Stripe test mode, la suscripción queda reflejada en backend (`plan`, `status`, `stripeCustomerId`, `stripeSubscriptionId`).
*   **Infra free-tier validada:** Deploy operativo sobre Render + Neon + Upstash con smoke tests reales de health, auth y billing.

### 🧠 Inteligencia Avanzada
*   **OCR Inteligente con Auto-Sugerencia:** Soporte mixto `spa+eng` con carga de imágenes o pegado directo desde el portapapeles. Al detectar texto, el sistema dispara automáticamente la generación de sugerencias.
*   **TTS (Text-To-Speech):** Escucha las sugerencias de la IA a través de tus auriculares.
*   **Memoria de Entrevista por Rol y Nivel:** Base general común + memoria específica para Backend, Java, Spring Boot, Full Stack y niveles Mid / Mid-Adv.
*   **Base de Conocimiento Local (PDF/TXT):** Ingesta, búsqueda, listado, reindexado y borrado de documentos desde la app.
*   **Pestaña dedicada de KB:** La gestión de la base de conocimiento vive en una pestaña separada (`Base de conocimiento`) con una interfaz optimizada.
*   **Trazabilidad de contexto:** Las sugerencias pueden devolver `knowledgeHits` para ver qué fragmentos KB se usaron.
*   **Wizard BYOK de OpenRouter en Ajustes:** Flujo guiado para crear/verificar/guardar API key y usarla por defecto.
*   **Clave del usuario como preferente:** Si el usuario guarda su OpenRouter API key, se usa por defecto en sugerencias, cover letters y follow-up emails.
*   **Analíticas:** Visualiza tu progreso con dashboards de búsqueda y éxito en entrevistas.

### ⚡ Rendimiento y Operación
*   **Arquitectura Modular:** Componentes críticos extraídos para mejorar mantenibilidad.
*   **Compresión HTTP:** API Fastify con compresión global para respuestas grandes.
*   **Carga Diferida de OCR:** `tesseract.js` se carga solo cuando se usa OCR (mejor arranque de API).
*   **Índices en Persistencia Local:** SQLite para jobs + SQLite FTS5 para chunks KB + índice Q/A dedicado para recuperación más precisa.
*   **Análisis de Bundle Desktop:** Script para inspeccionar tamaño y composición del bundle de renderer.
*   **Observabilidad:** Logs estructurados ultra-rápidos con `pino` y visualización legible en desarrollo con `pino-pretty`.
*   **Documentación Interactiva:** Endpoints del backend auto-documentados vía Swagger UI (`/docs`).
*   **CI/CD Automatizado:** Pipeline en GitHub Actions configurado para compilar y publicar releases (Tauri y Backend) de forma inteligente.

---

## 🖼️ Infografia del Proyecto
<!-- SYNC:FEATURES:END -->
<p align="center">
  <img src="./assets/infografia.png" alt="Infografia del proyecto Epsylon" width="100%">
</p>

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

---

## 📂 Estructura del Proyecto (referencia)

```text
Epsylon/
├── apps/
│   ├── api/          # Backend Fastify & Core AI Logic
│   └── desktop/      # Tauri App & React Frontend
├── packages/
│   └── shared/       # Shared Types, Schemas & Contracts
├── docs/             # Technical Documentation & Guides
├── assets/           # Media & Brand Assets
└── docker-compose.yml # Local Infrastructure Setup
```

---

## 📬 Contacto

¿Interesado en el proyecto?

- 📧 pacoaldev@gmail.com
- 🌐 [Portfolio](https://pacoal.dev)

---

## 📄 Licencia

Código fuente bajo licencia **All Rights Reserved**.
Este repositorio de escaparate es público solo con fines de presentación en portfolio.
