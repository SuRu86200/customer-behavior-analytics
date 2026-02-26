# customer-behavior-analytics
An end-to-end data analytics project uncovering purchasing patterns and customer lifecycles. This pipeline uses Pandas for ETL, MySQL for relational modeling and window-function analysis, and Power BI to visualize churn risk and top-performing product categories.

🛒 Customer Behavior Analysis: From Raw Data to Retention Insights

📋 Project Objective
The goal of this project is to understand how customers interact with our product categories. By analyzing purchase frequency and order volumes, we identify high-value customers and "hot" product trends to drive marketing efficiency.

🏗️ The Data Pipeline
The project moves through four distinct phases:

Data Wrangling (Python): Cleaned 3900+ rows of transaction data, handled duplicate columns (e.g., purchase_freaquency_days), and formatted timestamps.

Database Engineering (SQLAlchemy): Built a relational schema in MySQL to move from flat files to a scalable database environment.

Deep-Dive Analysis (SQL): Leveraged CTEs and Window Functions to rank the top 3 items per category and calculate customer order frequency.
Interactive Reporting (Power BI): Created a multi-page dashboard for executive-level reporting.

🔍 Analytical Highlights (The "SQL Magic")
I used advanced SQL to segment the data. For example, to find the most popular items within each category:

SQL
-- Ranking items by popularity per category
WITH item_rankings AS (
    SELECT category, item_purchased, COUNT(*) as volume,
    ROW_NUMBER() OVER(PARTITION BY category ORDER BY COUNT(*) DESC) as rank
    FROM customers GROUP BY 1, 2
)
SELECT * FROM item_rankings WHERE rank <= 3;

📈 Dashboard Preview

<img width="891" height="503" alt="Screenshot 2026-02-26 191159" src="https://github.com/user-attachments/assets/3cea3db2-e6e1-4a1c-83c6-d8e145961587" />

🛠️ Installation & Usage

Clone: git clone https://github.com/yourlink.git

Database Setup: Import the /sql/schema.sql into your MySQL instance.

Run ETL: Open the cleaning_script.ipynb to see the Pandas transformation logic.

