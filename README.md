![BathPro Logo](https://)

# BathPro — Supply Chain & Commercial Analytics

## Project Overview

This project is an end-to-end Supply Chain and Commercial Analytics solution built using Excel and Microsoft Power BI.

The project models a bathroom-products business across purchasing, supplier performance, inventory, sales, profitability and demand forecasting. The objective is to connect operational data from different business processes and turn it into a management reporting and decision-support solution.

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

The Power BI model connects several business areas through common business keys.

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

