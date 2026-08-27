# National Economic Indicators & Savings Capacity Analysis - (Power BI Project)

An end-to-end data transformation, modeling, and business intelligence pipeline evaluating the relationships between formal education tenure, sector employment, and capital preservation.

---

## Executive Summary & Key Discoveries
This project explores survey-driven economic indicators across multiple occupational sectors. By cleaning structural text anomalies and developing a multivariate analysis framework, the pipeline exposed a stark trend in human capital returns:
*   **Industry Leads Earnings:** The Industrial sector commands the highest average income (4,129.76), followed closely by Services (4,039.50), while Agriculture sits at the baseline (3,985.45).
*   **Wages Drive Savings:** Savings rates mirror income thresholds perfectly (Industry: 12.06%, Services: 12.04%, Agriculture: 12.01%). Higher wages unlock extra cash, allowing workers to roll money straight into savings instead of spending it all on basic survival.
*   **The Schooling Paradox:** Agricultural workers spend the most years in formal schooling, yet generate the lowest overall income. Conversely, Services workers hold the lowest academic averages but secure superior earnings and peak individual savings spikes.
*   **Experience Beats a Degree:** Spending so many years in a classroom does not guarantee wealth. In hands-on sectors like Industry and Services, practical on-the-job experience and specialized technical skills pay a far higher premium than a general degree.

---

## Data Pipeline Architecture & Engineering Workflow

A major focus of this project was executing proper data sanitation rules within Power Query to resolve hidden text-to-numeric data bottlenecks:

1.  **Anomaly Isolation & Type Casting:** Cleaned string text errors ("NA" values) blocking calculations within data fields. Forced text elements into clean blank states and cast the column into a Decimal Number structure to unlock calculations and chart features.
2.  **Grouped Mean Imputation:** To fill missing data fields without corrupting the natural distribution of the dataset, a staging query was architected to isolate and compute the exact mathematical average of the savings rate grouped by employment sector.
3.  **Relational Database Merging:** Merged the aggregate summary staging query back into the primary log via a Left Outer Join on the matching employment sector keys.
4.  **Conditional Logical Routing:** Constructed an immutable conditional column to substitute missing rows using contextual group means while preserving all raw, unmanipulated row variations.

---

## Data Modeling Architecture
Within the Model View, a high-performance database schema was implemented by mapping the aggregate summary lookup table to the core granular ledger file. This established a strict 1-to-Many relationship utilizing a Single cross-filter direction, ensuring that global dashboard slicers route structural filter parameters accurately across visual metrics without breaking data dependencies.

---

## Visualizations Implemented
*   **Univariate Analysis:** Baseline aggregate tables contrasting absolute macro means of income, savings rates, and education grouped by sector.
*   **Bivariate Analysis:** A clean scatter plot detailing the upward trajectory of education vs. personal savings, reinforced with a fitted line of best fit to map correlation.
*   **Multivariate Analysis:** Color-coded categorical legend partitioning by employment sector over the scatter coordinate space to expose the localized vocational premium anomalies.

---

## Repository File Directory
*   `Economic Data.xlsx`: The raw, uncleaned survey log containing string anomalies and missing values.
*   `Economic_Insights_Dashboard.pbix`: The complete Power BI Desktop file containing the data engineering steps, relational model, and visual canvas layouts.
*   `Economic_Savings_Analysis1.pdf`: A high-resolution presentation export optimized for immediate, mobile-friendly viewing.

