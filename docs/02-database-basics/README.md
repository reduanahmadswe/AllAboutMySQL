# 🗄️ Database Basics

[← Back to Main](../../README.md) | [← Previous: Introduction](../01-introduction/README.md) | [Next: Data Types →](../03-data-types/README.md)

---

## 📖 Table of Contents
- [Database তৈরি করা](#database-তৈরি-করা)
- [Database ব্যবহার করা](#database-ব্যবহার-করা)
- [সব Database দেখা](#সব-database-দেখা)
- [Database মুছে ফেলা](#database-মুছে-ফেলা)
- [Database-এর তথ্য দেখা](#database-এর-তথ্য-দেখা)

---

## Database তৈরি করা

```sql
CREATE DATABASE my_database;
```

**Example with character set:**
```sql
CREATE DATABASE my_database
CHARACTER SET utf8mb4
COLLATE utf8mb4_unicode_ci;
```

## Database ব্যবহার করা

```sql
USE my_database;
```

## সব Database দেখা

```sql
SHOW DATABASES;
```

**Filter databases:**
```sql
SHOW DATABASES LIKE 'my%';
```

## Database মুছে ফেলা

```sql
DROP DATABASE my_database;
```

**Safe drop:**
```sql
DROP DATABASE IF EXISTS my_database;
```

## Database-এর তথ্য দেখা

```sql
SHOW CREATE DATABASE my_database;
```

**Get database size:**
```sql
SELECT 
    table_schema AS 'Database',
    ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS 'Size (MB)'
FROM information_schema.tables
WHERE table_schema = 'my_database'
GROUP BY table_schema;
```

---

## 🔗 Navigation

- **Previous:** [← Introduction](../01-introduction/README.md)
- **Next:** [Data Types →](../03-data-types/README.md)
- **Main:** [← Back to Main README](../../README.md)
