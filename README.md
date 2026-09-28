# econ5200-lab03-eda-diagnostics
# Pipeline Health Check — EDA, Corruption & Distribution Shift

## Objective

Build a practical data-quality monitoring pipeline that uses exploratory data analysis (EDA), automated profiling, and Population Stability Index (PSI) to detect data corruption and distribution shift before they affect downstream models.

## Methodology

* Performed exploratory data analysis on a country-level panel dataset to identify data-quality issues.
* Detected and fixed five planted issues:

  * Negative GDP values
  * Life expectancy stored in months instead of years
  * Duplicate country-year records
  * Inconsistent percentage units in `trade_pct`
  * GDP unit mismatch
* Compared training and inference data distributions using Population Stability Index (PSI).
* Compared manual EDA results with automated profiling using `ydata-profiling`.
* Evaluated which data-quality issues could be detected automatically and which required domain knowledge.
* Developed reusable `eda_utils.py` functions for impossible-value checks, PSI calculation, and summary statistics.
* Built an interactive pipeline-health dashboard to monitor data quality and distribution changes.

## Key Findings

* The GDP variable showed a significant distribution shift, with a PSI of **2.4589** between the training and inference data.
* Several untouched variables also produced moderate PSI values, demonstrating that PSI can be affected by sampling variability when the dataset is small.
* Manual EDA and automated profiling can identify many common data-quality issues, but domain knowledge is still required to determine whether certain patterns represent actual data errors.
* Automated EDA is useful for scalable monitoring, while manual investigation remains important for interpreting unexpected changes and identifying domain-specific problems.
* The project demonstrates how automated data-quality checks, distribution monitoring, and human review can work together as part of a production data-monitoring workflow.
