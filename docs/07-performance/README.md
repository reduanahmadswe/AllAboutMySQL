# 🚀 Performance Optimization

[← Back to Main](../../README.md)

---

## 📖 Table of Contents
- [EXPLAIN](#explain)
- [Index Optimization](#index-optimization)
- [Query Optimization](#query-optimization)
- [Performance Monitoring](#performance-monitoring)

---

## EXPLAIN

```sql
EXPLAIN SELECT * FROM employees WHERE department = 'IT';
```

**Key columns to check:**
- `type`: Should be 'ref' or 'eq_ref', not 'ALL'
- `key`: Shows which index is used
- `rows`: Lower is better

## Index Optimization

### Create Index
```sql
CREATE INDEX idx_salary ON employees(salary);
```

### Composite Index
```sql
CREATE INDEX idx_dept_salary ON employees(department, salary);
```

### Check Index Usage
```sql
SHOW INDEX FROM employees;
```

## Query Optimization

### ❌ Bad
```sql
SELECT * FROM employees;  -- Fetches all columns
```

### ✅ Good
```sql
SELECT id, name, email FROM employees;  -- Only needed columns
```

### ❌ Bad
```sql
SELECT * FROM employees WHERE YEAR(join_date) = 2024;  -- Function on column
```

### ✅ Good
```sql
SELECT * FROM employees 
WHERE join_date >= '2024-01-01' AND join_date < '2025-01-01';
```

## Performance Monitoring

### Slow Query Log
```sql
SET GLOBAL slow_query_log = 1;
SET GLOBAL long_query_time = 2;  -- Queries > 2 seconds
```

### Query Profiling
```sql
SET profiling = 1;
SELECT * FROM orders WHERE customer_id = 123;
SHOW PROFILES;
```

---

## 🔗 Navigation

- **Main:** [← Back to Main README](../../README.md)
