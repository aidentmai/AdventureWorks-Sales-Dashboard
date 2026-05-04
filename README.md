# AdventureWorks Sales Performance Dashboard

A Power BI executive sales dashboard analyzing revenue performance, product profitability, and regional sales distribution using the Microsoft AdventureWorks dataset.

---

## Dashboard Preview

> *Open the `.pbix` file in Power BI Desktop or view the exported PDF for a static preview.*

---

## Business Questions Answered

- How does monthly revenue track against sales targets?
- Which regions generate the most revenue globally?
- Which products drive the most revenue and what are their margins?
- How has revenue trended month over month compared to the average?
- How does this year's revenue compare to the prior year?

---

## Key Metrics

| Metric | Description |
|---|---|
| Total Revenue | Total sales revenue across all products and regions |
| Revenue YTD | Year-to-date cumulative revenue |
| YoY Growth | Year-over-year revenue growth percentage |
| Gross Margin | Revenue minus product cost as a percentage of revenue |

---

## Visuals Built

- **KPI Cards** — snapshot of total revenue, revenue YTD, YoY growth, and gross margin
- **Clustered Bar Chart** — monthly revenue vs sales target side by side
- **Map** — global revenue distribution by sales territory with bubble sizing
- **Table** — top 10 products ranked by revenue with gross margin
- **Line Chart** — monthly revenue trend with average benchmark line

---

## Technical Highlights

- **Star schema data model** — Sales fact table connected to Product, Customer, SalesTerritory, and Date dimension tables
- **Time intelligence DAX** — TOTALYTD, SAMEPERIODLASTYEAR for YTD and YoY calculations
- **Sales Target measure** derived from prior year revenue with a 10% growth assumption
- **Gross Margin** calculated as a DAX ratio with separate display measure formatted as percentage
- **Top N filtering** — visual-level Top 10 filter on product table using Total Revenue

---

## DAX Measures

```
Total Revenue = SUM(Sales[SalesAmount])

Total Cost = SUM(Sales[TotalProductCost])

Gross Margin = DIVIDE([Total Revenue] - [Total Cost], [Total Revenue])

Revenue YTD = TOTALYTD([Total Revenue], 'Date'[Date])

Revenue Last Year = CALCULATE([Total Revenue],
    SAMEPERIODLASTYEAR('Date'[Date]))

YoY Growth = DIVIDE([Total Revenue] - [Revenue Last Year],
    [Revenue Last Year])

Sales Target = [Revenue Last Year] * 1.10

Vs Target = [Total Revenue] - [Sales Target]

Vs Target % = DIVIDE([Vs Target], [Sales Target])
```

---

## Data Source

**Microsoft AdventureWorks Sample Dataset**
- Source: [Power BI Desktop Samples](https://github.com/microsoft/powerbi-desktop-samples)
- Tables used: Sales, Product, Customer, SalesTerritory, Date
- Data range: FY2019 — FY2020

---

## Tools Used

| Tool | Purpose |
|---|---|
| Power BI Desktop | Report building, data modeling, DAX |
| Power Query (M) | Data ingestion and transformation |
| DAX | Measures, KPIs, time intelligence |

---

## Files in This Repository

| File | Description |
|---|---|
| `AdventureWorks_Sales_Dashboard.pbix` | Power BI file — open in Power BI Desktop |
| `AdventureWorks_Sales_Dashboard.pdf` | Static PDF export for quick preview |
| `README.md` | This file |

---

## About

Built as part of a Business Intelligence portfolio to demonstrate end-to-end BI development skills including star schema modeling, DAX time intelligence, and executive dashboard design.

*Developed by Vy Mai*
