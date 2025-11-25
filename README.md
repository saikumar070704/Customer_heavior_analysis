# Customer Shopping Behavior Analytics

## Overview
This project analyzes customer shopping behavior using Python, SQL, and Power BI.  
The goal is to understand purchasing patterns, customer segments, discount impact, and revenue drivers.  
It includes data loading, EDA, cleaning, SQL-based analysis on a relational database, and an interactive Power BI dashboard, ending with a written report and presentation.

---

## Dataset
- **File name:** `customer_shopping_behavior.csv`
- **Rows:** 3,900  
- **Columns:** 18 (after cleaning + feature engineering)  
- **Key fields:**
  - Customer demographics: `age`, `gender`, `location`
  - Purchase details: `item_purchased`, `category`, `purchase_amount`, `season`, `size`, `color`
  - Behavior indicators: `previous_purchases`, `frequency_of_purchases`
  - Service info: `shipping_type`, `subscription_status`, `discount_applied`
  - Feedback: `review_rating`

---

## Tools & Technologies
- **Python:** Pandas, NumPy, SQLAlchemy
- **SQL Databases:** PostgreSQL / MySQL / SQL Server
- **Visualization:** Power BI
- **Documentation:** Report (PDF/Word)
- **Presentation:** Gamma (PPT export)
- **Environment:** Jupyter Notebook

---

## Project Steps

### 1. Data Loading
- Loaded CSV into Pandas:
  ```python
  import pandas as pd
  df = pd.read_csv("customer_shopping_behavior.csv")
2. Exploratory Data Analysis (EDA)
Checked structure, datatypes, missing values, and distributions:

python
Copy code
df.info()
df.describe(include="all")
df.isnull().sum()
3. Data Cleaning
Filled missing review_rating using median per category

Standardized column names to snake_case

Removed redundant column (promo_code_used matched discount_applied)

4. Feature Engineering
Created age_group using quartiles:

Young Adult, Adult, Middle-age, Senior

Mapped frequency_of_purchases to numeric purchase_frequency_days

5. Load Data to SQL Database
Connected and inserted into database table customer

python
Copy code
from sqlalchemy import create_engine
engine = create_engine("YOUR_DB_CONNECTION_STRING")
df.to_sql("customer", engine, if_exists="replace", index=False)
6. SQL Analysis
Answered business questions such as:

Revenue by gender

Discount users spending above average

Top-rated products

Shipping type vs average spend

Subscription vs revenue

Discount-heavy products

Customer segmentation (New / Returning / Loyal)

Top products per category

Repeat buyers vs subscription

Revenue by age group

(Queries stored in queries.sql)

7. Dashboard (Power BI)
Built interactive dashboard highlighting:

Revenue breakdowns

Customer segments

Discount impact

Product/category performance

Shipping & subscription insights

8. Report & Presentation
Wrote a short analytics report with insights and visuals

Created a clean PPT using Gamma for easy explanation during interviews

Dashboard Highlights
Power BI dashboard includes:

KPI Cards: Total Revenue, Avg Spend, Total Customers

Slices/Filters: Gender, Age Group, Category, Season, Discount Applied

Charts:

Revenue by Gender & Subscription

Top Items per Category

Discount Rate per Product

Shipping Type vs Avg Spend

Age Group Revenue Contribution

Results & Insights (Sample)
Clothing is the highest revenue category.

Discount usage strongly affects purchase frequency and basket size.

Loyal customers contribute the majority of revenue.

Subscription users show higher repeat purchase patterns.

Express shipping users spend slightly more on average.

How to Run
1. Clone the repository
bash
Copy code
git clone <your-repo-link>
cd customer-shopping-analytics
2. Install dependencies
bash
Copy code
pip install pandas sqlalchemy psycopg2-binary mysql-connector-python
3. Run notebook
Open:

bash
Copy code
jupyter notebook
Run:
customer_analysis.ipynb

4. Load into SQL
Update your DB credentials in the notebook and run the load cell.

5. Run SQL queries
Open queries.sql in your SQL tool and execute.

6. Open Power BI Dashboard
Open:
dashboard.pbix

Repository Structure
pgsql
Copy code
customer-shopping-analytics/
│
├── data/
│   └── customer_shopping_behavior.csv
│
├── notebooks/
│   └── customer_analysis.ipynb
│
├── sql/
│   └── queries.sql
│
├── powerbi/
│   └── dashboard.pbix
│
├── report/
│   └── customer_behavior_report.pdf
│
├── presentation/
│   └── customer_behavior_ppt.pptx
│
└── README.md
Author
BEJJIPURAPU SAIKUMAR
Vunathi Technologies
📧 saikumar070704@gmail.com
