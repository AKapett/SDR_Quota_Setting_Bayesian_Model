# SDR Territory Quota Forecasting with Bayesian Modeling

This project analyzes SDR performance data to fairly forecast territory-level quotas and estimate the **probability that each SDR will hit their target** using Bayesian inference. Below is the execution in Jupyter as well as an interactive dashboard reporting on performance across employees, region, product, and opportunity type. A second dashboard shows trends in performance over time for those same factors.

This project highlights the capabilities to use multiple temporal and revenue contributing factors to strategically set quotas as well as confidently predict performance using Bayesian probabilities.

-> [Notebook](https://github.com/AKapett/SDR_Quota_Setting_Bayesian_Model/blob/main/SDR%20%20Quota%20Forecasting%20%26%20Rep%20Bayesian.ipynb) 

-> [Interactive Reporting](https://public.tableau.com/views/SDRQuarterlyIntelligence-Performance-Trends/Story1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

## Workflow Overview

### Data Cleaning & Validation

- Standardized column formats, parsed date fields, and normalized casing across all text fields.
- Converted monetary and percentage values into numeric format.
- Validated logic between stage, closed, and won flags.
- Removed invalid or mismatched entries (e.g., closed deals without proper stage labeling).


### Feature Engineering

- Created temporal fields: year, quarter, year_quarter, quarter_index.
- Generated territory_id by combining region and product.
- Aggregated performance by SDR × Territory × Quarter, enabling historical trend analysis.
- Engineered weighted average sales per SDR.
- Derived Q2 contribution ratio per SDR relative to their territory's total sales.


### Territory & SDR-Level Forecasting

Forecasted Q3 2015 performance at the territory level using:

- 60% weight on Q2 actuals
- 40% on 8-quarter historical average
- Applied ±35% cap to avoid extreme shifts.


Forecasted Q3 targets for each SDR using:

- Their Q2 sales contribution * Q3 territory forecast
- Their individual weighted historical sales average
- Output: custom Q3 target per rep


### Bayesian Modeling for SDR Performance Probability

Built individual Bayesian models to estimate:

- Probability of meeting or exceeding Q3 forecast
- Posterior mean sales for each SDR
- 94% credible intervals
- Sales pressure index (expected / historical average)
- Risk flag: high, moderate, or low


**Prior distribution:**

sales ~ Normal(mean=weighted_avg_sales, std_dev=historical_sales_std or fallback)


Outcome: Probabilistic insight into quota attainability and territory planning



---

## Final Outcome

This process provided a fair, data-backed quota setting system and helped identify which SDRs were most at risk of missing targets.

---

## Tools Used
- Python (Pandas, PyMC, ArviZ)
- Jupyter Notebook
- Tableau
- Data source: [Kaggle Data Source](https://www.kaggle.com/datasets/rahuldhanola/salesforce-sales-quota-data)
