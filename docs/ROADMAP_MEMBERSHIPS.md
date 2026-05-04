# 🗺️ Roadmap — Estrategia de Membresías Epsylon

> **Último estado:** decisión tomada en conversación de diseño de producto (mayo 2025).  
> **Aplicable a:** [epsylon.pacoal.dev](https://epsylon.pacoal.dev) · Pricing page · Backend billing service.

---

## 1. Decisión actual: diferenciación PRO vs PREMIUM

### Principio guía

| Principio | Detalle |
|---|---|
| **TOP del producto** | Teleprompter invisible (Ghost / click-through) para entrevistas en vivo con IA. |
| **Core accesible en PRO** | Ghost + teleprompter ya incluidos; nadie debe subir a PREMIUM solo para tener la función estrella. |
| **PREMIUM = Stealth Suite + volumen** | El upgrade justificado por discreción avanzada (cursor virtual, camuflaje Win32, control de capturas) y límites más altos. |
| **Sin "ilimitado" por ahora** | Mientras la infra dependa de tiers gratuitos/BYOK y de claves propias, NO prometer ilimitado. Usar **"límites altos" + Fair Use**. |

---

### 1.1 PRO — "Interview Copilot" ✅

**Objetivo:** que alguien pague PRO y pueda usar Epsylon en una entrevista real desde el día 1.

#### 🎤 Interview Copilot (núcleo)
- [x] Teleprompter en tiempo real + sugerencias IA
- [x] **Ghost (click-through)** — no roba foco ni clics durante la entrevista
- [x] Navegación de bloques con hotkeys globales `←/→` también en modo Ghost
- [x] Hotkeys globales configurables en UI (persistentes)
- [x] Detección automática de plataforma (Zoom, Teams, Google Meet)
- [x] Teleprompter Remoto (scroll sincronizado)
- [x] Personalización del copiloto (textarea "background personal")
- [x] Toggle "Priorizar LLM"

#### 🎭 Mock Interviews
- [x] Módulo completo de simulacros
- [ ] Con límites mensuales (ver §2)

#### 🔍 Job Search Engine
- [x] Crawlers principales (LinkedIn, WWR, DjangoJobs, Adzuna)
- [x] Tracking local en SQLite
- [x] Generación de carta de presentación por oferta
- [ ] Con límites mensuales (ver §2)

#### 🧠 Base de Conocimiento + IA
- [x] KB local (PDF/TXT) — ingest, búsqueda, listado, borrado
- [x] OCR + TTS + STT (con cuota incluida — ver §2)
- [x] Wizard BYOK OpenRouter (tour guiado de 3 pasos)
- [ ] Con cuota de documentos (ver §2)

#### 🔐 Dispositivos
- [ ] 1 dispositivo desktop

---

### 1.2 PREMIUM — "Stealth Suite + Power" ✅

**Objetivo:** upgrade obvio para usuarios que hacen muchas entrevistas y quieren máxima discreción + mayor capacidad.

Incluye **todo lo de PRO**, más:

#### 🥷 Stealth Suite (diferenciador principal de PREMIUM)
- [x] **Cursor Virtual** — oculta el cursor real en capturas/grabaciones; cursor SVG renderizado en frontend
- [x] **Control de visibilidad del teleprompter en capturas (Windows)** — check en Ajustes
- [x] **Camuflaje Windows avanzado completo**
  - Camuflaje de título (`"System Host Process"`)
  - Metadatos Win32 (`FileDescription`, `ProductName`) aplicados al `.exe`
  - Configurable y guardable desde UI

#### 🚀 Límites más altos (ver §2)
- [ ] STT Groq: más minutos/mes incluidos
- [ ] Auto-Apply & Outreach: más volumen/mes
- [ ] Mock Interviews: más sesiones/mes + historial ampliado
- [ ] Job Search: hasta 200 resultados por búsqueda
- [ ] KB: más documentos + reindexado sin restricción
- [ ] 3 dispositivos desktop

---

### 1.3 LIFETIME ✅

- Todo lo de PREMIUM, sin caducidad.
- Pago único (Stripe modo `payment`).

---

## 2. Límites concretos propuestos (v1)

> **Nota:** estos valores son punto de partida. Revísalos cuando tengas métricas reales de uso (ver §4).

| Feature | PRO | PREMIUM | LIFETIME |
|---|---|---|---|
| **STT — Speech-to-Text (Groq)** (key del proyecto, solo mic+chunks activos) | 120 min/mes | 600 min/mes | 600 min/mes |
| **Auto-Apply & Outreach** | 50/mes | 300/mes | 300/mes |
| **Mock Interviews** | 10/mes · historial 20 | 50/mes · historial amplio | Sin restricción |
| **Job Search: resultados** | hasta 100 por búsqueda | hasta 200 por búsqueda | hasta 200 por búsqueda |
| **KB: documentos** | 25 docs / ~200 MB | 200 docs / ~2 GB | Sin restricción |
| **Sugerencias en vivo (LLM via OpenRouter BYOK)** | Fair Use (rate limit moderado: 5 req/min) | Fair Use (rate limit alto: 15 req/min) | Fair Use |
| **Dispositivos desktop** | 1 | 3 | Sin restricción |
| **TheirStack** | No incluido | Habilitado (límites configurables: 5/consulta, 20/día) | Habilitado |
| **Trial** | 3 días (una vez en la vida) | 3 días (una vez en la vida) | — |

### 2.1 Notas sobre costes y claves

- **OpenRouter (LLM):** BYOK — el usuario trae su propia API key vía el **wizard de 3 pasos** en Ajustes. Si existe key propia del usuario, se usa por defecto; si no, el backend usa la clave base del sistema (también sujeta al rate limit por plan indicado en la tabla anterior). El coste de LLM no recae directamente sobre el proyecto para usuarios BYOK.
- **Groq STT:** la clave es **propiedad del proyecto**. Solo se consume cuando el usuario tiene el micrófono activo con captura de chunks activa. Por ello es el recurso más crítico a capar por plan.
- **Cuotas:** aplicar rate limiting en backend (middleware por `userId` + plan). Considerar ventana deslizante mensual reseteada en fecha de renovación de suscripción.

### 2.2 Fair Use y comunicación

- Añadir pie de página en pricing: *"Sujeto a Fair Use para garantizar la estabilidad del servicio para todos los usuarios."*
- No incluir la palabra **"ilimitado"** en ningún plan hasta tener métricas reales y costes controlados.
- En su lugar usar: **"límites altos"**, **"uso intensivo"**, **"hasta X/mes"**.

---

## 3. Mensajería / Copy para la landing (epsylon.pacoal.dev)

### 3.1 Titulares por plan (máx. 2 líneas)

```
PRO
  Teleprompter Invisible (Ghost) para entrevistas en vivo con IA.
  Automatización esencial de búsqueda de empleo.

PREMIUM
  Stealth Suite: cursor virtual + camuflaje Windows + control de capturas.
  Mayor capacidad para uso intensivo. Fair Use.

LIFETIME
  Todo lo de PREMIUM. Sin renovaciones. Para siempre.
```

### 3.2 Bullets de la tabla de precios (propuesta)

**PRO**
- ✅ Teleprompter IA en vivo + **Ghost (click-through)**
- ✅ Hotkeys globales + navegación por bloques
- ✅ Mock Interviews (10/mes) + Job Search (100 resultados)
- ✅ KB local (25 docs) + OCR + TTS
- ✅ **120 min/mes de transcripción STT incluidos**
- ✅ Wizard BYOK OpenRouter (modelos free incluidos)
- ✅ 50 Auto-Applies/mes
- ✅ 1 dispositivo · Trial 3 días

**PREMIUM**
- ✅ Todo lo de PRO
- 🥷 **Stealth Suite** (cursor virtual + camuflaje Win32 + control capturas)
- ✅ 600 min/mes de transcripción STT
- ✅ 300 Auto-Applies/mes · 200 resultados/búsqueda
- ✅ KB avanzada (200 docs) + TheirStack
- ✅ 3 dispositivos · Trial 3 días · Fair Use

**LIFETIME**
- ✅ Todo lo de PREMIUM, de por vida
- ✅ Sin renovaciones

### 3.3 Avisos / cautelas de copy

- ❌ **Evitar "ilimitado"** en cualquier plan hasta tener datos reales de uso.
- ❌ Evitar prometer "0 latencia" o "respuesta instantánea" (depende de OpenRouter/Groq).
- ✅ Usar *"Fair Use"* como cláusula visible, no en letra pequeña.
- ✅ Destacar **"BYOK OpenRouter"** como diferencial de transparencia (el usuario controla su key).
- ✅ Mencionar explícitamente que STT solo consume cuando el micrófono está activo: tranquiliza al usuario sobre privacidad y consumo.

---

## 4. Iteraciones futuras / Backlog

### 4.1 Mejoras de infraestructura de cuotas
- [ ] **Quota enforcement en backend:** middleware que consulta `subscriptions.plan` y contadores en Redis/Upstash antes de procesar cada request facturado (STT, auto-apply, LLM fallback).
- [ ] **Contadores mensuales:** tabla o hash en Redis por `userId` + `feature` + `period` (YYYY-MM). Reset automático en fecha de renovación Stripe.
- [ ] **Respuesta 429 con headers informativos:** `X-Quota-Remaining`, `X-Quota-Reset` para que la UI muestre estado de cuota en tiempo real.
- [ ] **Panel de cuota en la app:** widget en Ajustes o Dashboard que muestre STT min usados / disponibles, auto-applies restantes, etc.

### 4.2 Groq BYOK como feature Premium (futuro)
- [ ] Habilitar campo **Groq BYOK** solo en PREMIUM (ya existe el campo en Ajustes, pero sin restricción de plan).
- [ ] Si el usuario PREMIUM trae su propia key Groq, no consume cuota del proyecto → permite subir límite o dejarlo "sin tope" para esa key.
- [ ] Documentar en onboarding de PREMIUM como "desbloquea STT sin límites con tu key".

### 4.3 Analíticas y métricas operacionales
- [ ] Logging de consumo por usuario y feature (STT segundos, LLM tokens estimados, auto-applies generados).
- [ ] Dashboard interno (Grafana / Metabase sobre Neon/Postgres) para monitorear top consumers y detectar abuso.
- [ ] Alertas cuando un usuario supera el 80% de su cuota mensual (email o in-app).
- [ ] Métricas de conversión: trial → PRO, PRO → PREMIUM.

### 4.4 Experimentación de precios
- [ ] A/B test en landing: precio mensual vs. precio anual con descuento.
- [ ] Considerar plan anual con ~20% descuento respecto al mensual.
- [ ] Evaluar si TheirStack en PRO (modo muy capado: 1 resultado/consulta, 5/día) puede ser upsell hacia PREMIUM.
- [ ] Revisar límites de STT a los 3 meses de lanzamiento con datos reales de consumo por plan.

### 4.5 Anti-abuso y resiliencia
- [ ] Rate limiting global por IP en endpoints STT y LLM fallback.
- [ ] Detección de patrones de scraping desde la app (job search demasiado frecuente).
- [ ] Circuit breaker en Groq STT: si se agota cuota del proyecto, retornar error informativo en lugar de fallar silenciosamente.

### 4.6 Onboarding y activación
- [ ] Tour guiado en primera apertura post-pago: conectar OpenRouter BYOK → probar Ghost → primera entrevista mock.
- [ ] Email post-trial con resumen de uso y CTA a plan de pago.
- [ ] Checklist de "primera semana" en el panel de la app.

---

## 5. Próximas acciones inmediatas

- [ ] **Actualizar pricing page** (`epsylon.pacoal.dev`) con los nuevos límites (sin "ilimitado", con "Fair Use").
- [ ] **Mover Stealth Suite al gate de PREMIUM** en el backend (verificar plan en el middleware antes de responder a los endpoints de cursor virtual / camuflaje Win32 / control de capturas).
- [ ] **Capar STT por plan** en `POST /interview/stt/transcribe`: consultar plan del usuario y acumular minutos en contador mensual.
- [ ] **Capar Auto-Apply** en generación de cartas/follow-ups: consultar contador mensual por `userId`.
- [ ] **Actualizar `DEPLOYMENT.md`** con checklist de variables de entorno para cuotas (límites por plan como env vars para cambiarlos sin redeploy).
- [ ] Definir precios en € en Stripe (mensual + anual) y actualizar Price IDs en env.
- [ ] Revisión a los 90 días: ajustar límites de STT y auto-apply según datos reales.

---

*Documento de estrategia interna — no publicar en landing directamente.*
