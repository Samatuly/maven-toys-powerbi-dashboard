# Maven Toys Sales Dashboard (Power BI)

Interactive Power BI dashboard for **Maven Toys**, a chain of 50 toy stores in Mexico: where the business makes
money, which products and locations drive profit, and which items are about to run out of stock.

> 🚧 Work in progress — the dashboard and screenshots will be added stage by stage.

> **Note:** Maven Toys is a fictitious company. The data comes from the
> [Maven Analytics Data Playground](https://mavenanalytics.io/data-playground?search=Mexico%20Toy%20Sales) and is
> intended for learning and portfolio projects.

## Business questions

1. How do revenue, profit and margin change by month and versus the previous year?
2. Which categories and products bring the most profit, and which sell a lot at a low margin?
3. Which stores and location types (Downtown, Commercial, Residential, Airport) perform best?
4. How much money is tied up in inventory, and which products are at risk of running out?

## Tools

Power BI Desktop (Power Query, DAX, star-schema data model) · Python / pandas for data validation

## Data

| Table | Rows | Grain |
| --- | --- | --- |
| sales | 829,262 | one sale (date, store, product, units) |
| products | 35 | product with category, cost and price |
| stores | 50 | store with city, location type and open date |
| inventory | 1,593 | stock on hand per store + product (snapshot) |

Period: **Jan 2022 – Sep 2023** (2023 is a partial year, so year-over-year comparisons use the same months).

## Control figures (stage 1)

Calculated in `notebooks/01_data_check.ipynb`; every Power BI measure is checked against them.

| Metric | Value |
| --- | --- |
| Revenue | $14,444,572 |
| Profit | $4,014,029 |
| Margin | 27.8% |
| Units sold | 1,090,565 |
| Revenue growth, Jan–Sep 2023 vs. 2022 | +30.9% |
| Stock value at cost | $300,210 |
| Out-of-stock store + product pairs | 77 |

## Project structure

```
maven-toys-powerbi-dashboard/
├── data/raw/                 # 4 source CSV files (not tracked by Git)
├── notebooks/
│   └── 01_data_check.ipynb   # data quality checks and control figures
├── powerbi/                  # maven_toys.pbix
├── dax/                      # measures.md: every DAX measure with an explanation
├── docs/
│   ├── build_guide.md        # step-by-step build instructions
│   └── screenshots/          # dashboard pages used in this README
└── requirements.txt
```

## How to open

1. Download *Mexico Toy Sales* from the [Maven Analytics Data Playground](https://mavenanalytics.io/data-playground?search=Mexico%20Toy%20Sales)
   and unzip the CSV files into `data/raw/`.
2. Open `powerbi/maven_toys.pbix` in Power BI Desktop (free, Windows).
3. If Power BI asks for the data location: **Transform data → Data source settings** and point it to your `data/raw/` folder.
