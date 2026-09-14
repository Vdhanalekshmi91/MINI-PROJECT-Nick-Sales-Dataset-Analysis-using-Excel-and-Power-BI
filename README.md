# 👟 Nike Sales Performance: Excel Cleaning & Power BI Dashboard

This project builds a complete business intelligence pipeline using a **Nike Sales Dataset** from Kaggle. The goal is to clean a corrupted dataset in **Excel**, build a relational data model in **Power BI**, and create an interactive dashboard to uncover growth insights.

---

## 🛠️ Project Structure
1. **Phase 1: Data Engineering (Excel)** – Handled 5,283 missing cells, fixed corrupted data types, and engineered new tracking features.
2. **Phase 2: Business Intelligence (Power BI)** – Normalized data tables, built a star-schema model, wrote custom DAX formulas, and designed a 4-page interactive dashboard.

---

## 📊 Phase 1: Data Pre-Processing (Excel)

The raw CSV file contained **13 columns** with thousands of blank or broken entries. The following steps were taken to fix the data:

* **Size Imputation:** Standardized mixed numerical sizes (7–12) and categories (M, L, XL) using an `IFS` function. Remaining blanks were filled with the column's most common value (**M**) using `COUNTIF`.
* **MRP Imputation:** Created an `MRP Final` column and filled blanks with the median value to ignore extreme numbers.
* **Discount Imputation:** Assumed blank spaces meant the item was sold at full price. Filled blanks with `0` using `IF(ISBLANK())`.
* **Units Sold Imputation:** Checked the `Profit` column for blanks. If profit was positive, units sold was set to `1`. If profit was negative (returns/damages), it was set to `0`.
* **Order Date Imputation:** Filled empty date cells with `"Unknown Date"`.
* **Text & Format Cleanup:** Fixed typos, casing issues, and short-form names in the `Region` column. Enforced strict data formats (Text, Numbers, Currency, and Dates).
* **Feature Engineering:** 
  * Created a **Unique Order ID** by combining `[Order ID] & [Cleaned Order Date]` because system IDs were repeating.
  * Calculated **Sales Price** using: `[MRP Final] * (1 - [Cleaned Discount])`.
  * Rebuilt **Calculated Revenue** using: `[Units Sold Filled] * [Sales Price]` since the original revenue column was corrupted.
* **Master Table Consolidation:** Moved all clean data into a new sheet named `cleaned and transformed dataset` using `VLOOKUP` and `XLOOKUP`.

---

## 📈 Phase 2: Analytics & Dashboarding (Power BI)

The clean Excel data was imported into Power BI to build a normalized data model and design a **4-page interactive dashboard** with advanced UI navigation.

### 1. Model & DAX Setup
* Enforced strict formatting in Power Query and normalized the flat file into separate dimension tables.
* Engineered **2 Calculated Columns** and **1 Core Measure** using DAX for real-time aggregation.

### 2. Dashboard Pages & UX Features
* **Executive Dashboard:** High-level metrics for leadership.
* **Customer Analysis (Category-Wise):** Buyer behaviors and gender habits.
* **Products Analysis:** Top-sellers, weak items, and popular shoe sizes.
* **Sales Channel Analysis:** Performance comparison of Online vs. Retail.
* **UX Upgrades:** Used **Drill-Through** functions to dive deep into details, a **Page Navigator** header for easy clicking, and **Bookmarks** to clean up the screen.

---

## 📊 Executive Summary: Sales & Revenue Analysis

### 📈 The Big Numbers
* **Total Sales Volume:** 2,500 total orders processed.
* **Top-Line Revenue:** ₹3.52 Million.
* **Take-Home Profit:** ₹879.92 Thousand.

### 🔍 Key Insights
* **Omnichannel Split:** Orders are split 50/50 between channels, but online shopping is slightly more efficient:
  * *Retail:* 1,252 orders $\rightarrow$ ₹17.16M in profit.
  * *Online:* 1,248 orders $\rightarrow$ ₹17.31M in profit.
* **Geography:** Sales are heavily concentrated in 6 cities: **Delhi, Mumbai, Pune, Hyderabad, Bangalore, and Kolkata**.
* **Timeline:** Business performance peaked massively in **2024**, far outperforming 2023 and 2025.
* **Demographics:** Spending is evenly balanced between **Women (₹4.53M)**, **Men (₹4.47M)**, and **Kids (₹4.35M)**.
* **SKU Winners & Losers:** The crowd favorites are **SuperRep Go, Waffle One, and Premier III**. The slowest moving items are **Pegasus Turbo and Tiempo Legend**.
* **Price Elasticity:** Customers buy heavily at low price points. As prices go up, order volumes drop instantly.

---

## 🎯 Actionable Growth Recommendations

* **Optimize E-Commerce:** Online sales bring in higher profits despite having fewer orders. Direct more digital marketing spend to this channel.
* **Target Regional Hubs:** Focus logistics and fast-shipping centers around the high-density **Mumbai-Pune-Hyderabad corridor**.
* **Clear Slow Stock:** Run promotional discounts or bundles on the **Pegasus Turbo** to free up warehouse space.
* **Double Down on Winners:** Increase inventory and marketing budgets for the popular **SuperRep Go**.
* **Balance Marketing Budgets:** Keep advertisement spending perfectly equal between Men's, Women's, and Kids' lines since they generate the exact same revenue.

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for details.# MINI-PROJECT-Nick-Sales-Dataset-Analysis-using-Excel-and-Power-BI
