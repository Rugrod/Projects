# Power BI Data Model Documentation
## Supply Chain & Commercial Performance Optimisation

### 1. Overview

The Power BI data model was designed to support commercial, customer, product, and operational performance analysis.

The model uses a star-schema structure, with a central fact table connected to four dimension tables.

This structure separates transactional data from descriptive attributes and supports consistent filtering and aggregation across dashboard pages.

### 2. Data Model Structure

The model consists of five tables:

| Table | Type | Purpose |
|---|---|---|
| FactOrders | Fact table | Stores order-item-level transactional data |
| DimDate | Dimension table | Supports time-based analysis |
| DimProduct | Dimension table | Supports product, category, and department analysis |
| DimCustomer | Dimension table | Supports customer and segment analysis |
| DimShipping | Dimension table | Supports shipping-mode analysis |

### 3. Fact Table: FactOrders

`FactOrders` is the central table of the model.

It contains the cleaned transactional dataset, with each row representing an individual order item.

Important fields include:

- Order Id
- Order Item Id
- Customer Id
- Product Card Id
- Order Item Quantity
- Order Item Total
- Sales
- Order Profit Per Order
- Order Item Discount
- Shipping Mode
- Delivery Status
- Order Region
- Order Date
- Shipping Date
- Calculated Late Delivery

**Grain:** One row per order item.

Order-level measures use distinct Order IDs or order-level aggregation to avoid counting orders multiple times.

### 4. Dimension Tables

#### 4.1 DimDate

The date dimension was created to support time-based reporting.

Attributes include:

- Date
- Year
- Month Number
- Month
- Year Month
- Quarter
- Year Quarter

The table is marked as the model's date table.

The Month field is sorted by Month Number, while Year Month is sorted using a numeric Year Month Sort column.

The relationship uses `DimDate[Date]` and `FactOrders[order date (DateOrders)]`.

#### 4.2 DimProduct

The product dimension was created using the following attributes:

- Product Card Id
- Product Name
- Category Name
- Department Name

It supports product-, category-, and department-level performance analysis.

The dimension is created using distinct combinations of the product identifier and its descriptive attributes.

#### 4.3 DimCustomer

The customer dimension contains:

- Customer Id
- Customer Segment

It supports customer-level aggregation and comparisons between Consumer, Corporate, and Home Office segments.

Personally identifiable customer information is not included.

#### 4.4 DimShipping

The shipping dimension contains distinct shipping modes.

It supports comparisons of late-delivery rates, shipping durations, and cancellation rates across shipping methods.

### 5. Relationships

The model uses active, one-to-many relationships with single-direction filtering from dimension tables to the fact table.

| Dimension Table | Dimension Key | Fact Table Key | Cardinality |
|---|---|---|---|
| DimDate | Date | order date (DateOrders) | One-to-many |
| DimProduct | Product Card Id | Product Card Id | One-to-many |
| DimCustomer | Customer Id | Customer Id | One-to-many |
| DimShipping | Shipping Mode | Shipping Mode | One-to-many |

All four dimension tables connect directly to `FactOrders`.

### 6. Star Schema Design

The model follows this structure:

```text
                 DimDate
                    |
                    |
DimProduct ---- FactOrders ---- DimCustomer
                    |
                    |
               DimShipping
```

`FactOrders` stores transactional measures, while the dimension tables provide descriptive attributes used for filtering and grouping.

### 7. Modelling Decisions

The following design decisions were applied:

1. A separate date dimension was created for time intelligence and consistent date filtering.
2. Product attributes were separated into `DimProduct`.
3. Customer identifiers and customer segments were separated into `DimCustomer`.
4. Shipping modes were stored in `DimShipping`.
5. Dimension tables were connected using one-to-many relationships.
6. Relationships were configured with single-direction filtering.
7. The date table was marked as the official date table.
8. The active date relationship uses the order date.
9. Delivery measures use order-level aggregation because the fact table contains multiple items per order.

### 8. Model Validation

The dimension tables were checked against their corresponding fact-table attributes.

The mapping checks returned zero mismatches for the product and customer mappings.

The model was also checked to ensure that:

- Dimension keys represent the intended unique entities.
- Relationships are active.
- Relationships use the expected cardinality.
- Filtering flows from dimensions to the fact table.
- Measures return the expected baseline totals.

### 9. Benefits of the Model

The star-schema design provides:

- Clear separation between transactional and descriptive data.
- Consistent filtering across dashboard pages.
- Simplified DAX measure development.
- Reduced ambiguity in relationships.
- Easier maintenance and future expansion.
- Better organisation for commercial and operational reporting.

---

**Conclusion:** The Power BI model uses a central order-item fact table and four supporting dimensions to provide a structured foundation for interactive supply chain and commercial performance analysis.