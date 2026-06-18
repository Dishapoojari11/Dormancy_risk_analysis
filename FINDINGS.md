# Key Findings & Policy Implications

## 1. Dormancy grows every year, without exception

Total system-wide unclaimed deposits across the 175 banks in this dataset rose from ₹6,835 Cr in 2015 to ₹62,314 Cr in 2024 — a **9.1× increase** in a decade. A Mann-Kendall trend test on the year-by-year totals returns **τ = 1.0, p < 0.001**: every single year is higher than the one before it. This is a structural, one-directional climb, not a cyclical fluctuation.

## 2. Three statistically distinct behavioural clusters

K-Means clustering on standardized growth rate and prior-year balance (K=3, chosen via the elbow method) produces extremely well-separated groups — **silhouette score 0.93**, Davies-Bouldin index 0.42. A Kruskal-Wallis test confirms the clusters differ significantly in risk score (**H = 107.36, p < 0.001**), i.e. they are real behavioural segments, not arbitrary partitions.

- **Stable (Cluster 0):** the overwhelming majority of bank-years — modest, slow-moving dormancy.
- **High-Growth Emerging (Cluster 1):** a small number of bank-years with explosive year-over-year growth off a small base — mostly foreign and regional rural banks.
- **Large Legacy (Cluster 2):** large accumulated balances, slower relative growth — **100% Public Sector Banks** (SBI, PNB, Canara Bank, Bank of Baroda, Union Bank, Indian Bank, Bank of India).

## 3. Dormancy is concentrated, not evenly spread, across the system

Public Sector Banks held **81.7% of all system-wide dormancy in 2024** (₹50,908 Cr of ₹62,314 Cr) despite being a small fraction of the 175 banks studied. The top 3 banks alone — SBI, PNB, and Canara Bank — account for **45.4% of the 2024 total**. Across all 1,218 bank-year records since 2015, the "Large Legacy" cluster (exclusively PSBs) has contributed **48.8%** of all dormancy ever recorded in the dataset.

**Policy read:** this is good news for regulators in one specific sense — a concentrated problem is a *targetable* one. A small number of supervisory conversations with a handful of large PSBs would address the majority of the system's dormant-deposit exposure.

## 4. Account-type concentration (HHI) varies sharply by bank type

The Herfindahl-Hirschman Index, computed per bank-year across the four account types, shows **Regional Rural Banks (mean HHI 0.72)** and **Local Area Banks (0.61)** running the most concentrated dormancy — typically piled into a single account type (usually savings) — while **Payment Banks (0.08)** and **Foreign Banks (0.32)** are far more diversified. About **31% of bank-years exceed the 0.65 "high concentration" threshold**, and **37% sit below the 0.40 "diversified" threshold**.

A concentrated HHI is a vulnerability multiplier: if 80%+ of a bank's dormant funds sit in fixed deposits, a single process failure in FD handling becomes a bank-wide dormancy problem rather than a contained one.

## 5. Larger dormancy balances grow faster, not slower (the "size-growth paradox")

A Spearman correlation between a bank's prior-year dormancy size and its subsequent growth rate returns **ρ = 0.64, p < 0.001** — a moderate-to-strong positive relationship. Scale does not protect against further acceleration; if anything, larger legacy piles tend to keep growing faster than smaller ones. This directly undercuts the assumption that big, well-resourced banks "have it under control" simply because they're large.

## 6. COVID-19's effect is visible in the raw averages but not statistically confirmed

Average dormancy per bank-year rose from **₹115 Cr (2015–2019)** to **₹291 Cr (2020–2024)** — a 153% increase. However, a Mann-Whitney U test on the full distribution returns **p = 0.11**, which is not significant at the conventional 5% threshold (Cohen's d = 0.20, a small effect). The post-COVID period has much higher variance, driven by a few very large PSBs, which is enough to prevent the rank-based test from calling the shift "significant" even though the raw average moved substantially. This is a useful reminder that headline averages and formal hypothesis tests can tell different stories — both are reported here rather than only the more dramatic one.

## 7. Bank type is a strong, statistically validated driver of dormancy

A Kruskal-Wallis test across the 9 bank-type categories returns **H = 684.78, p < 0.001, η² = 0.56** — a large effect size. Bank type explains a substantial share of the variation in dormancy levels, supporting differentiated (rather than one-size-fits-all) regulatory treatment by bank category.

## Suggested policy directions

1. **Tiered supervisory attention.** Standard monitoring for Cluster 0 (stable majority), enhanced outreach requirements for Cluster 1 (fast-growing but small), and dedicated, ongoing review for Cluster 2 (the handful of large PSBs holding the bulk of system dormancy).
2. **HHI-based account-type review.** Banks above the 0.65 HHI threshold — disproportionately Regional Rural and Local Area Banks — warrant a specific look at why dormancy is piling into one account type rather than being addressed across the board.
3. **Customer outreach proportional to balance, not just account count.** Since PSBs carry the largest absolute balances, even modest improvements in reactivation/outreach rates there move the largest rupee amounts.
4. **Continued use of nomination, UDGAM, and "Your Money, Your Right"-style portals** to reduce the pool of genuinely unclaimed (vs. simply inactive) funds, especially for legacy/large-balance accounts where the original depositor may be deceased or untraceable.

## Limitations

- The dataset aggregates at the bank-year level; account-level or customer-level detail (which would explain *why* specific accounts go dormant) isn't available here.
- Only four account-type categories are tracked (Current, Savings, Fixed Deposit, Other) — finer product-level detail could sharpen the HHI analysis.
- The composite Risk Score's 40/40/20 weighting (growth/scale/cluster) is a reasonable, defensible choice but is ultimately a modeling decision, not a law of nature — different weights would re-rank banks somewhat.
- COVID-19's true causal effect on dormancy can't be cleanly isolated from this data alone (see Finding 6); a difference-in-differences design against a comparable non-banking control series would strengthen this further.
