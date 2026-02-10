# SQL Lesson 10: Queries with Aggregates (Part 1)

## 📘 Introduction

In addition to the simple expressions introduced in the previous lesson, SQL supports **aggregate functions** (also called **aggregate expressions**). These functions allow us to **summarize information** from a group of rows and extract meaningful insights from data.

Using the Pixar-style database in SQLBolt, aggregate functions help answer questions such as:

* *How many movies has Pixar produced?*
* *What is the highest-grossing Pixar film each year?*

In this lesson, we focus on using aggregate functions with the **Employees** table to calculate high-level metrics about teams.

---

## 📊 Employees Table Overview

The `Employees` table contains shared data across rows, making it ideal for practicing aggregate queries.

### Table: `Employees`

| Column Name    | Description                                                |
| -------------- | ---------------------------------------------------------- |
| Role           | Job role of the employee (Engineer, Artist, Manager, etc.) |
| Name           | Employee name                                              |
| Building       | Building where the employee works (e.g., 1e, 2w)           |
| Years_employed | Number of years the employee has worked at the studio      |

---

## 🔢 Aggregate Functions in SQL

Aggregate functions operate on **multiple rows** and return **a single summarized value**.

### General Syntax (All Rows)

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, ...
FROM mytable
WHERE constraint_expression;
```

* If **GROUP BY** is not used, the aggregate function runs on **all rows**.
* Using **aliases (`AS`)** makes output easier to read and understand.

---

## 🧮 Common Aggregate Functions

| Function        | Description                                   |
| --------------- | --------------------------------------------- |
| `COUNT(*)`      | Counts total number of rows in the result set |
| `COUNT(column)` | Counts number of non-NULL values in a column  |
| `MIN(column)`   | Returns the smallest numerical value          |
| `MAX(column)`   | Returns the largest numerical value           |
| `AVG(column)`   | Returns the average value                     |
| `SUM(column)`   | Returns the total sum of values               |

> ⚠️ Note: `COUNT(column)` ignores NULL values, while `COUNT(*)` does not.

---

## 👥 Grouped Aggregate Functions

Instead of summarizing the entire table, SQL allows us to apply aggregate functions to **specific groups** of data.

### General Syntax (Grouped Rows)

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, ...
FROM mytable
WHERE constraint_expression
GROUP BY column;
```

* `GROUP BY` groups rows with the **same value** in the specified column.
* One result is returned **per group**.

Example use cases:

* Average years employed **per role**
* Total employee years **per building**

---

## 🧪 Exercise: Employees Aggregates

For this exercise, we work with the `Employees` table and solve the following tasks.

### ✅ Task 1: Find the longest time an employee has been at the studio

```sql
SELECT MAX(years_employed) AS longest_time
FROM employees;
```

---

### ✅ Task 2: For each role, find the average number of years employed

```sql
SELECT role, AVG(years_employed) AS avg_years
FROM employees
GROUP BY role;
```

---

### ✅ Task 3: Find the total number of employee years worked in each building

```sql
SELECT building, SUM(years_employed) AS total_years
FROM employees
GROUP BY building;
```

---

## 🧠 Key Takeaways

* Aggregate functions summarize multiple rows into meaningful values
* Without `GROUP BY`, results are calculated over the **entire table**
* With `GROUP BY`, results are calculated **per group**
* Always use aliases (`AS`) for clarity

---

## 📚 Supported SQL Dialects

The concepts in this lesson work across:

* MySQL
* PostgreSQL
* SQLite
* Microsoft SQL Server

---

## 🎯 Conclusion

This lesson builds the foundation for analyzing data using SQL aggregates. Mastering these functions is essential for reporting, analytics, and interviews.

✔ Complete all tasks to move forward to the next lesson in SQLBolt.

Happy Learning! 🚀
