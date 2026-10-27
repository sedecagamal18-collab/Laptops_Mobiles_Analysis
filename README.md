# Mobile & Laptop Sales Analysis | Python

## Project Overview
This project analyzes mobile phone and laptop sales data using Python (Pandas) to understand sales performance, revenue distribution, product demand, and inventory holding time.

The main goal is to transform raw order-level sales data into clear business metrics, such as total revenue, best-performing brands, regional revenue distribution, the relationship between price and quantity sold, and how long products stay in stock before dispatch.

## Dataset Description
The dataset (`mobile_sales_data.csv`) contains **50,000 sales records and 16 columns**. Each row represents one sales order.

| Column | Description |
|---|---|
| Product | Product category (Laptop or Mobile Phone) |
| Brand | Brand name (20 brands) |
| Product Code | Unique product code |
| Product Specification | Text description of the product |
| Price | Unit price |
| Inward Date | Date the product entered the stock |
| Dispatch Date | Date the product was dispatched |
| Quantity Sold | Number of units sold in the order (1 to 10) |
| Customer Name | Customer name |
| Customer Location | Customer city |
| Region | Sales region (North, South, East, West, Central) |
| Core Specification | Processor core type (laptops only) |
| Processor Specification | Processor model |
| RAM | RAM size (4GB to 32GB) |
| ROM | Storage size |
| SSD | SSD size (laptops only) |

**Dataset scope:** orders with inward dates from **March 2023 to March 2025**, covering **25,017 laptop orders** and **24,983 mobile phone orders**.

## Tools Used
- Python
- Pandas and NumPy (data cleaning and analysis)
- Jupyter Notebook

## Project Workflow

### 1. Data Understanding
- Loaded the dataset and reviewed its structure, column names, and data types.

### 2. Data Cleaning & Preparation
- **Removing unneeded columns:** Dropped `Product Code`, `Product Specification`, `Core Specification`, and `Customer Name`.
- **Converting data types:** Converted `Inward Date` and `Dispatch Date` to datetime.
- **Creating new columns:**
  - `Revenue` = Price × Quantity Sold
  - `Days On Stock` = Dispatch Date − Inward Date (in days)
- **Handling missing values:** Only the `SSD` column had missing values (24,983 rows, all of them mobile phones, which have no SSD). These were filled with `0`.
- **Duplicates:** No duplicate rows were found.
- **Final dataset:** 50,000 rows × 14 columns.

### 3. Exploratory Data Analysis (EDA)

| Analysis | Method | Visualization |
|---|---|---|
| Total revenue | Sum of Revenue | — |
| Average price | Mean of Price | — |
| Most popular brand | Total quantity sold by brand | Bar chart |
| Highest revenue brand | Total revenue by brand | Horizontal bar chart |
| Top-selling product | Total quantity sold by product | Bar chart |
| Sales per region | Total revenue by region | Pie chart |
| Quantity sold and revenue per product | Group by product | — |
| Correlation between price and quantity sold | Correlation coefficient | Scatter plot |
| Average days in stock by brand | Mean of Days On Stock by brand | Bar chart |

## Key Findings

- The dataset generated total revenue of about **28.28 billion** from **275,689 units sold** across 50,000 orders. The average unit price is about **102,641**, and the average order has about 5.5 units.
- **Brand performance:** **Google** leads in both units sold (14,412) and revenue (about 1.51 billion, about 5.4% of total), followed by **Nokia** (14,239 units) and **Apple** (14,197 units). **Asus** is the lowest in both units (12,999) and revenue (about 1.32 billion). All 20 brands fall within a narrow range of about 4.7% to 5.4% of total revenue.
- **Product performance:** Laptops and mobile phones are almost equal. Laptops sold 138,019 units (about 14.19 billion in revenue), and mobile phones sold 137,670 units (about 14.09 billion). Their average prices are also very close (about 102,800 and 102,500).
- **Regional performance:** The **West** region has the highest revenue (about 5.86 billion, 20.7%), while the other four regions are almost identical (about 19.8% to 19.9% each).
- **Price and demand:** The correlation between price and quantity sold is about **−0.002**, which is practically zero. Orders at low prices and high prices have the same average quantity (about 5.5 units).
- **Inventory:** Products stay in stock for an average of **30.6 days** (between 1 and 60 days). **Samsung** has the highest average (about 31.1 days) and **Sony** the lowest (about 30.0 days), a difference of only about one day across all brands.

*Note: The findings describe this dataset and should not be interpreted as facts about the real mobile and laptop market.*

## Limitations
- The data looks synthetic: every brand sells both laptops and mobile phones in almost equal numbers (for example, Dell and Asus mobile phones, or Nokia laptops), and the distributions across brands, regions, and prices are very even.
- Because of this, the differences between brands, regions, and products are small (a few percent) and may not be meaningful. No statistical significance tests were applied.
- Brand rankings (for example, Google first and Samsung with the longest stock time) reflect small differences rather than strong performance gaps.
- Correlation shows association only and does not establish causation.
- Monetary values are reported in the dataset's original units.

## Business Value

This project demonstrates how Python can be used to:

- Calculate core sales KPIs such as revenue, average price, and units sold.
- Compare brands, products, and regions by sales volume and revenue.
- Test whether price is associated with the quantity customers buy.
- Measure inventory holding time and highlight brands for further review.

## Skills Demonstrated

- Data Cleaning & Preparation (Pandas)
- Feature Engineering (Revenue, Days On Stock)
- Group-based Analysis (`groupby`)
- Correlation Analysis
- Data Visualization
- Insight Communication

## How to Run

1. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib jupyter
   ```
2. Place `mobile_sales_data.csv` in the same folder as the notebook.
3. Open `Laptops_Mobiles_Analysis_ipynb.ipynb` in Jupyter Notebook and run all cells.

## Project Files

- `mobile_sales_data.csv` — Original dataset (50,000 rows, 16 columns).
- `Laptops_Mobiles_Analysis_ipynb.ipynb` — Jupyter Notebook containing the full cleaning, analysis, and visualizations.

## Conclusion

This project demonstrates the use of Python to turn raw mobile and laptop sales data into clear business metrics covering revenue, brand and regional performance, price and demand, and inventory holding time.

The results show that sales are spread very evenly across brands, regions, and products in this dataset, and that price has almost no relationship with the quantity sold.
