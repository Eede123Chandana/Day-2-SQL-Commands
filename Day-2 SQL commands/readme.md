# 🚀 SQL Commands | Schema, Roles & Constraints

## 📌 Overview

SQL (Structured Query Language) is used to define, manipulate, query, and control data in relational database systems.

This guide covers SQL schemas, database roles, constraints, command categories, and frequently asked interview questions with practical SQL examples.

**Objective:** Understand how SQL commands work and how database concepts support data integrity, security, and business operations.

---

## 1️⃣ What is a Schema?

A **schema** is a logical structure that organizes database objects, such as tables, views, and other related objects.

### Example (MySQL)

```sql
CREATE DATABASE company_db;
USE company_db;

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100),
    salary DECIMAL(10,2)
);
```

**Business Use Case:** Companies organize employee, customer, sales, and inventory data into structured database objects.

*Note: Schema and database terminology varies across database systems.*

---

## 2️⃣ Roles in Database Management

| Role | Responsibilities |
|---|---|
| DBA | Security, backups, performance, maintenance |
| Data Analyst (DA) | Querying, reporting, data analysis |
| Business Analyst (BA) | Business requirements, KPIs, insights |

### Real-World Example

In an e-commerce company:

- **DBA:** Maintains databases and access permissions.
- **DA:** Analyzes customer transactions and sales.
- **BA:** Uses insights to recommend business improvements.

---

## 3️⃣ SQL Constraints

Constraints are rules applied to table columns to maintain data integrity.

| Constraint | Purpose |
|---|---|
| PRIMARY KEY | Uniquely identifies each row; no NULLs |
| FOREIGN KEY | Enforces referential integrity |
| NOT NULL | Prevents NULL values |
| UNIQUE | Prevents duplicate values |
| CHECK | Validates specified conditions |
| DEFAULT | Supplies a value when omitted |

### Example

```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50) UNIQUE
);

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2) DEFAULT 30000,
    dept_id INT,
    FOREIGN KEY (dept_id)
        REFERENCES departments(dept_id)
);
```

**Why Constraints Matter:**

- Prevent invalid records
- Maintain relationships
- Improve data consistency
- Enforce business rules

---

## 4️⃣ Types of SQL Commands

SQL commands are commonly classified into five categories.

### 🔹 DDL – Data Definition Language

Used to define or modify database structures.

**Commands:** CREATE, ALTER, DROP, TRUNCATE

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100)
);

ALTER TABLE products
ADD price DECIMAL(10,2);
```

### 🔹 DML – Data Manipulation Language

Used to insert, update, or delete records.

**Commands:** INSERT, UPDATE, DELETE

```sql
INSERT INTO products
VALUES (101, 'Laptop', 55000);

UPDATE products
SET price = 52000
WHERE product_id = 101;

DELETE FROM products
WHERE product_id = 101;
```

### 🔹 DQL – Data Query Language

Used to retrieve information.

**Command:** SELECT

```sql
SELECT *
FROM products;
```

### 🔹 TCL – Transaction Control Language

Used to manage database transactions.

**Commands:** COMMIT, ROLLBACK, SAVEPOINT

```sql
START TRANSACTION;

UPDATE products
SET price = 50000
WHERE product_id = 101;

SAVEPOINT price_change;

UPDATE products
SET price = 48000
WHERE product_id = 101;

ROLLBACK TO SAVEPOINT price_change;

COMMIT;
```

*Example assumes a transactional storage engine such as InnoDB.*

### 🔹 DCL – Data Control Language

Used to manage database permissions.

**Commands:** GRANT, REVOKE

```sql
GRANT SELECT
ON company_db.*
TO 'analyst'@'localhost';

REVOKE SELECT
ON company_db.*
FROM 'analyst'@'localhost';
```

*Assumes the user account already exists and the executing account has the required privileges.*

---

## 5️⃣ SQL Interview Preparation

### Q1. Difference Between DDL & DML?

| DDL | DML |
|---|---|
| Defines database structure | Manipulates table data |
| CREATE, ALTER, DROP | INSERT, UPDATE, DELETE |
| Changes schema objects | Changes stored records |

### Q2. Primary Key vs Unique Key?

| Primary Key | Unique Key |
|---|---|
| Uniquely identifies rows | Enforces unique values |
| Cannot contain NULL | NULL behavior varies by DBMS |
| One per table | Multiple UNIQUE constraints allowed |

### Q3. DELETE vs TRUNCATE?

| DELETE | TRUNCATE |
|---|---|
| DML command | Usually classified as DDL |
| Supports WHERE | Removes all rows |
| Can delete selected records | Retains table structure |
| Can be rolled back within supported transactions | Rollback behavior varies by DBMS |

**MySQL Note:** TRUNCATE causes an implicit commit and cannot be rolled back like a transactional DELETE.

### Q4. What is the Role of a DBA?

A Database Administrator is responsible for:

- Database installation and configuration
- Security and user access
- Backup and recovery
- Performance optimization
- Availability and maintenance

---

## 6️⃣ Real-World Business Applications

### 🏦 Banking
TCL commands help maintain transaction consistency.

### 🛒 Retail
DML commands update product inventory and customer records.

### 🏥 Healthcare
Constraints maintain data integrity across patient-related records.

### 📊 Business Analytics
DQL commands retrieve data for reports and dashboards.

### 🔐 Enterprise Security
DCL commands control database access permissions.

---

## 🎯 Key Takeaways

✅ Schema organizes database objects.

✅ Database roles define responsibilities.

✅ Constraints maintain data integrity.

✅ DDL manages structures.

✅ DML modifies data.

✅ DQL retrieves information.

✅ TCL manages transactions.

✅ DCL controls permissions.

✅ SQL interview preparation requires understanding practical differences between commands.

---

## 💡 Final Thoughts

**Mastering SQL commands goes beyond memorizing syntax.**

Understanding database structures, constraints, access controls, and transactions builds a strong foundation for solving real-world data problems.

### 🏷️ Topics

`SQL` `DDL` `DML` `DQL` `TCL` `DCL` `Database Schema` `SQL Constraints` `SQL Interviews` `MySQL` `Data Analytics`
