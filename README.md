# Behaviour Patterns & Dormancy Risk of Unclaimed Deposits in Indian Banks (2015–2024)
## Project Overview

Unclaimed deposits in Indian banks increased from ₹6,835 Cr in 2015 to ₹62,314 Cr in 2024, highlighting growing concerns regarding dormant accounts, customer inactivity, and deposit management. This project investigates behavioural patterns and dormancy risk across Indian banks using machine learning, concentration analysis, and statistical testing.

The study analyses data from 175 banks over a 10 year period and develops a framework to identify high-risk institutions based on dormancy growth, concentration, and behavioural characteristics.
---------------------------------------
## Business Problem

Traditional analysis focuses only on aggregate dormant deposit amounts. This project aims to:

* Identify behavioural patterns among banks
* Measure concentration risk of dormant deposits
* Develop a Dormancy Risk Score
* Support risk-based regulatory monitoring
* Provide insights for customer reactivation strategies

These objectives align with the dissertation's research goals.
---------------------------------------------
## Methodology

| Step | Technique | Purpose |
|---|---|---|
| Feature engineering | Lagged values, % growth, account-type shares | Capture scale and momentum per bank-year |
| Concentration analysis | Herfindahl-Hirschman Index (HHI) | Measure how concentrated dormancy is within one account type vs. spread across all four |
| Behavioural segmentation | K-Means clustering (K=3, elbow method, silhouette/Davies-Bouldin validation) | Group banks into stable / high-growth / large-legacy behaviour profiles |
| Composite scoring | Weighted Risk Score = 0.4×growth + 0.4×scale + 0.2×cluster | Rank banks by overall dormancy behaviour intensity, 0–100 |
| Statistical validation | Kruskal-Wallis ×2, Mann-Kendall, Mann-Whitney U, Spearman correlation | Confirm patterns are statistically real, not artifacts of a small sample |

------------------------------------------
