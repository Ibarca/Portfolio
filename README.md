# ABC Revenue Analysis & SKU Prioritization for Category Management (SQL + BigQuery + Google Sheets) with synthetic data

## Overview 
This project showcases a production-ready analytical dataset built entirely with BigQuery SQL and integrated with Google Sheets to enable automated, scalable reporting for Category Management teams, using synthetic data. The report can be found [here](https://docs.google.com/spreadsheets/d/1dP4wzOw9nYpfIo4zUBvQJmEtER1iKRP6GJyMMoqcCr0/edit?gid=1324343453#gid=1324343453)

The dataset consolidates multiple operational sources into a single source of truth at SKU level, designed to support prioritization, performance monitoring, and optimization decisions in e-commerce environments. SKU prioritization follows the Pareto (ABC) principle, allowing Category Managers to focus their efforts on the products that drive the majority of revenue impact.

The underlying SQL query aggregates and enriches data from multiple operational domains : products, suppliers, margins, sales history, and inventory, and is directly connected to Google Sheets to generate an always-up-to-date report. All calculations are executed in SQL, ensuring that the Google Sheets layer remains fast, lightweight, and responsive, even with large assortments. In order to achieve this, CTEs and window functions are used.

This reporting framework has been implemented in two different companies, where it became the cornerstone for daily performance measurement within Category Management teams. The logic has been tested, refined, and validated in real business environments, supporting thousands of SKUs and evolving alongside operational needs.

Thanks to its SQL-first design, the report:
- Is able to handle thousands of SKUs efficiently
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
- Historical sales
- Inventory history (stock availability & service level)
- Margin structure (CM1 / CM2 / CM3)

All data is unified at **SKU level**.

---

## Data Flow Diagram

This pipeline transforms raw operational data into a single, analytics-ready dataset for SKU-level performance analysis.

Data flows through four logical layers:

- Raw Layer: Read-only source data stored in BigQuery with no business logic applied.
- Semantic Layer: Enriched and aggregated datasets that add business meaning and create reusable foundations.
- Analytical Layer: Centralized KPI calculations and prioritization logic to ensure consistency across reporting.
- Final Output: A consolidated dataset optimized for BI tools, serving as a single source of truth for decision-making.

The layered design ensures scalability, clarity, and maintainability of the analytical logic.


<img width="998" height="614" alt="image" src="https://github.com/user-attachments/assets/e599e77f-0036-4eac-b651-90ae83945c77" />



---

## Key Metrics
- Revenue & units sold (last 365 days)
- ABC classification (cumulative revenue logic)
- Revenue contribution per SKU
- Average selling price
- CM1 / CM2 / CM3 margins for the last 365 days
- Service level (stock availability over time)
- Current stock on hand
- Supplier, country & lead time

---

## Automation & Delivery
The query is executed directly in BigQuery and connected to Google Sheets as a live data source. Data is refreshed automatically, ensuring that users always work with up-to-date information. End users can interact with the data using filters, pivot tables, and conditional logic, without the need for any manual data extraction or file handling.



---

## Real-World Usage
I implemented this structure (adapted to each data model) in **two different e-commerce companies**, where it became:

- The **core dataset** for Category Management
- The entry point for weekly business reviews when KPIs adjusted to quicker time horizons
- A foundation that **significantly improved data accessibility and transparency**
- A bridge between analytics and business users
- A guidance to project priorization following revenue concentration
<img width="583" height="145" alt="Screenshot 2026-01-05 at 18 51 14" src="https://github.com/user-attachments/assets/2b55d18d-a0e2-4317-ae31-8e29458b2977" />

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

Running these calculations entirely in SQL ensures that heavy data processing happens at the database level, which guarantees high scalability and performance, avoiding resource-consuming lookup formulas in the spreadsheet.
As a result, the connected Google Sheets report remains fast and responsive, even when working with thousands of SKUs and live data refreshes, making it suitable for daily operational use.

<img width="502" height="400" alt="Screenshot 2026-01-05 at 14 19 35" src="https://github.com/user-attachments/assets/007fccfc-3322-47de-9ab5-a8113a9a0a99" />
<img width="450" height="94" alt="Screenshot 2026-01-05 at 14 28 30" src="https://github.com/user-attachments/assets/a3005060-33fd-4708-b8a7-0f14f735d91b" />

---

## Results & Key Findings

The ABC analysis highlights a strong revenue concentration across a limited number of SKUs, confirming the relevance of prioritization in inventory planning and projection.

Key findings

The portfolio generates a total revenue of approximately 29.2M € over the analyzed period.

- Class A SKUs make up just 17.5% of the assortment (7 SKUs) while generating 40% of total revenue (~€11.7M). These high-impact items are critical for service-level protection and inventory availability. As a top priority, product listing quality should be reviewed and, where needed, enhanced through improved visuals and content optimization.
- Class B SKUs represent 27.5% of the assortment (11 SKUs) and contribute a further 40% of revenue (~€11.7M). These products require balanced replenishment strategies and close performance monitoring. In addition, reviewing and improving listing quality may help unlock further sales potential, as B-class SKUs often represent future top sellers.
- Class C SKUs make up the majority of the assortment (55% or 22 SKUs) while contributing only 20% of revenue (~5.9M €), indicating long-tail behavior and higher overstock risk.
- The analysis shows that all top-selling items—particularly the top five SKUs—are mature products, from 2020 or older. This indicates a need to expand the assortment with new product introductions. It is essential to engage with suppliers to review their latest catalogs, discuss current market trends and best sellers, and identify potential gaps in the existing assortment. This initiative should be treated as a high-priority project, as continued reliance on mature A-class products carries the risk of market saturation over time.
- There are no major profitability issues across the assortment overall. However, the top-selling SKU (SKU 3) shows a below-average CM3 of 12%, driven by a relatively low CM1 of 31%. Given its high sales volume, this SKU represents a strong opportunity for supplier price renegotiation to improve overall margin performance.
- The top-selling SKUs (1 and 13) are currently out of stock, resulting in significant lost revenue given their high sales importance. A root cause analysis is required to understand how this situation occurred. In parallel, upcoming inbound orders should be reviewed and, where possible, expedited to minimize further revenue impact. The same happens with the mid seller sku 6. No correlation between suppliers or categories has been found.
- The top-selling SKU 33 shows a strong CM3 margin of 42%, indicating that purchasing prices were effectively negotiated in the past. This healthy margin provides sufficient budget flexibility to increase marketing investment and further scale sales.
- The low-selling SKUs 11, 35, and 30 exhibit CM3 margins above 40%. However, increasing marketing spend may be ineffective if these products serve niche demand. A competitive benchmarking analysis should be conducted to assess potential overpricing. If confirmed, selectively reducing prices toward market levels could help stimulate demand while preserving healthy margins.
  



---

## Suggestions


- AI-assisted report integration with Google Gemini.
  
Corporate Google Workspace accounts allow the integration of Google Gemini directly into Google Sheets. This enables automated prompting and natural-language queries on top of the report, allowing users to quickly generate tracking summaries, ad-hoc insights, and management-ready reports without additional manual analysis.

- Complement ABC analysis with trend-focused dashboards.

ABC analysis provides a strong snapshot of current performance and prioritization, but it does not capture trends, seasonality, or momentum over time. For decision-making that requires forward-looking insights, this report should be supplemented with in-depth dashboards (e.g. time-series analysis, demand evolution, stock risk trends, or forecast accuracy monitoring

- Adjust ABC thresholds in cases of high revenue concentration.
  
When revenue is highly concentrated in a small number of SKUs, standard ABC thresholds may not accurately reflect true business priorities. In such cases, testing alternative ABC ratios can provide a more balanced prioritization. High concentration also represents a structural risk: if one of these key SKUs is disrupted (supply, quality, pricing, or demand), overall revenue is disproportionately impacted. A more evenly distributed revenue mix is generally more resilient and reduces dependency risk.

- Note on Time Frames & Synthetic Data

This project uses synthetic data, therefore fixed reference dates (e.g. stock snapshot on 2024-12-31) and static time windows (e.g. last 365 days) are intentionally applied to ensure reproducibility and deterministic results.
In a production environment with live data, all time-based filters (sales period, inventory history, stock snapshots) would be implemented using dynamic, rolling windows relative to the current date (e.g. CURRENT_DATE()), allowing the report to update automatically without manual adjustments.

---
## 📬 Contact

If you’d like to discuss this project, analytics methodologies, or potential collaboration opportunities, please feel free to reach out, preferably by email:

Email: ibarreirocanda@gmail.com  
LinkedIn: https://www.linkedin.com/in/yago-b-35582644/

---
## 💖 Support & Donations

If you find this project useful and would like to support its continued development, you can do so via a donation.
Your support helps me invest more time in building, maintaining, and extending data analytics projects like this one.

Donations are entirely optional, but always appreciated 🙏

☕ Buy Me a Coffee: https://buymeacoffee.com/ibarca
