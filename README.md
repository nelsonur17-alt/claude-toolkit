# Claude Toolkit — Backup de Skills

Backup privado de las 95 skills instaladas en Claude Code (`~/.agents/skills/`).  
Invocar cualquier skill con `/nombre-skill` dentro de Claude Code.

---

## Backup y recuperación

**Agregar skill nueva al backup** (después de `npx skills add`):
```bash
cd ~/.agents/skills && git add . && git commit -m "Add [nombre-skill]" && git push
```

**Recuperar todo en un PC nuevo:**
```bash
git clone https://github.com/nelsonur17-alt/claude-toolkit.git ~/.agents/skills
```

---

## Catálogo de skills

### Diseño y UI

| Skill | Qué hace |
|-------|----------|
| `impeccable` | Sistema de diseño de alta calidad. Flujo: shape → design brief → build → iterate visualmente hasta que sea digno de mostrar |
| `shape` | Crear un design brief estructurado antes de implementar cualquier UI. Base de impeccable |
| `critique` | Evaluar calidad de diseño con heurísticas y scoring. Detecta problemas antes de que el usuario los vea |
| `emil-design-eng` | Filosofía Emil Kowalski: easings custom, :active states físicos, stagger animations, micro-detalles que se sienten premium |
| `redesign-existing-projects` | Mejoras visuales a proyectos ya existentes: font swap, shadow tinting, scroll reveal, bento grids |
| `high-end-visual-design` | Principios de diseño visual de alta gama aplicados a interfaces |
| `design-taste-frontend` | Criterio visual avanzado para frontend — la diferencia entre "funciona" y "se siente bien" |
| `stitch-design-taste` | Sistema de criterio de diseño Stitch: consistencia visual, ritmo espacial, jerarquía tipográfica |
| `layout` | Patrones de layout avanzados: grids, bento, asimétricos, composición visual |
| `typeset` | Tipografía como sistema: escala, ritmo, jerarquía, legibilidad en pantalla |
| `colorize` | Sistemas de color: paletas, tokens, contraste, dark mode, color semántico |
| `animate` | Animaciones e interacciones: timing, easing, propósito, motion design sin excesos |
| `minimalist-ui` | UI minimalista: reducir sin perder claridad ni funcionalidad |
| `industrial-brutalist-ui` | Estética industrial/brutalista: crudo, directo, intencional |
| `delight` | Micro-detalles que generan deleite: empty states, loading states, feedback táctil, sorpresa |
| `polish` | Pulir una UI existente: detectar inconsistencias, espaciado roto, estados faltantes |

---

### Video y animación (HyperFrames)

| Skill | Qué hace |
|-------|----------|
| `hyperframes` | Convertir HTML/CSS animado en video MP4 con FFmpeg. Sistema principal — define house style, paletas, motion principles |
| `hyperframes-cli` | Interfaz CLI de HyperFrames: comandos para renderizar, previsualizar y exportar frames |
| `hyperframes-media` | Integración de media (imágenes, video, audio) dentro de frames de HyperFrames |
| `hyperframes-registry` | Gestión del registry de componentes y bloques reutilizables de HyperFrames |
| `website-to-hyperframes` | Flujo en 7 pasos para convertir un sitio web existente en video animado |
| `remotion-to-hyperframes` | Migrar animaciones de Remotion (React) a HyperFrames (HTML puro) |
| `animejs` | Librería Anime.js: animaciones JS declarativas, timelines, morphing SVG |
| `css-animations` | Animaciones CSS puras: keyframes, transitions, transforms, performance |
| `gsap` | GSAP (GreenSock): animaciones profesionales, ScrollTrigger, timelines complejos |
| `lottie` | Lottie: reproducir animaciones After Effects exportadas como JSON en web/mobile |
| `tailwind` | Tailwind CSS: utility-first, configuración, componentes, dark mode |
| `three` | Three.js: escenas 3D en el browser, geometrías, materiales, luces, cámara |
| `waapi` | Web Animations API: animaciones nativas del browser sin librerías externas |

---

### Escritura y contenido

| Skill | Qué hace |
|-------|----------|
| `copywriting` | Copy de ventas y persuasión con frameworks probados (PAS, AIDA, antes/después/puente) |
| `copy-editing` | Editar y mejorar copy existente: claridad, tono, flujo, eliminar relleno |
| `bolder` | Hacer el copy más audaz, directo y con personalidad — menos corporativo |
| `quieter` | Hacer el copy más sobrio, menos agresivo — cuando bolder se fue de las manos |
| `distill` | Condensar texto largo en su esencia sin perder el mensaje |
| `adapt` | Adaptar contenido de un formato/canal/audiencia a otro |
| `optimize` | Optimizar copy existente para conversión o claridad |
| `social-content` | Contenido para redes sociales: LinkedIn, Twitter/X, Instagram. Formatos, hooks, estructura |
| `cold-email` | Emails en frío: personalización, estructura, subject lines, follow-ups |
| `email-sequence` | Secuencias de email: onboarding, nurture, recuperación, lanzamiento |
| `brainstorming` | Sesiones de ideación estructuradas con companion visual |
| `clarify` | Clarificar ideas confusas o mensajes ambiguos antes de escribir |
| `humanizer` | Eliminar señales de texto generado por IA: 29 patrones detectados (inflación de significado, vocabulario IA, em dash en exceso, etc.). Incluye calibración de voz personal con muestras de escritura propia |
| `full-output-enforcement` | Forzar output completo sin truncamientos — útil para documentos largos |
| `article-writing` | Artículos largos estructurados: investigación, estructura, argumentación, CTAs [ECC] |
| `brand-voice` | Definir y mantener voz de marca consistente en todos los canales [ECC] |
| `market-research` | Research de mercado estructurado: TAM, competidores, tendencias, síntesis [ECC] |

---

### Marketing y publicidad

| Skill | Qué hace |
|-------|----------|
| `ads` | Suite completa de publicidad paga: estrategia, copy, creativos, auditoría |
| `ads-meta` | Ads específicos para Meta (Facebook + Instagram): formatos, copy, targeting |
| `ads-google` | Ads para Google: Search, Display, Performance Max, extensiones |
| `ads-linkedin` | Ads para LinkedIn: B2B, formatos Sponsored Content, Message Ads |
| `ads-tiktok` | Ads para TikTok: creativos nativos, hooks, tendencias |
| `ads-youtube` | Ads para YouTube: pre-roll, skippable, scripts de video |
| `ads-apple` | Ads para Apple Search Ads: ASO + paid, keywords |
| `ads-microsoft` | Ads para Microsoft/Bing: búsqueda, importación desde Google |
| `ads-plan` | Planificación estratégica de campañas pagas: objetivos, presupuesto, canales |
| `ads-budget` | Distribución y optimización de presupuesto entre canales |
| `ads-audit` | Auditoría de cuentas publicitarias existentes: qué funciona, qué no, qué arreglar |
| `ads-competitor` | Análisis de publicidad de competidores: creativos, mensajes, estrategia |
| `ads-create` | Creación de ads desde cero: brief → copy → creativos |
| `ads-generate` | Generación masiva de variaciones de ads para testing |
| `ads-creative` | Dirección creativa para ads: concepto, visual, storytelling |
| `ad-creative` | Creativo individual de ad: headline, descripción, CTA, imagen |
| `ads-landing` | Landing pages optimizadas para tráfico pago |
| `ads-dna` | Extraer el ADN de marca para aplicarlo a ads (tono, valores, diferenciación) |
| `ads-photoshoot` | Brief para sesiones de foto/video orientado a assets publicitarios |
| `paid-ads` | Framework general de publicidad paga: planning, ejecución, optimización |
| `marketing-ideas` | Generación de ideas de marketing por categoría y canal |
| `marketing-psychology` | Principios de psicología aplicados a marketing: sesgos, persuasión, comportamiento |
| `product-marketing-context` | Configurar contexto del producto (audiencia, propuesta de valor, tono) que leen todas las skills de marketing automáticamente |

---

### SEO

| Skill | Qué hace |
|-------|----------|
| `seo-audit` | Auditoría SEO completa: técnico, contenido, links, velocidad |
| `ai-seo` | SEO para la era de IA: optimización para Search Generative Experience, AIO |
| `programmatic-seo` | SEO programático: páginas a escala, plantillas, datos estructurados |
| `schema-markup` | Schema.org markup: tipos, implementación, rich results |
| `site-architecture` | Arquitectura de sitio: estructura de URLs, navegación, silos de contenido |
| `competitor-alternatives` | Páginas de "[competidor] alternativas" para capturar tráfico de búsqueda |

---

### CRO y conversión

| Skill | Qué hace |
|-------|----------|
| `page-cro` | Optimización de páginas para conversión: estructura, jerarquía, CTAs |
| `form-cro` | Optimización de formularios: campos, fricción, validación, progreso |
| `popup-cro` | Popups y overlays: timing, triggers, copy, diseño |
| `onboarding-cro` | Flujo de onboarding: activación, primer valor, reducir fricción |
| `signup-flow-cro` | Flujo de registro: pasos, campos, social login, expectativas |
| `paywall-upgrade-cro` | Pantallas de upgrade y paywall: propuesta de valor, urgencia, pricing |
| `ab-test-setup` | Configuración de A/B tests: hipótesis, variantes, muestra, métricas |
| `analytics-tracking` | Implementación de tracking: eventos, GA4, GTM, conversiones |

