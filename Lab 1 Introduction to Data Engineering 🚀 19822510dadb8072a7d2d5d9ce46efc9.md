# Lab 1 : Introduction to Data Engineering 🚀

# 1️⃣ What is Data Engineering?

Data Engineering is the practice of **designing, building, and maintaining data pipelines,**

It enables data storage, processing, and analysis.,

It is the foundation for **Data Science, Machine Learning, and Business Intelligence (BI)**.

# 2️⃣ Data Engineering Workflow

## **Step 1: Data Ingestion**

Bringing raw data from multiple sources:

- **Databases**
- **APIs**
- **Streaming Data**
- **Flat Files**

## Step 2 : Data Storage

Storing data in a structured way for processing.

- **Relational Databases (OLTP):** MySQL, PostgreSQL, SQL Server
- **Data Warehouses (OLAP):** Amazon Redshift, Snowflake, Google BigQuery
- **Data Lakes:** AWS S3, Azure Data Lake, HDFS (Hadoop)

## Step 3: Data Processing (ETL & ELT)

Transforming raw data into usable formats.

- **ETL (Extract, Transform, Load)**
- **ELT (Extract, Load, Transform)**

## **Step 4: Data Analytics & Business Intelligence**

Using processed data for **reporting, dashboards, and AI/ML**.

- **BI Tools**: Power BI, Tableau, Looker
- **SQL Queries for Analysis**
- **Data Science Pipelines (Python, Pandas, PySpark)**

## **Data Engineering Tools & Technologies**

| Category | Tools & Technologies |
| --- | --- |
| **Data Ingestion** | Apache Kafka, AWS Kinesis, Google Pub/Sub |
| **Data Storage** | PostgreSQL, MySQL, Snowflake, Redshift |
| **Data Processing** | Apache Spark, Airflow, dbt, SQL |
| **Big Data** | Hadoop, Databricks, Google BigQuery |
| **BI & Visualization** | Power BI, Tableau, Looker |
| **Cloud Platforms** | AWS, Azure, Google Cloud |

# Why database?

- A database is a collection of information that is organized so that it can be easily accessed, managed and updated.
- Databases are stored on the hard disk of the database server.

# Types of Database

The two most popular types of database nowadays are:
● Relational (SQL)
● NoSQL (which stands for Not only SQL)

# Database Management System (DBMS)

- To manage databases, you need a database management system (DBMS).
- A DBMS is a program that stores, retrieves, and modifies data in databases on request. DBMS for relational databases are called Relational DBMS (RDBMS).

# Relational Databases

- A relational database uses relations or two-dimensional tables to store information.
- Each row of data in a table is uniquely identified by a “primary key”.

# **What is SQL?** 🛠️

SQL (**Structured Query Language**) is a **programming language** used to **store, retrieve, manage, and manipulate data** in relational databases.

# **SQL Commands: DDL, DML, DCL, TCL, and DQL** 🚀

SQL (Structured Query Language) is categorized into **five** major types of commands:

✅ **DDL (Data Definition Language)** – Defines the database structure.

✅ **DML (Data Manipulation Language)** – Manipulates data within tables.

✅ **DCL (Data Control Language)** – Controls access to data.

✅ **TCL (Transaction Control Language)** – Manages transactions.

✅ **DQL (Data Query Language)** – Retrieves data from the database.

## **1️⃣ DDL – Data Definition Language** 🏗️

     DDL commands **define and modify database schema** (structure).

### **🔹 CREATE TABLE (Define a New Table)**

```sql

CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName NVARCHAR(50) NOT NULL,
    LastName NVARCHAR(50) NOT NULL,
    Salary DECIMAL(10,2),
    Department NVARCHAR(50)
);

```

### **🔹 ALTER TABLE (Modify an Existing Table)**

```sql

ALTER TABLE Employees ADD Email NVARCHAR(100); -- Add a new column
ALTER TABLE Employees ALTER COLUMN Salary DECIMAL(12,2); -- Change column type
ALTER TABLE Employees DROP COLUMN Email; -- Remove a column

```

### **🔹 DROP TABLE (Delete a Table Permanently)**

```sql

DROP TABLE Employees;

```

### **🔹 TRUNCATE TABLE (Remove All Data but Keep Structure)**

```sql
sql

TRUNCATE TABLE Employees;

```

## **2️⃣ DML – Data Manipulation Language**

DML commands **modify data inside tables**.

### **🔹 INSERT (Add Data into Table)**

```sql

INSERT INTO Employees (EmployeeID, FirstName, LastName, Salary, Department)
VALUES (1, 'John', 'Doe', 5000, 'IT');

```

### **🔹 UPDATE (Modify Existing Data)**

```sql

UPDATE Employees
SET Salary = 6000
WHERE EmployeeID = 1;

```

### **🔹 DELETE (Remove Specific Records)**

```sql

DELETE FROM Employees WHERE EmployeeID = 1;

```

⚠️ **Warning:** `DELETE` removes only **selected records**, while `TRUNCATE` removes **all records**.

---

## **3️⃣ DCL – Data Control Language** 🔒

DCL commands **control access to the database**.

### **🔹 GRANT (Give User Privileges)**

```sql

GRANT SELECT, INSERT ON Employees TO user1;

```

### **🔹 REVOKE (Remove User Privileges)**

```sql
REVOKE INSERT ON Employees FROM user1;
```

---

## **4️⃣ TCL – Transaction Control Language** 🔄

TCL commands **manage transactions** in databases.

### **🔹 BEGIN TRANSACTION (Start a Transaction)**

```sql

BEGIN TRANSACTION;
UPDATE Employees SET Salary = 5000 WHERE EmployeeID = 2;

```

### **🔹 COMMIT (Save Changes)**

```sql

COMMIT;
```

### **🔹 ROLLBACK (Undo Changes)**

```sql
ROLLBACK;
```

---

## **5️⃣ DQL – Data Query Language** 🔍

DQL commands are used to **retrieve data** from the database.

### **🔹 SELECT (Fetch Data)**

```sql

SELECT * FROM Employees;
SELECT FirstName, LastName FROM Employees WHERE Salary > 4000;

```

### **🔹 ORDER BY (Sort Results)**

```sql

SELECT * FROM Employees ORDER BY Salary DESC;

```

### **🔹 GROUP BY & HAVING (Aggregation)**

```sql

SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 5;

```

## **Summary Table**

| Category | Commands | Purpose |
| --- | --- | --- |
| **DDL** (Definition) | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` | Define and modify database structure |
| **DML** (Manipulation) | `INSERT`, `UPDATE`, `DELETE` | Modify table data |
| **DCL** (Control) | `GRANT`, `REVOKE` | Manage permissions |
| **TCL** (Transactions) | `BEGIN`, `COMMIT`, `ROLLBACK` | Manage transactions |
| **DQL** (Query) | `SELECT` | Retrieve data |