![BathPro Logo](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/BatPro_logo.png)

# BathPro — Supply Chain & Commercial Analytics

## Project Overview

End-to-end data architecture and Power BI dashboard for BathPro, a European bathroom-fittings retailer sourcing from  suppliers across Poland, Spain, Switzerland, Germany, and Italy.

BathPro's supplier network, product catalogue structure, and operating rules (minimum order values, delivery lead times, return policy, channel mix) reflect the company's real business model. Purchasing and sales transaction data is modeled — generated to follow these same business rules and realistic seasonal demand patterns — so the full analytics pipeline could be built, tested, and demonstrated without using commercially sensitive transaction records.

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

---

## Business Context

The business operates in the bathroom-products sector, selling products such as toilets, vanity units, shower enclosures, shower screens, trays, taps, washbasins and accessories.

The business purchases products from multiple European suppliers and sells through several sales channels.

The analytical challenge is to understand how purchasing decisions, supplier performance, inventory levels and customer demand interact.

Management needs to answer questions such as:

## Business Questions

- How much are we spending on purchasing?
- Which suppliers account for the largest share of purchasing spend?
- Which suppliers consistently meet expected delivery dates?
- How much inventory is currently tied up in stock?
- Which product categories generate the most revenue?
- Which categories contribute most to gross profit?
- What seasonal patterns exist in customer demand?
- How might demand develop during 2027?
- Does the current inventory position provide sufficient coverage against forecast demand?
- Where may additional purchasing requirements arise?

### Purchasing & Supplier Performance

- What is total purchasing spend?
- How is purchasing spend distributed across suppliers?
- Which suppliers have the highest purchasing volumes?
- What is the supplier delivery performance?
- Which suppliers have the highest average delivery delays?
- How much purchasing spend is associated with suppliers with weaker delivery performance?

### Sales & Revenue

- How does sales activity change over time?
- Which product categories generate the most revenue?
- Which sales channels contribute most to revenue?
- What seasonal patterns can be identified?
- How has sales performance changed between years?
- Which products and categories contribute most to commercial performance?

### Inventory Management

- How many units are currently held in inventory?
- What is the value of inventory at cost?
- Which product categories hold the largest stock positions?
- How does inventory move over time?
- How much stock has been damaged?
- Which products may require closer inventory monitoring?

### Profitability

- What is total revenue excluding VAT?
- What is the cost of goods sold?
- What is gross profit?
- What is gross margin?
- How does profitability vary across product categories?
- How does landed cost affect commercial profitability?

### 2027 Demand Forecast

- What historical monthly sales patterns exist?
- Which months show stronger or weaker demand?
- What seasonal patterns can be identified?
- What could 2027 demand look like by product category?
- How does forecast demand compare with the existing inventory position?
- Where could future purchasing requirements emerge?

The forecast uses historical sales behaviour and monthly seasonality to produce a 2027 category-level demand forecast.

---

## Data Architecture

The Power BI data model shema tables and column relationship.
![Data_Model_Shema](https://github.com/NicolaeAm/BathPro-Supply-Chain-and-Commercial-Analytic-Using-Power-BI-Project/blob/main/BathPro_Power_BI_Shema.png)

### Core Tables

- `PRODUCTS`
- `Suppliers`
- `tblPurchases`
- `tblSales`
- `qryReceipts`
- `qryInventoryTransactions`
- `DateTable`

The **Internal SKU** acts as the common product identifier across purchasing, sales, products and inventory.

Supplier information is connected through **Supplier ID**.

The Date Table provides the common time dimension used across purchasing, sales and inventory analysis.

