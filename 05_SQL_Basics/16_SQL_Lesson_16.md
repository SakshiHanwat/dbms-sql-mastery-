# SQL Lesson 16: Creating Tables

This README is a **complete, beginner-friendly explanation** of **SQL Lesson 16 – Creating Tables** from SQLBolt.

Nothing is skipped. This file includes:

* What CREATE TABLE is
* Full CREATE TABLE syntax
* Data types explained simply
* Table constraints explained clearly
* Example schemas
* Exercise 16 tasks
* **Complete solution with explanation**

Use this as:

* SQL revision notes
* GitHub README.md
* Database fundamentals reference

---

## 1. What is CREATE TABLE?

When your database needs to store a **new type of data (entity)**, you must create a new table.

The **CREATE TABLE** statement:

* Defines table structure
* Defines column names
* Defines data types
* Defines constraints (rules)

This structure is called the **table schema**.

---

## 2. Basic CREATE TABLE Syntax

```sql
CREATE TABLE mytable (
    column DataType,
    another_column DataType
);
```

Each column has:

* Name
* Data type
* Optional constraints
* Optional default value

---

## 3. CREATE TABLE with Safety (IF NOT EXISTS)

```sql
CREATE TABLE IF NOT EXISTS mytable (
    column DataType,
    another_column DataType
);
```

Why use it?

* Prevents error if table already exists
* Safer in real projects

---

## 4. Common SQL Data Types (Important)

### Numeric Types

| Data Type             | Use                        |
| --------------------- | -------------------------- |
| INTEGER               | Whole numbers (count, age) |
| BOOLEAN               | True / False (0 or 1)      |
| FLOAT / DOUBLE / REAL | Decimal numbers            |

---

### Text Types

| Data Type  | Use                    |
| ---------- | ---------------------- |
| CHAR(n)    | Fixed-length string    |
| VARCHAR(n) | Variable-length string |
| TEXT       | Large text             |

---

### Date & Other Types

| Data Type | Use                         |
| --------- | --------------------------- |
| DATE      | Date only                   |
| DATETIME  | Date + time                 |
| BLOB      | Binary data (images, files) |

---

## 5. Table Constraints (Rules)

Constraints restrict what data can be stored.

| Constraint    | Meaning                |
| ------------- | ---------------------- |
| PRIMARY KEY   | Unique identifier      |
| AUTOINCREMENT | Auto increases integer |
| UNIQUE        | No duplicate values    |
| NOT NULL      | Cannot be empty        |
| CHECK         | Custom condition       |
| FOREIGN KEY   | Link to another table  |

---

## 6. Example: Movies Table Schema

```sql
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER,
    length_minutes INTEGER
);
```

Explanation:

* `id` uniquely identifies each movie
* Other columns store movie details

---

## 7. Exercise 16 – Task

Create a new table named **Database** with these columns:

| Column Name    | Data Type | Description          |
| -------------- | --------- | -------------------- |
| Name           | TEXT      | Name of the database |
| Version        | FLOAT     | Latest version       |
| Download_count | INTEGER   | Number of downloads  |

Rules:

* No constraints required

---

## 8. Exercise 16 – Solution

```sql
CREATE TABLE Database (
    Name TEXT,
    Version FLOAT,
    Download_count INTEGER
);
```

Explanation:

* Simple table creation
* No constraints added
* Matches task exactly

---

## 9. Verify Table Creation

```sql
SELECT * FROM Database;
```

If no error appears, table creation was successful.

---

## 10. Common Mistakes ❌

❌ Forgetting data types
❌ Using wrong data type
❌ Creating duplicate tables without IF NOT EXISTS
❌ Not planning schema properly

---

## 11. Key Takeaways ⭐

* CREATE TABLE defines structure
* Schema controls allowed data
* Data types matter a lot
* Constraints protect data integrity

---

## 12. Big Picture 🧠

You now know:

✔ INSERT
✔ UPDATE
✔ DELETE
✔ CREATE TABLE

This is **core SQL CRUD + Schema foundation** 💪

---

**End of README**
