# SQL Data Analytics Project

Exploratory and advanced SQL analytics built on top of a Medallion-architecture data warehouse (Gold layer), covering everything from initial database exploration to full customer and product reporting views.

Repo: [github.com/farnooshoa/sql-data-analytics-project](https://github.com/farnooshoa/sql-data-analytics-project/tree/main)

---

## About This Project

This project demonstrates how to go from raw warehouse tables to business-ready insights using pure SQL — no external BI tool required. It's structured as a progression: start by understanding what data exists, then measure it, then analyze how it changes over time, and finally package the findings into reusable reporting views.

It's built on the Gold layer of a data warehouse (`gold.fact_sales`, `gold.dim_customers`, `gold.dim_products`), following a star-schema design.

---

## What's Covered

### 1. Exploratory Data Analysis (EDA)
- **Database Exploration** — using `INFORMATION_SCHEMA.TABLES` / `.COLUMNS` to understand what tables and fields exist before writing any analysis
- **Dimension Exploration** — surfacing distinct categories and subcategories
- **Date Exploration** — finding the time range the data actually covers
- **Measure Exploration** — headline business metrics (total sales, total orders, total customers) combined into a single summary report using `UNION ALL`
- **Magnitude Analysis** — breaking totals down by dimension (e.g., customers by country)
- **Ranking** — top-N analysis using both simple `TOP` queries and flexible window-function ranking (`RANK() OVER`)

### 2. Advanced Analytics
- **Change Over Time** — monthly/yearly trend analysis using `DATETRUNC`, `YEAR()`/`MONTH()`, and `FORMAT()`
- **Cumulative Analysis** — running totals and moving averages with `SUM() OVER()` / `AVG() OVER()`
- **Performance Analysis (YoY)** — comparing each product's sales to its own historical average and to the prior year, using `LAG()` and `CASE` to flag Above/Below Average and Increase/Decrease trends
- **Part-to-Whole Analysis** — category contribution to total sales as a percentage, using `SUM() OVER()` with no partition for the grand total
- **Customer Segmentation & Reporting** — a full `gold.report_customers` view that segments customers into VIP / Regular / New based on lifespan and spend, with KPIs like recency, average order value, and average monthly spend
- **Product Segmentation & Reporting** — a matching `gold.report_products` view segmenting products into High-Performer / Mid-Range / Low-Performer based on total sales, with recency, average order revenue, and average monthly revenue

---

## Key SQL Techniques Used

- Window functions: `SUM() OVER()`, `AVG() OVER()`, `RANK()`, `LAG()`
- CTEs for multi-step, readable transformations
- `CASE WHEN` for business-rule segmentation (age groups, customer tiers, product tiers, trend direction)
- Views for packaging reusable, production-ready reports
- Defensive patterns: `NULLIF()` to guard against divide-by-zero in average calculations

---

## Why This Project

Built as a portfolio piece to demonstrate practical, production-style SQL — the kind of analysis a Data Analyst is actually asked to produce: not just isolated queries, but a coherent path from "what does this data even look like" to "here's a report a stakeholder can act on."
