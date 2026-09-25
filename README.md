# Credit Risk Analytics Dashboard

Identifying which customer segments drive credit card default risk, using a star-schema Power BI model on 30,000 customer records.

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-333333?style=flat-square)
![Data Modeling](https://img.shields.io/badge/Data_Modeling-333333?style=flat-square)
![Status](https://img.shields.io/badge/status-completed-2ea44f?style=flat-square)

<p align="center">
  <img src="Dashboard%20Overview.png" alt="Credit Risk Analytics dashboard overview" width="850">
</p>

> Open `Muhammad Yahya Ayyasy_Credit Risk Analytics.pbix` in <a href="https://github.com"><img src="https://shields.io" alt="Power BI Desktop"></a> (free) to explore the model interactively.



## Contents
- [Business Problem](#business-problem)
- [Data](#data)
- [Tools & Techniques](#tools--techniques)
- [Key Findings](#key-findings)
- [Recommendation](#recommendation)
- [How to Explore](#how-to-explore)
- [Limitations](#limitations)

## Business Problem
A bank wants to know which customer segments carry the highest risk of credit card payment default, so credit policy and early-warning monitoring can be targeted rather than applied uniformly.

## Data
- **Source:** [Default of Credit Card Clients Dataset](https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients) (Yeh & Lien, 2009), UCI Machine Learning Repository — Taiwan credit card client data, April–September 2005 (30,000 clients, 25 variables: demographics, credit limit, 6-month repayment history, bill statements, actual payments)
- **Model:** Star schema — one fact table (`TabelFakta`) plus dimension tables `DimEducation`, `DimMarriage`, `DimSex`, `DimStatusBayar`, and a custom DAX table `Tren_Bulanan` built to drive the monthly payment-trend visual

### Why this dataset
Published in *Expert Systems with Applications* (Yeh & Lien, 2009), this is one of the most widely-cited credit-risk benchmarks in both applied ML and fairness-in-ML research — it's used as a standard classification-on-mixed-features benchmark (OpenML tabular-benchmark suite) and, separately, in multiple fairness studies that treat sex, education, and marital status as protected attributes for bias testing. Its durability as a teaching and benchmarking dataset (30,000 real repayment records, no missing values, real behavioral history rather than anonymized PCA features) is why it was chosen over synthetic alternatives for this project.

## Tools & Techniques
Power BI · DAX (custom monthly trend measures) · data modeling · correlation analysis

## Key Findings

| Metric | Value |
|---|---|
| Overall default rate | **22.12%** (6,600 of 30,000 customers) |
| Low credit-limit tier (≤50K) default rate | **31.79%** |
| Very High credit-limit tier (>500K) default rate | 11.17% |
| Highest-risk age group | 60+ (28.32% default) |
| Lowest-risk age group | 30–39 (20.25% default) |
| Strongest single predictor | Recent payment-delay history (r = 0.325) |

- **Credit limit is the strongest segmentation driver:** customers in the Low tier default at nearly 3x the rate of the Very High tier.
- **Age tells a counter-intuitive story:** customers 60+ have the highest default rate — not the 18–29 group, as commonly assumed.
- **Recent payment-delay history is the single strongest predictor of default**, stronger than credit limit or age alone.
- **Risk factors compound:** 60+ age *and* Low limit customers default at ~31%, versus just 12.5% for young customers with a Very High limit.

## Recommendation
Credit scoring should not assume "older = safer" — senior customers need additional risk-assessment attention, likely tied to post-retirement income changes. Low-limit customers should be the primary target for risk-mitigation or financial-coaching programs, since that is where default risk concentrates most heavily.

## How to Explore
1. Download `dashboard.pbix`
2. Open in Power BI Desktop (free)
3. Use the slicers (Status, Age Group, Gender, Limit Group, Education) to filter any segment combination

## Limitations
The dataset covers a single 6-month window in Taiwan (2005) — default patterns and thresholds may not generalize directly to other countries, credit products, or economic periods. The star schema currently models demographic and repayment-history dimensions; it does not include external factors (employment status, macroeconomic conditions) that a production credit model would typically incorporate.

---

<sub>**Muhammad Yahya Ayyasy** — [LinkedIn](https://linkedin.com/in/muhammadayyass) · [muhammadayyas22@gmail.com](mailto:muhammadayyas22@gmail.com)</sub>
