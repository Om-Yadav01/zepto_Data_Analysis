# Zepto Data Analysis Using SQL

A PostgreSQL data analysis project focused on Zepto-style e-commerce inventory data. This project demonstrates how SQL can be used to clean raw retail data, explore product availability, compare pricing patterns, and generate business insights from inventory records.

## Project Overview

The goal of this project is to analyze product-level inventory data and answer practical business questions around:

- Product categories and stock availability
- Pricing, discounts, and selling price patterns
- High-value products and low-discount products
- Estimated revenue by category
- Inventory weight distribution
- Value-for-money products based on price per gram

## Repository Contents

| File | Description |
| --- | --- |
| `zepto_v2.csv` | Raw e-commerce inventory dataset used for analysis. |
| `Zepto_SQL_data_analysis.sql` | PostgreSQL script for table creation, cleaning, EDA, and business analysis. |
| `README.md` | Project documentation and usage guide. |
| `LICENSE` | Project license information. |

## Dataset Columns

| Column | Description |
| --- | --- |
| `sku_id` | Unique product identifier created as a primary key. |
| `category` | Product category. |
| `name` | Product name. |
| `mrp` | Maximum retail price. |
| `discountPercent` | Discount percentage applied to the product. |
| `availableQuantity` | Available inventory quantity. |
| `discountedSellingPrice` | Final selling price after discount. |
| `weightInGms` | Product weight in grams. |
| `outOfStock` | Stock status flag. |
| `quantity` | Product package quantity. |

## Workflow

### 1. Database Setup

The SQL script creates a `zepto` table using PostgreSQL data types:

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```

### 2. Data Exploration

The project explores the dataset by checking:

- Total number of records
- Sample rows
- Missing values
- Distinct categories
- In-stock vs out-of-stock products
- Products with multiple SKU entries

### 3. Data Cleaning

Cleaning steps include:

- Detecting rows where `mrp` or `discountedSellingPrice` is zero
- Removing invalid zero-MRP products
- Converting prices from paise to rupees for readable analysis

### 4. Business Analysis

The SQL script answers questions such as:

- Which products offer the highest discounts?
- Which high-MRP products are out of stock?
- What is the estimated revenue by category?
- Which expensive products have low discounts?
- Which categories provide the highest average discount?
- Which products offer the best price per gram?
- How can products be grouped by weight category?
- What is the total inventory weight by category?

## How to Run

1. Clone this repository:

```bash
git clone https://github.com/Om-Yadav01/zepto_Data_Analysis.git
cd zepto_Data_Analysis
```

2. Open PostgreSQL using pgAdmin, psql, or another PostgreSQL client.

3. Run the table creation section from `Zepto_SQL_data_analysis.sql`.

4. Import `zepto_v2.csv` into the `zepto` table.

You can also import using psql:

```sql
\copy zepto(category,name,mrp,discountPercent,availableQuantity,discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'zepto_v2.csv'
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```

5. Run the exploration, cleaning, and analysis queries from `Zepto_SQL_data_analysis.sql`.

## Tools Used

- PostgreSQL
- pgAdmin or psql
- SQL
- CSV dataset

## Author

**Om Yadav**

This project is part of my SQL and data analytics portfolio.
