# 🚀 Stochastic Divergence Strategy — Pine Script Strategy

**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel  

---

## 📖 Overview

**Stochastic Divergence Strategy** is a Pine Script® strategy that trades **classic divergences** between price action and the **Stochastic Oscillator**.  
It detects **bullish** and **bearish** divergences across multiple timeframes and automatically enters **long or short positions** with fixed-percentage **Stop Loss** and **Take Profit**.

The system is optimized for **major FX pairs** such as **EURUSD, USDCHF, and AUDUSD**, performing consistently from **1-minute to 1-hour** charts.  
By combining **momentum divergence** with **disciplined risk management**, it offers a robust framework for **mean-reversion** and **trend-reversal** trading.

---

## ⚙️ Input Parameters

| Parameter | Type | Description | Default Value |
|------------|------|-------------|----------------|
| `lot_size` | `int` | Contracts per trade | `1` |
| `periodK` | `int` | %K length | `14` |
| `smoothK` | `int` | %K smoothing | `1` |
| `periodD` | `int` | %D smoothing | `3` |
| `obLevel` | `int` | Overbought threshold | `80` |
| `osLevel` | `int` | Oversold threshold | `20` |
| `midLevel` | `int` | Middle reference line | `50` |
| `pivotLookbackLeft` | `int` | Bars left for pivot detection | `5` |
| `pivotLookbackRight` | `int` | Bars right for pivot detection | `5` |
| `maxBarsBack` | `int` | Max history to scan divergences | `100` |
| `removeBrokenDiv` | `bool` | Auto-delete invalidated lines | `true` |
| `useSL` | `bool` | Enable Stop Loss | `true` |
| `slPerc` | `float` | SL distance (%) | `2.0` |
| `useTP` | `bool` | Enable Take Profit | `true` |
| `tpPerc` | `float` | TP distance (%) | `4.0` |

---

## 🧠 Strategy Logic

1. **Stochastic Calculation**  
   - Classic **14-period Stochastic** is computed for %K and %D.  
   - Overbought (**80**) and oversold (**20**) levels act as reference zones.

2. **Pivot Detection**  
   - **Swing highs** and **swing lows** are identified using a **5-bar pivot** lookback.  
   - Each pivot records the **price** and the **%D value** at that bar.

3. **Divergence Identification**  
   - **Bullish divergence**: price prints a **lower low**, while %D forms a **higher low**.  
   - **Bearish divergence**: price prints a **higher high**, while %D forms a **lower high**.  
   - Only divergences within the last **100 bars** are considered.

4. **Trade Execution**  
   - **Long entry** triggered on **bullish divergence** detection.  
   - **Short entry** triggered on **bearish divergence** detection.  
   - Positions are sized according to `lot_size`.

5. **Risk Management**  
   - **Stop Loss** and **Take Profit** are set as a **percentage of entry price**.  
   - SL/TP levels are **symmetrical** for long and short trades.

6. **Visual Feedback**  
   - Divergences are drawn with **dotted lines** and **labeled** on the indicator pane.  
   - Broken divergences are **automatically removed** to keep the chart clean.

---

## 📊 Visual Examples of the Strategy

### 📊 EURUSD — 1 hour  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_1.png)

### 📊 USDCHF — 1 hour  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_2.png)

### 📊 AUDUSD — 30 minutes  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_3.png)

### 📊 AUDUSD — 15 minutes  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_4.png)

### 📊 AUDUSD — 5 minutes  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_5.png)

### 📊 AUDUSD — 3 minutes  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_6.png)

### 📊 AUDUSD — 1 minute  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b404778e1ffa6f7a1c114a3e6c52fd2ff3e65caa/Stochastic%20Divergence%20Strategy/Screenshot_7.png)
