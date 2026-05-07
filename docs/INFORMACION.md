# 📖 Guía de Usuario y Troubleshooting — Epsylon (Web + Desktop)

Esta guía es para **usuarios finales** . Aquí tienes los pasos para usar **la Web (portal)** y **la App Desktop**, además de soluciones a problemas comunes.

---

## 🌐 Web (Portal)

La web es el **panel de control** para gestionar tu cuenta: acceso, suscripción y descarga del instalador.

### 1) Crear cuenta / iniciar sesión
- Entra en la web y **regístrate** o **inicia sesión**.
- Si tienes acceso con Google, úsalo (es el método más rápido).

### 2) Suscripción (si aplica)
- En el panel, revisa tu estado de plan.
- La **descarga del instalador** requiere una suscripción con estado **Activo** o **Trial**.
- Los planes **PRO** y **PREMIUM** incluyen un **TRIAL de 3 días**: puedes **cancelar en cualquier momento** durante el trial para evitar cargos. Si cancelas, mantienes el acceso **hasta que finalicen los 3 días**.

### 3) Descargar el instalador de Windows
- Ve al área de **Descargas** del panel.
- Descarga e instala el archivo `epsylon-setup.exe`.
- Si no ves el botón de descarga, revisa:
  - que hayas iniciado sesión,
  - que tu plan/trial esté activo (si aplica),
  - que estés dentro del panel (normalmente una sección tipo “App/Panel”).

### 4) Contraseña de Escritorio (imprescindible para la app)
La App Desktop **NO usa** la contraseña de Google/GitHub.

- En el panel web, busca la sección **“Acceso Escritorio”**.
- Crea o cambia tu **Contraseña de Escritorio**.
- Esa contraseña es la que usarás para iniciar sesión en la app de Windows.

---

## 🖥️ Desktop (App de Windows)

### Inicio de Sesión
1. **Email**: El mismo que usas en el portal web.
2. **Contraseña**: No es la contraseña de Google/GitHub del portal, sino la **Contraseña de Escritorio** que configuras en el panel web (sección **“Acceso Escritorio”**).

> Nota: por seguridad, es posible que la app te pida iniciar sesión de nuevo al cerrarla y abrirla.

### Atajos de Teclado (Hotkeys)
Puedes personalizarlos en la pestaña **Ajustes**. Por defecto son:
- `Ctrl + Shift + T`: Mostrar/Ocultar Teleprompter.
- `Ctrl + Shift + A`: Iniciar/Detener Micrófono.
- `Ctrl + Shift + R`: Grabación por fragmentos (Chunks).
- `Ctrl + Shift + H`: Activar/Desactivar Modo Stealth (Invisible).
- `← / →`: Navegar entre bloques de sugerencias de la IA.

---

## 🛠 Troubleshooting (Solución de problemas)

### 🔐 No puedo entrar (login)
- **“Contraseña incorrecta”**: asegúrate de estar usando la **Contraseña de Escritorio** creada en la web (no la de Google/GitHub).
- **Olvidé la contraseña**: vuelve al panel web → **Acceso Escritorio** → crea una nueva y vuelve a intentar.

### 🔍 Buscador de Empleo (Crawlers)
- **Badge ⚠**: Falta configurar la API Key de esa fuente en **Ajustes**.
- **Badge ✗**: Error de conexión o la fuente ha bloqueado la petición (captcha/timeout).
- **0 resultados**: Intenta con filtros más genéricos (sin salario mínimo o ubicación más amplia).
- **Indeed/Glassdoor**: Requieren siempre API Key oficial debido a sus protecciones contra scraping.

### 📚 Base de Conocimiento (KB)
- **Error al importar PDF**:
  - Asegúrate de que el PDF no esté protegido por contraseña.
  - Si es un PDF escaneado (sin texto seleccionable), la IA no podrá leerlo directamente; debe pasar por un proceso de OCR previo.
  - El archivo no debe estar corrupto.

### 🤖 Inteligencia Artificial (LLM)
- **Timeout / Lentitud**:
  - Si usas el plan PRO, estás compartiendo cuota de OpenRouter; en momentos de alta carga puede tardar más.
  - Si usas PREMIUM con tu propia API Key, verifica que tengas saldo en el proveedor (OpenAI/Gemini/Anthropic).
- **Respuestas irrelevantes**: Activa **“Priorizar LLM”** en Ajustes para que la IA se ciña más a la lógica del modelo y menos a los documentos de la KB si estos no están actualizados.

### 🎤 Audio y Micrófono
- **Primera vez no detecta dispositivos**: es un tema de permisos. Pulsa **“Iniciar micrófono”** y acepta el permiso cuando Windows lo solicite.
- **No se genera texto**: verifica que el micrófono correcto esté seleccionado en el sistema y que la barra de volumen en la app se mueva al hablar.
- **Latencia en Chunks**: la grabación por fragmentos depende de la velocidad de tu conexión a internet para subir el audio al servidor de transcripción.

---

## 🔐 Seguridad y Privacidad en Windows

### Aviso de SmartScreen / "Windows protegió su PC"
Al no estar firmada con un certificado de desarrollador comercial (Authenticode), Windows puede mostrar este aviso. 
* **Solución**: Haz clic en `"Más información"` y luego en `"Ejecutar de todas formas"`. **Solo lo pedirá la primera vez**.

### Indetectabilidad (Stealth Suite)
- **Modo Stealth**: camufla el nombre del proceso en el Administrador de Tareas y oculta la ventana de cualquier software de captura de pantalla.
- **Camuflaje Win32**: en Ajustes puedes cambiar el nombre interno del ejecutable (ej: *"Audio Drivers"*) para una capa extra de discreción.

---

© 2026 Epsylon
