
---

# 📁 `docs/ETL_steps.md`

```md
# ETL & Data Modeling Process

## 1. Data Ingestion
- Imported Superstore CSV into Power BI
- Promoted headers and enforced data types

## 2. Data Cleaning
- Trimmed and cleaned all text columns
- Validated numeric ranges
- Standardized date formats

## 3. Dimension Creation
- Created DimProduct, DimCustomer, DimRegion, DimChannel via Power Query references
- Removed duplicates
- Added surrogate keys

## 4. Fact Table
- Built FactSales with transactional metrics
- Calculated:
  - SalesAmount
  - CostAmount
  - UnitPrice
  - UnitCost

## 5. Date Table
- Created DimDate using DAX
- Linked via model relationships (not merged)

## 6. Model Optimization
- One-to-many relationships
- Single direction filtering
- Hidden technical columns

Result: clean star schema optimized for analytical performance.
