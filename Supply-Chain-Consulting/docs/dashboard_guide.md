# Power BI Dashboard Guide
## Supply Chain & Commercial Performance Optimisation

### 1. Dashboard Overview

The Power BI report provides an interactive view of commercial performance, product profitability, customer contribution, and delivery operations using the DataCo Smart Supply Chain dataset.

The report is organised into three pages:

1. Executive Overview
2. Commercial Intelligence
3. Operational Intelligence

The dashboard uses a star-schema data model with `FactOrders` as the central fact table and separate date, product, customer, and shipping dimensions.

### 2. Page 1 — Executive Overview

**Purpose:** Provide a high-level summary of business performance and highlight the main commercial and operational indicators.

#### KPI Cards

| KPI | Description |
|---|---|
| Gross Sales | Total gross sales recorded |
| Net Item Revenue | Revenue after recorded item discounts |
| Recorded Profit | Total recorded profit |
| Profit to Net Revenue % | Recorded profit as a percentage of net item revenue |
| Total Orders | Number of distinct orders |
| Late Delivery Rate | Percentage of eligible orders classified as late |

#### Visuals

**Monthly Revenue Trend**
- Displays net item revenue over time.
- Helps identify changes and patterns in monthly revenue.
- Profit and order count are available as additional tooltip information.

**Revenue by Department**
- Compares net item revenue across departments.
- Highlights the departments contributing the largest share of revenue.

**Profit by Customer Segment**
- Compares recorded profit across Consumer, Corporate, and Home Office segments.
- Helps assess the contribution of each customer segment.

**Delivery Status Split**
- Compares eligible late and on-time orders.
- Cancelled orders are excluded from this visual.

### 3. Page 2 — Commercial Intelligence

**Purpose:** Examine profitability across products, categories, departments, and customer segments.

#### Visuals

**Recorded Profit by Product Category**
- Displays recorded profit across product categories.
- Helps identify categories with relatively strong or weak recorded profitability.

**Department Revenue vs Profitability**
- A scatter plot comparing net item revenue with profit to net revenue percentage.
- Helps identify departments with high revenue but comparatively lower profitability.

**Recorded Profit by Customer Segment**
- Compares recorded profit across customer segments.
- Supports analysis of commercial contribution by segment.

**Customer Revenue vs Recorded Profit**
- A scatter plot comparing customer-level net item revenue with recorded profit.
- Each point represents a customer.
- Customer segment is used to distinguish groups.
- A zero-profit reference line helps identify customers with negative recorded profit.

### 4. Page 3 — Operational Intelligence

**Purpose:** Analyse delivery performance, shipping duration, and order cancellations.

#### KPI Cards

| KPI | Description |
|---|---|
| Eligible Delivery Orders | Distinct orders excluding cancellations |
| Late Delivery Rate | Percentage of eligible orders classified as late |
| Average Actual Shipping Days | Average actual shipping duration per eligible order |
| Cancellation Rate | Cancelled orders as a percentage of total orders |

#### Visuals

**Late Delivery Rate by Shipping Mode**
- Compares late delivery rates across First Class, Second Class, Same Day, and Standard Class.
- Helps identify shipping modes that require further investigation.

**Late Delivery Rate by Region**
- Compares late delivery rates across the 23 regions.
- Highlights geographic variation in delivery performance.

**Actual vs Scheduled Shipping Days**
- Compares average actual and scheduled shipping duration by shipping mode.
- Helps identify differences between delivery commitments and recorded performance.

**Cancellation Rate by Shipping Mode**
- Compares the percentage of cancelled orders across shipping modes.
- Provides an additional operational performance indicator.

### 5. Dashboard Filters and Navigation

The report includes three slicers synchronised across all three pages.

| Slicer | Field | Purpose |
|---|---|---|
| Order Year | `DimDate[Year]` | Filter the report by order year |
| Customer Segment | `DimCustomer[Customer Segment]` | Analyse selected customer segments |
| Department | `DimProduct[Department Name]` | Focus on selected departments |

All slicers use dropdown selections to keep the report layout compact.

A page navigator allows users to move between Executive Overview, Commercial Intelligence, and Operational Intelligence.

### 6. How to Use the Dashboard

1. Start with the Executive Overview to understand the overall performance.
2. Select an order year, customer segment, or department using the slicers.
3. Move to Commercial Intelligence to investigate product, category, department, and customer profitability.
4. Use Operational Intelligence to examine delivery delays, shipping duration, and cancellations.
5. Hover over charts to view additional tooltip information.
6. Clear slicer selections to return to the complete dataset view.

### 7. Important Interpretation Notes

- The dataset contains multiple order-item records per order. Order-related KPIs use distinct order counts where appropriate.
- Cancelled orders are excluded from eligible delivery orders and late delivery calculations.
- The late delivery indicator is based on actual shipping days exceeding scheduled shipping days.
- Shipping-mode comparisons are descriptive. They do not establish that a particular shipping mode causes delivery delays.
- Profitability is based on the dataset's recorded profit fields. It should not be interpreted as an independently verified accounting margin.
- The dataset does not contain sufficient supplier, inventory, procurement, or carrier-level information to establish the root causes of operational issues.
- The dataset covers January 2015 to January 2018. January 2018 represents only a partial year.

### 8. Dashboard Objective

The dashboard is designed to help users:

- Monitor overall commercial performance.
- Identify products and categories requiring profitability investigation.
- Compare revenue and recorded profit across customer segments.
- Identify shipping modes and regions with weaker delivery performance.
- Explore performance through interactive filters.

The report is intended as a decision-support and investigation tool rather than a system that independently establishes operational root causes.