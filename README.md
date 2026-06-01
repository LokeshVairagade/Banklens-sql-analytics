
# 🏦Banklens-sql-analytics– Banking Analytics Project

A end-to-end SQL project built on a realistic banking dataset covering customer insights, account analysis, transaction monitoring, and loan portfolio management.

---

## 📁 Project Structure

```
Banklens-sql-analytics/
│
├── data/
│   ├── banking_customers.csv
│   ├── banking_accounts.csv
│   ├── banking_transactions.csv
│   └── banking_loans.csv
│
├── banking_create_tables.sql    ← Database & Table creation
├── banking_sql_queries.sql      ← 15 Analytical Queries
└── README.md
```

---

## 🗄️ Database Schema

### customers
| Column | Type | Description |
|---|---|---|
| customer_id | VARCHAR(10) | Primary Key |
| full_name | VARCHAR(100) | Customer full name |
| email | VARCHAR(100) | Unique email address |
| phone | BIGINT | Phone number |
| city | VARCHAR(50) | City of residence |
| dob | DATE | Date of birth |
| gender | ENUM | Male / Female / Other |
| joined_date | DATE | Account opening date |

### accounts
| Column | Type | Description |
|---|---|---|
| account_id | VARCHAR(10) | Primary Key |
| customer_id | VARCHAR(10) | Foreign Key → customers |
| account_type | ENUM | Savings / Current / FD / RD |
| balance | DECIMAL(15,2) | Current balance |
| currency | VARCHAR(5) | Default: INR |
| opened_date | DATE | Account opened date |
| status | ENUM | Active / Inactive / Frozen |
| branch | VARCHAR(100) | Branch name |

### transactions
| Column | Type | Description |
|---|---|---|
| transaction_id | VARCHAR(12) | Primary Key |
| account_id | VARCHAR(10) | Foreign Key → accounts |
| transaction_type | ENUM | Credit / Debit / UPI / NEFT etc. |
| amount | DECIMAL(15,2) | Transaction amount |
| txn_date | DATE | Transaction date |
| txn_time | TIME | Transaction time |
| status | ENUM | Success / Failed / Pending |
| reference_no | VARCHAR(20) | Reference number |

### loans
| Column | Type | Description |
|---|---|---|
| loan_id | VARCHAR(10) | Primary Key |
| customer_id | VARCHAR(10) | Foreign Key → customers |
| loan_type | ENUM | Home / Car / Personal / Education / Business |
| principal_amount | DECIMAL(15,2) | Loan amount |
| interest_rate_pct | DECIMAL(5,2) | Interest rate % |
| tenure_months | INT | Loan tenure in months |
| emi_amount | DECIMAL(15,2) | Monthly EMI |
| disbursement_date | DATE | Loan disbursement date |
| status | ENUM | Active / Closed / Defaulted |
| branch | VARCHAR(100) | Branch name |

---

## 📊 Dataset Overview

| Table | Rows | Description |
|---|---|---|
| customers | 400 | Unique bank customers |
| accounts | 600 | Bank accounts |
| transactions | 1,500 | Banking transactions (2021–2024) |
| loans | 300 | Loan records |

---

## 🔍 SQL Queries Covered

| # | Query | Concepts Used |
|---|---|---|
| Q1 | Total customers per city | GROUP BY, ORDER BY |
| Q2 | Account type distribution | AVG, GROUP BY |
| Q3 | Top 5 customers by balance | JOIN, SUM |
| Q4 | Monthly transaction trends (2023) | DATE_FORMAT, WHERE |
| Q5 | Transaction success/fail rate | Window Function (OVER) |
| Q6 | Top payment methods by amount | Filter + GROUP BY |
| Q7 | Loan type breakdown | Multi-column aggregation |
| Q8 | Loan health – Active/Closed/Defaulted | SUM + GROUP BY |
| Q9 | Customers with loans & active accounts | Subquery, IN |
| Q10 | Branch-wise loan disbursement | SUM, ORDER BY |
| Q11 | Gender-wise average balance | JOIN + AVG |
| Q12 | Risk flag – dormant high balance accounts | WHERE + JOIN |
| Q13 | Customers with multiple accounts | HAVING, COUNT |
| Q14 | High-value transactions (fraud detection) | 3-table JOIN |
| Q15 | Year-wise loan disbursement trend | YEAR(), GROUP BY |

---

## ⚙️ How to Run

### Step 1 – Setup Database
```sql
-- Run this file first
banking_create_tables.sql
```

### Step 2 – Import CSV Data (in this order)
```
1. banking_customers.csv     → customers table
2. banking_accounts.csv      → accounts table
3. banking_transactions.csv  → transactions table
4. banking_loans.csv         → loans table
```
> Use MySQL Workbench → Table Data Import Wizard

### Step 3 – Run Queries
```sql
-- Run this file
banking_sql_queries.sql
```

---

## 🛠️ Tools Used

- **Database:** MySQL 8.0
- **IDE:** MySQL Workbench
- **Language:** SQL
- **Data:** Synthetically generated realistic banking data

---

## 💡 Key Insights from Analysis

- Savings accounts have the highest count but Fixed Deposits hold higher average balance
- UPI and NEFT are the top transaction types by volume
- ~12% transactions fail — flagged for system reliability review
- Multiple customers hold Frozen/Inactive accounts with balance > ₹1,00,000 — risk flag
- Home Loans make up the largest share of loan portfolio

---

## 👤 Author

**[Lokeshwar Vairagade ]**  
Aspiring SQL Developer  
📧 [lokeshwarvairagade@gmail.com]  

---

> ⭐ If you found this project useful, give it a star on GitHub!
