# Skill: evaluate-skills

Analiza uno o más recursos candidatos (skills de Claude, MCP servers, librerías, plugins) antes de instalarlos. Produce un reporte estructurado con descripción, tipo, criterios de evaluación, y recomendación clara. Evita redundancias, conflictos, e instalaciones innecesarias.

## Cuándo usar esta skill

Cada vez que el usuario comparta links de GitHub, nombres de skills, o cualquier recurso que quiera agregar a su toolkit de Claude Code.

## Proceso

### Paso 0: Verificación de seguridad — SIEMPRE PRIMERO

Antes de evaluar utilidad, redundancia o cualquier otro criterio, verificar que el recurso es seguro:

1. Revisar el perfil del autor en GitHub — ¿cuándo fue creado? ¿tiene historial legítimo?
2. Revisar los archivos del repo — ¿hay ZIPs, ejecutables, o binarios pre-empaquetados?
3. Buscar el repo + "malware" en Google
4. ¿Promete algo técnicamente imposible? (Claude gratis, sin API key, bypass de límites)
5. ¿Hay integración con Telegram, webhooks a dominios desconocidos, o código ofuscado?

**Si el antivirus del usuario ya lo bloqueó → recomendación inmediata de NO instalar. Fin del análisis.**

Si pasa la verificación de seguridad, continuar con el resto de criterios.

---

### Paso 1: Identificar los candidatos

Para cada recurso compartido por el usuario:

1. Fetch del README o SKILL.md desde el repo
2. Determinar el **tipo de recurso**:
   - `skill` — tiene SKILL.md, se instala con `npx skills add`
   - `mcp-server` — se configura en `~/.claude/claude.json`
   - `python-library` — se instala con `pip install` por proyecto
   - `npm-package` — se instala con `npm install` por proyecto
   - `plugin` — usa lifecycle hooks de Claude Code (`npx [nombre] install`)
   - `otro` — especificar

   > Si el tipo no es `skill`, aclarar al usuario que la instalación es diferente a `npx skills add` antes de continuar el análisis.

### Paso 2: Inventario de lo existente

Listar las skills instaladas en `~/.agents/skills/` y los MCP servers en `~/.claude/claude.json`. Usar esto como base para detectar redundancia.

### Paso 3: Evaluar cada candidato

Para cada recurso aplicar los criterios del archivo [criteria.md](reference/criteria.md). Producir un análisis por recurso.

### Paso 4: Reporte final

Presentar el reporte con este formato:

---

## Reporte de evaluación

### Resumen

| Recurso | Tipo | Recomendación |
|---------|------|---------------|
| nombre  | skill / mcp / lib | ✅ Instalar / ❌ Omitir / ⚠️ Condicional |

---

### Análisis por recurso

Para cada candidato:

**[Nombre del recurso]**
- **Tipo:** skill / mcp-server / librería Python / etc.
- **Qué hace:** descripción en 2-3 oraciones desde el README
- **Potencial de uso:** alto / medio / bajo — con justificación concreta ligada a los proyectos actuales (Faro, Control Center, LinkedIn) o casos de uso futuros
- **Redundancia:** ¿existe algo instalado que ya cubre esto? ¿cuál?
- **Conflicto:** ¿podría crear sistemas duplicados o divergentes?
- **Alineación con el stack:** ¿encaja con Python/Flask, React Native/Expo, Supabase, Vercel?
- **Calidad del recurso:** ¿el repo está activo? ¿tiene documentación clara? ¿es un wrapper simple de prompt o agrega valor real que no se logra prompting directo?
- **Instalación:** comando exacto si se recomienda instalar
- **Recomendación:** ✅ Instalar / ❌ Omitir / ⚠️ Condicional (con condición explícita)
- **Razón:** una oración directa explicando el porqué

---

### Paso 5: Acciones sugeridas

Al final del reporte, listar las acciones concretas en orden:

1. Para cada ✅: comando de instalación listo para copiar
2. Para cada ⚠️: qué condición debe cumplirse antes de instalar
3. Para cada ❌: qué skill existente cubre el caso de uso (si aplica)
4. Si hay recursos ✅ instalados: recordar al usuario hacer backup con `cd ~/.agents/skills && git add . && git commit -m "Add [skill]" && git push`
