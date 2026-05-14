---
name: analizar-activo
description: Use this skill when the user wants to evaluate or analyze a stock, ETF, mutual fund, or other publicly-traded investment asset. Triggers include phrases like "analiza X", "evalúa Y", "qué opinas de Z", "vale la pena comprar W", "/analizar-activo TICKER", or mentions of specific tickers (NVDA, NU, IBIT, MCHI, etc.) in an investment context. Performs systematic fundamental analysis following a 7-section framework adapted to asset type (stock / single-asset ETF / basket ETF / active fund), with technical depth plus a plain-language summary and a clear recommendation tied to investment horizon.
---

# Análisis de Activos Financieros — Skill

Skill para evaluar acciones, ETFs y fondos de inversión usando análisis fundamental sistemático. Adaptada al método del creador "DLP" (validado contra estándares CFA: PEG ratio de Peter Lynch, ROE, Forward P/E, analyst consensus) con extensiones para banca, REITs, y ETFs.

---

## 🚨 REGLAS INVIOLABLES

1. **NUNCA inventar datos.** Si un dato no se encuentra vía WebSearch, decir explícitamente "no disponible" o "no pude obtener este dato". No estimar, no aproximar, no "completar con lo más probable".
2. **CADA dato lleva fuente + timestamp.** Mostrar de dónde viene el dato y cuándo se consultó.
3. **Disclaimer obligatorio al inicio** del output.
4. **Si más del 30% de datos clave faltan:** devolver evaluación PARCIAL con advertencia grande al inicio. No forzar conclusión.
5. **Esto NO es asesoría financiera.** Es framework de evaluación de información pública.

---

## Paso 1: Detectar tipo de activo

Identificar el tipo basado en el ticker o nombre que dio el usuario:

| Tipo | Ejemplos | Cómo identificar |
|---|---|---|
| **Acción individual** | NVDA, NU, AAPL, EC | Empresa cotizada en bolsa con un negocio operativo |
| **ETF de un solo activo** | IBIT, FBTC, GLD, SLV | Wrapper sobre cripto, commodity, o un solo activo |
| **ETF de canasta diversificada** | SPY, VOO, MCHI, KWEB, EWZ | Replica un índice o canasta de empresas |
| **Fondo activo / FIC / mutual fund** | Acciones Dinámicas (Trii), PEI, FIC | Gestor activo, no es un índice |

Si no es claro, preguntar al usuario o asumir el tipo más probable y declararlo.

---

## Paso 2: Recopilar datos vía WebSearch

Cascada de fuentes (en orden de preferencia):

1. **Yahoo Finance** (`finance.yahoo.com/quote/TICKER`)
2. **Stock Analysis** (`stockanalysis.com/stocks/ticker`)
3. **GuruFocus** (`gurufocus.com/stock/TICKER`)
4. **Macrotrends** (para datos históricos)
5. **Investing.com** (fallback general)
6. **SimplyWall.St** (para análisis y consensus)
7. **CNN Markets / Robinhood** (precios y básicos)
8. **Sitio oficial del emisor** (para ETFs: iShares.com, Vanguard, etc.)

Hacer **3-5 búsquedas en paralelo** para eficiencia. Buscar:
- Precio actual + 52w range + variación día
- P/E, Forward P/E, PEG, EPS
- ROE, financials, balance sheet
- Analyst consensus + price targets
- Historical returns por año

---

## Paso 3: Aplicar el framework adaptado al tipo

### 📈 Para ACCIONES INDIVIDUALES (7 secciones)

#### 1. Identidad
- Nombre completo de la empresa + ticker
- Sector y subsector
- Geografía principal de operación
- Modelo de negocio en 1-2 líneas

#### 2. ¿Dónde está hoy?
| Métrica | Mostrar |
|---|---|
| Precio actual | $X (fecha/hora, fuente) |
| Variación día | $ y % |
| Mín 52s | $X |
| Máx 52s | $X |
| Posición en rango 52s | % calculado: `(actual - min) / (max - min) * 100` |

