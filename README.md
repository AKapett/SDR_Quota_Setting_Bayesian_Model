# SDR Territory Quota Forecasting with Bayesian Modeling

This project analyzes SDR (Sales Development Representative) performance data to fairly forecast territory-level quotas and estimate the **probability that each SDR will hit their target** using Bayesian inference.

---

## Project Summary

I sourced the SDR sales dataset from **Kaggle**, cleaned and validated it, and built a multi-phase analysis pipeline to evaluate and forecast SDR success at both the **territory** and **rep** level.

-> [Notebook](https://github.com/AKapett/SDR_Quota_Setting_Bayesian_Model/blob/main/SDR%20%20Quota%20Forecasting%20%26%20Rep%20Bayesian.ipynb) 

*Coming Soon*:

*Will have an interactive Tableau Dashboard soon to easily find common SDR markers, like Region Performance, Product Performance, Rep, etc.*

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
  - Historical average and std dev of sales (excluding Q3)
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
- Data source: [Kaggle Data Source](https://www.kaggle.com/datasets/rahuldhanola/salesforce-sales-quota-data)
