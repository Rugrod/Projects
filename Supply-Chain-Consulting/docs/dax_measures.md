# DAX Measures Documentation
## Supply Chain & Commercial Performance Optimisation

### 1. Overview

DAX (Data Analysis Expressions) was used in Power BI to create dynamic measures for commercial, customer, product, and operational performance analysis.

The measures are calculated from the `FactOrders` table and respond to the dashboard's date, customer segment, and department filters.

### 2. Commercial Performance Measures

#### Total Gross Sales

```dax
Total Gross Sales =
SUM(FactOrders[Sales])
```

Calculates the total gross sales recorded in the dataset.

#### Net Item Revenue

```dax
Net Item Revenue =
SUM(FactOrders[Order Item Total])
```

Calculates total net item revenue using the source `Order Item Total` field.

#### Total Discounts

```dax
Total Discounts =
SUM(FactOrders[Order Item Discount])
```

Calculates the total recorded discounts across order items.

#### Recorded Profit

```dax
Recorded Profit =
SUM(FactOrders[Order Profit Per Order])
```

Calculates the total recorded profit across order-item records.

#### Total Orders

```dax
Total Orders =
DISTINCTCOUNT(FactOrders[Order Id])
```

Counts unique orders rather than individual order-item records.

#### Total Customers

```dax
Total Customers =
DISTINCTCOUNT(FactOrders[Customer Id])
```

Counts unique customers in the selected filter context.

#### Unique Products

```dax
Unique Products =
DISTINCTCOUNT(FactOrders[Product Card Id])
```

Counts distinct products.

#### Total Units Sold

```dax
Total Units Sold =
SUM(FactOrders[Order Item Quantity])
```

Calculates the total quantity of products sold.

### 3. Average Order Value Measures

#### Gross Average Order Value

```dax
Gross Average Order Value =
DIVIDE([Total Gross Sales], [Total Orders])
```

Calculates average gross sales per distinct order.

#### Net Average Order Value

```dax
Net Average Order Value =
DIVIDE([Net Item Revenue], [Total Orders])
```

Calculates average net item revenue per distinct order.

### 4. Profitability Measures

#### Profit to Net Revenue %

```dax
Profit to Net Revenue % =
DIVIDE([Recorded Profit], [Net Item Revenue])
```

Calculates recorded profit as a percentage of net item revenue.

This is an analytical ratio based on the available dataset fields and is not an independently verified accounting margin.

### 5. Delivery Performance Measures

#### Eligible Delivery Orders

```dax
Eligible Delivery Orders =
CALCULATE(
    DISTINCTCOUNT(FactOrders[Order Id]),
    FactOrders[Delivery Status] <> "Shipping canceled"
)
```

Counts distinct orders excluding cancelled orders.

#### Late Orders

```dax
Late Orders =
CALCULATE(
    DISTINCTCOUNT(FactOrders[Order Id]),
    FactOrders[Delivery Status] <> "Shipping canceled",
    FactOrders[Calculated Late Delivery] = 1
)
```

Counts distinct eligible orders classified as late using the calculated late-delivery indicator.

#### Late Delivery Rate

```dax
Late Delivery Rate =
DIVIDE([Late Orders], [Eligible Delivery Orders])
```

Calculates the percentage of eligible orders delivered later than their scheduled shipping duration.

#### On-Time Orders

```dax
On-Time Orders =
[Eligible Delivery Orders] - [Late Orders]
```

Calculates eligible orders that were not classified as late.

#### Average Actual Shipping Days

```dax
Average Actual Shipping Days =
AVERAGEX(
    VALUES(FactOrders[Order Id]),
    CALCULATE(
        MAX(FactOrders[Days for shipping (real)]),
        FactOrders[Delivery Status] <> "Shipping canceled"
    )
)
```

Calculates average actual shipping duration using one value per eligible order.

#### Average Scheduled Shipping Days

```dax
Average Scheduled Shipping Days =
AVERAGEX(
    VALUES(FactOrders[Order Id]),
    CALCULATE(
        MAX(FactOrders[Days for shipment (scheduled)]),
        FactOrders[Delivery Status] <> "Shipping canceled"
    )
)
```

Calculates average scheduled shipping duration using one value per eligible order.

### 6. Cancellation Measures

#### Cancelled Orders

```dax
Cancelled Orders =
CALCULATE(
    DISTINCTCOUNT(FactOrders[Order Id]),
    FactOrders[Delivery Status] = "Shipping canceled"
)
```

Counts distinct cancelled orders.

#### Cancellation Rate

```dax
Cancellation Rate =
DIVIDE([Cancelled Orders], [Total Orders])
```

Calculates the percentage of total distinct orders that were cancelled.

### 7. Date Table Calculated Column

The following calculated column was used to sort the Year Month field chronologically.

```dax
Year Month Sort =
YEAR(DimDate[Date]) * 100 + MONTH(DimDate[Date])
```

The `Year Month` column is sorted using `Year Month Sort` to ensure chronological ordering in time-series visuals.

### 8. Baseline Measure Validation

The following values were used to validate the dashboard against the full dataset without additional filters.

| Measure | Expected Value |
|---|---:|
| Total Gross Sales | 36,784,735.01 |
| Net Item Revenue | 33,054,402.38 |
| Total Discounts | 3,730,378.40 |
| Recorded Profit | 3,966,902.97 |
| Total Orders | 65,752 |
| Total Customers | 20,652 |
| Unique Products | 118 |
| Gross Average Order Value | 559.45 |
| Net Average Order Value | 502.71 |
| Profit to Net Revenue % | 12.00% |
| Eligible Delivery Orders | 63,097 |
| Late Orders | 36,048 |
| Late Delivery Rate | 57.13% |
| Cancelled Orders | 2,855 |
| Cancellation Rate | 4.34% |

### 9. Calculation Considerations

1. `DISTINCTCOUNT(Order Id)` is used for order counts because the fact table contains multiple order items per order.
2. Delivery measures exclude records marked as Shipping canceled.
3. Delivery duration measures use one value per order to avoid over-weighting multi-item orders.
4. Cancellation rate uses total distinct orders as its denominator.
5. `DIVIDE()` is used for percentage and ratio calculations to handle zero denominators safely.
6. Dashboard measures respond to the report's active relationships and slicers.
7. The baseline values represent the complete dataset before applying additional report filters.

---

**Document purpose:** This reference provides transparency into the Power BI calculations and makes the dashboard's KPI logic easier to review, validate, and maintain.