**Interpretación con semáforo:**
- 0-30% del rango → 🟢 Cerca de mínimos (potencial oportunidad o señal de problema)
- 30-70% del rango → 🟡 Punto medio
- 70-100% del rango → 🔴 Cerca de máximos (momentum bueno o riesgo de techo)

#### 3. ¿Está cara?
| Métrica | Valor | Semáforo |
|---|---|---|
| PEG | X | 🟢 <1 / 🟡 1-1.5 / 🔴 >1.5 |
| Forward P/E | X | 🟢 <S&P 500 / 🟡 ~S&P / 🔴 >S&P significativamente |
| P/E TTM | X | Comparar con S&P 500 (~22x) y peers del sector |

**Verdicto:** 🟢 BARATA / 🟡 JUSTA POR CRECIMIENTO / 🔴 CARA

#### 4. Rendimiento por año
Returns anuales últimos 4-5 años + YTD del año actual. Mostrar en tabla con semáforos verde (positivo) y rojo (negativo).

#### 5. ¿Empresa sana?

**IMPORTANTE: Adaptar las métricas al sector:**

- **Banco / Financiera**: ROE, Net Income growth YoY, Capital Tier 1, NPL ratio, Cost of Funding, Net Interest Margin
- **REIT (real estate)**: FFO, AFFO, Debt/Equity, Occupancy rate, Dividend yield
- **Tech / Industrial / Consumer**: Cash vs Debt, Current Ratio, ROE, EPS growth, Free Cash Flow
- **Utility**: Dividend yield, Payout ratio, Debt/EBITDA
- **Energy / Petróleo**: Reservas, costo de extracción, dividend yield, breakeven

Calcular **Score de salud 0-100** basado en las 4 métricas más relevantes del sector.

#### 6. ¿Qué dicen los expertos?
| Métrica | Valor |
|---|---|
| Sentimiento agregado | COMPRAR / NEUTRAL / VENDER |
| # analistas en consensus | X de Y |
| Precio objetivo promedio | $X |
| Precio objetivo low / high | $X / $X |
| Upside vs precio actual | % |
| Crecimiento esperado ingresos | % YoY |
| Crecimiento esperado ganancias | % YoY |

#### 7. Veredicto final
| Dimensión | Score |
|---|---|
| Posicionamiento | 🟢🟡🔴 |
| Valuación | 🟢🟡🔴 |
| Salud financiera | 🟢🟡🔴 |
| Consensus | 🟢🟡🔴 |
| Riesgos pendientes | 🟢🟡🔴 |

**Score global ponderado 0-100** y veredicto final: 🟢 COMPRAR / 🟡 ESPERAR / 🔴 EVITAR.

---

### 💰 Para ETF DE UN SOLO ACTIVO (ej. IBIT, GLD)

1. **Identidad**: qué activo replica, emisor (BlackRock, Fidelity, etc.), custodio del activo
2. **¿Dónde está hoy?**: precio del ETF + precio del activo subyacente, 52w range de ambos
3. **Tracking y costos**: expense ratio, tracking error vs underlying, premium/discount vs NAV
4. **Liquidez**: AUM (assets under management), volumen diario promedio
5. **El activo subyacente**: tesis del activo (BTC, oro, plata), performance histórico, drivers
6. **¿Qué dicen los expertos?** (sobre el activo subyacente, si aplica)
7. **Veredicto final**

---

### 🌍 Para ETF DE CANASTA (ej. SPY, MCHI, KWEB)

1. **Identidad**: índice que replica, emisor, # de holdings, geographic exposure
2. **¿Dónde está hoy?**: precio del ETF, 52w range, % del rango
3. **Composición**: top 10 holdings (% del fondo), sector breakdown (top 5 sectores con %)
4. **¿Caro o barato?**: P/E ponderado del índice, P/B ponderado, comparar con S&P 500
5. **Rendimiento histórico**: returns 1Y, 3Y, 5Y vs S&P 500
6. **Costos y eficiencia**: expense ratio, tracking error, dividend yield
7. **Veredicto final**

---

### 🏛️ Para FONDOS ACTIVOS / FICs

