![BathPro Logo](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/BathPro_logo.png)

# BathPro — Supply Chain & Commercial Analytics

## Project Overview

BathPro is a bathroom-products retailer and supplier, sourcing from a network of European manufacturers. The catalogue spans the full bathroom renovation basket — bathtubs, shower enclosures and screens, walk-in showers, trays, vanity units, brassware, toilets, and accessories.
BathPro sells across four points of sale: an in-person Showroom, an online store (Website), in-store POS terminals, and cash transactions.
This project builds the end-to-end analytics layer behind that operation — purchasing, supplier performance, inventory, sales, profitability, and demand planning — in Power BI. Purchasing and sales transaction data are modeled: generated to follow BathPro's real supplier terms, product structure, and realistic seasonal demand patterns, so the complete analytical workflow could be built and demonstrated without using commercially sensitive transaction records.

The project covers:
- Product and supplier data
- Purchasing and supplier performance
- Inventory movements and stock balances
- Sales and revenue analysis
- Gross profit and margin analysis
- Customer returns and damaged stock
- 2027 sales forecasting
- Forecast demand versus inventory position
- Purchasing requirements analysis

The analytical challenge is to understand how purchasing decisions, supplier performance, inventory levels and customer demand interact.
Management needs to answer questions such as:

## Key Business Questions

- Which suppliers account for the largest share of purchasing spend?
- Which suppliers consistently meet expected delivery dates?
- How much inventory is currently tied up in stock?
- Which product categories generate the most revenue?
- Which categories contribute most to gross profit?
- What seasonal patterns exist in customer demand?
- How has sales performance changed between years?
- How much stock has been damaged?
- How does profitability vary across product categories?
- What historical monthly sales patterns exist?
- What could 2027 demand look like by product category?
- How does forecast demand compare with the existing inventory position?
- Where could future purchasing requirements emerge?

The forecast uses historical sales behaviour and monthly seasonality to produce a 2027 category-level demand forecast.

## Data Architecture

The Power BI data model schema shows the main tables and relationships.

![Data_Model_Shema](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/BathPro_Power_BI_Schema.png)

The **Internal SKU** acts as the common product identifier across purchasing, sales, products and inventory.
Supplier information is connected through **Supplier ID**.
The Date Table provides the common time dimension used across purchasing, sales and inventory analysis.

#### 1. Date Table

``` DAX
DateTable =
ADDCOLUMNS(
    CALENDAR(DATE(2023,1,1), DATE(2027,12,31)),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month", FORMAT([Date], "MMM"),
    "Year Month", FORMAT([Date], "YYYY-MM"),
    "Quarter", "Q" & FORMAT([Date], "Q")
)
```
### DAX Measures
  The following DAX measures were used to calculate the main KPIs and analytical outputs in the Power BI model.
```Revenue =
SUMX(
    tblSales,
    tblSales[Quantity Out] *
    DIVIDE(tblSales[Sales], 1.23)
)
```
Calculates revenue excluding 23% VAT.

```Current Stock on Hand =
SUMX(
    VALUES(qryInventoryTransactions[Internal SKU]),
    CALCULATE(
        LASTNONBLANKVALUE(
            qryInventoryTransactions[SKU Ledger.Transaction Date],
            SUM(qryInventoryTransactions[SKU Ledger.Stock Balance])
        )
    )
)
```
Calculates the latest stock balance for each SKU and aggregates the current stock position.

```On-Time Delivery % =
DIVIDE(
    CALCULATE(
        COUNTROWS(tblPurchases),
        tblPurchases[Actual Delivery] <=
        tblPurchases[Expected Delivery]
    ),
    COUNTROWS(tblPurchases)
)
```
Measures the percentage of purchase orders delivered on or before the expected delivery date.

```COGS =
SUMX(
    tblSales,
    tblSales[Quantity Out] *
    tblSales[Landed Cost]
)
```
Cost of Goods Sold calculates the total cost of products sold by multiplying the quantity sold by the landed cost per unit, then summing the results across all sales transactions.

## Dashboards & Key Business Findings

### 1. Purchasing & Supplier Dashboard
![Purchasing and Supplying](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/Power%20Bi%20Dashboards/Purchasesing%20and%20Suppling.png)
### Purchasing & Supplier Performance
- Purchase spend reached €6.28M across 1,728 purchase orders.
- Overall on-time delivery was 70%, with late deliveries averaging 7 days.
- Supplier performance varied across the supplier base, creating opportunities to improve delivery reliability and purchasing planning.

Business focus: Use supplier delivery performance alongside purchase spend and lead times when reviewing suppliers, prioritising improvement discussions and adjusting purchasing timelines for less reliable suppliers.

### 2. Sales & Revenue 
![Sales and Revenue](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/Power%20Bi%20Dashboards/Sales%20%26%20Revenue.png)
### Sales & Revenue
- Revenue excluding VAT reached €5.65M, with €2.26M gross profit and a 40% gross margin.
- Revenue increased 8.2% in 2025, while units sold increased 6.6%, indicating slower growth following the stronger expansion in 2024.
- Demand showed clear seasonality, with stronger sales activity in April, May, September and October.
- Square POS was the largest sales channel in the dataset.
- Returns represented a small proportion of overall sales.

Business focus: Monitor revenue, margin, product mix and sales channels together to support profitable growth.
  
### 3. Inventory Management
![Inventory](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/Power%20Bi%20Dashboards/Inventory.png)
### Inventory
- Current stock was approximately 31.9K units, with an inventory value of €5.52M at cost.
- Stock levels varied significantly by product category.
- Some categories showed potential surplus while others showed potential shortfalls against expected demand.

Business focus: Align replenishment decisions with demand and current stock position to reduce excess inventory while protecting product availability.

### 4. 2027 Demand & Purchasing Scenario
![2027 Demand Scenario](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/Power%20Bi%20Dashboards/Demand%20%26%20Purchasing%20Scenario.png)
### 2027 Forecast 
- The 2027 baseline scenario indicates approximately 11K units and €2.51M revenue.
- The scenario preserves historical monthly seasonality and applies an 8% annual growth assumption, based on the latest observed revenue growth rate.
- Comparing projected demand with current stock highlights potential surplus and shortfall categories.
- The analysis provides a basis for prioritising future purchasing requirements.

Business focus: Use demand projections together with current inventory to support forward purchasing decisions rather than relying only on historical stock levels.

## Conclusion
This project demonstrates an end-to-end approach to supply chain and commercial analytics, connecting purchasing, supplier performance, inventory, sales, profitability and demand planning within a single Power BI model.

The analysis moves beyond descriptive reporting by linking supplier reliability to inventory risk, sales seasonality to demand planning, and projected demand to purchasing requirements.

The 2027 scenario provides a practical planning framework for identifying potential stock gaps and surplus positions, helping focus purchasing decisions where they are most relevant.

Overall, the project demonstrates how Power Query, Power BI and DAX can transform operational data into structured business insights and support commercial, inventory and supply chain decision-making.

## Tools & Technologies
Power BI — Data modelling, DAX, dashboards and visual analytics
Power Query — Data transformation, cleaning and preparation
DAX — KPI calculations, profitability, inventory and demand analysis
Excel — Source data preparation and validation

## Author - Nicolae 
This project is part of my data analytics portfolio, demonstrating practical experience with Power Query, Power BI, DAX, supply chain analytics, commercial analysis and business-focused reporting. 











