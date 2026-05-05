# 📖 Información y Troubleshooting - Epsylon Desktop

Bienvenido a la guía de soporte y uso de Epsylon Desktop. Aquí encontrarás soluciones a los problemas más comunes y consejos para sacar el máximo partido a la herramienta.

---

## 🚀 Uso Básico

### Inicio de Sesión
1. **Email**: El mismo que usas en el portal web.
2. **Contraseña**: No es la contraseña de Google/GitHub del portal, sino la **Contraseña de Escritorio** que debes configurar en tu Panel de Control web (sección "Acceso Escritorio").

### Atajos de Teclado (Hotkeys)
Puedes personalizarlos en la pestaña **Ajustes**. Por defecto son:
*   `Ctrl + Shift + T`: Mostrar/Ocultar Teleprompter.
*   `Ctrl + Shift + A`: Iniciar/Detener Micrófono.
*   `Ctrl + Shift + R`: Grabación por fragmentos (Chunks).
*   `Ctrl + Shift + H`: Activar/Desactivar Modo Stealth (Invisible).
*   `← / →`: Navegar entre bloques de sugerencias de la IA.

---

## 🛠 Troubleshooting (Solución de problemas)

### 🔍 Buscador de Empleo (Crawlers)
* **Badge ⚠**: Falta configurar la API Key de esa fuente en los Ajustes o en el servidor.
* **Badge ✗**: Error de conexión o la fuente ha bloqueado la petición (captcha/timeout).
* **0 resultados**: Intenta con filtros más genéricos (sin salario mínimo o ubicación más amplia).
* **Indeed/Glassdoor**: Requieren siempre API Key oficial debido a sus protecciones contra scraping.

### 📚 Base de Conocimiento (KB)
* **Error al importar PDF**:
    * Asegúrate de que el PDF no esté protegido por contraseña.
    * Si es un PDF escaneado (sin texto seleccionable), la IA no podrá leerlo directamente; debe pasar por un proceso de OCR previo.
    * El archivo no debe estar corrupto.

### 🤖 Inteligencia Artificial (LLM)
* **Timeout / Lentitud**: 
    * Si usas el plan PRO, estás compartiendo cuota de OpenRouter; en momentos de alta carga puede tardar más.
    * Si usas PREMIUM con tu propia API Key, verifica que tengas saldo en el proveedor (OpenAI/Gemini/Anthropic).
* **Respuestas irrelevantes**: Activa "Priorizar LLM" en Ajustes para que la IA se ciña más a la lógica del modelo y menos a los documentos de la KB si estos no son precisos.

### 🎤 Audio y Micrófono
* **No se genera texto**: Verifica que el micrófono correcto esté seleccionado en el sistema y que la barra de volumen en la app se mueva al hablar.
* **Latencia en Chunks**: La grabación por fragmentos depende de la velocidad de tu conexión a internet para subir el audio al servidor de transcripción.

---

## 🔐 Seguridad y Privacidad en Windows

### Aviso de SmartScreen / "Windows protegió su PC"
Al no estar firmada con un certificado de desarrollador comercial (Authenticode), Windows puede mostrar este aviso. 
*   **Solución**: Haz clic en `"Más información"` y luego en `"Ejecutar de todas formas"`.

### Indetectabilidad (Stealth Suite)
*   **Modo Stealth**: Camufla el nombre del proceso en el Administrador de Tareas y oculta la ventana de cualquier software de captura de pantalla.
*   **Camuflaje Win32**: En los Ajustes puedes cambiar el nombre interno del ejecutable (ej: *"Audio Drivers"*) para una capa extra de discreción.

---

© 2026 Epsylon - v1.0.2