1. **Identidad**: nombre, gestor/administradora, estrategia declarada, fecha creación
2. **Tamaño y liquidez**: AUM, flujos recientes (entradas/salidas), tipo de redención
3. **Performance vs benchmark** (LO MÁS IMPORTANTE): returns 1Y/3Y/5Y del fondo vs S&P 500 (o benchmark relevante), **después de comisiones**
4. **Composición actual**: top holdings, sector mix, concentración
5. **Comisiones totales**: management fee + performance fee + entrada/salida + IVA
6. **Riesgos específicos**: liquidez, concentración, drawdowns históricos (peor caída)
7. **Veredicto final**: ¿el gestor agrega valor sobre el benchmark **después de comisiones**? Si no le gana al S&P 500 después de comisiones, evitar.

---

## Paso 4: Sección final OBLIGATORIA — Resumen en simple

Después del análisis técnico, agregar SIEMPRE:

### 🗣️ En palabras simples

4-6 frases sin tecnicismos, como explicándole a un amigo que no sabe nada de finanzas. Incluir:
- Qué es la empresa/activo (1 frase)
- Cómo le va al negocio (1-2 frases con números traducidos)
- Si está cara o barata (1 frase con analogía cotidiana)
- Qué dicen los expertos (1 frase)
- Riesgos en palabras simples (2-3 viñetas)

### 🧠 Antes de comprar, hazte estas 5 preguntas

1. ¿Por qué estoy considerando esto HOY y no antes?
2. ¿Tengo tesis clara o estoy reaccionando a una subida/bajada reciente?
3. ¿La plata que voy a invertir tiene un propósito de corto plazo?
4. ¿Cuánto perdería emocionalmente si esto baja 30%?
5. ¿En qué condición vendería?

Si no puedes responder con confianza, **espera**.

### ✅ Recomendación clara con horizonte de tiempo

**Formato obligatorio** (la frase exacta que el usuario validó):

> **[Buena opción / Opción regular / Evitar]** para invertir si vas a dejar la plata quieta al menos **[N]** años. **No es buena opción** si la necesitas pronto — [razón corta en 1 frase].
>
> **Plata que pongas acá:** que sea plata que no necesites de aquí a **[N]** años. Si la necesitas antes, mejor déjala en [alternativa específica: Lulo, CDT, fondo de bajo riesgo].

**Cálculo del horizonte recomendado (N años):**
- Acciones growth/tech volátiles: **3-5 años**
- Acciones value/dividendos estables: **5-10 años**
- ETFs de canasta amplia (S&P 500, MSCI World): **5-10 años**
- ETF de cripto (BTC, ETH): **5-10 años** (alta volatilidad)
- ETF China / emerging markets: **5-10 años**
- Commodities (oro, plata): **5-10 años**
- Fondos activos: depende del lockup + estrategia

### ✍️ Tesis para tu nota de inversión (copy-paste)

Frase tipo a generar:
> _"Compré X acciones de TICKER a $Y el FECHA. Tesis: [3 líneas concretas]. Vendo si: [criterio claro]. Reviso esto en [tiempo, típicamente 6 meses o 1 año]."_

---

## Paso 5: PERSISTENCIA — Guardar el análisis como archivo

**Obligatorio:** después de mostrar el análisis completo en el chat, **generar un archivo Markdown** con todo el contenido.

### Ubicación y nombre del archivo

**Carpeta:** `C:\Users\ASUS\Documents\Finanzas\Analisis\`
- Si la carpeta no existe, créala con `mkdir -p` antes de escribir.

**Nombre del archivo:** `YYYY-MM-DD_TICKER.md`
- Ejemplo: `2026-05-14_NU.md`
- Si ya existe un archivo con ese nombre (porque se analizó el mismo activo el mismo día), agregar sufijo: `2026-05-14_NU_v2.md`, `_v3.md`, etc.

### Contenido del archivo

El archivo guardado debe contener **el análisis completo** que se mostró en el chat — incluye:
1. Header con disclaimer + fecha de consulta + fuentes
2. Las 7 secciones del análisis
3. Sección "En palabras simples"
4. Las 5 preguntas anti-FOMO
5. Recomendación con horizonte
6. Tesis sugerida (copy-paste)
7. Riesgos específicos
8. Footer con timestamp de cuándo se guardó el archivo
9. **Una sección vacía al final llamada "## Decisión Tomada"** — para llenar después si el usuario decide comprar

### Mensaje al final del chat

Después de mostrar el análisis en chat, agregar al final:

```
---

