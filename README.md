# SDR Territory Quota Forecasting with Bayesian Modeling

This project analyzes SDR performance data to strategically forecast territory-level quotas and estimate the probability that each SDR will meet their target using Bayesian inference. The execution is presented in Jupyter, alongside an interactive Tableau dashboard reporting performance across employees, regions, products, and opportunity types. A second dashboard visualizes performance trends over time.

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

By combining temporal, behavioral, and revenue-based features, this project delivers a data-driven quota-setting framework and a Bayesian probability model that identifies which SDRs are most at risk. This approach can assist with intentional territory planning and performance support.

---

## Tools Used
- Python (Pandas, PyMC, ArviZ)
- Jupyter Notebook
- Tableau
- Data source: [Kaggle Data Source](https://www.kaggle.com/datasets/rahuldhanola/salesforce-sales-quota-data)
