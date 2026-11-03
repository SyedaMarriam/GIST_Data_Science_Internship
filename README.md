# GIST_Data_Science_Internship Project

## 1. Project Overview

This project examines an e-commerce order-item dataset through data cleaning, exploratory data analysis (EDA), and an existing Power BI dashboard. Task 1 and Task 2 are provided as separate Jupyter notebooks. The existing Power BI file is preserved as Task 4.

**Task 3, prediction, was intentionally skipped.** This project contains no predictive model, model evaluation, or prediction results.

## 2. Project Objectives

- Check the source data for missing values, placeholders, duplicates, and unusual numeric values.
- Create a cleaned dataset without guessing missing information or discarding potentially valid transactions.
- Explore sales, order, product category, payment, and time patterns using clear summaries and charts.
- Preserve and review the existing Power BI dashboard without replacing its design.
- Document evidence-based findings and limitations in a reproducible project structure.

## 3. Project Scope

The project covers:

- **Task 1:** Basic data cleaning and exploration.
- **Task 2:** Exploratory analysis of relationships, trends, and business patterns.
- **Task 4:** Review of the existing interactive Power BI dashboard.

The analysis is descriptive. It does not estimate future outcomes or establish that observed relationships are causal.

## 4. Dataset Description

The source file, `Dataset/Original_Dataset.csv`, contains **584,524 order-item rows** and **21 columns**. Fields include item and order identifiers, status, date, SKU, price, quantity, order total, product category, discount, payment method, and customer ID.

The recorded dates run from **July 1, 2016, through August 28, 2018**. The first and last calendar years are partial. The source does not identify a currency, so monetary amounts in the notebooks and this README are described as *dataset units*.

The dataset includes:

- `Not provided` placeholders in `sales_commission_code`.
- One `#REF!` spreadsheet error in `BI Status`.
- 11 missing `Customer ID` values.
- Very large and some negative values in numeric fields. These are flagged for review, not assumed to be errors.

The cleaned output is `Dataset/Cleaned_Dataset.csv`. It retains the original rows while converting the known text placeholders to missing values.

## 5. Tools and Technologies Used

- Python
- Jupyter Notebook
- Pandas and NumPy
- Matplotlib and Seaborn
- Power BI Desktop (to open and interact with the existing `.pbix` file)

Power BI is not a Python dependency.

## 6. Project Folder Structure

```text
GIST_Data_Science_Internship/
├── README.md
├── requirements.txt
├── Dataset/
│   ├── Original_Dataset.csv
│   └── Cleaned_Dataset.csv
├── Task_1/
│   └── Task_1.ipynb
├── Task_2/
│   └── Task_2.ipynb
└── Task_4/
    └── PowerBI_Dashboard.pbix
```


## 7. Task 1 — Data Cleaning & Exploration

Notebook: [`Task_1/Task_1.ipynb`](Task_1/Task_1.ipynb)

Task 1 reads the original CSV and:

1. Reviews its dimensions, columns, data types, and numeric summaries.
2. Separately counts source nulls and known text placeholders before cleaning.
3. Converts `Not provided` and `#REF!` to missing values. Missing IDs and other unknown values are left blank rather than filled with guesses.
4. Checks for exact duplicate rows. No exact duplicate rows were found, so no rows were removed.
5. Uses the IQR rule and boxplots to flag unusual `price`, `qty_ordered`, `grand_total`, and `discount_amount` values. The flagged rows are retained because an extreme transaction may be genuine.
6. Summarizes the main numeric fields and plots their distributions and the most common product categories.
7. Saves the result to `Dataset/Cleaned_Dataset.csv` for Task 2.

After placeholder standardization, the cleaned data has **476,191 missing cells**: 476,179 in `sales_commission_code`, one in `BI Status`, and 11 in `Customer ID`. Missing commission codes make up **81.464%** of that column. The IQR review flags records for follow-up; it does not automatically classify them as errors.

## 8. Task 2 — Exploratory Data Analysis

Notebook: [`Task_2/Task_2.ipynb`](Task_2/Task_2.ipynb)

Task 2 uses the cleaned output from Task 1 and focuses on business analysis rather than repeating the cleaning workflow. It explores:

- Yearly and monthly sales trends.
- Fulfilled item sales by product category and SKU.
- Payment method and order status, counting each order once for order-level comparisons.
- The relationship between price and quantity, including a reproducible sample scatter plot.
- Correlations among price, quantity, discounts, and calculated item sales.

For notebook sales comparisons, item sales are calculated as `price × qty_ordered − discount_amount`. The notebook defines fulfilled orders as those with `complete` or `received` status. These are the analysis definitions used in this project, not verified accounting measures. The source includes multiple item rows per order, so the notebook avoids summing `grand_total` for its item-level sales analysis.


## 9. Task 4 — Interactive Power BI Dashboard

Dashboard: [`Task_4/PowerBI_Dashboard.pbix`](Task_4/PowerBI_Dashboard.pbix)

The existing one-page dashboard is preserved. Its report definition includes:

- **KPI cards:** Total Sales, Total Orders, Total Customers, Discount, Completed, and Cancelled.
- **Charts:** Sales by Product Category, Monthly Customer Distribution, Order Distribution by Status, and Monthly Sales Trend.
- **Slicers:** Year and Discount Status.
- A report heading, **E_COMMERCE SALES ANALYTICS**.

The layout places the heading and slicers above the KPI cards, with charts arranged below on a wide, single-page canvas. The visual definitions use a consistent navy, blue, and muted-gray palette. The report metadata shows that the category chart aggregates `grand_total` by category, while the monthly sales trend sums the `sales` field over a date hierarchy. The visuals also reference measures named `Total Orders`, `Total Customers`, `complete orders`, and `cancel orders`. Their DAX definitions and the dashboard's displayed values could not be verified from the report definition alone; inspect them in Power BI Desktop before relying on them.