📄 **Análisis guardado en:** `C:\Users\ASUS\Documents\Finanzas\Analisis\YYYY-MM-DD_TICKER.md`

¿Vas a comprar? Si sí, decime:
1. **Monto** que vas a invertir
2. **Precio de entrada** al que vas a comprar (verifica en Trii antes)
3. **Tu tesis final** (puede ser la que sugerí o una propia)

Anoto la decisión en el mismo archivo para que tengas trazabilidad completa.
```

---

## Paso 6: REGISTRO DE DECISIÓN (si el usuario confirma compra)

Si en el siguiente turno el usuario responde con info de compra (monto, precio, tesis), **modificar el archivo** que se generó en el Paso 5 agregando una sección al final:

```markdown
---

## 💰 Decisión Tomada

**Fecha de decisión:** YYYY-MM-DD HH:MM
**Acción tomada:** Compra confirmada
**Monto invertido:** $X COP (o USD según aplique)
**Precio de entrada:** $Y por unidad
**Cantidad de unidades:** Z (calcular: monto / precio)
**Plataforma de compra:** [Trii / otro]

### Tesis final (palabras del usuario):
> [Lo que Nelson escribió como tesis]

### Criterio de salida:
- [Vendo si X] (de la tesis)
- [Reviso en Y meses] (de la tesis)

### Próximo paso operativo
- [ ] Registrar esta compra en la pestaña `Decisiones` del Excel `Finanzas_Trazabilidad.xlsx`
- [ ] Actualizar `Bitacora_Financiera.md` con la entrada nueva de portafolio
- [ ] Próxima revisión agendada para: [calcular fecha en X meses]
```

**Importante:** después de modificar el archivo, confirmar al usuario:
> "✅ Decisión registrada en el archivo. Recordá actualizar también la pestaña Decisiones del Excel y la Bitácora cuando puedas — quedan apuntados como pendientes en el archivo."

### Si el usuario dice "no compro" o "lo pienso más"

Modificar el archivo con:

```markdown
---

## 💭 Decisión: NO comprar (o postergar)

**Fecha:** YYYY-MM-DD
**Razón:** [Lo que dijo el usuario]
**Re-evaluar:** [Si dijo "lo pienso más", agendar revisión en X días/semanas]
```

Esto sirve para que en el futuro, cuando Nelson revise sus análisis pasados, vea TAMBIÉN las decisiones de "no comprar" — porque saber qué NO compraste y por qué es tan importante como saber qué compraste.

---

## Disclaimer obligatorio (al INICIO del output)

```
> **Datos consultados:** [fecha y hora exactas].
> **Fuentes:** [listar las URLs usadas].
> **Disclaimer:** Esto NO es asesoría financiera. Es framework de evaluación de información pública. Precios con delay típico 15-20 min vs real-time. El framework está basado en análisis fundamental — no incluye información privilegiada ni proyecciones internas. La decisión final es del usuario.
```

---

## Formato del output — REGLA CRÍTICA

**El análisis completo (las 7 secciones + resumen simple + tesis + riesgos) NO se muestra en el chat. Se escribe ÚNICAMENTE en el archivo Markdown.**

**En el chat, solo se muestra un RESUMEN EJECUTIVO de máximo 15 líneas** con esta estructura exacta:

```
📊 **Análisis [TICKER] completado.**

[🟢/🟡/🔴] **Veredicto:** [COMPRAR / MANTENER / ESPERAR / EVITAR]
**Score global:** XX/100

**Resumen en 2 líneas:**
[Una oración sobre la salud del activo. Una oración sobre el contexto/momentum/posicionamiento.]

**Recomendación con horizonte:**
> Buena opción si vas a dejar la plata quieta al menos [N] años. No tan buena si la necesitas pronto — [razón corta].

