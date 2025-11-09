# ⏰ Time and Schedule — Pine Script Strategy

```pinescript
**Author:** Joel Pasapera Pinto  
**Language:** Pine Script® v6  
**License:** [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/)  
**Copyright:** © JJPP_Joel  
```

---

## 📖 Overview

**Time and Schedule** is a Pine Script® strategy designed to automate trades based on **specific trading hours and days of the week**.  
Its primary goal is to enable systematic backtesting of intraday market behavior within controlled time windows — removing subjective decision-making from the process.

The strategy lets you configure your **trading session time**, **day of execution**, **position direction (buy/sell)**, and **lot size** while automatically highlighting active trading sessions on the chart.

---

## ⚙️ Input Parameters

| Parameter | Type | Description | Default Value |
|------------|------|-------------|----------------|
| `lot_size` | `float` | Position size per trade | `1.0` |
| `start_time` | `int` | Hour to start trading (0–24) | `13` |
| `end_time` | `int` | Hour to stop trading (0–24) | `16` |
| `buy_or_sell` | `bool` | If `true`, execute buys (long); if `false`, execute sells (short) | `true` |
| `day_of_week` | `int` | Day of the week to trade (e.g., `dayofweek.friday`) | `dayofweek.friday` |
| `color_session` | `color` | Color of the session highlight | `color.red` |
| `transparency` | `int` | Transparency percentage of the background color | `80` |

---

## 🧠 Strategy Logic

1. The script checks whether the **current bar** falls within the defined trading session (`day_of_week`, `start_time`, `end_time`).
2. If it does:
   - A **long signal** is triggered at or before the session start.
   - A **short signal** is triggered at or after the session end.
3. Depending on the `buy_or_sell` setting, the script places either a **long** or **short** entry using `strategy.entry()`.

Additionally, the chart background is colored during active sessions for easy visual identification.

---

## 📊 Visual Example

![image](https://github.com/JoelPasapera/Strategies-in-Pine-Script-v6/blob/b182e01a940478438db39c05b57754f228d24787/time_and_schedule/Screenshot_1.png)







