# Supply Chain & Commercial Performance Optimisation

## Project Overview

An end-to-end business analytics project using the DataCo Smart Supply Chain dataset to evaluate commercial performance, product profitability, customer contribution, and delivery operations.

The project combines Python-based data cleaning and exploratory analysis with a Power BI dashboard to identify performance patterns, investigate areas of concern, and develop data-driven business recommendations.

The objective is to approach the dataset from a business consulting perspective rather than simply present descriptive statistics.

## Business Problem

Businesses need visibility into both commercial performance and operational efficiency to identify areas that may require attention.

This project investigates five key questions:

1. How are revenue and recorded profit changing over time?
2. Which departments and product categories contribute most to recorded profitability?
3. Which customer segments contribute most to revenue and profit?
4. Which shipping modes and regions have weaker delivery performance?
5. Where should the business investigate potential profitability and operational issues?

## Technology Stack

| Area                    | Tools                |
| ----------------------- | -------------------- |
| Programming             | Python               |
| Data Analysis           | Pandas, NumPy        |
| Visualisation           | Plotly               |
| Business Intelligence   | Microsoft Power BI   |
| Data Modelling          | Power BI Star Schema |
| Calculations            | DAX                  |
| Development Environment | Jupyter Notebook     |

## Dataset Overview

**Dataset:** DataCo Smart Supply Chain Dataset

The dataset contains 180,519 records and 53 original columns covering orders, products, customers, sales, profitability, and shipping performance.

After cleaning and feature engineering, the analytical dataset contains:

| Metric            |                       Value |
| ----------------- | --------------------------: |
| Records           |                     180,519 |
| Original Columns  |                          53 |
| Processed Columns |                          50 |
| Unique Orders     |                      65,752 |
| Unique Customers  |                      20,652 |
| Unique Products   |                         118 |
| Date Range        | January 2015 – January 2018 |

The dataset contains multiple records per order because each record represents an order item. Therefore, distinct order counts are used for order-level analysis.

## Project Workflow

### 1. Data Cleaning and Preparation

- Inspected dataset structure, data types, and missing values.
- Checked for duplicate records and invalid date sequences.
- Removed unnecessary customer-identifying information.
- Removed columns with excessive missing values or limited analytical value.
- Reviewed revenue calculations against the source order-item totals.
- Created additional analytical fields for shipping duration, calculated late delivery, and order date grouping.
- Exported the cleaned dataset for further analysis.

### 2. Exploratory Data Analysis

Performed analysis across five business areas:

- Commercial performance: gross sales, net item revenue, discounts, and recorded profit.
- Product performance: revenue and profitability by product and category.
- Customer analysis: revenue, orders, and recorded profit by customer segment.
- Delivery operations: late delivery rates, shipping duration, and cancellations.
- Regional performance: profitability and delivery variations across regions.

### 3. Business Findings and Recommendations

Translated analytical results into business findings and recommendations, distinguishing observed patterns from potential explanations that require further investigation.

### 4. Power BI Dashboard

Built an interactive Power BI report using a star-schema data model, DAX measures, and synchronised slicers.

## Key Business Findings

### 1. Commercial Performance

- Total gross sales reached **36.78 million** in the dataset's monetary units.
- Net item revenue was **33.05 million**.
- Recorded profit was **3.97 million**.
- The profit-to-net-revenue ratio was approximately **12.00%**.
- Between 2015 and 2017, net item revenue declined by approximately 4.3%, while recorded profit declined by approximately 1.1%.

### 2. Product and Department Profitability

- Fan Shop and Apparel together contributed approximately 68.5% of recorded profit.
- Outdoors and Fitness showed relatively strong profit-to-net-revenue ratios.
- Strength Training had a comparatively low ratio of approximately 0.68%.
- Three products had negative aggregate recorded profit, although their transaction counts were low.

These products and categories warrant further investigation rather than immediate discontinuation.

### 3. Customer Performance

- Consumer customers contributed approximately 51.9% of net item revenue and 52.3% of recorded profit.
- Corporate and Home Office customers showed broadly similar profitability ratios.
- The top 10% of customers contributed approximately 29.22% of net item revenue.
- Approximately 19.7% of customers had negative aggregate recorded profit.

The findings suggest that customer-level profitability monitoring should consider both revenue and recorded profit rather than revenue alone.

### 4. Delivery Performance

