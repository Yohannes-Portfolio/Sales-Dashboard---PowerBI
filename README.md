# Retail Sales Dashboard (Power BI)

An interactive, two page retail analytics dashboard built in Power BI, covering revenue, profitability, payment behaviour, product and supplier performance, and customer satisfaction across region, category, and customer segment.

## Table of contents

- [Business question](#business-question)
- [Data model](#data-model)
- [Tools](#tools)
- [Headline findings](#headline-findings)
- [Key metrics](#key-metrics)
- [Dashboard pages](#dashboard-pages)
- [Screenshots](#screenshots)
- [Repository structure](#repository-structure)
- [How to view](#how-to-view)

## Business question

Which products, suppliers, payment methods, regions, and customer segments drive revenue and profit, and where is margin being won or lost across the order base?

## Data model

A star schema held in a single workbook (`FACT_SALES.xlsx`) across three sheets: one fact table and two dimension tables, spanning January to April 2025. In Power BI the fact table relates to each dimension on its key, which is what powers the region, category, segment, supplier, and brand slicing across the report.

**SALES** (fact, 100 order level rows)

| Field | Description |
| --- | --- |
| OrderID | Unique order identifier |
| OrderDate | Date of the order |
| CustomerID | Foreign key to CUST_MASTER |
| ProductID | Foreign key to PROD_MASTER |
| Quantity | Units sold on the order |
| Discount% | Discount applied to the order |
| Sales | Order revenue |
| Profit | Order profit |
| PaymentMethod | Credit Card, UPI, Cash, or Debit Card |
| CustomerRating | Order satisfaction score, 1 to 5 |

**PROD_MASTER** (product dimension, 10 rows, joined to SALES on ProductID)

| Field | Description |
| --- | --- |
| ProductID | Primary key |
| Product | Product name (Laptop, Mobile, TV, and so on) |
| Category | Electronics, Furniture, Clothing, or Grocery |
| Brand | Product brand |
| UnitPrice | List price per unit |
| Supplier | Supplying vendor |

**CUST_MASTER** (customer dimension, 20 rows, joined to SALES on CustomerID)

| Field | Description |
| --- | --- |
| CustomerID | Primary key |
| CustomerName | Customer name |
| CustomerSegment | Premium, Regular, or New |
| Gender | Customer gender |
| AgeGroup | Age band (18 to 25, 25 to 35, 35 to 45) |
| Region | North, South, East, or West |
| MembershipYears | Years as a member |

Currency: US Dollars ($).

## Tools

Power BI Desktop for the data model, relationships, DAX measures, and the two report pages. Source data prepared in Excel.

## Headline findings

- **Electronics carries profitability.** Electronics accounts for $404K of total profit, about 73.6 percent, and also holds the strongest category margin at 22.55 percent. Grocery is the weakest at 16.37 percent.
- **Premium customers drive both volume and satisfaction.** The Premium segment generates $1.40M in sales, more than Regular and New combined, and carries the highest average rating at 4.85 out of 5.
- **Revenue concentrates in a few suppliers and products.** Dell alone supplies $836K of sales, about a third of the total, sold as the top product (Laptop), and Dell also holds the highest brand margin at 23.47 percent.
- **Credit Card carries the business.** Credit Card represents about 73.3 percent of all sales at the strongest margin of any method, while Cash sits lowest at 16.4 percent.
- **Overall performance.** $2.51M in total sales, $548K in total profit, a blended margin of 21.88 percent, an average order value of roughly $25,057, and an average customer rating of 4.46 out of 5.

## Key metrics

| Metric | Value |
| --- | --- |
| Total sales | $2.51M |
| Total profit | $548K |
| Profit margin | 21.88% |
| Orders | 100 |
| Average order value | ~$25,057 |
| Average customer rating | 4.46 / 5 |

## Dashboard pages

### Page 1: Retail Sales Dashboard (overview)

A performance overview answering how the business is doing and who is buying. Region, Category, and Month Year slicers control the whole page. It carries five KPI cards (Total Sales, Total Profit, Profit Margin, Orders, Avg Rating) above six visuals:

- Total Sales by Month Year (line), showing the trend across January to April
- Total Profit by Category (donut), led by Electronics at 73.58 percent
- Total Sales by Region (bar), led by North at $0.77M
- Total Sales by Customer Segment (column), led by Premium at $1.40M
- Avg Rating by Customer Segment (donut), with Premium highest at 4.85
- Total Sales by Age Group (column), led by the 25 to 35 group at $1.12M

### Page 2: Product Analysis

A deeper view of what sells and how profitably, controlled by the same Region, Category, and Month Year slicers. It carries five visuals:

- Profit Margin by Category (column), from Electronics at 22.55 percent down to Grocery at 16.37 percent
- Total Sales by Supplier (donut), led by Dell at $836K (33.36 percent)
- Total Sales by Product (bar), led by Laptop at $836K
- Total Sales by Payment Method (donut), with Credit Card at 73.25 percent
- Profit Margin by Brand (column), led by Dell at 23.47 percent

## Screenshots
