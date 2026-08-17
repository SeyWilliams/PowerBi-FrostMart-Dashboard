# PowerBi-FrostMart-Dashboard
Inventory Optimization: From Gut-Feel to Data-Driven
# ❄️ FrostMart UK — Inventory Optimization Analytics

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat&logo=microsoftexcel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-2EC4B6?style=flat)
![Type](https://img.shields.io/badge/Type-Capstone%20Project-0B2A4A?style=flat)

An inventory and supply chain intelligence project built for **FrostMart UK**, a national perishables retailer — turning five linked datasets (sales, products, stores, weather, and suppliers) into a three-page interactive Power BI dashboard that helps Store Managers and Procurement move from gut-feeling inventory planning to evidence-based decisions.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Objectives](#-objectives)
- [Data Dictionary](#-data-dictionary)
- [Dashboards](#-dashboards)
- [Key Insights](#-key-insights)
- [Business Questions Answered](#-business-questions-answered)
- [Core KPIs & Formulas](#-core-kpis--formulas)
- [Recommendations](#-recommendations)
- [Tech Stack](#️-tech-stack)
- [Author](#-author)

---

## 💡 Overview

FrostMart leadership is moving away from gut-feeling inventory planning. This analysis brings historical sales, weather, and supply chain data together into a single interactive Power BI dashboard — giving Store Managers and the Procurement Team a shared, evidence-based view of exactly what's driving product waste and missed sales.

The goal isn't just a report — it's a decision-making tool that turns "we think it's the bakery" into "here are the 7 products, 1 region, and 3 suppliers actually responsible for it."

---

## 🎯 Objectives

- Import and model all five source datasets into a single Power BI **Star Schema**, connecting a central Fact table to Dimension tables via primary/foreign keys
- Build core DAX metrics: Total Revenue, Total Wastage Cost, Total Units Sold
- Reveal overall financial health, and which product categories drive the most revenue versus the most waste
- Understand how external factors — temperature, rainfall, and holidays — impact sales volume by category, and which regions struggle most with waste
- Determine whether cold storage capacity affects waste, and which suppliers are tied to the highest-spoilage products
- Deliver a prioritized set of actionable recommendations to reduce the reported **£12.2M** annual loss

---

## 🧩 Data Dictionary

**`weekly_sales.csv`** (Fact Table) — historical weekly transaction records across all stores

| Field | Description |
|---|---|
| `Week_Number` | The specific week of the year (e.g., 2024-W01) |
| `Product_ID` | Unique identifier for the product sold |
| `Store_ID` | Unique identifier for the store location |
| `Units_Sold` | Total quantity of the product sold that week |
| `Marketing_Spend` | Amount (£) spent advertising the product |
| `Discount_Percent` | Percentage discount applied |
| `Wastage_Units` | Units that expired or spoiled and were discarded |
| `Price` | Retail price per unit (£) |

**`product_details.csv`** — `Product_ID` (PK), `Product_Name`, `Product_Category`, `Shelf_Life_Days`, `Supplier_ID` (FK)
**`store_info.csv`** — `Store_ID` (PK), `Region`, `Store_Size`, `Cold_Storage_Capacity`
**`weather_data.csv`** — `Week_Number`, `Region`, `Avg_Temperature`, `Rainfall`, `Holiday_Flag`
**`supplier_info.csv`** — `Supplier_ID` (PK), `Supplier_Name`, `Lead_Time_Days`, `Supply_Capacity`

---

## 📊 Dashboards

### 💰 Dashboard 1 — Executive View
- **KPI strip:** Expected Income, Total Revenue, Total Wastage, Units Sold
- **Revenue by Month:** monthly revenue trend across the full year
- **Waste Cost by Product Category:** wastage broken down by Bakery, Meat, Dairy, Beverages
- **Top Product by Wastage Cost:** the individual worst-performing SKUs
- **Revenue and Wastage Cost by Holidays:** performance split between holiday and non-holiday weeks
- **Revenue by Product:** revenue broken down by category

<img width="1000" height="752" alt="image" src="https://github.com/user-attachments/assets/16e374c8-e705-457c-9c43-1cd96355218b" />

*Dashboard 1, built in Power BI — overall financial health, and which categories drive revenue vs. waste.*

### 🌦️ Dashboard 2 — Environmental Impact
- **KPI strip:** Average Rainfall, Average Temperature
- **Sales and Total Wastage Cost by Season:** seasonal pattern across Winter, Spring, Summer, Autumn
- **Total Wastage by Region:** waste broken down across all six UK regions
- **Waste by Rainfall:** wastage cost bucketed by weekly rainfall level

<img width="1000" height="752" alt="image" src="https://github.com/user-attachments/assets/09c3d43c-8fa0-4d8e-a9b9-1a3cd832f303" />

*How season, region, and weather relate to sales and waste.*

### 🚚 Dashboard 3 — Supply Chain Operations
- **KPI strip:** Total Supply Capacity, Average Storage Capacity, Average Lead Time (Days)
- **Top Wastage Products table:** supplier, product, and wastage units for the 10 worst-performing SKUs
- **Total Wastage Cost & Avg. Cold Storage Capacity by Region:** repeated regional view for the supply chain lens
- **Supply Capacity by Supplier Name:** weekly capacity for every one of the 10 suppliers

<img width="1000" height="752" alt="image" src="https://github.com/user-attachments/assets/34ee8eb8-30d9-4ef5-9089-6095187763f3" />

*Which suppliers are tied to the highest-spoilage products, and where supply capacity is thinnest.*

---

## 📈 Key Insights

- **Bakery is a paradox category.** It has the lowest revenue of any category (£41M) and the highest waste (£6.3M) — a 15.4% waste rate, more than 6× Beverages (2.4%).
- **Just 7 products drive a quarter of all waste.** The worst 7 individual products — all Bakery — total ≈£3.76M in wastage, roughly 24% of FrostMart's entire £15.66M wastage bill, from a tiny slice of the catalogue.
- **Dairy is the profit engine to protect.** It has the highest revenue of any category (£67M) with a comparatively low ≈5.1% waste rate — the category the rest should learn from.
- **December alone reshapes the year.** Revenue jumps to £34.0M — about 2.2× a typical month (≈£15.6M) — a holiday surge current ordering may not be fully built around.
- **Waste is concentrated, not spread out.** London wastes 4.4× the lowest region (South East), and just 3 suppliers — LocalHarvest Distributors, TrustedSource Provisions, and PremiumGoods Wholesale — account for 61% of the worst-spoilage products.
- **The smallest supplier is tied to the biggest spoilage.** LocalHarvest Distributors has the smallest weekly capacity of any of the 10 suppliers (11K, under a third of the next-smallest) — yet its products are among the highest-spoilage in the entire catalogue.

---

## ❓ Business Questions Answered

| Question (from project brief) | Answer |
|---|---|
| What is the overall financial health? | £205.68M revenue against £15.66M wastage — a healthy top line with a concentrated, fixable waste problem |
| Which categories drive the most revenue vs. the most waste? | Dairy leads revenue (£67M); Bakery leads waste (£6.3M) — the same category is both the lowest earner and highest waster |
| How do temperature, rainfall & holidays impact category sales? | Waste appears higher in lower-rainfall weeks in the sample shown; holiday-week waste rate stays roughly flat vs. non-holiday weeks (~7–8%) |
| Which regions struggle most with waste? | London, by a wide margin — 70% higher than the next region and 4.4× the lowest |
| Do stores with lower cold storage capacity see more waste? | Not yet directly visualized — flagged as a recommended next step (a store-level capacity-vs-waste view) |
| Which suppliers are tied to the highest-spoilage products? | LocalHarvest Distributors, TrustedSource Provisions & PremiumGoods Wholesale — together 61% of the worst 10 products' wastage |

---

## 🧮 Core KPIs & Formulas

- **Total Revenue** = `Units_Sold × Price`
- **Total Wastage Cost** = `Wastage_Units × Price`
- **Total Units Sold** = `SUM(Units_Sold)`
- **Category Waste Rate (%)** = `Waste Cost (category) ÷ Revenue (category) × 100`
- **Supplier Spoilage Share (%)** = `Supplier's wasted units (top-10 list) ÷ Total wasted units (top-10 list) × 100`

---

## 💡 Recommendations

**Priority**

1. **Automate markdown-to-clear for near-expiry Bakery lines.** Flag SKUs approaching their `Shelf_Life_Days` limit and trigger tiered discounts (e.g. 25% off at 2 days left, 50% at 1 day) automatically at the till — piloting on just the 7 worst products targets the £3.76M (24% of total waste) they currently generate.
2. **Rebalance orders with the 3 concentrated-spoilage suppliers.** Review order size and frequency with LocalHarvest Distributors, TrustedSource Provisions & PremiumGoods Wholesale specifically; cap LocalHarvest's orders at its real 11K/week capacity instead of over-ordering against a supplier that structurally can't flex.
3. **Stand up a London waste taskforce.** With waste 4.4× the lowest region, a store-by-store review of cold storage, delivery timing, and local forecasting in London targets the single most concentrated regional problem in the data.

**Supporting**

4. **Build a December ordering playbook.** Pre-set higher safety stock for longer-shelf-life categories (Dairy, Beverages) ahead of the ≈2.2× holiday surge, while keeping Bakery orders staged closer to the date.
5. **Add a store-level Cold Storage vs. Waste view.** Closes one of the brief's open questions directly — whether under-equipped stores drive more waste — with evidence instead of assumption.

---

## ⚙️ Tech Stack

- **Data Source:** 5 linked CSV datasets (weekly sales, products, stores, weather, suppliers)
- **Transformation:** Power Query (data cleaning, type correction, Star Schema modeling)
- **Modeling & Metrics:** DAX (revenue, wastage cost, category/regional/supplier aggregations)
- **Visualization:** Microsoft Power BI (interactive 3-page report — Executive, Environmental Impact, Supply Chain Operations)

---

## 👨‍💻 Author

**Emmanuel Sey Williams**
📧 williamsemmanuel7382@gmail.com

📊 **Project Status:** Complete
