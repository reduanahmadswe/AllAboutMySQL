# 📊 Data Types

[← Back to Main](../../README.md) | [← Previous: Database Basics](../02-database-basics/README.md) | [Next: DDL Commands →](../04-ddl-commands/README.md)

---

## 📖 Table of Contents
- [Numeric Data Types](#numeric-data-types)
- [String Data Types](#string-data-types)
- [Date and Time Data Types](#date-and-time-data-types)
- [Binary Data Types](#binary-data-types)

---

## Numeric Data Types

| Data Type | Description | Size |
|-----------|-------------|------|
| `TINYINT` | Very small integer | 1 byte |
| `SMALLINT` | Small integer | 2 bytes |
| `MEDIUMINT` | Medium integer | 3 bytes |
| `INT` or `INTEGER` | Standard integer | 4 bytes |
| `BIGINT` | Large integer | 8 bytes |
| `DECIMAL(M,D)` | Fixed-point number | Variable |
| `FLOAT` | Single-precision floating point | 4 bytes |
| `DOUBLE` | Double-precision floating point | 8 bytes |

**Examples:**
```sql
CREATE TABLE numbers (
    tiny_num TINYINT,           -- -128 to 127
    small_num SMALLINT,         -- -32,768 to 32,767
    medium_num MEDIUMINT,       -- -8,388,608 to 8,388,607
    normal_num INT,             -- -2,147,483,648 to 2,147,483,647
    big_num BIGINT,             -- Very large numbers
    price DECIMAL(10,2),        -- 10 digits total, 2 after decimal
    weight FLOAT,               -- Approximate decimal
    distance DOUBLE             -- More precise decimal
);
```

## String Data Types

| Data Type | Description | Max Size |
|-----------|-------------|----------|
| `CHAR(n)` | Fixed-length string | 255 characters |
| `VARCHAR(n)` | Variable-length string | 65,535 characters |
| `TEXT` | Long text | 65,535 characters |
| `MEDIUMTEXT` | Medium text | 16,777,215 characters |
| `LONGTEXT` | Very long text | 4,294,967,295 characters |
| `ENUM` | Enumeration (predefined list) | 65,535 values |
| `SET` | Set of values | 64 members |

**Examples:**
```sql
CREATE TABLE strings (
    code CHAR(5),                    -- Fixed length: 'A001 '
    name VARCHAR(100),               -- Variable: 'John Doe'
    description TEXT,                -- Long text
    bio MEDIUMTEXT,                  -- Very long text
    status ENUM('Active', 'Inactive', 'Pending'),
    tags SET('urgent', 'important', 'featured', 'new')
);
```

## Date and Time Data Types

| Data Type | Format | Range |
|-----------|--------|-------|
| `DATE` | YYYY-MM-DD | 1000-01-01 to 9999-12-31 |
| `TIME` | HH:MM:SS | -838:59:59 to 838:59:59 |
| `DATETIME` | YYYY-MM-DD HH:MM:SS | 1000-01-01 to 9999-12-31 |
| `TIMESTAMP` | YYYY-MM-DD HH:MM:SS | 1970-01-01 to 2038-01-19 |
| `YEAR` | YYYY | 1901 to 2155 |

**Examples:**
```sql
CREATE TABLE dates (
    birth_date DATE,                 -- 1990-05-15
    appointment_time TIME,           -- 14:30:00
    created_at DATETIME,             -- 2024-11-21 10:30:45
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    graduation_year YEAR             -- 2024
);
```

## Binary Data Types

| Data Type | Description |
|-----------|-------------|
| `BINARY(n)` | Fixed-length binary |
| `VARBINARY(n)` | Variable-length binary |
| `BLOB` | Binary Large Object |
| `MEDIUMBLOB` | Medium BLOB |
| `LONGBLOB` | Long BLOB |

**Examples:**
```sql
CREATE TABLE binaries (
    hash BINARY(32),                 -- MD5 hash
    file_data BLOB,                  -- Small file
    image MEDIUMBLOB,                -- Image file
    video LONGBLOB                   -- Large video file
);
```

---

## 🔗 Navigation

- **Previous:** [← Database Basics](../02-database-basics/README.md)
- **Next:** [DDL Commands →](../04-ddl-commands/README.md)
- **Main:** [← Back to Main README](../../README.md)
