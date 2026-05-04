<p align="center">
  <video src="https://github.com/user-attachments/assets/105927ac-dded-4c58-8adb-c3c983dbf909" alt="video-banner">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.0.1-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/Status-Complete-green?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-red?style=for-the-badge" alt="License">
  <img src="https://img.shields.io/badge/Billing-Stripe-635BFF?style=for-the-badge" alt="Billing">
  <img src="https://img.shields.io/badge/Built%20with-Tauri%20%2B%20Next.js%2016-24c8db?style=for-the-badge" alt="Built with">
</p>

---

> ⚠️ **Repo de escaparate** — Este repositorio contiene únicamente documentación visual y descripción del proyecto. El código fuente es privado.

---

# 🛸 Epsylon

**Epsylon** es el asistente definitivo impulsado por IA diseñado para revolucionar tu carrera profesional. 

Combina la potencia de la automatización en la búsqueda de empleo, con la asistencia inteligente en tiempo real durante entrevistas técnicas, todo en una aplicación de escritorio discreta, potente e inteligente.

> "No solo busques trabajo. Prepárate mejor y afronta cada oportunidad con más confianza."

---

## 🖼️ Demo

<p align="center">
  <img src="./assets/demo.gif" alt="Demo de Epsylon en accion" width="100%">
</p>

---

## 🌀 Pantalla de login Desktop

<p align="center">
 <img src="./assets/login.png" alt="Pantalla de login" width="50%">
</p>

---

## 📸 Capturas de pantalla

<table>
  <tr>
    <td align="center">
      <img src="./assets/screenshot-copilot.png" alt="Asistente de entrevistas" width="100%">
      <sub><b>Asistente — apoyo contextual</b></sub>
    </td>
    <td align="center">
      <img src="./assets/screenshot-jobs.png" alt="Busqueda de empleo" width="100%">
      <sub><b>Empleos — búsqueda y gestión</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="./assets/screenshot-kb.png" alt="Base de conocimiento" width="100%">
      <sub><b>Base de conocimiento</b></sub>
    </td>
    <td align="center">
      <img src="./assets/screenshot-settings.png" alt="Ajustes" width="100%">
      <sub><b>Ajustes — personalización</b></sub>
    </td>
  </tr>
</table>

---

<!-- SYNC:FEATURES:START -->

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

### 🎭 Mock Interviews (Simulacros de Entrevista)
*   **Módulo de Práctica Interactiva:** Pestaña dedicada para realizar entrevistas de prueba con una IA que actúa como reclutador técnico.
*   **Configuración por Rol y Nivel:** Elige el puesto (ej: Senior Backend) y la empresa (ej: Google) para una experiencia personalizada.
*   **Sesiones Dinámicas:** Flujo de conversación inteligente que adapta las preguntas según el desempeño del candidato.
*   **Evaluación y Feedback Detallado:** Al finalizar, recibe una puntuación global y desglosada (técnica, comunicación, confianza) junto con fortalezas y áreas de mejora.
*   **Historial de Sesiones:** Registra y revisa tus simulacros previos para medir tu progreso en el tiempo.

### 🔍 Job Search Engine (Búsqueda Automatizada)
*   **Crawlers Multi-Fuente:** Rastreo en LinkedIn, Infojobs, WeWorkRemotely, DjangoJobs, Adzuna, TheirStack y más.
*   **Diagnóstico de Crawlers en tiempo real:** Tras cada búsqueda, la UI muestra un badge por fuente indicando cuántas ofertas encontró, si está mal configurada (⚠) o si falló (✗).
*   **UI de Ofertas compacta:** Filtros reorganizados en rejilla y controles de fuentes simplificados para reducir ruido visual y mejorar la lectura operativa.
*   **Filtros Avanzados:** Filtra por salario, experiencia, ubicación y modalidad remota. El filtro de ubicación reconoce aliases internacionales (España↔Spain, Alemania↔Germany, etc.).
*   **Hasta 200 resultados por búsqueda:** Límite ampliado para aprovechar al máximo todas las fuentes activas simultáneamente.
*   **Gestión de Candidaturas:** Tracking local en SQLite (`Guardado`, `Aplicado`, `Entrevista`, `Rechazado`).
*   **Auto-Apply & Outreach:** Generación automática de cartas de presentación y correos de seguimiento personalizados.
*   **Follow-up premium:** La generación de correo de seguimiento en Desktop queda disponible desde **PREMIUM/LIFETIME**.
*   **Carta de Presentación por Oferta:** Selección explícita de oferta guardada antes de generar la carta.
*   **Nota sobre fuentes:** Indeed y Glassdoor bloquean scraping público sin API key oficial. Las fuentes más fiables sin coste son LinkedIn, WeWorkRemotely, DjangoJobs y Adzuna (requiere key gratuita).

### 💎 Membresías y Cuotas (Stripe)

Epsylon utiliza un sistema de suscripción basado en cuotas mensuales para garantizar la sostenibilidad del servicio.

| Característica | FREE | PRO (19€/mes) | PREMIUM (49€/mes) |
| :--- | :--- | :--- | :--- |
| **STT (Transcripción)** | 0 min | 120 min/mes | 600 min/mes |
| **Mock Interviews** | 0 | 10 sesiones/mes | 50 sesiones/mes |
| **Auto-Apply** | 0 | 50 aplicaciones/mes | 300 aplicaciones/mes |
| **Stealth Suite** | No | Básico | Completo (Win32 + Capturas) |
| **LLMs Avanzados** | No | No | Sí (OpenAI, Gemini, Claude) |
| **TheirStack API** | No | No | Habilitado |
| **Base Conocimiento** | 5 docs | 25 docs | 200 docs |

