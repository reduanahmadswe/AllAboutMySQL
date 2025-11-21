# 🎓 Interview Questions

[← Back to Main](../../README.md)

---

## 📖 Table of Contents
- [Basic Level](#basic-level)
- [Intermediate Level](#intermediate-level)
- [Advanced Level](#advanced-level)

---

## Basic Level

### 1️⃣ What is SQL?
**SQL (Structured Query Language)** is a standard language for managing and manipulating relational databases.

### 2️⃣ What are different types of SQL commands?
- **DDL** - CREATE, ALTER, DROP, TRUNCATE
- **DML** - INSERT, UPDATE, DELETE
- **DQL** - SELECT
- **DCL** - GRANT, REVOKE
- **TCL** - COMMIT, ROLLBACK, SAVEPOINT

### 3️⃣ Find second highest salary
```sql
-- Method 1
SELECT MAX(salary) AS second_highest
FROM employees 
WHERE salary < (SELECT MAX(salary) FROM employees);

-- Method 2
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;

-- Method 3
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM employees
) ranked
WHERE rnk = 2;
```

### 4️⃣ Difference between WHERE and HAVING
```sql
-- WHERE: Filters before grouping
SELECT department, COUNT(*) 
FROM employees
WHERE salary > 50000
GROUP BY department;

-- HAVING: Filters after grouping
SELECT department, AVG(salary) 
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```

### 5️⃣ What is a Primary Key and Foreign Key?
```sql
-- Primary Key
CREATE TABLE departments (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL
);

-- Foreign Key
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(id)
);
```

## Intermediate Level

### 1️⃣ Explain Normalization
- **1NF:** Atomic values, no repeating groups
- **2NF:** 1NF + no partial dependencies
- **3NF:** 2NF + no transitive dependencies

### 2️⃣ ACID Properties
- **Atomicity:** All or nothing
- **Consistency:** Valid state always
- **Isolation:** Transactions don't interfere
- **Durability:** Committed data is permanent

### 3️⃣ Types of Indexes
- **Clustered:** Physical order matches index order (one per table)
- **Non-Clustered:** Separate structure (multiple allowed)

## Advanced Level

### 1️⃣ Query to find duplicates
```sql
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

### 2️⃣ Nth highest salary
```sql
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM employees
) ranked
WHERE rnk = :N;
```

### 3️⃣ Delete duplicates keeping one
```sql
DELETE e1 FROM employees e1
INNER JOIN employees e2 
WHERE e1.id > e2.id 
AND e1.email = e2.email;
```

---

## 🔗 Navigation

- **Main:** [← Back to Main README](../../README.md)
