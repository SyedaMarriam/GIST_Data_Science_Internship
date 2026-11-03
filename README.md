# E-commerce Data Science Internship Project

## Project Overview

This project explores an e-commerce order-item dataset through basic data cleaning, exploratory data analysis, and a Power BI report. Task 1 and Task 2 are provided as separate Jupyter notebooks. Task 3 is provided as a Power BI report file.

The project focuses on understanding the supplied data and describing observed patterns. The files inspected do not include a separate predictive-model notebook or prediction code, so no prediction results are claimed.

## Project Objectives

- Inspect and prepare the supplied dataset for analysis.
- Summarize numerical and categorical fields.
- Explore sales, order, category, payment, and time patterns.
- Present additional analysis in the included Power BI report.

## Dataset Description

The source file is `Task_1/dataset.csv`. It contains 584,524 order-item records and 21 columns, including order status, creation date, product SKU, price, quantity, order total, category, discount, payment method, and customer ID.

The dataset covers July 2016 through August 2018. Some fields contain missing or placeholder values, which are documented in Task 1. The notebook saves its prepared data as `Task_1/Cleaned_Data.csv`; Task 2 loads that file.

## Tools and Technologies Used

- Python
- Jupyter Notebook
- Pandas and NumPy
- Matplotlib and Seaborn
- Power BI Desktop for the `.pbix` report

## Project Folder Structure

```text
GIST_Data_Science_Internship/
├── README.md
├── Task_1/
│   ├── Task_1.ipynb
│   ├── dataset.csv
│   └── Cleaned_Data.csv
├── Task_2/
│   └── Task_2.ipynb
└── Task_3/
    └── Ecommerce.pbix
```

## Task 1 — Data Cleaning & Exploration

Notebook: `Task_1/Task_1.ipynb`

Task 1 uses the original CSV to:

- Review the dataset structure, column types, and summary statistics.
- Identify missing values and standardize the `Not provided` and `#REF!` placeholders as missing.
- Check for exact duplicate records. No exact duplicate rows were found.
- Flag potential outliers in selected numeric columns with the IQR method and boxplots. The flagged rows were retained rather than removed automatically.
- Create basic missing-value, histogram, boxplot, and category-count visualizations.
- Save the resulting dataset to `Task_1/Cleaned_Data.csv`.

## Task 2 — Exploratory Data Analysis (EDA)

Notebook: `Task_2/Task_2.ipynb`

Task 2 loads the cleaned CSV and explores:

- Numerical and categorical variables.
- Monthly and yearly fulfilled item sales.
- Sales by category and top products.
- Payment method and order status counts.
- Price and quantity patterns, along with a correlation heatmap.

For its sales analysis, the notebook calculates item sales as `price × quantity − discount` and uses orders with `complete` or `received` status. It counts unique order IDs for order-level comparisons, avoiding repeated counts for multi-item orders. These are analysis definitions used in the notebook, not a separate accounting measure.

## Task 3 — Data Analysis (Power BI)

The `Task_3` folder contains `Ecommerce.pbix`, a Power BI report. Its report definition includes category and order-status visuals, a line chart, summary cards, and slicers.

No separate predictive-model code, prediction results, or model accuracy measures were present in the inspected project files. This README therefore describes Task 3 as a Power BI analysis report and does not claim that a predictive model was implemented.

## Key Findings and Insights

The following figures come from the Task 2 notebook and use its stated sales and order-count definitions:

- The dataset contains **408,782 unique orders**; **205,321** are marked `complete` or `received`.
- Fulfilled item sales total approximately **1,216,863,948** in the dataset's amount units. The dataset does not identify a currency in the notebook.
- **Mobiles & Tablets** is the largest fulfilled-sales category, at approximately **583,508,701** (about **48.0%** of fulfilled item sales).
- **Cash on delivery** is the most common payment method, used for **182,449 orders** (about **44.6%** of unique orders).
- There are **148,656 canceled orders**, approximately **36.4%** of unique orders.
- **November 2017** is the highest fulfilled-sales month in the available period, at approximately **302,551,730**. The first and last years in the dataset are partial years.

## How to Run the Project

### 1. Install Python libraries

Open a terminal in the main project folder and install the required packages:

```bash
pip install pandas numpy matplotlib seaborn jupyter ipykernel
```

### 2. Run Task 1

Run Jupyter from the Task 1 folder so the notebook can find `dataset.csv` using its relative path:

```bash
cd Task_1
jupyter notebook Task_1.ipynb
```

In the browser, open `Task_1.ipynb` if it is not already open, then choose **Kernel → Restart & Run All** (or **Run All**). This runs the notebook from top to bottom and creates `Cleaned_Data.csv` in the same folder.

### 3. Run Task 2

After Task 1 finishes successfully, stop its Jupyter server if needed. From the main project folder, start Jupyter in the Task 2 folder:

```bash
cd Task_2
jupyter notebook Task_2.ipynb
```

Run all cells from top to bottom. Task 2 reads `../Task_1/Cleaned_Data.csv`, so Task 1 must be run first.

### 4. Open the Task 3 report

Open `Task_3/Ecommerce.pbix` using Power BI Desktop to view the report.

## Required Python Libraries

The notebooks use:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

Jupyter Notebook and `ipykernel` are also needed to run the notebooks in the described setup.

## Conclusion

This project documents a practical workflow from checking and preparing an existing dataset to exploring its business patterns and viewing a Power BI report. The notebooks preserve unusual records where their validity is uncertain and explain the definitions used for sales and order comparisons. The findings describe the available data and should be considered alongside its partial date range and other data limitations.
