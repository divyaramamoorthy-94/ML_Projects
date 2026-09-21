#  New-Wheels: E-Commerce Resale Platform Quarterly Business Diagnostics (SQL)

An end-to-end relational database querying and business intelligence project utilizing advanced SQL analytical operations to diagnose operational bottlenecks, evaluate logistics performance, and arrest a steady decline in quarterly sales.

---

##  Executive Summary & Business Problem
New-Wheels, a fast-growing digital vehicle resale application offering end-to-end listing-to-shipping fulfillment, faces a severe corporate crisis. Steady multi-quarter drops in transaction volume and alarming spikes in negative public user ratings have severely choked new customer acquisition. 

This project involves importing a complex database schema dump and writing highly optimized relational queries to generate a diagnostic **Quarterly Business Intelligence Report** for the CEO. The objective is to map consumer distributions, locate operational failures, and provide data-grounded revenue restoration actions.

---

##  Database Infrastructure & Technical Frameworks
The data pipeline and query logic were constructed using enterprise-grade SQL design structures:
* **Relational Schema Integration**: Merged separate operational dimensions across multi-table joins (`order_t`, `customer_t`, `product_t`) to establish unified historical transactional views.
* **Advanced Aggregations**: Applied rigorous nested conditional logic via `CASE WHEN` algorithms to evaluate categorical performance, track percent distributions, and normalize alphanumeric survey metrics into a standardized 1–5 score grid.
* **Window Inferences**: Implemented analytic windowing operations like `RANK() OVER (PARTITION BY ...)` to parse high-cardinality ties at the state level and `LAG() OVER (...)` to isolate structural Quarter-over-Quarter (QoQ) growth patterns.
* **Common Table Expressions (CTEs)**: Formulated clean, multi-layered sequential CTE blocks to maximize processing efficiency and maintain highly structured query clarity.

---

##  Diagnostic Data Insights & Revenue Vulnerabilities

### 1. Market Penetration & Inventory Alignment
* **Demographic Concentration**: A total of **994 unique customers** generated 1,000 baseline transactions. Core volume concentrates heavily within major regional hubs: **California (97)** and **Texas (97)** tie for peak demand, closely trailed by Florida (86) and New York (69).
* **Manufacturer Focus**: Inventory consumption pivots tightly around a few domestic and international giants. **Chevrolet leads consumer acquisition with 83 orders**, followed by Ford (63) and Toyota (52), with Dodge (50) and Pontiac (50) tied.
* **Dynamic Regional Shifts**: State-by-state mapping shows that customer preferences are highly localized, requiring distinct geographic inventory planning rather than flat national forecasting.

### 2. The Sales & Revenue Tailspin
* **Order Contraction**: Transaction volume drops continuously across every operational frame, sliding from a high of **310 orders in Q1** down to a weak **199 orders in Q4**.
* **Financial Erosion**: Cumulative revenue totals 124.71 million. However, quarterly net velocity reflects a massive downward spiral, collapsing from 39.42 million in Q1 to a baseline of 23.35 million in Q4. The financial collapse peaked in Q4 with a devastating **QoQ net revenue drop of -20.13%**.

### 3. The Operational Bottleneck: Logistics Failure
* **Shipping Backlogs**: The root cause of the platform's decline is a complete failure in logistics operations. The average time to ship an order increased drastically, climbing from **57.17 days in Q1** to a massive, unsustainable **174.10 days in Q4**. 
* **The Customer Satisfaction Collapse**: This logistics breakdown directly explains the erosion of customer trust. The average customer satisfaction rating plummeted from **3.55 (Good/Okay) in Q1 down to a failing 2.40 (Bad) in Q4**. 
* **Feedback Inversion**: Over the course of the year, extreme dissatisfaction (*Very Bad* feedback) exploded from **10.97% to 30.65%**, while elite customer retention metrics (*Very Good* scores) fell off a cliff, dropping from **30.00% to just 10.05%**.

---

##  Quarterly Performance Diagnostics Summary
The baseline financial grid highlights the strong correlation between operational lag and structural revenue drops across the enterprise:

| Operational Period | Total Volume (Orders) | Net Revenue Generated | QoQ Revenue Change (%) | Avg Logistics Delay (Days to Ship) | Severe User Dissatisfaction (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Quarter 1 (Q1)** | `310` | `39,421,580.16` | *Baseline* | `57.17` | **`10.97%`** |
| **Quarter 2 (Q2)** | `262` | `32,715,830.34` | **`-17.01%`** | `71.11` | **`14.89%`** |
| **Quarter 3 (Q3)** | `229` | `29,229,896.19` | **`-10.66%`** | `117.76` | **`17.90%`** |
| **Quarter 4 (Q4)** | `199` | `23,346,779.63` | **`-20.13%`** | `174.10` | **`30.65%`** |
| **Cumulative / Avg** | **`1,000`** | **`124,714,086.32`** | **N/A** | **`97.96`** | **`20.48%`** |

---

##  Executive Strategic Action Plan for New-Wheels Management
* **Immediate Logistics Overhaul**: Stricter delivery SLAs must be established. Leadership should auditing the current shipping partner network, eliminate bottleneck nodes, and transition logistics operations toward local hubs to bring the 174-day shipping delay down.
* **Targeted Regional Supply Chains**: Allocate inventory assets dynamically by placing heavy concentrations of high-demand makes (Chevrolet, Ford, Toyota) directly within distribution facilities inside peak revenue states (California, Texas, Florida).
* **Churn Mitigation & Service Recovery**: Establish an immediate after-sales response unit to automatically flag and follow up with users submitting sub-optimal feedback, utilizing credit incentives to protect customer lifetime value.

---

* **`New_Wheels_SQL_Analytics/`** 
  * `README.md` — Relational overview, business diagnostics, performance metrics, and tactical action plans.
  * `New_Wheels_Analysis.sql` — Optimized script file containing database configuration codes, multi-table joins, and window analytics.
  * `new_wheels_db.sql` — Schema dump asset tracking transaction historical dimensions.
