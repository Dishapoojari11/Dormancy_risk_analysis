# Data Dictionary — `Unclaimed_Deposits.xlsx`

**Source:** Reserve Bank of India (RBI) — unclaimed/dormant deposit disclosures, compiled from RBI circulars and annual reports, 2015–2024.

**Shape (raw):** 1,228 rows × 15 columns (one row per bank per year, plus 10 "TOTAL" summary rows removed during cleaning) → **1,218 bank-year records** across **175 unique banks** and **9 bank types** after cleaning.

The sheet ships with a two-row header (account type, then sub-metric). The notebook flattens this into single column names by joining them with `_`.

| Column (flattened) | Type | Description |
|---|---|---|
| `Year` | int | Calendar/financial year of the record (2015–2024) |
| `Bank` | text | Bank name, as reported by RBI |
| `Bank Type` | text | One of 9 categories: Public Sector Bank, Private Sector Bank, Regional Rural Bank, Cooperative/Nationalised Bank, Small Finance Bank, Payment Bank, Foreign Bank, Local Area Bank, SBI and Its Associates |
| `Current Account_No of Accounts` | int | Number of dormant current accounts |
| `Current Account_Amount Outstanding` | float (₹ Cr) | Unclaimed balance held in current accounts |
| `Savings Account_No of Accounts` | int | Number of dormant savings accounts |
| `Savings Account_Amount Outstanding` | float (₹ Cr) | Unclaimed balance held in savings accounts |
| `Fixed Deposits_No of Accounts` | int | Number of dormant fixed deposit accounts |
| `Fixed Deposits_Amount Outstanding` | float (₹ Cr) | Unclaimed balance held in fixed deposits |
| `Other Deposits_No of Accounts` | int | Number of dormant "other" deposit accounts |
| `Other Deposits_Amount Outstanding` | float (₹ Cr) | Unclaimed balance held in other deposit types |
| `Other Deposits_Interest Credited` | float (₹ Cr) | Interest credited on other deposits |
| `Other Deposits_Incidental Charges` | float (₹ Cr) | Incidental charges applied |
| `Total Unclaimed Deposits_No of Accounts` | int | Sum of all dormant accounts for that bank-year |
| `Total Unclaimed Deposits_Amount Outstanding` | float (₹ Cr) | Sum of all unclaimed balances for that bank-year — the primary variable used throughout the analysis |

## Features engineered in the notebook (not in the raw file)

| Feature | Formula |
|---|---|
| `lag_total` | Previous year's `Total Unclaimed Deposits_Amount Outstanding` for the same bank |
| `Growth_Rate` | Year-over-year % change in total dormancy for that bank |
| `*_Share` | Each account type's amount ÷ sum of the four account-type amounts |
| `HHI_Concentration` | Sum of squared account-type shares (0.25–1.0; higher = more concentrated in one account type) |
| `Cluster` | K-Means cluster label (0/1/2) on standardized `[Growth_Rate, lag_total]` |
| `Risk_Score` | `0.4×growth_norm + 0.4×lag_norm + 0.2×cluster_weight`, scaled to 0–100 |
| `Risk_Level` | `Low Risk` (<20) / `Moderate Risk` (20–40) / `High Risk` (≥40), bucketed from `Risk_Score` |

₹ Cr = Indian Rupees, Crore (1 Crore = 10,000,000).
