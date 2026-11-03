# Project Summary

**Project:** CarDekho Used Car Price Analysis - Depreciation & Regression

**Business goal:** Understand what drives used-car prices, how prices vary with vehicle age, and how accurately listing prices can be estimated from vehicle attributes.

**Dataset:** 15K+ used-car listings with brand, model, age, kilometres driven, seller type, fuel, transmission, mileage, engine, max power, seats, and selling price.

**Key analytical findings:**
- Max power had the strongest numerical relationship with price (r = 0.751).
- Engine size also showed a strong positive relationship (r = 0.587).
- Vehicle age had a stronger negative association with price than kilometres driven.
- Age and kilometres driven were moderately correlated (r = 0.490), so usage should not be interpreted independently of age.
- Automatic vehicles had a median listing price of ₹10.5L versus ₹5.0L for manual vehicles, a raw 110% premium.

**Modeling:** Four regression approaches were compared. Gradient Boosting performed best overall with R² = 0.8086 and RMSE = ₹4.80L. Random Forest achieved the lowest MAE at ₹1.16L.

**Dashboard:** Three Power BI pages were built: Market Overview, Depreciation & Value Retention, and Regression & Pricing Intelligence.
