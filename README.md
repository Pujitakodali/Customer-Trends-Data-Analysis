# Customer Trends Data Analysis (SQL, Python, Power BI)

This project analyzes customer shopping behavior using:
- Python (data cleaning + feature engineering)
- SQL (business analysis queries)
- Power BI (interactive dashboard)

The goal is to turn raw transaction data into business insights around revenue, customer segments, discounts, product performance, and subscription behavior.

## Project Overview

The end-to-end workflow in this repository is:
1. Load and clean customer shopping data in Python.
2. Engineer analysis-ready fields (for example `age_group`, `purchase_frequency_days`).
3. Push cleaned data into a SQL database table (`customer`).
4. Run analytical SQL queries for key business questions.
5. Build a Power BI dashboard and presentation outputs.

## Dataset

- Source file: `customer_shopping_behavior.csv`
- Records: 3,900 rows (plus header)
- Main fields include:
  `Customer ID`, `Age`, `Gender`, `Item Purchased`, `Category`,
  `Purchase Amount (USD)`, `Review Rating`, `Subscription Status`,
  `Shipping Type`, `Discount Applied`, `Previous Purchases`,
  `Payment Method`, `Frequency of Purchases`, and more.

## Repository Structure

- `Customer_Shopping_Behavior_Analysis.ipynb`  
  Main notebook for cleaning, feature engineering, and loading data to SQL.
- `customer_behavior_sql_queries.sql`  
  SQL queries used for business analysis.
- `customer_behavior_dashboard.pbix`  
  Power BI dashboard file.
- `Customer Shopping Behavior Analysis.pdf`  
  Report/export artifact.
- `Customer-Shopping-Behavior-Analysis.pptx`  
  Presentation deck.
- `Business Problem  Document.pdf`  
  Problem framing and context.
- `customer_shopping_behavior.csv`  
  Raw input dataset.

## Tech Stack

- Python `>=3.13`
- pandas
- SQLAlchemy
- psycopg2-binary (PostgreSQL connector)
- PostgreSQL / MySQL / SQL Server (examples included in notebook)
- Power BI Desktop

## Setup

### 1) Clone and enter project

```bash
git clone https://github.com/Pujitakodali/\Customer-Trends-Data-Analysis.git
cd customer-trends-data-analysis-SQL-Python-PowerBI
```

### 2) Install dependencies

Using `uv` (recommended in this repo):

```bash
uv sync
```

Or using `pip`:

```bash
python -m venv .venv
source .venv/bin/activate  # macOS/Linux
pip install pandas sqlalchemy psycopg2-binary
```

### 3) Launch the notebook

```bash
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

## How to Run the Analysis

1. Open `Customer_Shopping_Behavior_Analysis.ipynb`.
2. Run cells in order:
   - Load data and inspect (`head`, `info`, `describe`)
   - Handle missing values in `Review Rating`
   - Standardize column names to snake_case
   - Create engineered columns:
     - `age_group` (quartile-based)
     - `purchase_frequency_days` (mapped from text frequency)
   - Drop redundant `promo_code_used` column
3. Configure DB credentials in the notebook for your environment.
4. Run the DB load cell to create/replace table `customer`.
5. Execute queries from `customer_behavior_sql_queries.sql`.

## SQL Business Questions Covered

The SQL script answers questions such as:
- Revenue split by gender
- High spenders using discounts
- Top-rated products
- Standard vs express shipping spend comparison
- Subscriber vs non-subscriber spending behavior
- Products with highest discount usage rates
- Customer segment counts (new/returning/loyal)
- Top products by category
- Repeat buyer subscription tendency
- Revenue by age group

## Power BI

Use `customer_behavior_dashboard.pbix` to explore dashboard visuals and KPIs built from the transformed dataset/query outputs.

## Notes

- Update database username/password/host/port before running DB upload cells.
- The notebook includes example connection code for PostgreSQL, MySQL, and SQL Server.
- For SQL Server, install a compatible ODBC driver locally (for example ODBC Driver 17).

## Future Improvements

- Add a `requirements.txt` export for pip-only users.
- Parameterize database configuration via environment variables.
- Add automated data quality checks and unit tests.
- Add dashboard screenshots in this README.
