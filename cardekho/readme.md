# CarDekho Used Car Price Analysis & Pricing Intelligence

An end-to-end data science and business intelligence project analyzing $15\text{K}+$ used-car listings from CarDekho. This repository covers data cleaning, exploratory data analysis, cross-sectional market depreciation modeling, predictive machine learning regression, and an interactive Power BI executive dashboard.

---

## 📌 Project Overview & Objectives

A used-car marketplace requires a structured, transparent, and accurate mechanism to estimate vehicle listing prices, explain resale value drivers, and understand vehicle depreciation dynamics. 

### Key Business Questions:
1. **Price Drivers:** Which vehicle specifications (power, engine, transmission, age, mileage) have the strongest impact on resale value?
2. **Depreciation & Value Retention:** How do different car brands retain their value over time?
3. **Predictive Intelligence:** Can machine learning models accurately predict used car listing prices based on structural vehicle attributes?

---

## 📊 Dataset & Workflow

The analysis was performed on a dataset containing over **15,000 used car listings** with attributes including brand, model, vehicle age, kilometers driven, fuel type, transmission, mileage, engine capacity, max power, seating capacity, and selling price.

```
       ┌─────────────┐     ┌─────────────┐     ┌─────────────────────┐
       │  Raw Data   │ ──> │ Data Clean  │ ──> │ Feature Engineering │
       └─────────────┘     └─────────────┘     └─────────────────────┘
                                                          │
       ┌─────────────┐     ┌─────────────┐                │
       │  Power BI   │ <── │ Regression  │ <──────────────┘
       │ Dashboard   │     │  Modeling   │
       └─────────────┘     └─────────────┘
```

### Data Cleaning & Preprocessing
* **Duplicate Removal:** Dropped redundant index columns and 2 duplicate records.
* **Data Correction:** Corrected invalid seating capacity entries ($0$ seats) for Honda City and Nissan Kicks to $5$ seats.
* **Outlier Capping:** Applied a business cap excluding extreme mileage observations ($> 300,000\text{ km}$) to ensure regression stability.
* **Feature Engineering ($5+$ features created):**
  * `Selling Price in Lakh` ($\text{₹}$)
  * `Kilometres per Year`
  * `Vehicle Age Groups` & `KM Bands`
  * `Power per Litre`

---

## 🔍 Key Analytical Findings

### 1. Feature Correlations with Price

| Relationship | Correlation ($r$) | Key Interpretation |
| :--- | :---: | :--- |
| **Max Power vs. Price** | **$+0.751$** | Strongest overall numerical correlation with price |
| **Engine vs. Price** | **$+0.587$** | Strong positive relationship |
| **Mileage (km/l) vs. Price** | **$-0.306$** | Negative association (economy cars tend to be priced lower) |
| **Vehicle Age vs. Price** | **$-0.241$** | Vehicle age impacts price significantly more than distance driven |
| **KM Driven vs. Price** | **$-0.121$** | Weak negative direct association |
| **KM Driven vs. Vehicle Age** | **$+0.490$** | Moderate positive relationship (KM driven should be evaluated alongside age) |

### 2. Transmission Price Disparity
* **Automatic Vehicles:** Median listing price of **$\text{₹}10.5\text{ Lakh}$**
* **Manual Vehicles:** Median listing price of **$\text{₹}5.0\text{ Lakh}$**
* **Raw Premium:** **$110\%$** higher median listing price for automatic variants.
* *Note:* This represents an observational market difference. Automatic cars in the dataset also tend to be newer, feature higher power outputs, or belong to premium brand segments.

### 3. Cross-Sectional Depreciation & 5-Year Value Retention
* **Cross-Sectional Baseline:** Normalized using the median used-market price of 1-year-old vehicles.
* **5-Year Value Retention Rate:**
  * **Maruti:** Retains **$84.8\%$** of its 1-year used-market value.
  * **Hyundai:** Retains **$82.3\%$** of its 1-year used-market value.

---

## 🤖 Regression Model Comparison

Four regression models were trained and evaluated to predict vehicle listing prices. Non-linear and ensemble algorithms significantly outperformed standard linear models.

| Model | $R^{2}$ Score | MAE ($\text{₹}$) | RMSE ($\text{₹}$) | Notes |
| :--- | :---: | :---: | :---: | :--- |
| **Linear Regression** | $0.5277$ | $2.19\text{L}$ | $7.53\text{L}$ | Baseline model; struggles with non-linear interactions |
| **Log-Linear Regression** | $0.7083$ | $1.57\text{L}$ | $5.92\text{L}$ | Reduced variance issues via log transform |
| **Random Forest** | $0.7670$ | **$1.16\text{L}$** | $5.29\text{L}$ | **Best MAE** (Lowest absolute error) |
| **Gradient Boosting** | **$0.8086$** | $1.29\text{L}$ | **$4.80\text{L}$** | **Best Overall Model** (Highest $R^2$, lowest RMSE) |

> **Selected Model:** **Gradient Boosting** was selected as the optimal production model, accounting for **$\sim 81\%$** of observed price variation.

---

## 📈 Power BI Interactive Dashboard

The dashboard is structured into three executive views designed for interactive exploration:

1. **Page 1: Market Overview**
   * High-level market KPIs, listing volume by brand, median pricing, fuel & transmission mix, price distribution bands.
2. **Page 2: Depreciation & Value Retention**
   * Price degradation curves by vehicle age, age-group price distributions, 5-year retention rates across volume brands.
3. **Page 3: Regression & Pricing Intelligence**
   * Model KPI metrics ($R^2$, MAE, RMSE), feature importance rankings, actual vs. predicted price plots, and error breakdowns by brand segment.

---

## 💡 Strategic Business Recommendations

1. **Core Pricing Features:** Prioritize vehicle age, maximum power, engine displacement, brand category, and transmission type as primary pricing inputs.
2. **Multi-Variable Mileage Rules:** Evaluate kilometers driven in conjunction with vehicle age rather than as a standalone metric.
3. **Model Selection:** Use non-linear ensemble models (e.g., Gradient Boosting / XGBoost) for algorithmic marketplace valuation engines.
4. **Segment Calibration:** Monitor evaluation errors by vehicle brand; implement localized/specialized models for high-variance luxury brands (e.g., Land Rover, Jaguar, BMW).
5. **Transparency Tools:** Leverage cross-sectional depreciation trends to provide price transparency to buyers and realistic listing range guidance to sellers.

---

## ⚠️ Limitations

* **Listing vs. Transaction Price:** Analysis is based on listing prices, which may differ slightly from final negotiated transaction prices.
* **MSRP Availability:** Original manufacturer suggested retail price (MSRP) was not available in the dataset; depreciation is cross-sectional across current market listings.
* **Vehicle History:** Granular parameters such as accident history, individual vehicle condition, service logs, and specific trim lines were not captured.

---

## 🛠️ Tools & Technologies Used

* **Languages:** Python
* **Data Processing & EDA:** Pandas, NumPy, Plotly
* **Machine Learning:** Scikit-Learn (Linear Regression, Random Forest, Gradient Boosting)
* **Business Intelligence:** Power BI, DAX