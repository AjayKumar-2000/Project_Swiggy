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
* **Average Customer Rating:** 4.34 / 5.0

### 🍔 Menu & Preference Trends
* **Food Category Performance:** Non-Vegetarian food heavily dominates customer preferences, accounting for **63.7% (₹33.77M)** of total sales, whereas Vegetarian options generate **36.3% (₹19.24M)**.

### 🏆 Top Market Drivers
* **Top 5 Cities (by Sales):** Bengaluru leads the market by a wide margin (**₹5.5M**), followed closely by Lucknow (**₹3.1M**), Hyderabad (**₹3.0M**), Mumbai (**₹3.0M**), and New Delhi (**₹2.8M**).
* **Top 5 Restaurant Partners:** KFC is the highest-grossing partner (**₹4.2M**), followed by McDonald's (**₹3.3M**), Pizza Hut (**₹2.1M**), Burger King (**₹1.9M**), and Domino's Pizza (**₹1.8M**).

### 📅 Time-Series Trends
* **Monthly Flux:** Sales peak dramatically in **May** and **August** at **₹6.79M** each, rebounding from a yearly low in February of **₹6.27M**.
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
