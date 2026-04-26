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

**Epsylon** es un asistente de escritorio impulsado por IA diseñado para revolucionar el proceso de búsqueda de empleo. Combina automatización de búsqueda de ofertas con asistencia inteligente en tiempo real durante entrevistas técnicas, todo en una app de escritorio discreta y potente construida con Tauri + React.

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
      <sub><b>Interview copilot — asistencia en tiempo real</b></sub>
    </td>
    <td align="center">
      <img src="./assets/screenshot-jobs.png" alt="Job Search Engine" width="100%">
      <sub><b>Job search engine — búsqueda automatizada</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="./assets/screenshot-kb.png" alt="Base de conocimiento" width="100%">
      <sub><b>Base de conocimiento — RAG local</b></sub>
    </td>
    <td align="center">
      <img src="./assets/screenshot-settings.png" alt="Ajustes y hotkeys" width="100%">
      <sub><b>Ajustes — hotkeys globales configurables</b></sub>
    </td>
  </tr>
</table>

---

## 🚀 Características principales

### 🎤 Interview copilot
- Transcripcion en tiempo real con cadena STT: Groq → Whisper local → OpenAI Whisper
- Sugerencias LLM multi-modelo: Gemini, OpenRouter y OpenAI con fallback automatico
- RAG local: recuperacion automatica de contexto desde base de conocimiento propia (PDF/TXT)
- Teleprompter remoto con scroll sincronizado
- **Modo stealth (Ghost):** opacidad ajustable, ocultacion de taskbar, camuflaje del titulo de ventana
- Hotkeys globales 100% configurables desde la UI sin recompilar

### 🔍 Job search engine
- Crawlers multi-fuente: LinkedIn, Infojobs, Indeed, Glassdoor, RemoteOK, Adzuna y mas
- Filtros avanzados por salario, experiencia, ubicacion y modalidad
- Tracking de candidaturas en SQLite (`Guardado` → `Aplicado` → `Entrevista` → `Rechazado`)
- Generacion automatica de cartas de presentacion personalizadas por oferta

### 🧠 Inteligencia avanzada
- OCR con auto-sugerencia (imagen o portapapeles)
- TTS para escuchar las sugerencias por auriculares
- Memoria de entrevista por rol y nivel (Backend, Java, Spring Boot, Full Stack, Mid, Mid-Adv)
- Dashboard de analiticas de busqueda y exito en entrevistas

---

## 🛠️ Stack tecnologico

| Capa | Tecnologias |
| :--- | :--- |
| **Desktop app** | Tauri, React, TypeScript, Vite |
| **Backend API** | Node.js, Fastify, Zod |
| **Persistencia** | SQLite (jobs + KB FTS5 + KB Q/A) |
| **IA / ML** | Groq STT, OpenAI, Anthropic Claude, Google Gemini, OpenRouter, Tesseract.js |
| **Tooling** | NPM Workspaces, Docker, GitHub Actions |

---

## 🖼️ Arquitectura del sistema

<p align="center">
  <img src="./assets/infografia.png" alt="Diagrama de arquitectura de Epsylon" width="100%">
</p>

---

## 💡 Por que lo construi

Durante mi busqueda de practicas como desarrollador, el proceso de entrevistas tecnicas me parecia un cuello de botella donde la preparacion previa no era suficiente. Queria una herramienta que combinara gestion de ofertas con asistencia activa, de forma discreta y sin depender de servicios en la nube para lo critico.

Epsylon es el resultado: un proyecto complejo y real que me permitio trabajar con Tauri, sistemas RAG, pipelines de audio y multiples APIs de IA integradas en un monorepo.

---

## 📂 Estructura del proyecto (referencia)

```text
Epsylon/
├── apps/
│   ├── api/          # Backend Fastify y logica de IA
│   └── desktop/      # App Tauri y frontend React
├── packages/
│   └── shared/       # Tipos, esquemas y contratos compartidos
├── docs/             # Documentacion tecnica interna
└── assets/           # Recursos visuales y marca
```

---

## 📬 Contacto

¿Interesado en el proyecto o en colaborar?

- 📧 pacoaldev@gmail.com
- 🌐 [Portfolio](#) *(enlaza aqui tu portfolio)*

---

## 📄 Licencia

Codigo fuente bajo licencia **All Rights Reserved**.
Este repositorio de escaparate es publico solo con fines de presentacion en portfolio.
