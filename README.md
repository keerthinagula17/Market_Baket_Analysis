# Market Basket Analysis

## Internship Project — Data Analyst

### Project Overview
This project analyzes real transaction data from the **Online Retail** dataset published by the UCI Machine Learning Repository. The analysis combines exploratory data analysis with Market Basket Analysis using the Apriori algorithm and association rules. The final outputs are designed for Python/Jupyter and Power BI.

> **Dataset source:** UCI Machine Learning Repository, Online Retail, Chen (2015), DOI 10.24432/C5BW33. The dataset contains 541,909 transaction-line records from 01/12/2010 to 09/12/2011 for a UK-based non-store online retailer. It is licensed CC BY 4.0.

## Problem Statement
Retail transaction data contains valuable information about what customers purchase together. The objective is to identify high-frequency products, purchasing patterns, and strong product associations that can support bundling, cross-selling, merchandising, and inventory decisions.

## Objectives
- Understand transaction-level retail data and data quality.
- Clean cancellations, returns, missing values, duplicates, and invalid prices/quantities.
- Analyze products, countries, revenue, transaction trends, and basket size.
- Build a transaction-item matrix using one-hot encoding.
- Discover frequent itemsets using Apriori.
- Generate association rules using support, confidence, and lift.
- Produce dashboard-ready outputs for Power BI.

## Dataset
The official dataset is distributed by UCI as `Online Retail.xlsx`. The notebook automatically downloads the official ZIP from:

`https://archive.ics.uci.edu/static/public/352/online+retail.zip`

If automatic download is unavailable, download the official file manually from the UCI Online Retail dataset page and place the converted CSV at:

`data/Online_Retail.csv`

The CSV must contain: `InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country`.

## Technologies
Python, Pandas, NumPy, Matplotlib, Seaborn, mlxtend, Jupyter Notebook and Power BI.

## Methodology
1. Load the official Online Retail data.
2. Inspect shape, columns, data types, missing values and duplicates.
3. Remove cancelled invoices, non-positive quantities/prices, blank product descriptions and records without CustomerID for customer/basket analysis.
4. Create `Revenue = Quantity × UnitPrice`.
5. Perform EDA for products, countries, revenue and time.
6. Aggregate products by invoice to form baskets.
7. One-hot encode product presence/absence.
8. Apply Apriori with a configurable minimum support.
9. Generate association rules with configurable minimum confidence/lift.
10. Export frequent itemsets and rules as CSV.
11. Use the CSV outputs in Power BI.

## EDA
The notebook includes:
- Missing-value and duplicate checks
- Cancellation/return analysis
- Top products by quantity and revenue
- Top countries by revenue
- Monthly revenue trend
- Basket-size distribution
- Transaction counts and average order value

## Market Basket Analysis
For a basket of products, **support** measures how often an itemset appears in all baskets. **Confidence** measures how often the consequent appears when the antecedent appears. **Lift** compares the observed co-occurrence with the expected co-occurrence if the items were independent.

The notebook uses `mlxtend.frequent_patterns.apriori` and `association_rules`. Parameters are deliberately kept configurable because support/confidence thresholds affect the number of discovered patterns.

## Results
The repository includes CSV output examples based on published analyses of this same UCI Online Retail dataset. The notebook is the authoritative reproducible pipeline: running all cells with the official dataset recalculates the outputs using the project thresholds and overwrites the CSV files.

Examples reported in public analyses of this dataset include strong associations among Regency Teacup products and related Jumbo Bag products. Exact values depend on preprocessing, country selection, minimum support, and confidence thresholds.

## Business Insights
- Frequently co-purchased products can be promoted as bundles.
- High-lift relationships can support cross-selling recommendations.
- Product-level demand supports inventory planning.
- Country-level revenue highlights geographic concentration and expansion opportunities.
- Monthly trends help identify seasonality and operational peaks.
- Basket-size analysis helps understand typical order composition.

## Power BI Dashboard
Import the notebook-generated CSV outputs and create KPI cards, product/country charts, a monthly trend line, basket-size visuals, and a Market Basket table containing antecedent, consequent, support, confidence and lift. See `dashboard/PowerBI_Dashboard_Guide.md` for exact setup steps.

## Installation
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
# source .venv/bin/activate

pip install -r requirements.txt
```

## Execution
1. Open `Market_Basket_Analysis.ipynb` in Jupyter Notebook or VS Code.
2. Run all cells.
3. If `data/Online_Retail.csv` is missing, the notebook attempts to download the official UCI ZIP and convert `Online Retail.xlsx` to CSV.
4. If the environment blocks downloads, manually place the official CSV at `data/Online_Retail.csv`.
5. The notebook writes `outputs/frequent_itemsets.csv` and `outputs/association_rules.csv`.

## Project Structure
```text
Market_Basket_Analysis/
├── data/
│   └── Online_Retail.csv
├── Market_Basket_Analysis.ipynb
├── README.md
├── requirements.txt
├── outputs/
│   ├── frequent_itemsets.csv
│   └── association_rules.csv
└── dashboard/
    └── PowerBI_Dashboard_Guide.md
```

## Future Scope
- Build a recommendation engine from association rules.
- Compare rules across countries and customer segments.
- Add time-aware association analysis.
- Combine market basket analysis with RFM segmentation.
- Deploy the recommendation logic as an API or business application.

## Dataset Citation
Chen, D. (2015). *Online Retail* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5BW33.

Dataset license: Creative Commons Attribution 4.0 International (CC BY 4.0).
