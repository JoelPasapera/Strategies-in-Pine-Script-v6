# 🚀 Estrategia Donchian Breakout — Pine Script® v6

**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel

---

## 📖 Resumen

**Estrategia Donchian Breakout** es una estrategia en Pine Script® v6 creada para capturar **rupturas (breakouts)** sobre un canal Donchian desplazado.  
La estrategia coloca una **orden Buy-Stop** en el borde superior del canal exactamente en una **hora objetivo** configurable (minuto 0). La orden permanece activa por un número limitado de horas (`validHours`) y se cancela si no se ejecuta. La salida de la posición larga se realiza mediante la **banda inferior del Donchian** como stop dinámico.

Recomendado para marcos temporales como **30m** y **1h** (EURUSD, GBPUSD), aunque puede probarse en otros activos ajustando parámetros y gestión de riesgo.

---

## ⚙️ Parámetros de entrada

| Parámetro | Tipo | Descripción | Valor por defecto |
|-----------|------|-------------|-------------------|
| `donchianLen` | `int` | Longitud del canal Donchian (lookback para máximo/mínimo) | `25` |
| `targetHour` | `int` | Hora del exchange para colocar la orden (minuto 0) | `17` |
| `validHours` | `int` | Horas de validez de la orden (si no se ejecuta, se cancela) | `60` |
| `lot_size` | `int` | Volumen de la posición (cantidad fija) | `900` |
| `initial_capital` (strategy) | `int` | Capital inicial en backtest | `1000` |
| `default_qty_type` (strategy) | `enum` | Tipo de tamaño de posición | `strategy.fixed` |
| `default_qty_value` (strategy) | `float` | Valor por defecto del tamaño | `1` |

---

## 🧠 Lógica de la estrategia

1. **Cálculo del Canal Donchian**  
   - `upperBand = ta.highest(high, donchianLen)[1]` — máximo de `donchianLen` barras cerradas previas (desplazado con `[1]` para evitar repaint).  
   - `lowerBand = ta.lowest(low, donchianLen)[1]` — mínimo equivalente.

2. **Hora objetivo y colocación de orden**  
   - En la barra que coincide con `targetHour` y `minute == 0`, se guarda `pendingPrice := upperBand` y se coloca una orden `strategy.entry(..., stop=pendingPrice, qty=lot_size)` (Buy Stop).

3. **Validez de la orden**  
   - Si la orden no se ejecuta en `validHours` (medido en barras desde `entryBarIndex`), la estrategia cancela la orden pendiente (`strategy.cancel("Long Breakout")`).

4. **Salida (exit)**  
   - Si hay una posición abierta, se aplica `strategy.exit("Exit Long", "Long Breakout", stop=lowerBand)` para cerrar la operación cuando el precio toque la banda inferior.

5. **Visualización**  
   - Se plotean `upperBand` y `lowerBand`.  
   - Se pinta el fondo en la barra objetivo y se añade una forma (`plotshape`) indicando la colocación de la orden (triángulo con texto "Buy\nStop").

---

## ⚠️ Consideraciones y recomendaciones

- El uso de `[1]` en los cálculos evita señales basadas en la barra en formación y reduce repainting.  
- `lot_size` es fijo; se recomienda adaptar a gestión de riesgo real (porcentaje de capital, `strategy.percent_of_equity`, etc.).  
- Verificar la zona horaria del servidor de TradingView antes de operar en real. `targetHour` corresponde a la hora del exchange/servidor.  
- Incluir comisiones y slippage en backtests para obtener resultados más realistas.  
- Probar en forward-test (paper trading) antes de operar con capital real. Considerar añadir filtros (ATR, sesiones, volumen) para mejorar la calidad de señales.

---

## 🔧 Cómo instalar en TradingView

1. Abrir TradingView → Pine Editor.  
2. Crear nuevo script y pegar el código incluido abajo.  
3. Guardar y añadir al gráfico. Seleccionar símbolo y timeframe preferido (ej. `EURUSD 30m / 1h`).  
4. Ejecutar el backtest en la pestaña *Strategy Tester* y ajustar parámetros según resultados.

---

## 📊 Capturas de ejemplo

- **EURUSD — 30 minutos**  
  https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_1.png

- **EURUSD — 1 hora**  
  https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_2.png

- **EURUSD — 1 hora (otro ejemplo)**  
  https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_3.png

- **GBPUSD — 30 minutos**  
  https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_4.png

- **GBPUSD — 1 hora**  
  https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_5.png

---
