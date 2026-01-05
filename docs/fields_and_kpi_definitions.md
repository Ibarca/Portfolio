📦 Dataset Fields & KPI Definitions

Each row represents one SKU.
All KPIs are calculated in BigQuery SQL and exposed to Google Sheets for scalable reporting.


🗓 Product Lifecycle & Supplier Attributes

- listed_year – Year the SKU was first listed, used to analyze product maturity and lifecycle.

- supplier – Identifier of the main supplier, linking performance to sourcing decisions.

- supplier_country – Supplier location, used to assess logistics, lead time, and geopolitical risk.


💰 Sales & Revenue Performance

- sales_365 – Total units sold in the last 365 days, measuring demand and sales velocity.

- revenue_365 – Total revenue in the last 365 days, used for SKU prioritization.

- contribution_revenue – Cumulative share of total assortment revenue contributed by the SKU.

- class (ABC) – Revenue-based SKU classification following the Pareto principle (A/B/C).


💲 Pricing & Margin Structure

- avg_selling_price – Average selling price, linking volume to revenue and margins.

- cm1 – Gross contribution margin after product cost, measuring base profitability.

- cm2 – Contribution margin after variable operational costs.

- cm3 – Contribution margin after marketing and overheads, approximating net profitability.


📊 Inventory & Availability

- stock_on_hand – Current physical inventory level of the SKU.

- reach_days – Estimated number of days current stock will last based on historical demand.

- lead_time_days – Average supplier lead time, indicating replenishment speed and risk.

- service_level – Percentage of days the SKU was in stock over the last 365 days.
