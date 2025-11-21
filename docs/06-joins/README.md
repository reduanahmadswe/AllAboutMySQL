# 🔗 Joins

[← Back to Main](../../README.md)

---

## 📖 Table of Contents
- [INNER JOIN](#inner-join)
- [LEFT JOIN](#left-join)
- [RIGHT JOIN](#right-join)
- [FULL OUTER JOIN](#full-outer-join)
- [CROSS JOIN](#cross-join)
- [SELF JOIN](#self-join)

---

## INNER JOIN

Returns only matching rows from both tables.

```sql
SELECT employees.name, departments.department_name  
FROM employees  
INNER JOIN departments  
ON employees.department_id = departments.id;
```

**Visual:**
```
Table A     Table B
  ⭕         ⭕
    ╲     ╱
      ⬤    ← Only this part (matching records)
    ╱     ╲
  ⭕         ⭕
```

## LEFT JOIN

Returns all rows from left table + matching rows from right table.

```sql
SELECT employees.name, departments.department_name  
FROM employees  
LEFT JOIN departments  
ON employees.department_id = departments.id;
```

**Visual:**
```
Table A     Table B
  ⬤         ⭕
    ╲     ╱
      ⬤    ← Left table + matches
    ╱     ╲
  ⬤         ⭕
```

## RIGHT JOIN

Returns all rows from right table + matching rows from left table.

```sql
SELECT employees.name, departments.department_name  
FROM employees  
RIGHT JOIN departments  
ON employees.department_id = departments.id;
```

## FULL OUTER JOIN

Returns all rows from both tables.

```sql
SELECT employees.name, departments.department_name  
FROM employees  
LEFT JOIN departments ON employees.department_id = departments.id
UNION
SELECT employees.name, departments.department_name  
FROM employees  
RIGHT JOIN departments ON employees.department_id = departments.id;
```

## CROSS JOIN

Returns Cartesian product (all possible combinations).

```sql
SELECT employees.name, departments.department_name  
FROM employees  
CROSS JOIN departments;
```

## SELF JOIN

Table joined with itself.

```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
INNER JOIN employees e2 ON e1.manager_id = e2.id;
```

---

## 🔗 Navigation

- **Main:** [← Back to Main README](../../README.md)
