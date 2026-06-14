# Retail Sales Dashboard (Power BI)

An interactive, two page retail analytics dashboard built in Power BI, covering revenue, profitability, payment behaviour, product and supplier performance, and customer satisfaction across region, category, and customer segment.

## Table of contents

- [Screenshots](#screenshots)
- [Business question](#business-question)
- [Data model](#data-model)
- [Tools](#tools)
- [Headline findings](#headline-findings)
- [Key metrics](#key-metrics)
- [Dashboard pages](#dashboard-pages)
- [Recommendations](#recommendations)
- [Repository structure](#repository-structure)
- [How to view](#how-to-view)

## Screenshots

<p align="center"><strong>Retail Sales Dashboard</strong></p>
<p align="center">
  <img src="Retail%20Dashboard-1.png" alt="Retail Sales Dashboard overview" width="850">
</p>

<p align="center"><strong>Product Analysis</strong></p>
<p align="center">
  <img src="Retail%20Dashboard-2.png" alt="Product Analysis page" width="850">
</p>

## Business question

Which products, suppliers, payment methods, regions, and customer segments drive revenue and profit, and where is margin being won or lost across the order base?

## Data model

A star schema held in a single workbook (`FACT_SALES.xlsx`) across three sheets: one fact table and two dimension tables, spanning January to April 2025. In Power BI the fact table relates to each dimension on its key, which is what powers the region, category, segment, supplier, and brand slicing across the report.

<p align="center"><strong>SALES</strong> (fact, 100 order level rows)</p>

<div align="center">

<table>
<tr><th>Field</th><th>Description</th></tr>
<tr><td>OrderID</td><td>Unique order identifier</td></tr>
<tr><td>OrderDate</td><td>Date of the order</td></tr>
<tr><td>CustomerID</td><td>Foreign key to CUST_MASTER</td></tr>
<tr><td>ProductID</td><td>Foreign key to PROD_MASTER</td></tr>
<tr><td>Quantity</td><td>Units sold on the order</td></tr>
<tr><td>Discount%</td><td>Discount applied to the order</td></tr>
<tr><td>Sales</td><td>Order revenue</td></tr>
<tr><td>Profit</td><td>Order profit</td></tr>
<tr><td>PaymentMethod</td><td>Credit Card, UPI, Cash, or Debit Card</td></tr>
<tr><td>CustomerRating</td><td>Order satisfaction score, 1 to 5</td></tr>
</table>

</div>

<p align="center"><strong>PROD_MASTER</strong> (product dimension, 10 rows, joined to SALES on ProductID)</p>

<div align="center">

<table>
<tr><th>Field</th><th>Description</th></tr>
<tr><td>ProductID</td><td>Primary key</td></tr>
<tr><td>Product</td><td>Product name (Laptop, Mobile, TV, and so on)</td></tr>
<tr><td>Category</td><td>Electronics, Furniture, Clothing, or Grocery</td></tr>
<tr><td>Brand</td><td>Product brand</td></tr>
<tr><td>UnitPrice</td><td>List price per unit</td></tr>
<tr><td>Supplier</td><td>Supplying vendor</td></tr>
</table>

</div>

<p align="center"><strong>CUST_MASTER</strong> (customer dimension, 20 rows, joined to SALES on CustomerID)</p>

<div align="center">

<table>
<tr><th>Field</th><th>Description</th></tr>
<tr><td>CustomerID</td><td>Primary key</td></tr>
<tr><td>CustomerName</td><td>Customer name</td></tr>
<tr><td>CustomerSegment</td><td>Premium, Regular, or New</td></tr>
<tr><td>Gender</td><td>Customer gender</td></tr>
<tr><td>AgeGroup</td><td>Age band (18 to 25, 25 to 35, 35 to 45)</td></tr>
<tr><td>Region</td><td>North, South, East, or West</td></tr>
<tr><td>MembershipYears</td><td>Years as a member</td></tr>
</table>

</div>

<p align="center">Currency: US Dollars ($).</p>

## Tools

Power BI Desktop for the data model, relationships, DAX measures, and the two report pages. Source data prepared in Excel.

## Headline findings

- **Electronics carries profitability.** Electronics accounts for $404K of total profit, about 73.6 percent, and also holds the strongest category margin at 22.55 percent. Grocery is the weakest at 16.37 percent.
- **Premium customers drive both volume and satisfaction.** The Premium segment generates $1.40M in sales, more than Regular and New combined, and carries the highest average rating at 4.85 out of 5.
- **Revenue concentrates in a few suppliers and products.** Dell alone supplies $836K of sales, about a third of the total, sold as the top product (Laptop), and Dell also holds the highest brand margin at 23.47 percent.
- **Credit Card carries the business.** Credit Card represents about 73.3 percent of all sales at the strongest margin of any method, while Cash sits lowest at 16.4 percent.
- **Overall performance.** $2.51M in total sales, $548K in total profit, a blended margin of 21.88 percent, an average order value of roughly $25,057, and an average customer rating of 4.46 out of 5.

## Key metrics

<div align="center">

<table>
<tr><th>Metric</th><th>Value</th></tr>
<tr><td>Total sales</td><td>$2.51M</td></tr>
<tr><td>Total profit</td><td>$548K</td></tr>
<tr><td>Profit margin</td><td>21.88%</td></tr>
<tr><td>Orders</td><td>100</td></tr>
<tr><td>Average order value</td><td>~$25,057</td></tr>
<tr><td>Average customer rating</td><td>4.46 / 5</td></tr>
</table>

</div>

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

## Recommendations

- **Protect the Electronics line, but reduce reliance on it.** Electronics drives about 73.6 percent of profit at the strongest margin, so it deserves priority on stock and promotion. That same concentration is a risk, so growing the healthier Furniture margin (21.15 percent) would broaden the profit base.
- **Address supplier and product concentration.** With Dell supplying about a third of all sales through a single product, the business is exposed to one vendor and one line. Securing backup suppliers and promoting the next tier of products would lower that single point of failure.
- **Convert New customers.** The New segment brings the lowest sales ($0.49M) and the lowest satisfaction (4.04 versus 4.85 for Premium). Improving onboarding and the early purchase experience is the clearest path to lifting both numbers.
- **Shift payment mix toward higher margin methods.** Cash carries the weakest margin at 16.4 percent while Credit Card leads at 22.5 percent. Encouraging card and UPI use, for example through small incentives, would support overall margin.
- **Review Grocery economics.** Grocery is the weakest category at 16.37 percent margin despite steady volume. Renegotiating sourcing or adjusting pricing would decide whether it earns its shelf space.

## Repository structure

```
Sales-Dashboard---PowerBI/
├── README.md
├── Retail Dashboard.pbix     the Power BI report file
├── Retail Dashboard-1.png    Retail Sales Dashboard page
├── Retail Dashboard-2.png    Product Analysis page
└── FACT_SALES.xlsx           source data (3 sheets)
```

## How to view

The fastest way to see this project is the screenshots above. To open the live report, download `Retail Dashboard.pbix` and open it in Power BI Desktop (free).
