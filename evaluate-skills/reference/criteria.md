# Criterios de evaluación de recursos

Aplicar estos criterios en el Paso 3 de evaluate-skills. No todos aplican igual a todos los tipos — adaptar según corresponda.

---

## 1. Tipo correcto para el trabajo

**Pregunta:** ¿Este recurso se instala de la forma en que el usuario espera?

- Skills (`npx skills add`) → van en `~/.agents/skills/`, disponibles como slash commands
- MCP servers → van en `~/.claude/claude.json`, disponibles como herramientas en toda sesión
- Librerías Python/npm → se instalan por proyecto, no globalmente
- Plugins de Claude Code → usan lifecycle hooks, requieren un servicio en background

Si el usuario dice "instalar esta skill" pero el recurso es un MCP server o una librería, aclarar la distinción antes de cualquier recomendación.

---

## 2. Redundancia con lo existente

**Pregunta:** ¿Hay alguna skill o MCP ya instalado que cubra el mismo caso de uso?

- Listar las skills en `~/.agents/skills/` y MCPs en `~/.claude/claude.json`
- Si hay solapamiento: ¿cuál es superior? ¿vale la pena reemplazar?
- Si son complementarias: ¿pueden coexistir sin confusión?

**Regla general:** ante la duda, conservar la que ya está funcionando. Menos es más.

---

## 3. Valor real vs. prompt wrapper

**Pregunta:** ¿Este recurso hace algo que no se logra con un buen prompt directo?

Alta valor real:
- Tiene referencias, frameworks, o conocimiento especializado empaquetado
- Orquesta flujos multi-paso complejos
- Accede a sistemas externos (MCP servers)
- Tiene criterios de calidad difíciles de articular en cada sesión

Bajo valor (probable wrapper):
- Es básicamente una instrucción de sistema genérica
- No tiene archivos de referencia ni estructura más allá del SKILL.md
- Hace algo que ya se logra pidiendo directamente

---

## 4. Potencial de uso

**Pregunta:** ¿Con qué frecuencia se usaría realmente?

- **Alto:** aplica a tareas que ocurren semanalmente o en múltiples proyectos
- **Medio:** aplica a proyectos específicos o fases específicas del trabajo
- **Bajo:** caso de uso muy puntual o hipotético, poco probable en práctica

Proyectos activos de referencia:
- **Faro** — app móvil React Native + Expo, IA con Claude, mercado colombiano
- **Control Center** — Flask + Supabase, gestión operacional interna Hunter Douglas
- **LinkedIn** — contenido de marca personal sobre IA y productividad

---

## 5. Calidad del recurso

**Preguntar:**
- ¿El repo tiene commits recientes (últimos 6 meses)?
- ¿La documentación es clara o hay que adivinar cómo usarlo?
- ¿Tiene ejemplos reales de output?
- ¿El autor tiene credibilidad en el ecosistema?

Un recurso abandonado o mal documentado es un riesgo aunque la idea sea buena.

---

## 6. Conflicto con sistemas existentes

**Pregunta:** ¿Instalar esto crearía dos sistemas haciendo lo mismo de forma divergente?

Casos críticos:
- Dos sistemas de memoria que no se sincronizan
- Dos flujos de deploy que tienen configuraciones distintas
- Dos skills para el mismo caso de uso con criterios contradictorios

Si hay conflicto potencial: elegir uno, desinstalar el otro.

---

## 7. Alineación con el stack

**Pregunta:** ¿Este recurso asume un stack diferente al de Nelson?

Stack de Nelson: Python/Flask, React Native/Expo, Supabase, Vercel, Tailwind/NativeWind.

Si el recurso asume Ruby on Rails, .NET, o tecnologías incompatibles, su valor práctico es limitado aunque la idea sea buena.

---

## 8. Instalación y mantenimiento

**Pregunta:** ¿Qué implica mantener esto instalado?

- ¿Requiere un servicio en background corriendo siempre?
- ¿Necesita credenciales o API keys adicionales?
- ¿Tiene dependencias externas que pueden romperse?
- ¿El proceso de actualización es claro?

Preferir recursos que funcionen sin fricción operacional.