---

### Estrategia de producto y negocio

| Skill | Qué hace |
|-------|----------|
| `pricing-strategy` | Estrategia de precios: tiers, psicología de precios, freemium vs. trial |
| `launch-strategy` | Estrategia de lanzamiento: secuencia, canales, momentum, métricas |
| `free-tool-strategy` | Estrategia de herramientas gratuitas como canal de adquisición |
| `lead-magnets` | Lead magnets: formatos, temas, distribución, conversión |
| `referral-program` | Programas de referidos: mecánica, incentivos, viral loop |
| `churn-prevention` | Prevención de churn: detección temprana, intervención, winback |
| `customer-research` | Investigación de clientes: entrevistas, surveys, análisis de reseñas |
| `content-strategy` | Estrategia de contenido: pilares, calendario, distribución, métricas |
| `sales-enablement` | Materiales de ventas: decks, one-pagers, scripts, objeciones |
| `revops` | Revenue Operations: procesos, automatización, alineación ventas-marketing |

---

### Universidad

| Skill | Qué hace |
|-------|----------|
| `university-docs` | Resolver y entregar actividades de Asturias como .docx en APA 7: portada, desarrollo con cálculos, aplicación práctica y referencias. Incluye estilo visual (Times New Roman, tablas sobrias, sin recuadros, texto humanizado), proceso de estandarización para estadística, checklist de calidad y plantilla de portada |

---

### Desarrollo y arquitectura

| Skill | Qué hace |
|-------|----------|
| `systematic-debugging` | Diagnóstico de bugs con metodología: root cause tracing, hipótesis, verificación |
| `test-driven-development` | TDD: escribir tests primero, red-green-refactor, anti-patterns |
| `tdd-workflow` | ⭐ TDD con ciclo gateado RED→GREEN→REFACTOR con evidencia obligatoria por paso. Acepta plan.md como input. Más robusto que test-driven-development — usar este en proyectos reales [ECC] |
| `verification-before-completion` | Verificar que el trabajo realmente funciona antes de declararlo terminado |
| `verification-loop` | ⭐ Verificación en 6 fases: build, type check, lint, tests con coverage, security grep y diff review. Produce reporte PASS/FAIL. Más completo que verification-before-completion [ECC] |
| `subagent-driven-development` | Arquitectura multi-agente: orquestar subagentes para tareas paralelas |
| `dispatching-parallel-agents` | Despachar múltiples agentes en paralelo para maximizar velocidad |
| `executing-plans` | Ejecutar planes de implementación paso a paso con trazabilidad |
| `writing-plans` | Escribir planes de implementación claros y ejecutables |
| `writing-skills` | Crear nuevas skills de Claude Code: estructura, SKILL.md, referencias |
| `finishing-a-development-branch` | Checklist para cerrar una rama de desarrollo: tests, review, merge |
| `requesting-code-review` | Preparar y solicitar code reviews efectivos |
| `receiving-code-review` | Recibir y procesar feedback de code review |
| `using-git-worktrees` | Git worktrees para trabajar en múltiples ramas simultáneamente |
| `security-review` | Revisión de seguridad de código: OWASP top 10, injection, auth, secrets, dependencias [ECC] |
| `e2e-testing` | Tests end-to-end: flujos completos de usuario, Playwright/Cypress, CI integration [ECC] |
| `api-design` | Diseño de APIs REST: contratos, versionado, error handling, documentación OpenAPI [ECC] |
| `database-migrations` | Migraciones de base de datos: estrategia, rollback, zero-downtime, Supabase/Postgres [ECC] |
| `git-workflow` | Workflow de Git: branching, commits semánticos, PRs, squash, rebase [ECC] |
| `context-budget` | Gestión del presupuesto de contexto en sesiones largas: qué compactar, cuándo limpiar [ECC] |
| `continuous-learning` | Extrae patrones de sesiones completadas y los guarda como instintos reutilizables [ECC] |
| `deep-research` | Research estructurado con múltiples fuentes, síntesis y verificación cruzada [ECC] |
| `prompt-optimizer` | Optimizar prompts para Claude: claridad, eficiencia de tokens, system prompts [ECC] |

#### Por stack (ECC)

| Skill | Qué hace |
|-------|----------|
| `react-native-patterns` | Patrones React Native + Expo: navegación, estado, performance, offline-first [ECC] |
| `python-patterns` | Patrones Python: estructura de proyectos, typing, dataclasses, async [ECC] |
| `python-testing` | Testing en Python: pytest, fixtures, mocks, coverage, Flask testing [ECC] |
| `postgres-patterns` | Patrones PostgreSQL: queries avanzadas, índices, RLS, Supabase-specific [ECC] |
| `nextjs-turbopack` | Patrones Next.js 15 con Turbopack: App Router, Server Components, optimización [ECC] |

