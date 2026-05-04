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
| `verification-before-completion` | Verificar que el trabajo realmente funciona antes de declararlo terminado |
| `subagent-driven-development` | Arquitectura multi-agente: orquestar subagentes para tareas paralelas |
| `dispatching-parallel-agents` | Despachar múltiples agentes en paralelo para maximizar velocidad |
| `executing-plans` | Ejecutar planes de implementación paso a paso con trazabilidad |
| `writing-plans` | Escribir planes de implementación claros y ejecutables |
| `writing-skills` | Crear nuevas skills de Claude Code: estructura, SKILL.md, referencias |
| `finishing-a-development-branch` | Checklist para cerrar una rama de desarrollo: tests, review, merge |
| `requesting-code-review` | Preparar y solicitar code reviews efectivos |
| `receiving-code-review` | Recibir y procesar feedback de code review |
| `using-git-worktrees` | Git worktrees para trabajar en múltiples ramas simultáneamente |

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

Subagentes especializados que Claude activa en flujos agénticos. Se invocan con: *"Usa el agente X para..."*

| Agente | Qué hace | Cuándo usarlo |
|--------|----------|---------------|
| `engineering-mobile-app-builder` | React Native, Swift, Flutter. Optimización de batería, offline-first, push notifications, App Store | Features de Faro — delegar implementación mobile |
| `engineering-backend-architect` | Diseño de APIs, esquemas de BD, microservicios, seguridad, caching. Respuestas <200ms | Arquitectura de Faro backend o escalado de Control Center |
| `engineering-code-reviewer` | Revisión en 5 dimensiones: corrección, seguridad, mantenibilidad, performance, testing. Severidades 🔴🟡💭 | Antes de hacer commit o deploy en cualquier proyecto |
| `testing-reality-checker` | Validación final antes de producción. Busca activamente qué está mal, requiere evidencia visual, por defecto dice "NEEDS WORK" | Última revisión antes de lanzar cualquier feature a producción |

**Recuperar en PC nuevo:**
```bash
mkdir -p ~/.claude/agents
# Clonar y copiar manualmente los 4 archivos desde:
# https://github.com/msitarzewski/agency-agents
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
