# SQL-EDA-project-Data-Cleaning-
# 🧹 Tech Layoffs — SQL Data Cleaning & EDA

> End-to-end data cleaning and exploratory analysis on a real-world global tech layoffs dataset using MySQL.

---

## 📌 Project Overview

This project demonstrates professional SQL data cleaning and exploratory data analysis (EDA) on a dataset tracking **2,300+ tech company layoffs** worldwide (2020–2023).

The goal was to transform a messy, raw dataset into a clean, analysis-ready table — then use that clean data to uncover meaningful trends.

**Dataset source:** [Kaggle — Layoffs 2022](https://www.kaggle.com/datasets/swaptr/layoffs-2022)

---

## 🗂️ Files

| File | Description |
|------|-------------|
| `Portfolio Project - Data Cleaning.sql` | Full data cleaning pipeline in MySQL |
| `Portfolio Project - EDA.sql` | Exploratory analysis queries on the cleaned data |

---

## 🛠️ Tools & Skills Used

- **MySQL** — all queries written and executed in MySQL Workbench
- **Window Functions** — `ROW_NUMBER()` with `PARTITION BY` for duplicate detection
- **CTEs** — `WITH` clause for clean, readable deduplication logic
- **String Functions** — `TRIM`, `STR_TO_DATE`, `LIKE` for standardization
- **Self Joins** — to populate missing values from matching rows
- **DDL** — `ALTER TABLE`, `CREATE TABLE`, `DROP COLUMN`

---

## 🔄 Data Cleaning Steps

### 1. 🗃️ Staging Table
Created a staging copy of the raw data to preserve originals and safely work on a clean version.

### 2. 🔁 Duplicate Removal
Used `ROW_NUMBER()` window function partitioned across all columns to flag exact duplicates.
Wrapped in a CTE for clean deletion logic. Added a `row_num` column, deleted rows ≥ 2, then dropped the helper column.

### 3. 📐 Standardization
- Converted empty strings `''` to `NULL` for consistent NULL handling
- Used a **self JOIN** to populate missing `industry` values from other rows of the same company
- Standardized category variations (e.g., `"Crypto Currency"`, `"CryptoCurrency"` → `"Crypto"`)
- Removed trailing periods from `country` values (e.g., `"United States."` → `"United States"`)
- Converted `date` column from text to proper `DATE` type using `STR_TO_DATE()`

### 4. 🗑️ Removing Irrelevant Rows
Deleted rows where both `total_laid_off` and `percentage_laid_off` were NULL — these records had no analytical value.

---

## 📊 Exploratory Data Analysis (EDA)

After cleaning, ran exploratory queries to surface insights such as:

- Which **industries** had the highest total layoffs?
- Which **countries** were most affected?
- How did layoffs trend **over time**?
- Which **funding stages** saw the most cuts?
- Which companies laid off **100% of their workforce**?

---

## 💡 Key Takeaways

- Real-world data is messy — same data can appear in multiple formats (`"United States"` vs `"United States."`)
- Staging tables are essential to protect raw data during transformation
- Window functions and CTEs make duplicate removal far more robust than naive approaches
- Populating NULLs intelligently (via self JOIN) is better than dropping incomplete rows blindly

---

## 👩‍💻 Author

**Meduri Sai Medha**
[LinkedIn](https://linkedin.com/in/saimedhameduri) • [GitHub](https://github.com/MEDHA-MEDURI04)
