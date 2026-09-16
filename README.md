# Credit Risk Analytics Dashboard — Power BI

Identifying which customer segments drive credit card default risk, using a star-schema Power BI model on 30,000 customer records.

![Dashboard Overview](screenshots/dashboard-overview.png)

📁 Open `dashboard.pbix` in Power BI Desktop to explore interactively.

## Business Problem
A bank wants to know which customer segments carry the highest risk of credit card payment default, so credit policy and early-warning monitoring can be targeted rather than applied uniformly.

## Data
- **Source:** Taiwan credit card client dataset, April–September 2005 (30,000 clients, 25 variables: demographics, credit limit, 6-month repayment history, bill statements, actual payments)
- **Model:** Star schema — one fact table (`TabelFakta`) plus dimension tables `DimEducation`, `DimMarriage`, `DimSex`, `DimStatusBayar`, and a custom DAX table `Tren_Bulanan` built to drive the monthly payment-trend visual

## Tools & Techniques
Power BI · DAX (custom monthly trend measures) · data modeling · correlation analysis

## Key Findings
- Overall default rate: **22.12%** (6,600 of 30,000 customers)
- **Credit limit is the strongest segmentation driver:** customers in the Low tier (≤50K) default at **31.79%**, nearly 3x the Very High tier (>500K) at **11.17%**
- **Age tells a counter-intuitive story:** customers 60+ have the *highest* default rate (28.32%) — not the 18-29 group as commonly assumed — while 30-39 has the lowest (20.25%)
- **Recent payment-delay history is the single strongest predictor of default** (correlation r = 0.325), stronger than credit limit or age alone
- Combining risk factors compounds the effect: 60+ age *and* Low limit customers default at ~31%, versus just 12.5% for young customers with a Very High limit

## Recommendation
Credit scoring should not assume "older = safer" — senior customers need additional risk-assessment attention, likely tied to post-retirement income changes. Low-limit customers should be the primary target for risk-mitigation or financial-coaching programs, since that is where default risk concentrates most heavily.

## How to Explore
1. Download `dashboard.pbix`
2. Open in Power BI Desktop (free)
3. Use the slicers (Status, Age Group, Gender, Limit Group, Education) to filter any segment combination

## Limitations
The dataset covers a single 6-month window in Taiwan (2005) — default patterns and thresholds may not generalize directly to other countries, credit products, or economic periods. The star schema currently models demographic and repayment-history dimensions; it does not include external factors (employment status, macroeconomic conditions) that a production credit model would typically incorporate.

---
**Author:** Muhammad Yahya Ayyasy — [LinkedIn](https://linkedin.com/in/muhammadayyass) · muhammadayyas22@gmail.com