*   **Modelo de Prueba (Trial) de 3 días:** En planes **PRO** y **PREMIUM**, el checkout puede crear una suscripción en Stripe con `trial_period_days: 3` **solo si la cuenta aún no ha usado el trial de pago** (una vez en la vida por usuario).
*   **Control de Descargas:** El backend bloquea el acceso al ejecutable si el usuario no tiene una suscripción válida (`active` o `trial`).
*   **Portal de cliente:** `POST /billing/customer-portal` para gestionar facturación, planes y cancelaciones directamente en Stripe desde el panel web.

### 🔐 Seguridad e Infraestructura
*   **Auth lista para cloud:** Registro, login, `me`, refresh token rotatorio y logout verificados contra la API desplegada.
*   **Superuser Bypass (Dev/Personal):** Sistema de acceso total mediante la variable de entorno `SUPERUSER_EMAILS`. Los emails listados obtienen rol `admin` y suscripción Premium automática.
*   **Infra free-tier validada:** Deploy operativo sobre Render + Neon + Upstash con smoke tests reales de health, auth y billing.

### 🌐 Landing Web Premium (Next.js)
*   **Carrusel Continuo de Portales de Empleo (Crawler Logos):** Un carrusel dinámico e infinito que muestra logos vectoriales de las fuentes más populares.
*   **Consentimiento de Cookies Inteligente:** Banner de privacidad no intrusivo persistido mediante almacenamiento local.
*   **Rich Aesthetics (Diseño Inmersivo):** Transición fluida entre secciones, iluminaciones ambientales con orbes difusos y diseño visual unificado.
*   **Auth con Clerk Personalizado:** Registro e inicio de sesión integrados con Clerk. Interfaz de usuario adaptada a modo oscuro.
*   **Descarga del instalador Windows:** Enlace a `/api/download` solo para usuarios Clerk con suscripción `active` o `trial`.

### 🧠 Inteligencia Avanzada
*   **OCR Inteligente con Auto-Sugerencia:** Soporte mixto `spa+eng` con carga de imágenes o pegado directo.
*   **TTS (Text-To-Speech):** Escucha las sugerencias de la IA a través de tus auriculares.
*   **Base de Conocimiento Local (PDF/TXT):** Ingesta, búsqueda, listado, reindexado y borrado de documentos desde la app.
*   **Wizard BYOK de OpenRouter en Ajustes:** Flujo guiado de 3 pasos para que el usuario use sus propias claves IA.
*   **Groq STT BYOK (opcional) en Ajustes:** Campo dedicado para guardar una clave de Groq en el equipo para transcripción de alta velocidad.

### ⚡ Rendimiento y Operación
*   **Arquitectura Modular:** Componentes críticos extraídos de la vista principal para mejorar mantenibilidad.
*   **Compresión HTTP:** API Fastify con compresión global.
*   **Carga Diferida de OCR:** `tesseract.js` se carga solo cuando se usa.
*   **Observabilidad:** Logs estructurados ultra-rápidos con `pino`.
*   **Tests Unitarios e Integración:** Suite de pruebas automatizada para garantizar estabilidad.

---

<!-- SYNC:INFOGRAPHIC:START -->

## 🖼️ Infografia del Proyecto

<details>
  <summary>Ver infografia del proyecto</summary>
  <br />
  <p align="center">
    <img src="./assets/infografia.png" alt="Infografia del proyecto Epsylon" width="100%">
  </p>
</details>

---

<!-- SYNC:FEATURES:END -->
<details>
  <summary>Ver infografia del proyecto</summary>
  <br />
  <p align="center">
    <img src="./assets/infografia.png" alt="Infografia del proyecto Epsylon" width="100%">
  </p>
</details>

---

<!-- SYNC:FEATURES:END -->
<details>
  <summary>Ver infografia del proyecto</summary>
  <br />
  <p align="center">
    <img src="./assets/infografia.png" alt="Infografia del proyecto Epsylon" width="100%">
  </p>
</details>

---

<!-- SYNC:FEATURES:END -->

## ⚠️ Nota de Uso

Epsylon es una herramienta de apoyo y entrenamiento. Su objetivo es ayudar a los usuarios a prepararse y mejorar sus habilidades profesionales.

**No sustituye el conocimiento ni el desempeño individual del usuario en procesos reales**.

---

## 🛠️ Stack Tecnológico

| Capa | Tecnologías |
| :--- | :--- |
| Desktop | Tauri, React, TypeScript |
| Backend | Node.js, Fastify |
| IA | OpenAI, Gemini, OpenRouter |
| Persistencia | SQLite, PostgreSQL |
| Web | Next.js |

---

## 📂 Estructura del Proyecto

```text
Epsylon/
├── apps/
│   ├── api/
│   └── desktop/
├── packages/
│   └── shared/
├── docs/
├── assets/
└── docker-compose.yml
```

---

## 📬 Contacto

¿Interesado en el proyecto?

- 📧 pacoaldev@gmail.com
- 🌐 [Portfolio](https://pacoal.dev)

---

## 📄 Licencia

Código fuente bajo licencia **All Rights Reserved**.
Este repositorio de escaparate es público solo con fines de presentación para el proyecto Epsylon.
