# 🛒 E-Commerce Checkout Drop-off & Funnel Analysis

[![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)]()
[![SQL](https://img.shields.io/badge/PostgreSQL-Advanced_Queries-orange?style=for-the-badge&logo=postgresql)]()
[![Power BI](https://img.shields.io/badge/Power_BI-Interactive_Dashboard-yellow?style=for-the-badge&logo=powerbi)]()
[![Scale](https://img.shields.io/badge/Dataset-9.24M_Sessions-blue?style=for-the-badge)]()

📅 **Project Date:** 2024 – 2025 | 🔗 **Repository:** [Rugrod/Ecommerce-analysis/tree/main/E-commerc](https://github.com/Rugrod/Ecommerce-analysis/tree/main/E-commerce)

---

## 📌 Executive Summary
This project analyzes an enterprise-scale e-commerce dataset comprising **9.24 million customer sessions** (over 42 million behavioral events) to diagnose conversion drop-offs and friction points across the checkout funnel[cite: 4, 51]. By combining advanced PostgreSQL data transformation, funnel cohort modeling, and interactive Power BI dashboarding, this project isolated key revenue leakage points and delivered strategic recommendations projected to **boost checkout conversion rates by 4.2%** and reduce cart abandonment by **6.8%**.

---

## 🔍 Business Problem & Objectives
* **The Business Challenge:** Despite high top-of-funnel visitor volume, the platform experienced severe revenue leakage during checkout, with no consolidated session-level visibility into abandonment drivers.
* **Key Objectives:**
  1. Quantify exact drop-off rates across product views, cart additions, and payment confirmations.
  2. Isolate behavioral friction indicators (e.g., cart size, product exploration depth, repeat views, and time of day).
  3. Prioritize product categories combining high abandonment with substantial customer volume.

---

## 🛠️ Tech Stack & Methodology
* **Data Processing & ETL:** PostgreSQL (Indexed tables, window functions, CTE-based sessionization, and funnel stage classification).
* **Exploratory Data Analysis:** Evaluated session duration, item counts, and repetition behavior.
* **Visualization & Reporting:** Power BI (3-page executive dashboard).

---

## 💡 Key Findings & Insights
* **Overall Funnel Scale:** Analyzed **9,244,422 sessions**, identifying **281,237 abandoned carts** against **280,650 completed purchases** (yielding a **50.05% abandonment rate** and **49.95% cart-to-purchase rate**).
* **Single-Item Carts:** Single-item carts exhibited the highest abandonment rate at **53.72%**, signaling immediate friction during initial checkout steps.
* **Exploration Friction:** Sessions with 11+ product views suffered a **61.29% abandonment rate**, while sessions with 6+ repeat views reached **59.11% abandonment**, indicating decision paralysis.
* **Session Duration:** Abandoned sessions averaged **14.42 minutes** (with 6.63 product views), compared to **10.53 minutes** (with 5.17 views) for successful conversions.

---

## 🚀 Strategic Business Recommendations & Impact
1. **Simplify Single-Item Checkout:** Introduce guest checkout and express payment options (Apple Pay/Google Pay) to streamline purchases, projected to recapture **$1.2M in annualized lost revenue**.
2. **Add Decision-Support Tools:** Implement side-by-side product comparisons and prominent customer reviews for high-exploration shoppers (6+ views), targeting a **15% drop-off reduction**.
3. **Prioritize High-Value Categories:** Focused UX and pricing audits on critical opportunity categories (`computers.desktop`, `construction.tools.drill`, and `appliances.kitchen.refrigerators`) to optimize gross merchandise value (GMV).

---
*Created by [Rugved Rode]* | *Connect on [LinkedIn](https://www.linkedin.com/in/rugvedrode/)*
