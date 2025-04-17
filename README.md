# SDR Territory Quota Forecasting with Bayesian Modeling

This project analyzes SDR performance data to fairly forecast territory-level quotas and estimate the **probability that each SDR will hit their target** using Bayesian inference. Below is the execution in Jupyter as well as an interactive dashboard reporting on performance across employees, region, product, and opportunity type. A second dashboard shows trends in performance over time for those same factors.

This project highlights the capabilities to use multiple temporal and revenue contributing factors to strategically set quotas as well as confidently predict performance using Bayesian probabilities.

-> [Notebook](https://github.com/AKapett/SDR_Quota_Setting_Bayesian_Model/blob/main/SDR%20%20Quota%20Forecasting%20%26%20Rep%20Bayesian.ipynb) 

-> [Interactive Reporting](https://public.tableau.com/views/SDRQuarterlyIntelligence-Performance-Trends/Story1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

## Workflow Overview

### 1. **Data Cleaning & Validation**
- Parsed and standardized monetary fields, dates, and column formats.
- Verified logical consistency across sales outcomes and pipeline stages.

### 2. **Territory-Level Quota Forecasting**
- Aggregated 8 quarters of historical sales.
- Forecasted Q3 2015 sales using:
  - **60% recent quarter (Q2)**
  - **40% historical average**
  - Applied ±35% cap for stability.

### 3. **SDR Contribution-Based Target Setting**
- Calculated each SDR's sales contribution in Q2 within their territory.
- Used this to derive a **custom Q3 target per SDR** based on territory forecasts.

### 4. **Bayesian Modeling for Forecast Accuracy**
- Built Bayesian models per SDR using:
  - Historical average and std dev of sales
  - Q3 forecasted target
- Output:
  - Posterior mean sales
  - Probability of meeting or exceeding quota
  - 94% credible intervals
  - Risk classification (high, moderate, low)

---

## Final Outcome

This process provided a fair, data-backed quota setting system and helped identify which SDRs were most at risk of missing targets — all powered by Bayesian forecasting.

---

## Tools Used
- Python (Pandas, PyMC, ArviZ)
- Jupyter Notebook
- Tableau
- Data source: [Kaggle Data Source](https://www.kaggle.com/datasets/rahuldhanola/salesforce-sales-quota-data)
