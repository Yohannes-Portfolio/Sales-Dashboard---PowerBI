# Sales Performance Dashboard (Power BI)

An interactive sales analytics dashboard built in Power BI on a transactional sales fact table, covering revenue, profitability, payment behaviour, product performance, and customer satisfaction.

> Note on currency: figures are shown in the unit recorded in the source data (assumed Indian Rupees, INR). Update the symbol if this is incorrect.

## Business question

Which products, payment methods, and periods drive revenue and profit, and where is margin being won or lost across the order base?

## Dataset

A single sales fact table (`FACT_SALES.xlsx`) of 100 order level rows spanning 1 January to 10 April 2025, with 20 distinct customers and 10 products.

| Field | Description |
| --- | --- |
| OrderID | Unique order identifier |
| OrderDate | Date of the order |
| CustomerID | Customer identifier (20 unique) |
| ProductID | Product identifier (10 unique) |
| Quantity | Units sold on the order |
| Discount% | Discount applied to the order |
| Sales | Order revenue |
| Profit | Order profit |
| PaymentMethod | Credit Card, UPI, Cash, or Debit Card |
| CustomerRating | Order satisfaction score, 1 to 5 |

## Tools

Power BI Desktop for the data model, DAX measures, and report pages. Source data prepared in Excel.

## Headline findings

- **Credit Card carries the business.** 50 of 100 orders run through Credit Card, generating roughly 1.84M in sales (about 73 percent of total revenue) at the strongest margin of any method, 22.5 percent. Cash sits lowest at 16.4 percent margin.
- **Revenue is concentrated in a few high value products.** Product P001 alone drove 836,000 in sales (about a third of total revenue) from only 16 units, at a 23.5 percent margin. By contrast the cheap high volume lines such as P009 (84 units sold) returned the weakest margins near 16 percent.
- **Customer satisfaction is high.** Average rating of 4.46 out of 5, with 52 orders rated 5 and none rated below 3.
- **Overall performance.** 2,505,670 in total sales, 548,350 in total profit, a blended margin of 21.9 percent, and an average order value of roughly 25,057.

## Key metrics

| Metric | Value |
| --- | --- |
| Total sales | 2,505,670 |
| Total profit | 548,350 |
| Overall margin | 21.9% |
| Orders | 100 |
| Average order value | ~25,057 |
| Average customer rating | 4.46 / 5 |

### Sales and margin by payment method

| Payment method | Orders | Sales | Margin |
| --- | --- | --- | --- |
| Credit Card | 50 | 1,835,410 | 22.5% |
| UPI | 21 | 466,660 | 21.2% |
| Cash | 16 | 105,700 | 16.4% |
| Debit Card | 13 | 97,900 | 19.9% |

## Dashboard pages

<!--
Fill this section in with what your report actually shows. For each page,
name it, say what question it answers, and list the visuals on it.
Example structure below, replace with your own.
-->

**Page 1 (overview):** _describe the KPIs and visuals here_

**Page 2 (...):** _describe here_

## Screenshots

<!-- Export each report page as a PNG into the images folder and embed it here. -->

![Dashboard overview](images/overview.png)

## Repository structure

```
sales_dashboard_powerbi/
├── README.md
├── images/        screenshots of each dashboard page
├── dashboard/      the .pbix file
└── data/           FACT_SALES.xlsx
```

## How to view

The fastest way to see this project is the screenshots above. To open the live report, download the `.pbix` file from the `dashboard` folder and open it in Power BI Desktop (free).
