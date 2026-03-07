# Supply Chain Performance Dashboard
### Power BI Analytics Project

---

## Project Overview

This Power BI report analyzes global supply chain performance across multiple countries and product categories. The dashboard covers order fulfillment, sales trends, profit margins, and category-level performance based on transactional data from 2015 to 2018.

---

## Dashboard Pages

### Page 1 — Supply Chain Performance Dashboard
Interactive executive dashboard with KPI cards (Total Orders, Total Quantity Sold, Total Sales, Profit Margin %), filterable by country and year. Includes Sales by Order Month, Top 10 Products by Average Price, Top 10 Products by Sales, and Orders by Status.


### Page 2 — Category & Geographic Analysis
Global sales map, Profit and Sales by Category, Order Item Quantity by Category, and Total Sales trend by Month and Year (2015–2017).


### Page 3 — Recommendations & Business Insights
Data-driven key insights, business risks, and actionable recommendations based on full-year 2015–2017 data.


---

## ⚠️ Important Data Quality Note — 2018 Dataset

During analysis, a significant data quality issue was identified with the 2018 records:

**Finding:**
- 2018 data contains **only January transactions**
- Records are limited exclusively to **Asia-Pacific countries** (Afghanistan, Australia, Bangladesh, Cambodia, China, South Korea, Philippines, Hong Kong, India, Indonesia, Japan, Laos, Malaysia, Myanmar, Pakistan, Papua New Guinea, Singapore, Sri Lanka, Thailand, Vietnam)
- No records exist for USA, Europe, Latin America, or Africa in 2018
- Total 2018 sales amount to only **$331.65K** compared to **~$12.3M** in previous full years

**Investigation Steps Taken:**
1. Checked order count for 2018 → 2,123 orders confirmed (not negligible)
2. Checked months available in 2018 → Only January present
3. Checked countries available in 2018 → Only Asia-Pacific region
4. Compared average order value across years → Significantly lower in 2018

**Conclusion:**
The 2018 dataset was most likely **exported or collected mid-January 2018**, capturing only the Asia-Pacific region before data collection stopped. This is a data pipeline/collection issue, not a business disruption or supply chain failure. The healthy **10.20% profit margin** in January 2018 further confirms normal business operations at the time.

**Impact on Analysis:**
All trend analysis, KPIs, and recommendations in this report are based on **complete full-year data from 2015–2017** to ensure analytical accuracy. The 2018 filter remains available in the dashboard for transparency but should not be used for year-over-year comparisons.

---

## Key Findings

- **USA** is the top performing market at $4.88M in sales with an 11.07% profit margin
- **USA demand is seasonal** — peaking April through August, driven by outdoor and sports products
- **Fishing ($6.9M)** leads globally in total sales by category
- **Cleats** generate the highest order quantity globally
- Sales remained stable from 2015–2017, averaging ~$1M per month

---

## Data Modeling & Transformation

The raw dataset (**DataCoSupplyChainDataset**) was provided as a **flat CSV file** and transformed into a structured **Star Schema** before building the dashboard.

**Schema Design:**
```
Flat CSV → Star Schema (5 Tables)

📊 Fact Table:
└── Order_details     — core transactional data (sales, profit, quantity, order status)

📋 Dimension Tables:
├── Customer_details  — customer information
├── Product_details   — product & category information
└── Date_details      — date & time intelligence
```

**Steps Performed:**
1. Loaded flat CSV (DataCoSupplyChainDataset) into Power BI Power Query
2. Identified and separated dimensions from facts
3. Created relationships between fact and dimension tables
4. Performed data cleaning, type formatting and column renaming
5. Built DAX measures on top of the star schema for KPIs and analysis

---

## Tools Used
- Microsoft Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query

---

## Skills Demonstrated
- Data Modeling (Star Schema)
- DAX Measures & KPI Design
- Power Query Data Transformation
- Interactive Dashboard Design
- Supply Chain Performance Analysis
- Data Quality Investigation

---

## License
This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Notes for Reviewers
- Use the **Order Country** and **Order Year** slicers on Page 1 to explore market-specific performance
- Avoid selecting **2018** in isolation for comparative analysis due to the data quality issue documented above
- All monetary values are in **USD**
