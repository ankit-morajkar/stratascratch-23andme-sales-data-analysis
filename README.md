# 📈 Store Sales Analysis & Demographic Trends

![Python](https://img.shields.io/badge/Python-3.12-blue) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-orange) ![SciPy](https://img.shields.io/badge/SciPy-Statistical%20Testing-green)

## 📋 Project Overview
This project analyzes 50 weeks of timestamped sales data to identify trends, anomalies, and customer demographic shifts. The analysis was conducted as part of a data science take-home assignment (23andMe recruitment case study).

The primary objective was to investigate a sudden discontinuity in daily sales volume, determine its statistical significance, and assess if changing gender demographics were a contributing factor.

## 📂 Repository Structure
```text
├── data/                   # Contains the 50 raw CSV files (one per week)
├── images/                 # Generated plots and charts for this README
├── analysis.ipynb          # Main Jupyter Notebook containing code and commentary
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation

## 🔍 Key Findings

### 1. Identification of Sales Surge
Visual inspection of the time-series data revealed a distinct discontinuity in sales volume.
* **Event Date:** April 29, 2013
* **Observation:** Daily sales volume shifted from a mean of **~504 units** to **~703 units**.

![Sales Trend](images/sales_trend.png)
*(Figure 1: Daily sales over 50 weeks showing the clear step-change in late April)*

### 2. Statistical Significance (A/B Testing)
To confirm this was a fundamental shift rather than random volatility, I performed an independent two-sample t-test comparing daily sales before and after April 29th.

* **Hypothesis:** $H_0$: $\mu_{before} = \mu_{after}$ vs $H_1$: $\mu_{before} \neq \mu_{after}$
* **T-Statistic:** `-45.94`
* **P-Value:** `3.49e-138`

**Conclusion:** With a p-value effectively at zero ($p < 0.05$), the increase in sales is **statistically significant**.

### 3. Gender Demographics Analysis
I investigated whether the sales spike was driven by a shift in the proportion of male vs. female customers.
* **Before April 29:** Mean female ratio ~64.8%
* **After April 29:** Mean female ratio ~39.8%

**Insight:** While there was a significant drop in the proportion of female customers, the decline was **gradual** over the 50-week period and did not align with the sudden spike on April 29. Therefore, the data suggests the sales surge was **not** caused by a sudden demographic shift.

### 4. Peak Trading Hours (Daypart Analysis)
Sales volume is highest during the afternoon block.

| Daypart | Time Window | % of Total Sales |
| :--- | :--- | :--- |
| **Afternoon** | 12:00 PM - 6:00 PM | **39.4%** |
| **Morning** | 6:00 AM - 12:00 PM | 30.8% |
| **Evening** | 6:00 PM - 12:00 AM | 20.9% |
| **Night** | 12:00 AM - 6:00 AM | 9.0% |
