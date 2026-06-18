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
## Key Insights

- **Dormancy has grown every single year since 2015** — total system-wide unclaimed deposits rose from ₹6,835 Cr to ₹62,314 Cr (9.1×). A Mann-Kendall trend test confirms this is a real, near-perfect monotonic trend (τ = 1.0, p < 0.001), not a cyclical pattern.
- **Banks split into three statistically distinct behavioural clusters** (K-Means, silhouette score 0.93): a stable majority, a small fast-growing group, and a "Large Legacy" group holding outsized balances.
- **The Large Legacy cluster is 100% Public Sector Banks.** PSBs held **81.7% of all system-wide dormancy in 2024** despite being a small fraction of the 175 banks studied — the top 3 alone (SBI, PNB, Canara Bank) account for 45.4% of the total.
- **Larger dormancy balances grow faster, not slower** — a "size-growth paradox" (Spearman ρ = 0.64, p < 0.001) that undercuts the assumption that scale brings stability.
- **Concentration risk (HHI) varies sharply by bank type** — Regional Rural Banks run the most concentrated dormancy (mean HHI 0.72, mostly piled into one account type), while Payment Banks are the most diversified (0.08).
- **The raw COVID-era jump in average dormancy (+153%) is not statistically significant** at α=0.05 (Mann-Whitney p = 0.11) once the high variance in the post-2020 period is accounted for — a useful reminder that a striking average and a confirmed effect aren't always the same thing.
  
Full detail, including the composite Risk Score's top-10 highest-risk banks and policy implications, is in [`FINDINGS.md`](FINDINGS.md).

-----------------------------------------
## Visualizations

**Total system-wide dormancy, 2015–2024** — a one-directional climb in every year of the dataset.
<img width="1581" height="977" alt="01_total_dormancy_trend" src="https://github.com/user-attachments/assets/b9e9c905-d402-41a3-812e-fdb70b55df5d" />

**Behavioural clusters** — three groups emerge cleanly from growth rate and prior-year balance.
<img width="1479" height="1077" alt="04_behaviour_clusters" src="https://github.com/user-attachments/assets/2377e432-0c14-49b7-ba3e-fc30ce30010a" />

**Bank type composition by cluster** — the "Large Legacy" cluster (rightmost bar) is exclusively Public Sector Banks.
<img width="1778" height="1078" alt="05_cluster_by_banktype" src="https://github.com/user-attachments/assets/f1ad3010-1979-4968-9681-f3fe45428ee2" />

**HHI concentration by bank type** — Regional Rural Banks and Public Sector Banks run the most concentrated dormancy.
<img width="2781" height="977" alt="02_hhi_concentration" src="https://github.com/user-attachments/assets/a62eaad8-c057-4536-81be-3b87cd220afa" />

---------------------------------
## Limitations & Future Work

- Bank-year level aggregation — no account-level or customer-level data to explain *why* specific accounts go dormant.
- Only four account-type categories tracked; finer product-level detail could sharpen the HHI analysis.
- The Risk Score's 40/40/20 weighting is a defensible modeling choice, not a fixed law — different weights would re-rank banks somewhat.
- Natural next steps: account-level churn prediction, a cross-country comparison of unclaimed-funds frameworks, and isolating the COVID-19 effect with a proper control series.

Full discussion in [`FINDINGS.md`](FINDINGS.md).

----------------------------------------------------
## Documentation

- [`FINDINGS.md`](FINDINGS.md) — detailed key findings and policy recommendations
- [`Final_Report.pdf`](Final_Report.pdf) — the complete academic dissertation this project is based on
- [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md) — full column reference for the dataset

---------------------------
## Author

**Disha Poojari** 

