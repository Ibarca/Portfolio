# ABC Report for Category Management (SQL + BigQuery + Google Sheets) with syntetic data

## Overview 
This project showcases a production-ready analytical dataset built entirely with BigQuery SQL and integrated with Google Sheets to enable automated, scalable reporting for Category Management teams, using synthetic data.

The dataset consolidates multiple operational sources into a single source of truth at SKU level, designed to support prioritization, performance monitoring, and optimization decisions in e-commerce environments. SKU prioritization follows the Pareto (ABC) principle, allowing Category Managers to focus their efforts on the products that drive the majority of revenue impact.

The underlying SQL query aggregates and enriches data from multiple operational domains : products, suppliers, margins, sales history, and inventory, and is directly connected to Google Sheets to generate an always-up-to-date report. All calculations are executed in SQL, ensuring that the Google Sheets layer remains fast, lightweight, and responsive, even with large assortments. In order to achieve this, CTEs and window functions are used.

This reporting framework has been implemented in two different companies, where it became the cornerstone for daily performance measurement within Category Management teams. The logic has been tested, refined, and validated in real business environments, supporting thousands of SKUs and evolving alongside operational needs.

Thanks to its SQL-first design, the report:
- Handles thousands of SKUs efficiently
- Supports live data refreshes configurable directly in Google Sheets (frequency and timing)
- Allows for easy extension with additional KPIs (e.g. returns, funnel metrics, delivery performance, forecasting inputs) without changing the reporting layer

The goal of this project is to give Category Managers one central place to:
- Set priorities based on data-driven impact
- Identify optimization opportunities across assortment, pricing, and stock
- Monitor performance consistently across the full catalog

<img width="1357" height="770" alt="Screenshot 2026-01-05 at 13 53 02" src="https://github.com/user-attachments/assets/7428057c-f74b-4ded-a1f7-951f7ef252d9" />

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

---

## Data Flow Diagram

<img width="1106" height="257" alt="Screenshot 2025-12-31 at 10 50 59" src="https://github.com/user-attachments/assets/0227ad89-e48b-4f52-a70b-8d953e52ab64" />

---

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

## Challenges

One of the main challenges of this project was handling complex aggregations and business logic directly in SQL.
Building SKU-level KPIs such as rolling 365-day sales, cumulative revenue contribution, and ABC classification required extensive use of Common Table Expressions (CTEs) and window functions to ensure correctness, readability, and maintainability.

Running these calculations entirely in BigQuery SQL ensures that heavy data processing happens at the database level, which guarantees high scalability and performance.
As a result, the connected Google Sheets report remains fast and responsive, even when working with thousands of SKUs and live data refreshes, making it suitable for daily operational use.

<img width="502" height="400" alt="Screenshot 2026-01-05 at 14 19 35" src="https://github.com/user-attachments/assets/007fccfc-3322-47de-9ab5-a8113a9a0a99" />
<img width="450" height="94" alt="Screenshot 2026-01-05 at 14 28 30" src="https://github.com/user-attachments/assets/a3005060-33fd-4708-b8a7-0f14f735d91b" />

---

## 📬 Contact

If you want to discuss my work, analytics methods, or e-commerce projects:

- **LinkedIn:** [https://www.linkedin.com/in/yago-b-35582644/]
- **Email:** ibarreirocanda@gmail.com 
