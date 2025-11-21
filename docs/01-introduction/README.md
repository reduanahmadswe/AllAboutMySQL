# 🎯 Introduction to SQL & MySQL

[← Back to Main](../../README.md)

---

## 📖 Table of Contents
- [SQL কি?](#sql-কি)
- [RDBMS কি?](#rdbms-কি)
- [MySQL Features](#mysql-features)
- [SQL vs NoSQL Databases](#sql-vs-nosql-databases)
- [Basic SQL Syntax](#basic-sql-syntax)
- [SQL Keywords](#sql-keywords)
- [PostgreSQL Basics](#postgresql-basics)

---

## SQL কি?
**SQL (Structured Query Language)** হলো একটি প্রোগ্রামিং ল্যাঙ্গুয়েজ যা ডাটাবেজ ম্যানেজমেন্টের জন্য ব্যবহার করা হয়।

## RDBMS কি?
**RDBMS (Relational Database Management System)** হলো এমন একটি সিস্টেম যেখানে ডাটা টেবিল আকারে সংরক্ষিত থাকে এবং টেবিলগুলোর মধ্যে সম্পর্ক (Relation) থাকে।

## MySQL Features:
✅ Open Source  
✅ Fast & Reliable  
✅ Supports Large Databases  
✅ Cross-Platform Support  
✅ Security Features

## 🔄 SQL vs NoSQL Databases

### SQL Databases (Relational)

**বৈশিষ্ট্য:**
- টেবিল-ভিত্তিক কাঠামো (Table-based structure)
- নির্দিষ্ট স্কিমা (Fixed schema)
- ACID properties সমর্থন করে
- Vertical scaling (CPU, RAM বাড়ানো)
- জটিল queries এবং joins সমর্থন করে

**উদাহরণ:**
- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite

**কখন ব্যবহার করবেন:**
- যখন data structure স্থির
- Complex queries প্রয়োজন
- Transaction integrity গুরুত্বপূর্ণ
- Banking, Finance, E-commerce

### NoSQL Databases (Non-relational)

**বৈশিষ্ট্য:**
- Document, Key-Value, Graph, Column-family based
- Dynamic schema (নমনীয়)
- BASE properties (Basically Available, Soft state, Eventually consistent)
- Horizontal scaling (বেশি servers যোগ করা)
- Large-scale data এবং high performance

**উদাহরণ:**
- MongoDB (Document)
- Redis (Key-Value)
- Cassandra (Column-family)
- Neo4j (Graph)
- DynamoDB (Key-Value)

**কখন ব্যবহার করবেন:**
- যখন data structure পরিবর্তনশীল
- Large-scale, distributed data
- Real-time applications
- Social media, IoT, Big Data

**তুলনা টেবিল:**

| Feature | SQL | NoSQL |
|---------|-----|-------|
| **Schema** | Fixed, predefined | Dynamic, flexible |
| **Scaling** | Vertical | Horizontal |
| **Query Language** | Standard SQL | Varies by database |
| **Transactions** | Strong ACID | Eventually consistent |
| **Best for** | Complex queries | Large-scale data |
| **Examples** | MySQL, PostgreSQL | MongoDB, Redis |

## 📝 Basic SQL Syntax

```sql
-- Single line comment

/* 
   Multi-line 
   comment 
*/

-- Basic query structure
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column1;
```

## 🔑 SQL Keywords

**Must-know SQL Keywords:**

```sql
-- Data Query
SELECT, FROM, WHERE, ORDER BY, GROUP BY, HAVING, LIMIT, OFFSET

-- Data Manipulation
INSERT, UPDATE, DELETE

-- Data Definition
CREATE, ALTER, DROP, TRUNCATE

-- Constraints
PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, CHECK, DEFAULT

-- Joins
INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, CROSS JOIN

-- Aggregation
SUM, COUNT, AVG, MIN, MAX

-- Conditional
CASE, WHEN, THEN, ELSE, END, IF, IFNULL, COALESCE, NULLIF

-- Logical Operators
AND, OR, NOT, IN, BETWEEN, LIKE, EXISTS

-- Set Operations
UNION, UNION ALL, INTERSECT, EXCEPT

-- Subqueries
ANY, ALL, SOME

-- Transactions
BEGIN, COMMIT, ROLLBACK, SAVEPOINT

-- Access Control
GRANT, REVOKE

-- Functions
DISTINCT, AS, IS NULL, IS NOT NULL
```

## 🎨 PostgreSQL Basics

**PostgreSQL** হলো একটি powerful, open-source relational database system যা MySQL এর চেয়ে বেশি features সমর্থন করে।

### PostgreSQL vs MySQL

| Feature | PostgreSQL | MySQL |
|---------|------------|-------|
| **ACID Compliance** | Full | Partial (depends on engine) |
| **JSON Support** | Native JSON & JSONB | Basic JSON |
| **Window Functions** | Excellent | Limited |
| **Inheritance** | ✅ Supports | ❌ No |
| **Full Text Search** | Built-in | Basic |
| **Recursive Queries** | ✅ Advanced | ✅ Basic |

### PostgreSQL Specific Features

**1️⃣ JSONB Data Type**
```sql
-- Creating table with JSONB
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    attributes JSONB
);

-- Inserting JSON data
INSERT INTO products (name, attributes) VALUES
('Laptop', '{"brand": "Dell", "ram": "16GB", "storage": "512GB SSD"}'),
('Phone', '{"brand": "Samsung", "ram": "8GB", "camera": "108MP"}');

-- Querying JSON data
SELECT name, attributes->>'brand' AS brand
FROM products;

-- JSON operators
SELECT * FROM products WHERE attributes @> '{"brand": "Dell"}';
```

**2️⃣ Array Data Type**
```sql
-- Creating table with array
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    subjects TEXT[]
);

-- Inserting array data
INSERT INTO students (name, subjects) VALUES
('Karim', ARRAY['Math', 'Physics', 'Chemistry']),
('Nusrat', ARRAY['Biology', 'Chemistry', 'English']);

-- Querying arrays
SELECT name FROM students WHERE 'Physics' = ANY(subjects);
SELECT name FROM students WHERE subjects @> ARRAY['Math'];
```

**3️⃣ SERIAL Auto-increment**
```sql
-- PostgreSQL uses SERIAL instead of AUTO_INCREMENT
CREATE TABLE employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);
```

**4️⃣ RETURNING Clause**
```sql
-- Get inserted/updated data immediately
INSERT INTO employees (name, salary) 
VALUES ('Ahmed', 50000)
RETURNING id, name, salary;

UPDATE employees 
SET salary = salary * 1.1 
WHERE department = 'IT'
RETURNING id, name, salary;
```

**5️⃣ Table Inheritance**
```sql
-- Parent table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

-- Child table inherits from parent
CREATE TABLE premium_users (
    subscription_end_date DATE
) INHERITS (users);

-- Querying includes child tables
SELECT * FROM users;  -- Shows both regular and premium users
SELECT * FROM ONLY users;  -- Shows only parent table data
```

---

## 🔗 Navigation

- **Next:** [Database Basics →](../02-database-basics/README.md)
- **Main:** [← Back to Main README](../../README.md)