---

### Finanzas e inversión

| Skill | Qué hace |
|-------|----------|
| `analizar-activo` | Análisis fundamental sistemático de acciones, ETFs y fondos. Framework de 7 secciones adaptado al tipo de activo (acción / ETF un solo activo / ETF canasta / fondo activo). Incluye: valuación (PEG, Forward P/E), salud financiera por sector, consensus de analistas, resumen en lenguaje simple, preguntas anti-FOMO y recomendación con horizonte de tiempo claro. Nunca inventa datos — cada métrica lleva fuente y timestamp. |

---

### Meta-skills (gestión de Claude)

| Skill | Qué hace |
|-------|----------|
| `evaluate-skills` | Analizar skills/MCPs/librerías candidatas antes de instalar: redundancia, conflictos, tipo, potencial de uso, recomendación |
| `find-skills` | Buscar entre todas las skills instaladas por nombre o caso de uso |
| `using-superpowers` | Maximizar capacidades de Claude Code: herramientas avanzadas, patrones |
| `overdrive` | Modo de máxima capacidad: calidad sobre velocidad, sin atajos |
| `audit` | Auditoría general de un proyecto, sistema, o proceso |

---

## Claude Code Agents (`~/.claude/agents/`)

Subagentes especializados que Claude activa autónomamente (descripciones con `PROACTIVELY` / `MUST BE USED`) o que puedes invocar con: *"Usa el agente X para..."*

### Agentes generalistas (agency-agents)

| Agente | Qué hace | Cuándo usarlo |
|--------|----------|---------------|
| `engineering-mobile-app-builder` | React Native, Swift, Flutter. Optimización de batería, offline-first, push notifications, App Store | Features de Faro — delegar implementación mobile |
| `engineering-backend-architect` | Diseño de APIs, esquemas de BD, microservicios, seguridad, caching. Respuestas <200ms | Arquitectura de Faro backend o escalado de Control Center |
| `engineering-code-reviewer` | Revisión en 5 dimensiones: corrección, seguridad, mantenibilidad, performance, testing. Severidades 🔴🟡💭 | Antes de hacer commit o deploy en cualquier proyecto |
| `testing-reality-checker` | Validación final antes de producción. Busca activamente qué está mal, requiere evidencia visual, por defecto dice "NEEDS WORK" | Última revisión antes de lanzar cualquier feature a producción |

### Agentes especializados (ECC)

| Agente | Activación | Qué hace |
|--------|-----------|----------|
| `build-error-resolver` | Automática al fallar un build | Arregla errores de build y TypeScript con diffs mínimos. No toca arquitectura. |
| `react-build-resolver` | Automática en fallo de build React | Hydration mismatches, server/client boundaries, Next.js/Vite/Turbopack |
| `database-reviewer` | Automática al escribir SQL | Queries, schemas, migraciones, RLS — con prácticas específicas de Supabase |
| `typescript-reviewer` | Automática en proyectos TS | Type safety, async correctness, patrones idiomáticos. Para Soul, Catálogo DIVA, Faro |
| `python-reviewer` | Automática en proyectos Python | PEP 8, type hints, seguridad y performance. Para Control Center Flask |
| `security-reviewer` | Automática al manejar inputs de usuario | OWASP Top 10, injection, SSRF, secrets expuestos |
| `silent-failure-hunter` | Manual | Busca errores silenciosos: catch vacíos, fallbacks incorrectos, errores que no propagan |
| `performance-optimizer` | Manual | Bundle size, memory leaks, render optimization, mejoras algorítmicas |
| `refactor-cleaner` | Manual | Elimina dead code con knip/depcheck. Para limpiezas de proyecto |

**Recuperar en PC nuevo:**
```bash
mkdir -p ~/.claude/agents
# Agentes generalistas: https://github.com/msitarzewski/agency-agents
# Agentes ECC: copiar desde agents/ en este mismo repo
cp agents/*.md ~/.claude/agents/
```

---

## MCP Servers (`~/.claude/claude.json`)

| MCP | Qué hace |
|-----|----------|
| `n8n-mcp` | Acceso a documentación completa de 1,396 nodos de n8n. Sin credenciales = documentación; con `N8N_API_URL` + `N8N_API_KEY` = crea y ejecuta workflows |

---

## Librerías a considerar en proyectos nuevos

| Librería | Cuándo usarla |
|----------|--------------|
| `lightrag-hku` | Cuando la IA necesite recordar historial del usuario o consultar un corpus de documentos. RAG con búsqueda vectorial + grafo de conocimiento. Alternativa a flujos manuales PDF → MD → embeddings en n8n |
