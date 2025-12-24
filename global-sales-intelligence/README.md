# Global Sales & Profit Intelligence Dashboard

This project delivers an end-to-end executive-level sales intelligence dashboard built in Power BI using a Superstore-style transactional dataset.

It demonstrates professional data modeling, KPI design, time-series analysis, and multi-page analytical storytelling suitable for enterprise BI roles.

---

## Business Objective

Enable leadership to:
- Track revenue, cost, profit, and margins
- Identify high- and low-performing products and regions
- Monitor trends, growth, and operational risk
- Drill from executive KPIs to transactional detail

---

## Dataset

**Source:** Superstore sales dataset (CSV)

**Grain:** One row per sales transaction

**Key fields:**
- OrderDate, ProductID, CustomerID
- Sales, Quantity, Discount, ShippingCost
- Profit, Region, Category, Channel

The raw dataset is included for transparency and reproducibility.

---

## Data Model

A clean **star schema** was designed:

- **FactSales** (central transactional fact table)
- **DimDate**
- **DimProduct**
- **DimCustomer**
- **DimRegion**
- **DimChannel**

All relationships are **one-to-many**, single-direction, optimized for performance.

![Data Model](docs/data_model.png)

---

## Key Metrics (DAX)

- Total Sales
- Total Cost (incl. Shipping)
- Net Profit
- Profit Margin %
- Rolling 12-Month Sales
- Sales YoY %
- Avg Order Value
- Repeat Customer %
- Top-N Product Sales

Full definitions are documented in `/DAX/Measures.md`.

---

## Report Pages

### 1. Sanity Checks
Data validation layer for trust:
- Row counts, totals, distributions
- Sales by year, category, region
- Key numeric cross-checks

### 2. Executive Overview
High-level performance snapshot:
- Total Sales: **3.39B**
- Net Profit: **27.53M**
- Profit Margin: **11%**
- Customer Count: **14.02M**
- Trend analysis and top regions

### 3. Revenue & Margin Deep Dive
- Channel-level revenue trends
- Category & subcategory performance
- Profit waterfall analysis

### 4. Product Detail
- Single-product drilldown
- Sales, profit, margin trend
- Transaction-level breakdown

### 5. Geographic Performance
- Regional and city-level analysis
- Sales, profit, quantity by location
- Interactive map with drilldowns

### 6. Product Portfolio
- Category & product comparison
- Margin vs volume positioning
- Trend analysis by product

---

## Results & Key Insights

### Overall Performance
- Total Sales reached **$3.39B**, with a **Net Profit of $27.5M**.
- Overall **Profit Margin is 11%**, indicating tight margins despite high revenue.
- Rolling 12-month sales show steady growth with seasonal spikes.

### Regional Performance
- Top 3 regions contribute over **60% of total sales**.
- Some high-revenue regions operate at **below-average profit margins**, highlighting cost or discount inefficiencies.
- City-level drill-downs reveal concentrated sales dependency in a small number of markets.

### Product Portfolio
- A small subset of products generates the majority of revenue (Pareto effect).
- Several high-volume products operate at **negative or near-zero margins**, creating profit risk.
- Product categories show significantly different margin profiles despite similar sales volumes.

### Channel & Discount Analysis
- Shipping and discount costs materially reduce net profitability.
- Certain ship modes drive higher sales but at increased shipping cost.
- Waterfall analysis shows how sales degrade into net profit across cost layers.

### Data Validation
- Sanity check page confirms alignment between transactional totals and aggregated KPIs.
- Customer counts, sales totals, and quantities reconcile across fact and dimension views.
- This ensures the analytical outputs are reliable and audit-ready.

### Business Recommendations
- Review pricing and discount strategy for consistently unprofitable products.
- Optimize shipping methods in regions with high logistics cost.
- Focus growth efforts on high-margin categories rather than volume-only sales.

---

## How to Open

1. Download the repository
2. Open `pbix/Global_Sales_Intelligence.pbix`
3. Refresh data if prompted (CSV path may need adjustment)

---

## Tools Used
- Power BI Desktop (2025)
- Power Query (GUI)
- DAX
- GitHub for version control

---

**Zahra Vakilifard**    

- GitHub: https://github.com/ZahraVakilifard
- LinkedIn: https://www.linkedin.com/in/zahravakilifard