**Riesgos críticos** (top 2):
- [Riesgo principal en 1 línea]
- [Segundo riesgo en 1 línea]

📄 **Análisis completo en:** `C:\Users\ASUS\Documents\Finanzas\Analisis\YYYY-MM-DD_TICKER.md`

¿Vas a [comprar/vender/mantener]? Si sí, decime monto + precio + tu tesis (la registro en el mismo archivo).
```

### Lo que va en el archivo .md (NO en chat)

El archivo contiene **todo el análisis completo**:
- Disclaimer + fecha + fuentes
- Las 7 secciones detalladas (identidad, posición, valuación, rendimiento, salud, expertos, veredicto)
- Tablas con todas las métricas
- "En palabras simples"
- Las 5 preguntas anti-FOMO
- Tesis sugerida copy-paste
- Riesgos específicos
- Sección "Decisión Tomada" (vacía o llena según haya decisión)

**Razón de este split:** el chat se satura con análisis largo. El archivo .md es el lugar correcto para guardar análisis completo. El usuario revisa el archivo cuando quiera. El chat solo muestra lo que necesita para decidir si profundizar o ejecutar.

### Excepción

Solo se muestra el análisis completo en chat si el usuario explícitamente pide "muéstrame todo el análisis en chat" o "no me lo guardes en archivo".

---

## Manejo de errores y datos faltantes

### Si WebSearch falla totalmente:
> ⚠️ **NO PUDE OBTENER DATOS**: Las búsquedas web fallaron o están bloqueadas. No tengo manera de evaluar este activo en este momento. Intenta de nuevo más tarde o verifica los datos manualmente en Yahoo Finance.

### Si faltan algunos datos clave (>30%):
> ⚠️ **EVALUACIÓN PARCIAL**: No se pudieron obtener los siguientes datos: [listar]. La conclusión final puede no ser confiable. Recomiendo verificar manualmente antes de decidir.

### Si una métrica específica no existe (ej. PEG para empresa sin proyecciones):
- Mostrar "no disponible" en la celda
- Explicar por qué falta
- Continuar con el análisis usando las métricas disponibles

### Si dos fuentes dan datos ligeramente diferentes:
- Usar la fuente más reciente
- Mencionar la discrepancia: _"Precio: $13.49 (Yahoo Finance) o $14.16 (GuruFocus) — diferencia probablemente por timing intradía"_
- NO promediar fuentes

---

## Adaptaciones por industria (para sección "¿Empresa sana?")

| Industria | Métricas críticas |
|---|---|
| Banca / Financiera | ROE, Net Income growth, Capital Tier 1, NPL ratio, Cost of Funding, NIM |
| REIT / Real Estate | FFO, AFFO, Debt/Equity, Occupancy, Dividend yield |
| Tech / SaaS | Revenue growth, Gross margin, FCF, Rule of 40, ARR |
| Consumer / Retail | Same-store sales, Gross margin, Inventory turnover, EBITDA |
| Energy / O&G | Reservas, breakeven cost, dividend yield, capex/revenue |
| Utility | Dividend yield, Payout ratio, Debt/EBITDA, Regulated return on equity |
| Healthcare / Pharma | R&D as % of revenue, pipeline value, patent expirations |
| Industrial | ROIC, FCF conversion, debt/equity, backlog |

---

## Notas finales sobre criterio

1. **El horizonte de tiempo es lo más importante** que recibe el usuario. Más que el "comprar/no comprar". Una buena acción puede ser pésima inversión si el horizonte está mal.

2. **No proyectar el precio futuro.** Solo decir si el setup actual es favorable, neutral o desfavorable.

3. **Cuando hay duda, default a más conservador.** Es mejor decir "espera" que recomendar comprar sin convicción.

4. **El método DLP está validado para empresas tradicionales y growth tech.** Para activos especiales (cripto, commodities, fondos), las adaptaciones son necesarias — usar el sentido común financiero.

5. **Anti-FOMO:** si el usuario menciona "subió mucho últimamente" o "me lo voy a perder", siempre incluir advertencia explícita sobre comprar por momentum vs por tesis.
