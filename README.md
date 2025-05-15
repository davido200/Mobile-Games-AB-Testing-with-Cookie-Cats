# 🍪 Cookies Game A/B Test Documentation

## 📌 Objective

To evaluate whether **delaying the first gate from level 30 to level 40** in the game improves **player retention**. A *gate* is a game mechanism that forces a player to either wait or make an in-app purchase to proceed. The hypothesis is that **delaying the first gate** will improve player experience and engagement, leading to better retention.

---

## Target Metrics

We analyzed the impact of the gate position using the following metrics:

| Metric           | Description                                                          |
| ---------------- | -------------------------------------------------------------------- |
| `retention_1`    | Whether the player came back 1 day after installing the game.        |
| `retention_7`    | Whether the player returned **every day** for 7 days after install.  |
| `sum_gamerounds` | Total number of rounds played within 14 days of installing the game. |

---

## Test Groups

| Version   | Description                   |
| --------- | ----------------------------- |
| `gate_30` | First gate placed at level 30 |
| `gate_40` | First gate placed at level 40 |

---

## Statistical Methods Used

### 1. **Z-Test for Proportions**

Used to test **retention_1** and **retention_7** between the two groups.

#### Results:

Day 1 Retention Z-Test: Z = 1.784, p = 0.074
Day 7 Retention Z-Test: Z = 3.164, p = 0.002


* **Day 1 Retention**: Not statistically significant (p > 0.05), but suggests a trend favoring gate_30.
* **Day 7 Retention**: Statistically significant (p < 0.05), indicating **higher retention when gate is at level 30**.

---

### 2. **T-Test for Means**

Used to test the difference in the average `sum_gamerounds`.

#### Results:

T-Statistic = 0.885, p = 0.376


* **Not statistically significant**: No meaningful difference in total gameplay between groups.

---

### 3. **Bootstrapping**

A resampling method used to estimate **confidence intervals** and probability distributions for retention differences.

#### Results (Bootstrap):

| Metric       | Mean Difference (Gate 30 - Gate 40) | 95% Confidence Interval | Probability Gate 30 > Gate 40 |
| ------------ | ----------------------------------- | ----------------------- | ----------------------------- |
| retention_1  | ~1.17%                             | [-0.01%, +1.23%]       | 97.2%                         |
| retention_7  | ~1.32%                             | [+0.31%, +1.32%]       | 100.0%                        |

---

## Visualizations

* Kernel Density Estimates of 1-day and 7-day retention bootstrap distributions
* Confidence intervals on retention differences
* Evidence of a difference in retention, though relatively small in magnitude

---

## ✅ Conclusion

* ✅ **7-Day retention** significantly improved when the gate was placed at level **30**.
* ⚠️ **1-Day retention** showed improvement but was not statistically significant at the 95% confidence level.
* ❌ No significant difference in gameplay rounds (`sum_gamerounds`).

### 📌 Recommendation:

> Keep the first gate at **level 30** to optimize player retention and long-term engagement.


