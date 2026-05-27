# 🛵 Swiggy End-to-End Data Analytics Project

This repository hosts an end-to-end data analytics pipeline designed to ingest, clean, model, and visualize Swiggy's operational food delivery data. Built entirely within the **Microsoft Fabric** ecosystem, this solution transforms raw, disconnected datasets into a unified star-schema data warehouse and an interactive executive dashboard for business stakeholders.

---

## 🛠️ Technology Stack & Architecture

The project leverages Microsoft's unified data platform alongside industry-standard SQL and BI modeling techniques to construct a robust modern data stack:

| Layer | Component / Technology | Purpose |
| :--- | :--- | :--- |
| **Data Storage** | Microsoft Fabric Lakehouse | Serves as the landing and storage zone for raw operational CSV files. |
| **Data Orchestration** | Fabric Data Pipelines | Automates data movement and ingestion processes. |
| **Data Cleaning** | SQL (Lakehouse / Warehouse Engine) | Cleans data, handles missing values, and enforces relational validation. |
| **Data Modeling** | Fabric Data Warehouse | Hosts the multi-dimensional Star Schema (`fact` and `dim` tables). |
| **Semantic Layer** | Power BI Semantic Model | Manages data relationships, dimensions, and core business DAX measures. |
| **Visualization** | Power BI Service Workspace | Delivers an interactive, production-ready dashboard for business stakeholders. |

### 📐 Data Modeling (Star Schema)
The data warehouse splits operational data into distinct tables to optimize query performance and reporting efficiency:
* **Fact Table:** `fact_orders` (captures order transactions and core metrics).
* **Dimension Tables:** `dim_date`, `dim_restaurants`, `dim_dish`, and `dim_location`.

---

## 📊 Core Business Insights

Based on the initial run of the Power BI dashboard, the following high-level operational and financial insights were uncovered:

### 💰 High-Level Performance Metrics
* **Total Sales:** ₹53.01M
* **Total Orders:** 197K
* **Average Order Value (AOV):** ₹268.51
* **Total Ratings Received:** 5.59M *(sum of individual rating counts per order)*
* **Average Customer Rating:** 4.34 / 5.0

### 🍔 Menu & Preference Trends
* **Food Category Performance:** Non-Vegetarian food heavily dominates customer preferences, accounting for **63.7% (₹33.77M)** of total sales, whereas Vegetarian options generate **36.3% (₹19.24M)**.

  > **Note:** The Veg / Non-Veg classification is not a raw column in `dim_dish`. It is derived as a **calculated column in the Power BI semantic model**, which maps each dish category (e.g., *North Indian Gravy*, *South Indian Dishes*, *Snack*) to a dietary tag using a DAX `SWITCH` expression. The mapping logic is documented in the semantic model inside `Dashboard.pbix`.

### 🏆 Top Market Drivers
* **Top 5 Cities (by Sales):** Bengaluru leads the market by a wide margin (**₹5.5M**), followed closely by Lucknow (**₹3.1M**), Hyderabad (**₹3.0M**), Mumbai (**₹3.0M**), and New Delhi (**₹2.8M**).
* **Top 5 Restaurant Partners:** KFC is the highest-grossing partner (**₹4.2M**), followed by McDonald's (**₹3.3M**), Pizza Hut (**₹2.1M**), Burger King (**₹1.9M**), and Domino's Pizza (**₹1.8M**).

### 📅 Time-Series Trends
* **Monthly Flux:** Sales peak in **January** at **₹6.83M**, with secondary peaks in **May** and **August** at **₹6.79M** each, rebounding from the yearly low in **February** of **₹6.27M**.
* **Weekly Consistency:** Weekly revenue remains highly steady and uniform, consistently tracking between **₹7.4M and ₹7.8M**.

---

## 🎛️ Interactive Reporting: Power BI Slicers

To move beyond static reporting, the dashboard incorporates dynamic slicers that allow business managers to filter, slice, and cross-examine metrics on the fly:

* **City Slicer:** Cleansed and standardized using SQL, this slicer lets regional heads drill down into localized performances (e.g., assessing Bengaluru vs. New Delhi).
* **Restaurant Slicer:** Empowers account managers to track specific franchise contracts, isolated volumes, and target sales contributions for individual restaurant chains.
* **Food Type Slicer:** Breaks down sales metrics further, allowing teams to filter historical trends to specific dietary tags and item categories.
* **Quarter Slicer:** Provides a high-level macro timeline filter to check seasonal growth patterns across Q1, Q2, Q3, and Q4.

---

## 🚀 Data Quality & Validation Rules Implemented
Before hitting the dashboard, the raw data underwent strict QA rules via SQL to guarantee report reliability:
* **Referential Integrity Checks:** Eliminated orphan orders that lacked corresponding customer or restaurant records.
* **Business Logic Constraints:** Flagged and handled anomalies such as negative order amounts or delivery timestamps recorded prior to order pickup timestamps.
* **Data Cleansing:** Standardized mismatched city strings and unified date string formats into indexable datatypes.

---

## 💡 Business Recommendations

### 1. 🗓️ Defend the February Dip
February is the yearly low at ₹6.27M — an **8% drop** from January. Pre-schedule cashback offers and combo deals (e.g., Valentine's specials) to prop up demand during this predictable slump.

### 2. 🌆 Replicate Bengaluru's Success in Tier-2 Cities
Bengaluru (₹5.5M) nearly doubles Lucknow and Hyderabad (₹3.0–3.1M each). Audit what drives Bengaluru's performance — restaurant density, SLAs, promos — and apply that playbook to the next-tier cities.

### 3. 🥗 Grow the Veg Segment
Veg accounts for only **36.3% of sales** despite India's large vegetarian population. Better homepage placement and onboarding more veg-specialist restaurants could meaningfully shift this split.

### 4. 📦 Reduce Dependency on Top 2 Restaurants
KFC and McDonald's alone drive **14.2% of total revenue**. Negotiate deeper co-marketing deals with them while actively developing Pizza Hut and Burger King to build a more resilient revenue mix.

---

## 📊 Dashboard Preview

<img width="1222" height="728" alt="dashboard_preview" src="https://github.com/user-attachments/assets/f0d1e8d5-a8cc-4e53-847b-31ca8120e8b3" />