### Dashboard review recommendations

- **Check category sales aggregation:** the source is at order-item level and `grand_total` can repeat across items in an order. Confirm that summing it does not double-count order totals. Consider an item-level sales calculation or an order-level distinct total, with the chosen definition stated in the chart title or tooltip.
- **Clarify the sales definition:** identify which statuses are included and whether the value is item sales, order total, gross sales, or another measure.
- **Label units:** the dataset does not name a currency. Format cards and axes with an explicit unit or note rather than implying a currency.
- **Verify card and slicer behavior:** inspect the DAX and test that Year and Discount Status filters affect the intended cards and charts.
- **Keep labels consistent:** make sure the displayed KPI titles clearly match their measure definitions and use consistent number formatting. Preserve the existing navy-and-blue palette as visuals are updated.

These are recommendations only. The `.pbix` file was not edited, and the dashboard should be opened in Power BI Desktop for visual and DAX validation.

## 10. Methodology

1. Preserve the original CSV and inspect its shape, columns, and data types.
2. Standardize only known missing-value placeholders; do not infer missing identifiers or statuses.
3. Check exact duplicates and flag outliers for review without automatic removal.
4. Save the cleaned dataset and use it as the input to Task 2.
5. Define order-item sales and fulfilled statuses explicitly before comparing results.
6. Use item-level calculations for item sales and unique order IDs for order-level counts.
7. Interpret trends within the available date range and report observations as descriptive findings.

## 11. Key Findings and Insights

The following findings come from the Task 2 notebook and use its stated definitions:

- The dataset has **408,782 unique orders**; **205,321** have `complete` or `received` status.
- Fulfilled item sales total approximately **1,216,863,948 dataset units**.
- **Mobiles & Tablets** is the largest fulfilled-sales category, at approximately **583,508,701 dataset units** (**47.95%** of fulfilled item sales).
- **Cash on delivery** is the most common payment method, used for **182,449 unique orders** (about **44.6%**).
- **148,656 unique orders** are marked canceled (about **36.4%**).
- **November 2017** is the highest fulfilled-sales month, at approximately **302,551,730 dataset units**.
- The price-to-quantity correlation among fulfilled rows is approximately **−0.019**, indicating little linear association in this dataset. Correlations with calculated item sales are partly expected because price, quantity, and discount are inputs to that calculation.

These are patterns in the available records, not proof of cause or profitability.

## 12. Dashboard Features

The existing dashboard combines summary cards, category and time charts, a status distribution, and Year and Discount Status slicers on one report page. See [Task 4](#10-task-4--interactive-power-bi-dashboard) for the visual inventory and specific review recommendations.

## 13. How to Install and Run the Project

The notebooks use paths relative to their task folders. Start Jupyter from the relevant folder so the CSV paths resolve as written.

### Set up Python and Jupyter (PowerShell)

From the project root:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt jupyter ipykernel
```

### Run Task 1

```powershell
Set-Location Task_1
python -m jupyter notebook Task_1.ipynb
```

Run the notebook from top to bottom. This reads `Dataset/Original_Dataset.csv` and writes `Dataset/Cleaned_Dataset.csv`.

### Run Task 2

After Task 1 has completed successfully, open a new terminal at the project root (or stop the first Jupyter server) and run:

```powershell
Set-Location Task_2
python -m jupyter notebook Task_2.ipynb
```

Run the notebook from top to bottom. It reads `Dataset/Cleaned_Dataset.csv`.

### Open the dashboard

Open `Task_4/PowerBI_Dashboard.pbix` in Power BI Desktop. Power BI Desktop is installed separately and is not included in the Python requirements.

## 14. Required Python Libraries

The notebooks import these Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

Jupyter and `ipykernel` are notebook-running tools and are installed alongside the requirements in the setup commands above.

## 15. Project Outcomes

- A documented cleaned copy of the supplied dataset, with the original retained.
- Separate notebooks for data cleaning and descriptive EDA.
- Reproducible charts and findings based on the provided data.
- The existing Power BI dashboard retained under Task 4, with review recommendations documented.
- A clear record that prediction was intentionally skipped.

## 16. Limitations

- The dataset covers partial years at the beginning and end of the date range.
- No currency is identified, and product costs are not available; sales values cannot be interpreted as profit.
- Some source statuses and fields are unusual or incomplete. Placeholder standardization does not recover the true missing values.
- IQR flags identify statistical extremes, not confirmed data errors.
- The notebook's fulfilled-sales formula and status definition are analysis choices; they may differ from the dashboard's measures or accounting definitions.
- The Power BI report's DAX formulas and interactive behavior were not verified in Power BI Desktop.
- Task 3 prediction was not implemented, as intended.

## 19. Future Improvements

- Validate the dashboard's DAX measures and filter interactions in Power BI Desktop.
- Confirm the business definitions for sales, completed orders, discounts, and cancellations with the data owner.
- Add data-quality checks for inconsistent order-level values and date parsing.
- Compare equivalent time periods when evaluating seasonal changes.
- Add product cost, margin, and return information if profitability analysis is required.

## 20. Conclusion

This project provides a transparent workflow from data cleaning to exploratory business analysis and a review of the existing dashboard. Missing information and unusual values are documented rather than guessed away, and the notebook sales and order-count definitions are stated so the findings can be explained and reproduced. Task 3 remains intentionally skipped; no predictive results are presented.
