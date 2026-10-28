# Superstore Retail Business Intelligence | AnalystLab Africa Week 2

**Business Intelligence & Interactive Dashboard Development**  
*Microsoft Power BI · Power Query · DAX · Data Modelling · Executive Analytics*

## Project overview

This portfolio project analyses the Sample Superstore retail transaction dataset to help management understand sales performance, profitability, customer segments, product performance and geographic differences. It was completed as a Week 2 Business Analytics case study during the AnalystLab Africa Data Analytics Internship Programme.

The report contains three pages:

1. **Executive Overview** — financial KPIs, monthly sales trend, regional profit, category revenue and customer-segment mix.
2. **Product & Regional Insights** — profitable products, sub-category profits, geographic sales and a regional/category matrix.
3. **Management Insights** — five findings, three risks, three opportunities and five recommended actions.

The `.pbix` file is an interactive Power BI Desktop project; the PDF export provides a static, shareable version.

## Key results (2014–2017)

| Metric | Result |
|---|---:|
| Sales | 2,297,200.86 |
| Profit | 286,397.02 |
| Orders (distinct Order ID) | 5,009 |
| Customers (distinct Customer ID) | 793 |
| Average sales per order line | 229.86 |
| Profit margin | 12.47% |
| Source rows | 9,994 |

**Note:** Figures are in the dataset's numerical monetary units. For this case study, the source CSV does not contain an explicit currency metadata field. The results describe a historical sample, not a current operating company.

## Business highlights

- **Profitability concentration:** Technology contributed approximately 145,455 in profit, or 50.8% of overall profit.
- **Weak margin:** Furniture generated approximately 742,000 in sales but only 18,451 in profit (2.49% margin).
- **Regional variation:** West achieved approximately 14.94% profit margin versus 7.92% in Central.
- **Discount exposure:** Order lines discounted by more than 20% produced approximately 362,770 in sales but an aggregate loss of 135,376. This is an association, not proof of causation.
- **Loss-making categories:** Tables, Bookcases and Supplies generated negative aggregate profit.

## Methods and data quality

- Imported `Sample - Superstore.csv` into Power BI using Power Query.
- Promoted headers, validated all 21 column types, interpreted US-format order and shipping dates, trimmed product names, and assessed nulls, duplicates and anomalies.
- Retained genuine outliers and negative-profit transactions for analysis.
- Modelled `FactSales` with `DimDate` through an active, single-direction, one-to-many relationship using Order Date.
- Added calendar fields including Year, Quarter, Month, and YearMonth for chronological reporting.
- Created interactive DAX measures and slicers.

### Core DAX measures

```dax
Total Sales = SUM('FactSales'[Sales])
Total Profit = SUM('FactSales'[Profit])
Total Orders = DISTINCTCOUNT('FactSales'[Order ID])
Average Sales = AVERAGE('FactSales'[Sales])
Profit Margin = DIVIDE([Total Profit], [Total Sales])
```

*The Average Sales measure represents the mean sales amount per **order line**, not average order value per distinct order.*

## Repository contents

```text
.
├── README.md
├── powerbi/
│   └── Superstore_Business_Intelligence.pbix
├── docs/
│   ├── Business_Intelligence_Overview.pdf
│   ├── Executive_Summary_and_Recommendations.pdf
│   └── Data_Quality_and_KPI_Dictionary.pdf
└── assets/
    └── (add screenshots from Power BI Desktop)
```

**Before publishing:** Add the official dashboard export (`docs/Superstore_Executive_Dashboard.pdf`) and screenshots (`assets/executive-overview.png`, `assets/product-regional-insights.png`, and `assets/management-insights.png`). These are not included in this starter because the report must first be exported and visually verified in Power BI Desktop.

## Data source and attribution

Dataset: [Superstore Dataset — Kaggle](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final). The assignment permitted this dataset. Download the source from Kaggle; the raw CSV is not redistributed in this repository starter. Check the dataset's licence and attribution requirements before uploading any raw data publicly.

## How to open

1. Download `powerbi/Superstore_Business_Intelligence.pbix`.
2. Open it with a current installation of Power BI Desktop.
3. If Power BI cannot find the CSV on refresh, update the data source path in **Transform data → Data source settings** and point it to your locally downloaded dataset.
4. Clear any report slicer selections to view full-period totals.

## Limitations

- Historical illustrative sample, not current business performance.
- Findings are descriptive; transactions do not establish causal effects of discounting.
- Product ID values are not consistently one-to-one with product names, so product rankings use Product Name.
- The Management Insights page contains a fixed full-period narrative, not slicer-driven text.

## Deliverables

The PDF dashboard, Business Intelligence overview, executive report and technical KPI dictionary are provided in `docs/` once publication is complete. The Power BI project is in `powerbi/`.

## Acknowledgement

Prepared as part of the AnalystLab Africa Data Analytics Internship Programme, Week 2 Business Analytics Case Study.
