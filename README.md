# 🛒 E-Commerce Sales & Profitability Dashboard

An end-to-end Microsoft Power BI analytics solution designed to track top-line revenue growth, product margin health, regional cost drivers, and operational fulfillment expenses. This multi-page report delivers interactive executive views to help e-commerce decision-makers optimize margins and evaluate cost efficiencies.
## 📌 Executive Summary

 Total Revenue: $484,559 across 2,000 orders
 Total Net Profit: $158,872
 Profit Margin: 32.79% retention rate
 Units Sold: 7,115 products

## 📊 Dashboard Overview & Multi-Page Layout

Page 1: Revenue & Profit
Focuses on top-line sales trends, seasonal demand spikes, category performance, payment preferences, and top-performing SKUs.
<img width="1712" height="763" alt="image" src="https://github.com/user-attachments/assets/63a098af-f01c-459e-a80e-0dbb6466357e" />

 Key Features: Monthly trend lines, top 10 products ranking, category distribution donut chart, and exact-figure KPI cards.

Page 2: Expense & Profit

Shifts focus to operational cost control, regional expense ratios, country-level cost drivers, and margin sustainability.

<img width="1718" height="755" alt="image" src="https://github.com/user-attachments/assets/00b24c73-1aba-41c5-846a-ea9d70c62d68" />

 Key Features: Regional expense breakdowns, side-by-side expense vs. profit comparisons, and country-level expense rankings.

## 🏗️ Data Architecture & Modeling

The project utilizes a relational Star Schema centered around an `E-Sales` fact table connected to single-direction dimension tables (`Calendar`, `Products`, `Regions`, `Customers`).

### Custom Calendar Table
Engineered a DAX-driven `Calendar` table (spanning 2022–2025) to power dynamic date slicing, year-month drilldowns, and robust time-intelligence measures.
## 📐 Advanced DAX Measures & Financial Logic
To ensure accounting precision, discounts are categorized as contra-revenue (reducing gross revenue to net revenue), while shipping fees are treated as operating fulfillment expenses.
### Data Analysis Expressions (DAX)
Total Sales
Total Sale = SUMX('E-Sales', 'E-Sales'[Quantity]  'E-Sales'[Unit_Price])

Total Profit Margin (%)
Profit Margin = DIVIDE([Total Profit], [Total Sale], 0)

Time Intelligence: Prior Year Sales
Prior Year Sales = CALCULATE([Total Sale], SAMEPERIODLASTYEAR('Calendar'[Date]))

Time Intelligence: Year-over-Year Growth ($)
YOY = [Total Sale] - [Prior Year Sales]

Time Intelligence: Year-over-Year Growth (%)
YOY% = DIVIDE([YOY], [Prior Year Sales], 0)

Key Business Insights

1. Category Performance: Furniture dominates top-line revenue at 52.89%, followed by Technology at 28.79%.
2. Top SKUs: Product lines are led by high-margin workspace items including the Standing Desk Converter and Ergonomic Office Chair.
3. Q4 Seasonality: Order volumes and net profits consistently surge during Q4 (October–December), while Q1 experiences predictable post-holiday dips.
4. Fulfillment Cost Drivers: Europe and North America generate the highest overall sales volume but also absorb the largest share of operational fulfillment expenses

Tech Stack & Tools
Business Intelligence: Microsoft Power BI Desktop
Data Transformation: Power Query (ETL)
Data Modeling: DAX (Data Analysis Expressions), Star Schema
UI Design: Dark Theme, Custom Color Palette, Dynamic Slicers & Drillthrough
