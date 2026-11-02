# Supply Chain & Commercial Performance Optimisation

An end-to-end business analytics project exploring how a distribution business can improve commercial profitability and delivery performance through data-driven decision-making.

## Business Problem

Distribution businesses need to balance revenue growth, profitability and delivery performance. However, aggregate business metrics can hide loss-making transactions, underperforming products and operational delivery issues.

This project investigates:

**How can a distribution business improve profitability and delivery performance through data-driven operational and commercial decisions?**

The analysis uses the DataCo Smart Supply Chain dataset to examine sales, customers, products, profitability, regions and shipping performance.

## Project Objectives

- Analyse revenue, discounts and recorded profitability.
- Identify products and categories with weaker profitability.
- Evaluate customer-level commercial performance.
- Investigate late deliveries across shipping modes and regions.
- Examine cancellation rates and actual versus scheduled shipping durations.
- Build an interactive Power BI dashboard to communicate business findings.

## Tools & Technologies

- **Python:** Data cleaning, exploratory data analysis and business analysis.
- **Pandas & NumPy:** Data manipulation and numerical analysis.
- **Plotly:** Interactive data visualisation.
- **Power BI:** Interactive dashboard development and reporting.
- **DAX:** Measures and KPI calculations.
- **SQL:** Include project queries here if used in the final repository.

## Dataset

**DataCo Smart Supply Chain Dataset**

Source: Mendeley Data  
Licence: CC BY 4.0

The dataset contains approximately 180,519 transaction records covering orders, products, customers, sales, profitability and shipping information.

The cleaned analytical dataset contains 180,519 rows and 50 columns.

*Note: Add the original Mendeley Data record URL here so readers can access the dataset and attribution details.*

## Project Structure

```text
Supply-Chain-Consulting/
│
├── data/
│   ├── raw/
│   └── processed/
│       └── supply_chain_clean.csv
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
│   └── 03_business_findings_and_recommendations.ipynb
│
├── sql/
│
├── powerbi/
│   └── supply_chain_dashboard.pbix
│
├── visuals/
│   
├── reports/
│   └── Executive Summary & Business Report.pdf
├── presentation/
│
├── docs/
│
└── README.md
```

*Update filenames in this structure to match the actual files committed to the repository.*

## Key Business Findings

### 1. Overall Commercial Performance

| Metric | Result |
|---|---:|
| Gross Sales | 36.78M |
| Net Item Revenue | 33.05M |
| Recorded Profit | 3.97M |
| Profit to Net Revenue | 12.00% |
| Total Orders | 65,752 |
| Total Customers | 20,652 |

*Monetary values are presented in the dataset's recorded units; the currency was not independently confirmed.*

### 2. Delivery Performance

| Shipping Mode | Late Delivery Rate |
|---|---:|
| First Class | 100.00% |
| Second Class | 79.99% |
| Same Day | 48.37% |
| Standard Class | 39.85% |

Across 63,097 eligible delivery orders, 57.13% were classified as late.

Regional late-delivery rates ranged from 52.58% to 60.04%, indicating that delivery delays were widespread.

### 3. Commercial Profitability

- 34,961 transactions, or 19.36%, recorded negative profit.
- 4,069 customers, approximately 19.7% of the customer base, recorded negative aggregate profit.
- Strength Training recorded a profit-to-net-revenue ratio of approximately 0.68%.
- Men's Clothing recorded approximately 5.10%.

### 4. Product-Level Investigation

Two products were identified for further investigation:

| Product | Recorded Profit | Transactions |
|---|---:|---:|
| SOLE E35 Elliptical | -965.12 | 15 |
| SOLE E25 Elliptical | -169.56 | 10 |

These findings indicate areas for further review, not automatic product discontinuation.

## Power BI Dashboard

The interactive dashboard is organised into three pages:

**01 – Executive Overview**
- Overall business KPIs
- Monthly revenue trend
- Revenue by department
- Profit by customer segment
- Late versus on-time deliveries

**02 – Commercial Intelligence**
- Profitability by product category
- Department revenue versus profitability
- Customer segment profitability
- Customer revenue versus recorded profit

**03 – Operational Intelligence**
- Late-delivery rate by shipping mode
- Regional delivery performance
- Actual versus scheduled shipping days
- Cancellation rate by shipping mode

## Business Recommendations

1. **Review delivery commitments:** Investigate the feasibility of scheduled delivery times, particularly for First Class and Second Class shipments.
2. **Investigate low-profitability products:** Examine transaction-level pricing, discounts and recorded profit for products with recurring losses.
3. **Monitor transaction profitability:** Introduce regular monitoring of negative-profit transactions and unusually low profit ratios.
4. **Strengthen customer profitability analysis:** Evaluate revenue, order frequency and recorded profitability together.
5. **Improve operational monitoring:** Track delivery performance across regions and shipping modes to identify areas requiring further investigation.

## Limitations

- Carrier-level costs and fulfilment costs are unavailable.
- Inventory, supplier performance and purchase order information are not covered.
- Detailed carrier and route information is unavailable.
- Customer acquisition costs and sufficient retention history for customer lifetime value analysis are unavailable.
- The dataset covers January 2015 to January 2018, with 2018 containing January only.
- Recorded profit measures were checked for mathematical consistency, but their underlying accounting definitions could not be independently validated.

The findings are descriptive and do not establish causation. Recommendations are investigation priorities rather than claims of proven financial impact.

## Conclusion

This project demonstrates how transaction-level analysis and interactive business intelligence reporting can uncover performance issues that may be hidden by aggregate business metrics.

By combining commercial and operational analysis, the project provides a structured approach to identifying profitability concerns, evaluating delivery performance and translating data into practical business recommendations.