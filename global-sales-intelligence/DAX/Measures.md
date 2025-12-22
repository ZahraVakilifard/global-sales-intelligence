# DAX Measures — Global Sales & Profit Intelligence

This document lists all business measures used in the Power BI report built on the Superstore dataset.
All measures are evaluated at report level and respect slicers and relationships.

Total Sales =
```DAX
SUM(FactSales[SalesAmount])
```

Total Quantity =
```DAX
SUM(FactSales[Quantity])
```

Total Shipping =
```DAX
SUM(FactSales[ShippingCost])
```

Total Cost =
```DAX
SUM(FactSales[CostAmount])
```

Total Cost incl Shipping =
```DAX
[Total Cost] + [Total Shipping]
```

Gross Profit =
```DAX
[Total Sales] - [Total Cost]
```

Net Profit =
```DAX
[Total Sales] - [Total Cost incl Shipping]
```

Profit Margin % =
```DAX
DIVIDE([Gross Profit], [Total Sales], 0)
```

Net Margin % =
```DAX
DIVIDE([Net Profit], [Total Sales], 0)
```

Avg Unit Price =
```DAX
AVERAGE(FactSales[UnitPrice])
```

Avg Unit Cost =
```DAX
AVERAGE(FactSales[UnitCost])
```

Avg Order Value =
```DAX
DIVIDE([Total Sales], DISTINCTCOUNT(FactSales[SalesID]))
```

Discount Amount =
```DAX
SUMX(FactSales, FactSales[SalesAmount] * FactSales[Discount])
```

Customers =
```DAX
DISTINCTCOUNT(FactSales[CustomerKey])
```

Repeat Customers % =
```DAX
VAR CustomerOrders =
    SUMMARIZE(
        FactSales,
        FactSales[CustomerKey],
        "OrderCount", DISTINCTCOUNT(FactSales[SalesID])
    )
VAR RepeatCustomers =
    COUNTROWS(FILTER(CustomerOrders, [OrderCount] > 1))
RETURN
DIVIDE(RepeatCustomers, [Customers], 0)
```

Sales YTD =
```DAX
TOTALYTD([Total Sales], DimDate[Date])
```

Sales MTD =
```DAX
TOTALMTD([Total Sales], DimDate[Date])
```

Sales LY =
```DAX
CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DimDate[Date]))
```

Sales YoY % =
```DAX
DIVIDE([Total Sales] - [Sales LY], [Sales LY])
```

Rolling 12M Sales =
```DAX
CALCULATE(
    [Total Sales],
    DATESINPERIOD(DimDate[Date], MAX(DimDate[Date]), -12, MONTH)
)
```

Sales Growth Rate (12M) =
```DAX
VAR CurrentPeriod = [Rolling 12M Sales]
VAR PreviousPeriod =
    CALCULATE([Rolling 12M Sales], DATEADD(DimDate[Date], -12, MONTH))
RETURN
DIVIDE(CurrentPeriod - PreviousPeriod, PreviousPeriod, BLANK())
```

Top N Product Sales (Top 10) =
```DAX
CALCULATE(
    [Total Sales],
    TOPN(
        10,
        VALUES(DimProduct[ProductKey]),
        [Total Sales],
        DESC
    )
)
```

At Risk Product (%) =
```DAX
VAR RiskProducts =
    CALCULATE(
        DISTINCTCOUNT(DimProduct[ProductKey]),
        FILTER(DimProduct, [Net Margin %] < 0)
    )
VAR TotalProducts = DISTINCTCOUNT(DimProduct[ProductKey])
RETURN DIVIDE(RiskProducts, TotalProducts, 0)
```

All measures are ready to use in all report pages and respect slicers and filters.
