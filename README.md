# GIST Data Science Internship Project

## 1. Project Overview

This project focuses on analyzing an e-commerce order-item dataset through data cleaning, exploratory data analysis (EDA), and interactive Power BI visualization.

The project includes separate Jupyter notebooks for data cleaning and exploratory analysis, along with an interactive Power BI dashboard for presenting business insights.

The main objective is to transform raw data into meaningful information and identify useful patterns related to sales, orders, customers, products, and payment methods.

## 2. Project Objectives

- Inspect and clean the original dataset.
- Identify missing values, placeholders, duplicates, and unusual numeric values.
- Perform exploratory data analysis using Python.
- Analyze sales, orders, product categories, payment methods, and monthly trends.
- Create meaningful charts and statistical summaries.
- Present key business metrics through an interactive Power BI dashboard.
- Document the complete workflow and findings.

## 3. Project Scope

The project covers three main areas:

- **Task 1:** Basic Data Cleaning and Exploration.
- **Task 2:** Exploratory Data Analysis (EDA).
- **Task 4:** Interactive Power BI Dashboard.

The analysis is descriptive and focuses on understanding historical business data and identifying trends.

## 4. Dataset Description

The original dataset, `Dataset/Original_Dataset.csv`, contains **584,524 order-item rows and 21 columns**.

The dataset includes information about:

- Order and item identifiers
- Order status and dates
- Product SKU and category
- Product prices and quantities
- Grand total and discounts
- Payment methods
- Customer IDs

The recorded dates range from **July 1, 2016, to August 28, 2018**.

### Data Quality Observations

- `Not provided` placeholders in `sales_commission_code`.
- One `#REF!` spreadsheet error in `BI Status`.
- 11 missing values in `Customer ID`.
- Some unusually large and negative numeric values.

These values were reviewed and documented rather than automatically removed.

The cleaned dataset is saved as `Dataset/Cleaned_Dataset.csv`.

It retains all original rows while standardizing known text placeholders as missing values.

**Note:** The dataset does not specify a currency. Therefore, monetary values are represented as dataset units.

## 5. Tools and Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Power BI Desktop

## 6. Project Folder Structure

```text
GIST_Data_Science_Internship/
│
├── Dataset/
│   ├── Original_Dataset.csv
│   └── Cleaned_Dataset.csv
│
├── Task_1/
│   └── Task_1.ipynb
│
├── Task_2/
│   └── Task_2.ipynb
│
├── Task_4/
│   └── PowerBI_Dashboard.pbix
│
├── README.md
└── requirements.txt
```

## 7. Task 1 — Data Cleaning and Exploration

**Notebook:** `Task_1/Task_1.ipynb`

This task focuses on understanding and preparing the original dataset.

### Activities Performed

1. Examined dataset dimensions, columns, and data types.
2. Identified missing values and text placeholders.
3. Standardized `Not provided` and `#REF!` values.
4. Checked exact duplicate records.
5. Applied the IQR method to identify unusual numeric values.
6. Created boxplots and distribution charts.
7. Analyzed important numerical fields and product categories.
8. Exported the cleaned dataset for further analysis.

### Results

- Original records: 584,524.
- Exact duplicate rows found: 0.
- Missing cells after placeholder standardization: 476,191.
- Missing commission codes represent approximately 81.464% of that column.

Unusual numeric values were flagged for review rather than automatically deleted.

## 8. Task 2 — Exploratory Data Analysis (EDA)

**Notebook:** `Task_2/Task_2.ipynb`

This task explores business patterns and relationships in the cleaned dataset.

### Analysis Performed

- Yearly and monthly sales trends.
- Sales distribution across product categories.
- Top-performing products and SKUs.
- Payment method analysis.
- Order status distribution.
- Relationship between product price and quantity.
- Correlation analysis among numerical variables.

For item-level analysis, sales were calculated using:

`Item Sales = (Price × Quantity Ordered) − Discount Amount`

Fulfilled orders were defined as orders with `complete` or `received` status.

### Key Results

- Total unique orders: 408,782.
- Fulfilled unique orders: 205,321.
- Fulfilled item sales: approximately 1,216,863,948 dataset units.
- Mobiles & Tablets contributed approximately 583,508,701 dataset units.
- Cash on Delivery was the most frequently used payment method, with 182,449 unique orders.
- Canceled orders: 148,656.
- November 2017 recorded the highest fulfilled item sales, approximately 302,551,730 dataset units.

These results describe patterns in the available dataset and do not establish causation or profitability.

## 9. Task 4 — Interactive Power BI Dashboard

**Dashboard:** `Task_4/PowerBI_Dashboard.pbix`

An interactive Power BI dashboard was used to present important e-commerce business metrics and visual insights.

**Data Scope:** The Power BI dashboard analysis was performed on a selected sample of **1,000 rows** from the original dataset. Therefore, dashboard results represent a sample-based analysis rather than the complete 584,524-row dataset.

### Dashboard Components

**KPI Cards**
- Total Sales
- Total Orders
- Total Customers
- Discount
- Completed Orders
- Cancelled Orders

**Visualizations**
- Sales by Product Category
- Monthly Customer Distribution
- Order Distribution by Status
- Monthly Sales Trend

