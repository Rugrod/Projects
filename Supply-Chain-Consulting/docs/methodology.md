# Project Methodology
## Supply Chain & Commercial Performance Optimisation

### 1. Project Overview

This project follows a structured data analytics workflow to evaluate commercial performance, product profitability, customer behaviour, and supply chain delivery performance using the DataCo Smart Supply Chain dataset.

The methodology combines Python-based data preparation and exploratory analysis with Power BI data modelling, DAX calculations, and interactive dashboard development.

### 2. Project Workflow

The project was completed through the following stages:

1. Dataset acquisition and inspection
2. Data cleaning and preparation
3. Data quality validation
4. Exploratory data analysis
5. Business findings and recommendations
6. Power BI data modelling
7. DAX measure development
8. Dashboard development and validation
9. Business reporting and presentation

### 3. Dataset Inspection

The initial dataset was examined to understand its structure, size, data types, missing values, and available business dimensions.

The dataset contained:

- 180,519 order-item records.
- 53 original columns.
- 65,752 distinct orders.
- 20,652 distinct customers.
- 118 distinct products.

The available information covered sales, discounts, recorded profit, products, customers, delivery status, shipping modes, dates, and geographic regions.

### 4. Data Cleaning and Preparation

Python and Pandas were used to prepare the dataset for analysis.

Key activities included:

- Checking for duplicate records.
- Assessing missing values.
- Removing unnecessary columns and personally identifiable information.
- Converting date and numerical fields into appropriate data types.
- Standardising regional labels.
- Creating additional date attributes.
- Calculating calendar shipping duration.
- Creating a separate calculated late-delivery indicator.

The original dataset measures were retained where appropriate to preserve source information.

The cleaned dataset was exported as a CSV file for further analysis and Power BI development.

### 5. Data Quality Validation

Several validation checks were performed before proceeding with the analysis.

These included:

- Duplicate record validation.
- Missing-value assessment.
- Order and shipping date validation.
- Net revenue reconciliation.
- Comparison of original and calculated late-delivery indicators.
- Validation of identifier uniqueness and repetition.

Cancelled orders were handled separately from eligible delivery orders to avoid distorting delivery performance calculations.

Detailed results are documented in `data_quality_report.md`.

### 6. Exploratory Data Analysis

Exploratory data analysis was performed using Python, Pandas, NumPy, and Plotly.

The analysis focused on five business areas:

**Commercial Performance**
- Gross sales and net item revenue.
- Recorded profit.
- Monthly and annual revenue trends.
- Average order value.

**Product and Department Performance**
- Product-level revenue and recorded profit.
- Department contribution.
- Category-level profitability.
- Identification of products with negative aggregate recorded profit.

**Customer Performance**
- Revenue and profit by customer segment.
- Customer-level profitability.
- Customer revenue concentration.
- Identification of loss-making customers.

**Delivery Performance**
- Late-delivery rates.
- Shipping-mode comparisons.
- Actual versus scheduled shipping duration.
- Cancellation rates.

**Regional Performance**
- Regional revenue and recorded profit.
- Negative-profit transaction rates.
- Regional delivery performance.

The findings were used to identify business areas requiring further investigation.

### 7. Power BI Data Modelling

The cleaned dataset was imported into Power BI as the central fact table, `FactOrders`.

Dimension tables were created to organise the analytical model:

- `DimDate`
- `DimProduct`
- `DimCustomer`
- `DimShipping`

The model follows a star-schema structure, with the dimension tables connected to the central fact table through one-to-many relationships.

A dedicated date table was created and marked as the model's date table. Appropriate sorting was applied to month and year-month fields.

The model was validated using mapping checks to ensure that dimension records correctly represented the corresponding fact-table attributes.

### 8. DAX Measure Development

DAX measures were created to calculate the dashboard KPIs dynamically.

The measures cover:

- Gross sales and net item revenue.
- Recorded profit and profitability ratio.
- Total orders and customers.
- Average order value.
- Late orders and late-delivery rate.
- Eligible delivery orders.
- Cancelled orders and cancellation rate.
- Average actual and scheduled shipping duration.

Order-level aggregation was used for delivery measures to prevent multiple order items from inflating order counts.

### 9. Dashboard Development

An interactive Power BI dashboard was developed with three analytical pages.

**Executive Overview**

Provides a high-level summary of commercial and operational performance through KPI cards, revenue trends, department comparisons, customer segment profitability, and delivery status.

**Commercial Intelligence**

Focuses on product category profitability, department performance, customer segment contribution, and customer-level revenue versus recorded profit.

**Operational Intelligence**

Examines delivery performance through shipping-mode comparisons, regional late-delivery rates, actual versus scheduled shipping duration, and cancellation rates.

Interactive slicers were added for order year, customer segment, and department. These filters allow users to explore performance across different business dimensions.

### 10. Business Interpretation

The results were translated into business findings and recommendations.

The recommendations focus on:

- Reviewing shipping commitments.
- Investigating low-profit products and categories.
- Monitoring negative-profit transactions.
- Tracking commercial performance across customer segments.
- Monitoring regional operational performance.

Recommendations are presented as investigation priorities rather than proven solutions because the dataset does not contain all the operational and financial information needed to establish causality.

### 11. Tools and Technologies

| Technology | Application |
|---|---|
| Python | Data preparation and analysis |
| Pandas | Data manipulation and aggregation |
| NumPy | Numerical calculations |
| Plotly | Interactive data visualisations |
| tqdm | Progress monitoring |
| Jupyter Notebook | Analysis environment |
| Power BI | Data modelling and