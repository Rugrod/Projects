# KPI Definitions
## Supply Chain & Commercial Performance Optimisation

### 1. Purpose

This document defines the key performance indicators used in the project's Python analysis and Power BI dashboard.

Each KPI includes its calculation, interpretation, and relevant considerations to ensure consistent reporting.

### 2. Commercial Performance KPIs

| KPI | Definition | Calculation |
|---|---|---|
| Total Gross Sales | Total gross sales recorded in the dataset | SUM(Sales) |
| Net Item Revenue | Total revenue after recorded item discounts | SUM(Order Item Total) |
| Total Discounts | Total discounts applied to order items | SUM(Order Item Discount) |
| Recorded Profit | Total recorded profit across order-item records | SUM(Order Profit Per Order) |
| Total Orders | Number of distinct orders | DISTINCTCOUNT(Order Id) |
| Total Customers | Number of distinct customers | DISTINCTCOUNT(Customer Id) |
| Unique Products | Number of distinct products | DISTINCTCOUNT(Product Card Id) |
| Total Units Sold | Total quantity of products sold | SUM(Order Item Quantity) |

### 3. Average Order Value KPIs

**Gross Average Order Value**

Calculation:

`Total Gross Sales / Total Orders`

Measures the average gross sales value per distinct order.

**Net Average Order Value**

Calculation:

`Net Item Revenue / Total Orders`

Measures the average net item revenue per distinct order.

Both measures use distinct Order IDs as the denominator rather than the number of order-item records.

### 4. Profitability KPIs

**Profit to Net Revenue %**

Calculation:

`Recorded Profit / Net Item Revenue`

Measures recorded profit relative to net item revenue.

The result is expressed as a percentage.

This is an analytical profitability ratio based on the available dataset fields. It should not be interpreted as an independently verified accounting margin.

**Negative-Profit Transactions**

Definition:

Number of order-item records where recorded profit is below zero.

Calculation:

`COUNTROWS(FactOrders where Order Profit Per Order < 0)`

This measure helps identify transactions requiring further profitability investigation.

### 5. Delivery Performance KPIs

Delivery performance is calculated at order level rather than transaction level to avoid counting multi-item orders multiple times.

**Eligible Delivery Orders**

Definition:

Distinct orders excluding orders marked as Shipping canceled.

Calculation:

`DISTINCTCOUNT(Order Id)` excluding `Delivery Status = "Shipping canceled"`.

**Late Orders**

Definition:

Distinct eligible orders where the calculated late-delivery indicator equals 1.

Calculation:

`DISTINCTCOUNT(Order Id)` where:

- Delivery Status is not Shipping canceled.
- Calculated Late Delivery = 1.

**Late Delivery Rate**

Calculation:

`Late Orders / Eligible Delivery Orders`

Measures the proportion of eligible orders delivered later than their scheduled shipping duration.

**On-Time Orders**

Calculation:

`Eligible Delivery Orders - Late Orders`

**Average Actual Shipping Days**

Definition:

Average actual shipping duration calculated using one shipping-duration value per eligible order.

**Average Scheduled Shipping Days**

Definition:

Average scheduled shipping duration calculated using one scheduled-duration value per eligible order.

### 6. Cancellation KPIs

**Cancelled Orders**

Definition:

Distinct orders marked as Shipping canceled.

**Cancellation Rate**

Calculation:

`Cancelled Orders / Total Orders`

Measures the proportion of all distinct orders that were cancelled.

Cancelled orders are excluded from the eligible delivery order denominator.

### 7. Customer Performance KPIs

Customer performance is evaluated using aggregated customer-level data.

| KPI | Calculation |
|---|---|
| Customer Net Revenue | SUM(Order Item Total) grouped by Customer Id |
| Customer Recorded Profit | SUM(Order Profit Per Order) grouped by Customer Id |
| Orders per Customer | Distinct Order Id count grouped by Customer Id |
| Revenue per Customer | Customer Net Revenue |
| Loss-Making Customers | Customers with aggregate recorded profit below zero |

Customer-level profitability is used to identify customers whose aggregated transactions generate negative recorded profit.

The analysis does not calculate customer lifetime value because the dataset does not provide sufficient acquisition, retention, and customer lifecycle information.

### 8. Product and Department Performance KPIs

| KPI | Calculation |
|---|---|
| Product Net Revenue | SUM(Order Item Total) grouped by Product Card Id |
| Product Recorded Profit | SUM(Order Profit Per Order) grouped by Product Card Id |
| Department Net Revenue | SUM(Order Item Total) grouped by Department Name |
| Department Recorded Profit | SUM(Order Profit Per Order) grouped by Department Name |
| Category Net Revenue | SUM(Order Item Total) grouped by Category Name |
| Category Recorded Profit | SUM(Order Profit Per Order) grouped by Category Name |
| Category Profitability Ratio | Recorded Profit / Net Item Revenue |

These metrics help compare revenue contribution and profitability across products, categories, and departments.

### 9. Regional Performance KPIs

| KPI | Calculation |
|---|---|
| Regional Net Revenue | SUM(Order Item Total) grouped by Order Region |
| Regional Recorded Profit | SUM(Order Profit Per Order) grouped by Order Region |
| Regional Late Delivery Rate | Late Orders / Eligible Delivery Orders within each region |
| Negative-Profit Transaction Rate | Negative-Profit Transactions / Total Transactions |
| Regional Profit to Net Revenue % | Recorded Profit / Net Item Revenue |

Regional delivery metrics exclude cancelled orders. Profitability metrics include all applicable order-item records.

### 10. Important Calculation Considerations

1. The source dataset is at order-item level, while delivery performance is measured at order level.
2. Distinct Order IDs are used when calculating order counts.
3. Cancelled orders are excluded from late-delivery calculations.
4. Cancellation rate uses all distinct orders as its denominator.
5. Net item revenue uses the original `Order Item Total` field.
6. Recorded profit is calculated by summing `Order Profit Per Order`.
7. Profitability percentages use net item revenue as the denominator.
8. Customer, product, department, category, and regional metrics are aggregated according to the relevant grouping.
9. Blank or zero denominators should be handled using safe division in Power BI.

---

**Document purpose:** This KPI reference establishes consistent calculation rules across the project's Python analysis and Power BI dashboard.