# Data Quality Report
## Supply Chain & Commercial Performance Optimisation

### 1. Objective

This report documents the data quality assessment and preparation performed on the DataCo Smart Supply Chain dataset before exploratory analysis and Power BI development.

The objective was to identify missing values, duplicate records, inconsistencies, and potential issues that could affect the accuracy of business analysis.

### 2. Dataset Profile

| Attribute | Result |
|---|---:|
| Original records | 180,519 |
| Original columns | 53 |
| Duplicate records | 0 |
| Unique orders | 65,752 |
| Unique customers | 20,652 |
| Unique products | 118 |
| Data coverage | January 2015 – January 2018 |

The dataset contains order-item-level records. Multiple records can belong to a single order.

### 3. Missing Value Assessment

The following columns required attention:

| Column | Missing Values | Missing Percentage | Action |
|---|---:|---:|---|
| Product Description | 180,519 | 100% | Removed |
| Order Zipcode | 155,679 | 86.24% | Removed |
| Customer Lname | 8 | Minimal | Removed as personally identifiable information |
| Customer Zipcode | 3 | Minimal | Removed as personally identifiable information |

Other customer fields, including names, email addresses, passwords, and street addresses, were excluded from the cleaned analytical dataset because they were not required for the analysis.

### 4. Duplicate Record Assessment

An exact duplicate check was performed on the original dataset.

**Result:** No exact duplicate rows were identified.

Identifier checks were also performed:

- Order Item Id: unique at transaction level.
- Order Id: repeated because orders can contain multiple items.
- Customer Id: repeated across customer transactions.
- Product Card Id: repeated across product transactions.

These repetitions are expected because of the order-item-level structure of the dataset.

### 5. Date and Delivery Validation

The order and shipping date fields were converted to datetime format.

Validation checks included:

- Checking for invalid order and shipping dates.
- Identifying shipping dates occurring before order dates.
- Comparing calendar shipping duration with the recorded shipping duration.
- Comparing actual shipping days with scheduled shipping days.

**Results:**

- Invalid order and shipping dates: 0.
- Shipping dates before order dates: 0.
- The recorded shipping duration matched the calendar-day difference exactly.
- Some differences were observed when comparing recorded shipping duration with exact elapsed hours. This is consistent with the dataset's calendar-day measurement.

### 6. Revenue Reconciliation

A reconciliation check was performed using:

`Calculated Net Value = (Order Item Quantity × Order Item Product Price) - Order Item Discount`

This calculated value was compared with the source field `Order Item Total`.

| Validation Result | Count |
|---|---:|
| Differences greater than 0.01 | 0 |
| Differences exactly equal to 0.01 | 4,613 |

The small differences are consistent with rounding. The original `Order Item Total` field was retained for revenue analysis rather than replacing source values with recalculated values.

### 7. Late Delivery Validation

The original `Late_delivery_risk` field was compared with a separately calculated late-delivery indicator.

The calculated indicator uses:

`Calculated Late Delivery = Actual Shipping Days > Scheduled Shipping Days`

A total of 4,423 mismatches were identified. All mismatches were associated with records marked as `Shipping canceled`.

To avoid mixing cancelled orders with completed delivery performance:

- The original `Late_delivery_risk` field was retained.
- A separate `Calculated Late Delivery` field was created.
- Cancelled orders were excluded from eligible delivery calculations.
- Cancellation performance was measured separately.

### 8. Data Cleaning Actions

The following preparation steps were performed:

1. Removed duplicate records, although no exact duplicates were found.
2. Removed fully missing and high-missing-value columns that were not needed for the analysis.
3. Excluded personally identifiable customer information.
4. Converted date fields into datetime format.
5. Converted relevant numerical fields into numeric data types.
6. Created order year, month, and year-month fields.
7. Created a calendar shipping duration field.
8. Created a separate calculated late-delivery indicator.
9. Standardised whitespace in regional labels.
10. Exported the cleaned dataset for subsequent analysis.

### 9. Final Data Quality Assessment

The cleaned dataset contains 180,519 records and 50 columns.

The preparation process addressed the identified missing-value, date, revenue-reconciliation, and delivery-validation issues relevant to the project's analysis.

The original source measures were retained where appropriate, and derived measures were added separately to maintain transparency.

### 10. Limitations

- The source dataset does not provide sufficient information to independently validate the accounting definition of recorded profit.
- Revenue