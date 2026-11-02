# Data Dictionary
## Supply Chain & Commercial Performance Optimisation

### 1. Dataset Overview

The project uses the DataCo Smart Supply Chain dataset to analyse commercial performance, customer behaviour, product profitability, and delivery operations.

| Attribute | Description |
|---|---|
| Dataset | DataCo Smart Supply Chain |
| Original records | 180,519 |
| Original columns | 53 |
| Date coverage | January 2015 – January 2018 |
| Unique orders | 65,752 |
| Unique customers | 20,652 |
| Unique products | 118 |
| Data granularity | Order-item / transaction level |

**Important:** Each row represents an order item, not necessarily an entire order. An order can contain multiple items, so order-level metrics must use distinct Order IDs or an appropriate order-level aggregation.

### 2. Order and Transaction Fields

| Column | Description | Usage |
|---|---|---|
| Order Id | Unique identifier for an order | Order counting and aggregation |
| Order Item Id | Identifier for an individual order item | Transaction-level analysis |
| Order Item Quantity | Number of units purchased | Sales volume analysis |
| Order Item Product Price | Product price recorded for the order item | Revenue analysis |
| Order Item Discount | Discount amount applied to the order item | Discount analysis |
| Order Item Discount Rate | Recorded discount rate | Discount comparisons |
| Order Item Total | Net item revenue recorded in the dataset | Net revenue calculations |
| Order Status | Recorded order status | Order status analysis |
| Type | Order type information | Descriptive analysis |

### 3. Sales and Profitability Fields

| Column | Description | Usage |
|---|---|---|
| Sales | Gross sales value recorded in the dataset | Gross sales analysis |
| Order Profit Per Order | Recorded profit value associated with an order item | Profitability analysis |
| Order Item Profit Ratio | Recorded profit ratio for an order item | Transaction-level profitability |
| Benefit per order | Recorded benefit value associated with an order item | Supporting profitability analysis |
| Sales per customer | Sales value associated with a customer | Customer performance analysis |

**Calculation note:** The project uses `Order Item Total` as the net item revenue measure and sums `Order Profit Per Order` for recorded profit. The profit-to-net-revenue ratio is calculated as:

`Recorded Profit / Net Item Revenue`

This is an analytical ratio based on the available dataset fields, not an independently verified accounting margin.

### 4. Product Fields

| Column | Description | Usage |
|---|---|---|
| Product Card Id | Product identifier | Product-level grouping |
| Product Name | Product name | Product performance analysis |
| Product Category Id | Product category identifier | Category mapping |
| Category Id | Category identifier | Category analysis |
| Category Name | Product category name | Category performance |
| Department Id | Department identifier | Department mapping |
| Department Name | Department name | Department performance |
| Product Price | Recorded product price | Product analysis |
| Product Image | Product image reference | Descriptive information |
| Product Status | Product status field | Supporting product information |

### 5. Customer Fields

| Column | Description | Usage |
|---|---|---|
| Customer Id | Unique customer identifier | Customer-level aggregation |
| Customer Segment | Customer classification | Segment performance analysis |
| Customer City | Customer city | Geographic analysis |
| Customer State | Customer state | Geographic analysis |
| Customer Country | Customer country | Geographic analysis |

Personally identifiable fields such as customer names, email addresses, passwords, and street addresses were excluded from the cleaned analytical dataset.

### 6. Shipping and Delivery Fields

| Column | Description | Usage |
|---|---|---|
| Shipping Mode | Shipping service selected for an order | Shipping performance comparison |
| Delivery Status | Recorded delivery status | Delivery and cancellation analysis |
| Days for shipping (real) | Actual shipping duration recorded in the dataset | Delivery duration analysis |
| Days for shipment (scheduled) | Scheduled shipping duration | Delivery commitment comparison |
| Late_delivery_risk | Original late-delivery risk indicator | Source-field validation |
| shipping date (DateOrders) | Recorded shipping date | Date validation |
| order date (DateOrders) | Recorded order date | Date analysis |

The project also creates a separate calculated late-delivery indicator using actual shipping days compared with scheduled shipping days. Cancelled orders are excluded from late-delivery rate calculations and analysed separately.

### 7. Geographic Fields

| Column | Description | Usage |
|---|---|---|
| Market | Market classification | Market-level analysis |
| Order Region | Region associated with the order | Regional performance |
| Order Country | Country associated with the order | Geographic analysis |
| Order State | State associated with the order | Geographic analysis |
| Order City | City associated with the order | Geographic analysis |
| Latitude | Geographic latitude value | Geographic reference |
| Longitude | Geographic longitude value | Geographic reference |

### 8. Derived Fields Created During Data Preparation

| Derived Field | Definition | Usage |
|---|---|---|
| Order Year | Year extracted from the order date | Annual trend analysis |
| Order Month | Month number extracted from the order date | Monthly analysis |
| Order Year Month | Year and month formatted as YYYY-MM | Monthly trend analysis |
| Calendar Shipping Days | Difference between shipping date and order date at calendar-day level | Date validation |
| Calculated Late Delivery | 1 when actual shipping days exceed scheduled shipping days; otherwise 0 | Late-delivery analysis |

### 9. Data Interpretation Notes

1. The dataset is at order-item level. Order counts should use distinct Order IDs.
2. Multiple order-item records can belong to the same order.
3. `Order Item Total` is used for net item revenue.
4. `Order Profit Per Order` is summed at transaction level for recorded profit.
5. Cancelled orders are excluded from eligible delivery orders.
6. The calculated late-delivery indicator is retained separately from the original `Late_delivery_risk` field.
7. The dataset does not contain sufficient supplier, procurement, inventory, carrier-cost, or customer acquisition information to support analysis of those areas.
8. The dataset covers January 2015 through January 2018, with 2018 containing January data only.

---

**Document purpose:** This data dictionary establishes consistent definitions for the fields used in the project's Python analysis and Power BI dashboard.