# 🔢 Fibonacci Strategy — Pine Script Strategy

**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel  

---

## 📖 Overview

**Fibonacci Strategy** is a Pine Script® algorithm designed to automate entries based on **daily Fibonacci retracement levels**, focusing primarily on the **0.382 retracement** zone — one of the most statistically significant pullback levels in trending markets.  

The system retrieves the **previous day’s high and low**, computes the Fibonacci retracement, and triggers limit buy orders when price approaches the target level. Additionally, it includes a time-based exit system to close positions after a configurable number of hours.

Its simplicity and clarity make it ideal for backtesting **trend-continuation scenarios**, while maintaining robustness and reproducibility for quantitative strategy development.

---

## ⚙️ Input Parameters

| Parameter | Type | Description | Default Value |
|------------|------|-------------|----------------|
| `lot_size` | `float` | Position size per trade | `1.0` |
| `hold_hours` | `int` | Number of hours to keep the trade open before auto-closing | `8` |
| `fib_level` | `float` | Fibonacci retracement level to calculate entry | `0.382` |
| `entry_hour` | `int` | Hour at which to check for the entry condition | `8` |

---

## 🧠 Strategy Logic

1. **Retrieve previous day’s range**  
   The function `get_prev_day_high_low()` obtains the previous day’s **high** and **low** prices using the daily timeframe.

2. **Calculate Fibonacci retracement**  
   The script calculates the **Fibonacci 0.382 level**:
