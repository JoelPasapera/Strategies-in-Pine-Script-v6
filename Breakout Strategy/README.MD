# 🚀 Breakout Strategy — Pine Script Strategy

**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel  

---

## 📖 Overview

**Breakout Strategy** is a Pine Script® strategy designed to capture **momentum breakouts** from well-defined price channels.  
It automatically identifies **entry and exit breakouts** based on configurable lookback periods, while managing trades through **ATR-based Stop Loss and Take Profit levels**.

The goal of this system is to trade price volatility efficiently — entering at the breakout of previous highs/lows and managing exits using volatility-adjusted risk parameters.  
This makes it a versatile model for both **trend-following** and **volatility expansion** strategies across multiple asset classes.

---

## ⚙️ Input Parameters

| Parameter | Type | Description | Default Value |
|------------|------|-------------|----------------|
| `entryLength` | `int` | Lookback period used to detect entry breakouts | `20` |
| `exitLength` | `int` | Lookback period for detecting breakout exits | `10` |
| `useSL` | `bool` | Enable or disable Stop Loss | `true` |
| `slMultiplier` | `float` | ATR multiplier for Stop Loss distance | `2.0` |
| `useTP` | `bool` | Enable or disable Take Profit | `true` |
| `tpMultiplier` | `float` | ATR multiplier for Take Profit distance | `4.0` |
| `atrPeriod` | `int` | ATR calculation period for volatility-based risk control | `14` |
| `useBarConfirm` | `bool` | Wait for candle close confirmation to avoid repainting | `true` |

---

## 🧠 Strategy Logic

1. **Channel Calculation**  
   - The strategy calculates two main channels:  
     - **Entry Channels:** based on `entryLength` (previous highs/lows).  
     - **Exit Channels:** based on `exitLength`.  
   - These levels represent potential **breakout thresholds**.

2. **Entry Conditions**  
   - A **long position** is triggered when the closing price breaks above the upper entry channel.  
   - A **short position** is triggered when the closing price breaks below the lower entry channel.  
   - If `useBarConfirm` is enabled, entries are only executed once the candle closes beyond the threshold (avoiding false signals).

3. **Exit Conditions**  
   - The system exits trades when the opposite breakout occurs (crossing the opposite exit channel).  
   - Additionally, trades can be closed automatically via **Stop Loss (SL)** or **Take Profit (TP)** if enabled.

4. **Risk Management**  
   - The distance for both SL and TP is determined using the **Average True Range (ATR)** multiplied by user-defined coefficients (`slMultiplier`, `tpMultiplier`).  
   - This ensures that position exits adapt to the asset’s volatility.

5. **Visualization**  
   - Entry channels are drawn as **solid green/red lines**.  
   - Exit channels are displayed as **translucent circles** for clear differentiation on the chart.

---

# 📊 Visual examples of the strategy: Equity curve

## 📊 Cryptocurrencies

**BTCUSD**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_1.png)

---

## 📊 Index

**Dollar Index TVC**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_2.png)

---

## 📊 Forex

**EURUSD**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_3.png)

**GBPUSD**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_4.png)

**USDJPY**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_8.png)

---

## 📊 Stocks

**Apple Inc.**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_5.png)

---

## 📊 Metals

**XAUUSD (Gold)**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_6.png)

**Silver**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_7.png)

---

## 📊 Index (US)

**S&P 500**

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/e4add3d8f0ddf91e8a8f65dc0c8d68e05d8eb4c7/Breakout%20Strategy/Screenshot_9.png)

 
