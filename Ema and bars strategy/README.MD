# 📈 EMA and Bars — Pine Script Strategy

**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel  

---

## 📖 Overview

**EMA and Bars** is a Pine Script® strategy built around the **crossover of two exponential moving averages (EMAs)** combined with a **bar-based closing mechanism**.  
Its primary goal is to identify **short-term trend shifts** and capitalize on **momentum entries**, automatically closing positions after a user-defined number of bars.

This approach is ideal for traders who want a **clean, fast-reacting system** that adjusts dynamically to different assets such as **commodities, metals, and forex pairs**.

---

## ⚙️ Input Parameters

| Parameter | Type | Description | Default Value |
|------------|------|-------------|----------------|
| `lot_size` | `float` | Position size per trade | `1.0` |
| `variable` | `int` | Number of bars before position closure | `50` |
| `ema1` | `int` | Period of the first EMA | `50` |
| `ema2` | `int` | Period of the second EMA | `20` |

---

## 🧠 Strategy Logic

1. The strategy calculates two EMAs:  
   - `ema1` (default 50)  
   - `ema2` (default 20)
2. A **buy signal** is triggered when `ema2` crosses **above** `ema1` (`ta.crossover(ema50, ema20)`).
3. The system enters a **long trade** with the defined `lot_size`.
4. After a specific number of bars (`variable`), the position is automatically **closed**.
5. Both EMAs are plotted on the chart for visual tracking — orange for EMA 20 and blue for EMA 50.

This method ensures controlled trade duration and consistent exposure to new price movements.

---

# 📊 Visual examples of the strategy: Equity curve

## 🟡 Metals

**XAUUSD — Gold**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/abdf305363be34f7c41542a72b1dc8ba772f5cf0/Ema%20and%20bars%20strategy/Screenshot_2.png)

## 🛢️ Commodities

**WTI Crude Oil**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/abdf305363be34f7c41542a72b1dc8ba772f5cf0/Ema%20and%20bars%20strategy/Screenshot_1.png)
