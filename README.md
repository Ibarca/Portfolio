# ABC Report for Category Management (SQL + BigQuery + Google Sheets)

## Overview
This project showcases a **production-ready analytical dataset** built with **BigQuery SQL** and **integrated with Google Sheets** to enable automated, scalable reporting for Category Management teams.

The dataset consolidates multiple operational sources into a **single source of truth at SKU level**, designed to support prioritization, performance monitoring, and optimization decisions.
This project provides a **single, consolidated dataset** designed to support **Category Management decision-making** in e-commerce environments.

The SQL query aggregates and enriches data from multiple operational sources (products, margins, sales, inventory, suppliers) and is **directly integrated with Google Sheets** to generate an **automated, always-up-to-date report**.

The goal is to give Category Managers **one central place** to:
- Set priorities
- Identify optimization opportunities
- Monitor performance across the full assortment

---

## Business Purpose
This report acts as the **first level of data access** for Category Management teams.

It answers core questions such as:
- Which SKUs generate most of the revenue?
- Which products belong to A / B / C classes?
- Where do stock-outs hurt performance?
- Which suppliers and lead times create operational risk?
- How do margins and pricing affect category contribution?

For **deeper analysis**, more specialized dashboards (e.g. forecasting, funnel analysis, profitability deep-dives) are recommended on top of this dataset.

---

## Data Sources
The query combines data from:
- Product master data
- Supplier information (lead times, countries)
- Historical sales (last 365 days)
- Inventory history (stock availability & service level)
- Margin structure (CM1 / CM2 / CM3)

All data is unified at **SKU level**.

## Key Metrics
- Revenue & units sold (last 365 days)
- ABC classification (cumulative revenue logic)
- Revenue contribution per SKU
- Average selling price
- CM1 / CM2 / CM3 margins
- Service level (stock availability over time)
- Current stock on hand
- Supplier, country & lead time

---

## Automation & Delivery
- Query runs in **BigQuery**
- Connected directly to **Google Sheets**
- Automatic refresh
- End users work with filters, pivots, and conditional logic
- No manual data extraction required

---

## Real-World Usage
I implemented this structure (adapted to each data model) in **two different e-commerce companies**, where it became:

- The **core dataset** for Category Management
- The entry point for weekly business reviews
- A foundation that **significantly improved data accessibility and transparency**
- A bridge between analytics and business users

---

## Scalability
The model is intentionally flexible and can be extended with additional KPIs such as:
- Funnel metrics (views, add-to-cart, conversion)
- Return rates
- Delivery performance
- Forecast accuracy
- Supplier reliability

---

## Data Flow Diagram

<img width="1106" height="257" alt="Screenshot 2025-12-31 at 10 50 59" src="https://github.com/user-attachments/assets/0227ad89-e48b-4f52-a70b-8d953e52ab64" />


## 📬 Contact

If you want to discuss my work, analytics methods, or e-commerce projects:

- **LinkedIn:** [https://www.linkedin.com/in/yago-b-35582644/]
- **Email:** ibarreirocanda@gmail.com 