**Interactive Filters**
- Year
- Discount Status

### Dashboard Design

- Professional single-page layout.
- Navy blue, blue, and muted-gray color palette.
- KPI cards positioned at the top.
- Charts arranged below the summary metrics.
- Interactive slicers for filtering the report.

The existing Power BI dashboard file is preserved.

### Dashboard Review

- Verify sales calculations to avoid double-counting repeated order totals.
- Check the definitions of completed and cancelled orders.
- Validate DAX measures in Power BI Desktop.
- Confirm that slicers filter the intended visuals.
- Clearly identify monetary values as dataset units because the currency is unspecified.
- Remember that dashboard results are based on the selected 1,000-row sample.

## 10. Methodology

The project follows a structured data analysis workflow:

1. Load and inspect the original dataset.
2. Identify missing values and placeholders.
3. Clean known placeholder values.
4. Check duplicate records and unusual numeric values.
5. Save the cleaned dataset.
6. Perform exploratory analysis using Python.
7. Generate charts and statistical summaries.
8. Present business metrics through Power BI.
9. Document findings and limitations.

## 11. Key Findings and Insights

The exploratory analysis identified several important patterns:

- The dataset contains 408,782 unique orders.
- Approximately 205,321 unique orders are classified as fulfilled.
- Mobiles & Tablets is the largest fulfilled-sales category.
- Cash on Delivery is the most common payment method.
- Approximately 36.4% of unique orders are marked as cancelled.
- November 2017 recorded the highest fulfilled item sales.
- The price-to-quantity correlation among fulfilled rows is approximately -0.019, indicating very little linear association.

These insights help describe historical e-commerce activity and customer purchasing patterns.

## 12. Installation and Environment Setup

### Prerequisites

Install the following software before running the project:

- **Python 3:** Required for data cleaning and analysis.
- **Jupyter Notebook:** Required to run the Python notebooks.
- **Power BI Desktop:** Required to open and interact with the dashboard.
- **Visual Studio Code (Optional):** Can be used to manage the project files and notebooks.

### Step 1: Install Python

1. Visit the official Python website: https://www.python.org/downloads/
2. Download and install Python 3.
3. During installation, select **Add Python to PATH**.
4. Verify installation using PowerShell:

```powershell
python --version
pip --version
```

### Step 2: Open the Project

1. Download or clone this repository.
2. Extract the project folder if downloaded as a ZIP file.
3. Open the `GIST_Data_Science_Internship` folder in VS Code.
4. Open a terminal in the project root directory.

### Step 3: Install Python Libraries

Install the required dependencies:

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
pip install jupyter ipykernel
```

### Step 4: Run Task 1

Open the terminal from the project root and run:

```powershell
cd Task_1
python -m jupyter notebook Task_1.ipynb
```

Run all notebook cells from top to bottom.

This notebook reads the original dataset and generates the cleaned dataset.

### Step 5: Run Task 2

After Task 1 completes successfully, return to the project root and run:

```powershell
cd ..
cd Task_2
python -m jupyter notebook Task_2.ipynb
```

Run all notebook cells from top to bottom.

This notebook uses the cleaned dataset generated by Task 1.

### Step 6: Install and Open Power BI Desktop

1. Visit the official Microsoft Power BI website: https://www.microsoft.com/en-us/power-platform/products/power-bi/desktop
2. Download Power BI Desktop.
3. Install the application on your computer.
4. Open Power BI Desktop.
5. Select **File → Open Report**.
6. Browse to `Task_4/PowerBI_Dashboard.pbix`.
7. Open the dashboard and interact with the available charts and filters.

**Note:** Power BI Desktop is installed separately and is not included in the Python requirements.

## 13. Required Python Libraries

The project uses the following Python libraries:

- `pandas` — Data manipulation and analysis.
- `numpy` — Numerical calculations.
- `matplotlib` — Data visualization.
- `seaborn` — Statistical data visualization.

Jupyter Notebook and ipykernel are installed separately using the setup commands above.

## 14. Project Outcomes

- Original and cleaned e-commerce datasets.
- Separate Jupyter notebooks for data cleaning and EDA.
- Statistical summaries and data visualizations.
- Business insights based on historical transaction records.
- An interactive Power BI dashboard based on a 1,000-row sample.
- Documented methodology, findings, and limitations.

## 15. Limitations

- The dataset contains partial calendar years at the beginning and end of its date range.
- The currency is not specified.
- Some fields contain missing or unusual values.
- Statistical outliers are not necessarily data errors.
- The fulfilled-sales calculation is an analytical definition and may differ from accounting measures.
- Power BI dashboard results are based on 1,000 selected rows, not the complete dataset.
- Dashboard DAX measures and filter interactions should be validated in Power BI Desktop.
- Product costs and profit margins are not available.

## 16. Conclusion

This project demonstrates a descriptive data analysis workflow, starting with data cleaning and continuing through exploratory data analysis and interactive Power BI visualization.

Python was used to prepare the dataset, explore business patterns, and generate meaningful insights, while Power BI provided an interactive way to present important business metrics.

The project highlights the importance of data quality, accurate analysis, clear visualizations, and evidence-based business insights.