- There were 63,097 eligible delivery orders after excluding cancellations.
- 36,048 eligible orders were classified as late.
- The overall late delivery rate was approximately 57.13%.
- First Class had a 100% late delivery rate.
- Second Class had a late delivery rate of approximately 79.99%.
- Standard Class had a comparatively lower late delivery rate of approximately 39.85%.
- The overall cancellation rate was approximately 4.34%.

Shipping-mode comparisons indicate areas for further investigation into delivery commitments and operational performance. They do not establish that shipping mode itself causes delays.

### 5. Transaction-Level Profitability

- Approximately 19.36% of order-item transactions had negative recorded profit ratios.
- These transactions represented approximately 6.38 million in net item revenue.
- Their combined recorded profit was approximately -3.88 million.

This highlights the importance of monitoring profitability at the transaction level rather than relying exclusively on aggregate revenue figures.

## Business Recommendations

Based on the observed findings, the following actions are recommended for further investigation:

| Area                      | Recommendation                                                                          |
| ------------------------- | --------------------------------------------------------------------------------------- |
| Shipping Performance      | Review delivery commitments for First Class and Second Class orders.                    |
| Product Profitability     | Investigate low-profit categories and products with negative aggregate recorded profit. |
| Transaction Profitability | Introduce transaction-level monitoring to identify unusually negative profit ratios.    |
| Customer Performance      | Monitor customer-level revenue and recorded profit together.                            |
| Regional Operations       | Investigate regional variations in delivery performance and profitability.              |

These recommendations are investigation priorities, not confirmed root causes. Additional procurement, inventory, carrier, and cost data would be required to validate the underlying explanations.

## Power BI Dashboard

The Power BI report is organised into three pages.

### 01 — Executive Overview

Provides a high-level view of gross sales, net item revenue, recorded profit, orders, profitability, and delivery performance.

### 02 — Commercial Intelligence

Explores profitability by product category and department, along with customer-segment and customer-level performance.

### 03 — Operational Intelligence

Examines late delivery rates, shipping duration, and cancellation rates across shipping modes and regions.

**Dashboard screenshots:** Add screenshots of your completed report to the `visuals/` folder and embed them below.

```markdown
![Executive Overview](visuals/executive_overview.png)

![Commercial Intelligence](visuals/commercial_intelligence.png)

![Operational Intelligence](visuals/operational_intelligence.png)
```

## Repository Structure

```text
Supply-Chain-Consulting/
│
├── data/
│   ├── raw/
│       ├──DataCoSupplyChainDataset.csv
│   └── processed/
│       └── supply_chain_clean.csv
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
├── powerbi/
│   ├──Supply-chain-dashboard.pbix
│   ├──Supply-chain-dashboard.pdf
├── reports/
│   ├──Executive Summary & Business Report
├── presentation/
│
├── visuals/
│   ├── 01 - Executive Overview
│   ├── 02 - Commercial Intelligence
│   ├── 03 - Operational Intelligence
├── docs/
│   ├── data_dictionary.md
│   ├── data_quality_report.md
│   ├── kpi_definitions.md
│   ├── methodology.md
│   ├── data_model.md
│   ├── dax_measures.md
│   └── dashboard_guide.md
│
└── README.md
```

## Data Limitations

The analysis is subject to the following limitations:

- The dataset covers January 2015 to January 2018, with 2018 containing January data only.
- Supplier, purchase order, procurement, and inventory information is unavailable.
- Carrier-level costs, routes, and capacity information are unavailable.
- Customer acquisition cost, retention, and lifetime value information is unavailable.
- The underlying accounting definition of recorded profit could not be independently verified.
- Delivery and profitability patterns are observational and do not establish causation.

These limitations are considered when interpreting findings and making recommendations.

## Documentation

Additional project documentation is available in the `docs/` directory:

- [Data Dictionary](docs/data_dictionary.md)
- [Data Quality Report](docs/data_quality_report.md)
- [KPI Definitions](docs/kpi_definitions.md)
- [Methodology](docs/methodology.md)
- [Data Model](docs/data_model.md)
- [DAX Measures](docs/dax_measures.md)
- [Dashboard Guide](docs/dashboard_guide.md)

## Project Objective

This project demonstrates an end-to-end analytics workflow, from raw data preparation and exploratory analysis to business interpretation, data modelling, and interactive dashboard development.

The focus is on translating data into measurable business findings and practical recommendations while clearly communicating analytical assumptions and limitations.
