# 🔨 DDL - Data Definition Language

[← Back to Main](../../README.md) | [← Previous: Data Types](../03-data-types/README.md) | [Next: DML Commands →](../05-dml-commands/README.md)

---

## 📖 Table of Contents
- [CREATE TABLE](#create-table)
- [ALTER TABLE](#alter-table)
- [DROP TABLE](#drop-table)
- [TRUNCATE TABLE](#truncate-table)
- [RENAME TABLE](#rename-table)

---

## CREATE TABLE

### Basic Syntax
```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    column3 datatype constraints,
    ...
);
```

### Example
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT, 
    name VARCHAR(50) NOT NULL,
    department VARCHAR(30),
    age INT CHECK (age >= 18),
    salary DECIMAL(10,2),
    join_date DATE
);
```

### IF NOT EXISTS
```sql
CREATE TABLE IF NOT EXISTS employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    department VARCHAR(30)
);
```

## ALTER TABLE

### Add Column
```sql
ALTER TABLE employees 
ADD email VARCHAR(100);
```

### Drop Column
```sql
ALTER TABLE employees 
DROP COLUMN email;
```

### Modify Column
```sql
ALTER TABLE employees 
MODIFY COLUMN salary DECIMAL(12,2);
```

### Rename Column
```sql
ALTER TABLE employees 
CHANGE COLUMN department dept_name VARCHAR(50);
```

### Add Constraint
```sql
ALTER TABLE employees
ADD CONSTRAINT chk_age CHECK (age >= 18);
```

## DROP TABLE

### Basic Drop
```sql
DROP TABLE employees;
```

### Safe Drop
```sql
DROP TABLE IF EXISTS employees;
```

## TRUNCATE TABLE

```sql
TRUNCATE TABLE employees;
```

**Note:** TRUNCATE is faster than DELETE but cannot be rolled back.

## RENAME TABLE

```sql
RENAME TABLE employees TO staff_members;
```

---

## 🔗 Navigation

- **Previous:** [← Data Types](../03-data-types/README.md)
- **Next:** [DML Commands →](../05-dml-commands/README.md)
- **Main:** [← Back to Main README](../../README.md)
