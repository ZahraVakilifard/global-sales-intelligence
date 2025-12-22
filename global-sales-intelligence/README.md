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

