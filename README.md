# Hypothesis Prioritization and A/B Testing for an Online Store

## The Challenge

An online store wanted to increase revenue but had more improvement ideas than capacity to implement them. The product team needed two things: know **which experiments to launch first**, and once launched, **decide with data whether the change actually worked**.

**Goal:** apply prioritization frameworks (ICE and RICE) to rank business hypotheses, then analyze the results of a running A/B experiment to determine whether the test group generated statistically significantly better outcomes.

---

## Process

**1. Hypothesis prioritization with ICE and RICE**

Nine improvement hypotheses were evaluated using two frameworks:

- **ICE** (Impact × Confidence ÷ Effort): prioritizes by ease of execution.
- **RICE** (Reach × Impact × Confidence ÷ Effort): incorporates the number of users affected.

Both rankings were compared to identify hypotheses that shifted significantly between methods. The "birthday promotion" hypothesis dropped sharply in RICE despite scoring well in ICE, revealing that its actual user reach was limited — a critical finding for resource allocation.

**2. A/B experiment exploratory analysis**

Groups A and B were analyzed across three dimensions:

- **Cumulative revenue:** daily revenue evolution per group.
- **Average order value (AOV):** how much each buyer spends on average.
- **Conversion rate:** proportion of visitors who made at least one purchase.

**3. Anomaly detection and treatment**

Users with extreme order counts or purchase amounts were identified. Two versions of the analysis were built — with full data and with outliers removed — to assess the robustness of conclusions.

**4. Hypothesis testing**

| Test | Metric | Dataset |
|------|--------|---------|
| Z-test for proportions | Conversion rate per user | Full and outlier-free |
| Mann-Whitney U | Number of orders per user (visitors with no purchase = 0) | Full and outlier-free |

The per-user analysis included all experiment visitors to avoid selection bias.

---

## Results

- **Group B generated higher cumulative revenue**, though with an abrupt spike that coincided with high-value outliers.
- After removing anomalies, the AOV difference between groups **decreased significantly**, indicating the initial result was driven by a small number of atypical users.
- Group B's conversion rate was **statistically superior** across the tests performed.
- RICE reordered hypotheses relative to ICE, favoring initiatives with broader user reach — a key insight for the product team's decision-making.

---

## Stack

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458)
![Scipy](https://img.shields.io/badge/Scipy-stats-8CAAE6)
![Statsmodels](https://img.shields.io/badge/Statsmodels-0.14-red)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0)

- **Language:** Python
- **Libraries:** Pandas, Scipy, Statsmodels, Matplotlib, Seaborn, NumPy
- **Techniques:** ICE/RICE frameworks, A/B testing, outlier detection (IQR), z-test for proportions, Mann-Whitney U

---

## Dataset

Online store data from three sources: a hypothesis list with impact/confidence/effort/reach scores, an order log per user and group, and a daily visit log per group.

---

## Repository Structure

```
├── ab_testing_analysis.ipynb   # Main notebook with full analysis
├── README.md
└── data/
    ├── hypotheses_us.csv
    ├── orders_us.csv
    └── visits_us.csv
```
