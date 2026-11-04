# 🚀 Indian Startup Funding Analysis (2015–2021)

An end-to-end data analytics project exploring capital distribution across sectors, funding stages, startup hubs, and company-level concentrations within the Indian startup ecosystem.

---

## 📌 Executive Summary

This project analyzes **5,074 Indian startup funding records** spanning **2015 to 2021**, capturing **₹610,548.29 Cr** in total funding across **3,139 normalized startups**.

The central finding of this analysis is that aggregate startup funding metrics are heavily skewed by mega-deal activity:
- **Mega Deals (≥ ₹500 Cr):** Accounted for **70.58%** of total capital raised.
- **Skewed Distribution:** The average disclosed deal size (**₹175.70 Cr**) is more than **10× the median** (**₹16.50 Cr**).
- **Data Disclosure:** Only **68.49%** of raw records disclosed investment values, making separate evaluation of deal volume vs. capital volume essential.
- **Geographic Concentration:** The top 3 hubs (**Bengaluru, Delhi NCR, Mumbai**) captured **85.37%** of all funding.
- **Sector Leadership:** **FinTech** led all sectors with **17.65%** of total capital raised.

---

## 🛠 Tech Stack & Tools

- **Data Wrangling & Cleaning:** Python (`pandas`, `NumPy`)
- **Exploratory Data Analysis (EDA):** `Plotly`, `Matplotlib`, `Seaborn`
- **Business Intelligence & Dashboards:** Power BI, DAX, Power Query

---

## 📊 Key Performance Indicators (KPIs)

| Metric | Value | Description / Note |
| :--- | :--- | :--- |
| **Total Recorded Funding** | **₹610,548.29 Cr** | Cumulative funding (2015–2021) |
| **Total Funding Records** | **5,074** | Complete dataset record count |
| **Normalized Startups** | **3,139** | Unique companies after canonical matching |
| **Disclosed Funding Records** | **3,475** | Records with `amount > 0` |
| **Funding Disclosure Rate** | **68.49%** | Share of records reporting financial values |
| **Average Disclosed Deal Size** | **₹175.70 Cr** | Mean of disclosed deals |
| **Median Disclosed Deal Size** | **₹16.50 Cr** | Median of disclosed deals (reflects typical deal size) |
| **Largest Single Round** | **₹16,650.00 Cr** | Single largest deal recorded |
| **Mega Deal Share (≥ ₹500 Cr)** | **70.58%** | Share of capital captured by mega rounds |

---

## 🔍 Key Findings & Insights

### 1. 📈 Annual Funding Trend
Headline capital peaked dramatically in **2020**, driven predominantly by massive growth-stage and mega-round investments. Outside of this surge, baseline annual funding remained relatively steady between ₹30,000 Cr and ₹70,000 Cr.

### 2. 🏢 Sector Intelligence
Capital deployment was heavily concentrated in top tech sectors:
* **FinTech:** ₹107,771.03 Cr (**17.65%** share)
* **E-Commerce & Retail:** ₹81,428.66 Cr (**13.34%** share)
* **EdTech:** ₹68,387.70 Cr (**11.20%** share)
* **FoodTech:** ₹49,406.01 Cr (**8.09%** share)
* **Mobility:** ₹40,100.95 Cr (**6.57%** share)

*The Top 3 sectors captured **42.19%** of capital; the Top 5 captured **56.85%**.*

### 3. 📍 Geographic Ecosystem Concentration
Startup capital in India exhibits an extremely high geographic concentration:
* **Bengaluru:** ₹253,840.80 Cr (**41.58%** share | 1,643 records)
* **Delhi NCR:** ₹145,067.78 Cr (**23.76%** share | 1,502 records)
* **Mumbai:** ₹122,315.60 Cr (**20.03%** share | 971 records)
* **Chennai:** ₹20,684.92 Cr (**3.39%** share)
* **Pune:** ₹13,240.93 Cr (**2.17%** share)

*Bengaluru, Delhi NCR, and Mumbai combined accounted for **85.37%** of total funds raised.*

### 4. 🏢 Company Concentration
* **Top Funded Company:** BYJU'S (~₹31,445.25 Cr cumulative).
* **Concentration Ratios:**
  * Top 5 Startups: **14.33%** of total capital
  * Top 10 Startups: **21.86%** of total capital
  * Top 20 Startups: **33.39%** of total capital

---

## 📈 Data Cleaning & Standardization Methodology

1. **Whitespace & Formatting:** Removed index columns, standardized text casing, and trimmed whitespace across all string fields.
2. **Handling Undisclosed Amounts:** Encoded `amount = 0` as undisclosed values. Engineered a dedicated `disclosed_amount` column so that averages and medians reflect true disclosed rounds without zero-value skew.
3. **Entity Normalization:**
   * **Sectors:** Standardized 71 raw sector/vertical labels into core business buckets (FinTech, EdTech, HealthTech, Enterprise Tech, etc.).
   * **Cities:** Consolidated 72 raw location strings into regional startup hubs (e.g., standardizing New Delhi, Gurugram, Noida, Ghaziabad, Faridabad, and Azadpur under `Delhi NCR`).
   * **Companies:** Grouped company variations using case-insensitive canonical matching.
4. **Feature Engineering:** Added indicators for disclosure flags, funding-size buckets, mega-deal flags (`≥ ₹500 Cr`), and repeat fundraising indicators.

---

## 🖥 Power BI Dashboard Architecture

The interactive dashboard is structured across 4 specialized report pages:

1. **Executive Overview:** High-level KPIs, yearly trends, macro sector distribution, geographic split, and funding stages.
2. **Sector Intelligence:** Deep dive into sector rankings by funding vs. deal count, ticket size distributions, and growth trajectories.
3. **Startup & Funding Analysis:** Top funded companies, deal frequency, funding stage counts, and deal-size bucket distributions.
4. **Geographic Ecosystem Analysis:** Map visuals, city/hub rankings, average ticket size by hub, and state-level breakdowns.

---

## 💡 Strategic Business Recommendations

1. **Track Capital Quality alongside Volume:** Always evaluate total funding in tandem with deal counts, median deal sizes, and unique startup numbers to distinguish broad ecosystem maturity from outlier mega-rounds.
2. **Isolate Mega Deals in Reporting:** Report executive figures both *including* and *excluding* deals ≥ ₹500 Cr to reveal underlying market dynamics.
3. **Monitor Pre-Capital Sector Momentum:** Keep track of sectors where deal activity accelerates *before* total funding surges to spot early-stage investment themes.
4. **Screen Beyond Tier-1 Hubs:** While Bengaluru, Delhi NCR, and Mumbai capture >85% of funding, secondary hubs like Chennai, Pune, and Hyderabad should be monitored for specialized emerging sectors.

---

## ⚠️ Data Limitations

- **Undisclosed Values:** 31.51% of records do not report deal size; aggregate financial figures represent reported deals only.
- **Co-investments:** Investor fields list multiple names per round without individual investment breakdowns.
- **Historical Scope:** Data spans 2015–2021 and should be evaluated as historical context rather than current market conditions.

---

## 📂 Project Deliverables

- 📄 **Executive Report:** Detailed analytical report (`Indian_Startup_Funding_Project_Report.pdf`)
- 📊 **Presentation Deck:** Executive presentation (`Indian_Startup_Funding_Analysis.pptx`)
- 🐍 **Python EDA Notebook:** Data cleaning, normalization, and exploratory script
- 📉 **Power BI Dashboard:** Interactive `Indian Startup Dashboard.pbix` report file