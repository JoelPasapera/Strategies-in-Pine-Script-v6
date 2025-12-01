# 🚀 Donchian Breakout Strategy — Pine Script Strategy

**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel  

---

## 📖 Overview

**Donchian Breakout Strategy** is a Pine Script® strategy designed to capture **momentum breakouts** using the classic **Donchian Channel** indicator.  
It places **pending buy-stop orders** at a fixed time each day, targeting breakouts above the channel’s upper band, while managing exits via the lower band.

The system is optimized for **EURUSD and GBPUSD** on **30-minute and 1-hour** timeframes, but can be adapted to other instruments.  
Its disciplined **time-based entry** and **channel-based exit** make it a robust tool for **trend-following** strategies with controlled risk.

---

## ⚙️ Input Parameters

| Parameter | Type | Description | Default Value |
|------------|------|-------------|----------------|
| `donchianLen` | `int` | Lookback period for Donchian Channel calculation | `25` |
| `targetHour` | `int` | Exchange hour to place the pending order | `17` |
| `validHours` | `int` | Maximum hours the pending order remains active | `60` |
| `lot_size` | `int` | Position size per trade | `900` |

---

## 🧠 Strategy Logic

1. **Channel Calculation**  
   - The strategy calculates the **Donchian Channel** using the highest high and lowest low over the last `donchianLen` bars.  
   - These levels define the **breakout thresholds** for entry and exit.

2. **Entry Conditions**  
   - At the **target hour** (e.g., 17:00), a **buy-stop order** is placed at the **upper band** of the Donchian Channel.  
   - The order is **pending** and only triggers if price breaks above this level.

3. **Exit Conditions**  
   - Once in a position, the strategy exits when price touches the **lower band** of the Donchian Channel.  
   - This ensures a **channel-based trailing exit** that adapts to market volatility.

4. **Order Management**  
   - If the order is **not filled** within `validHours`, it is **automatically canceled** to avoid stale entries.  
   - No new orders are placed until the next target hour.

5. **Visualization**  
   - The **upper and lower bands** are plotted for clarity.  
   - A **blue background** and **green triangle** mark the target hour for easy identification.

---

## 📊 Visual Examples of the Strategy

### 📊 EURUSD — 30 minutes
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_1.png)

### 📊 EURUSD — 1 hour  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_2.png)

### 📊 EURUSD — 1 hour  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_3.png)

### 📊 GBPUSD — 30 minutes  
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_4.png)

### 📊 GBPUSD — 1 hour 
![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/3c778c5d461ea458a43bdfcf16dc05c6330881b3/Donchian%20Breakout%20Strate/Screenshot_5.png)
