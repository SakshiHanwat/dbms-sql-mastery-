# SQL Lesson 8: A Short Note on NULLs

## Overview

As promised in the previous lesson, this lesson focuses on **NULL values** in SQL databases.

A **NULL value** represents missing, unknown, or incomplete data. While NULLs are sometimes necessary, they require special care when:

* Writing queries
* Applying constraints
* Using aggregate functions (some behave differently with NULLs)
* Processing query results

For this reason, it is generally a good practice to **minimize NULL values** where possible.

---

## Alternatives to NULL Values

Instead of allowing NULLs, databases can sometimes use **default values** that are appropriate for the data type, such as:

* `0` for numeric columns
* Empty strings (`''`) for text columns

However, NULL values are still important and sometimes necessary.

### When NULLs Are Appropriate

NULL values should be used when:

* The data is genuinely unknown or incomplete
* Using a default value would distort analysis

**Example:**
If a numeric column is later used to calculate averages, storing `0` instead of NULL may produce incorrect results.

---

## NULLs in JOIN Operations

In the previous lesson on **OUTER JOINs**, NULL values appeared naturally when:

* Rows existed in one table
* But had no matching row in the joined table

In such cases, NULLs are unavoidable and must be handled correctly in queries.

---

## Checking for NULL Values in SQL

To test whether a column contains NULL values, SQL provides two special conditions:

* `IS NULL`
* `IS NOT NULL`

> Important: You **cannot** use `=` or `!=` to compare NULL values.

---

## Select Query with Constraints on NULL Values

```sql
SELECT column, another_column, …
FROM mytable
WHERE column IS NULL / IS NOT NULL
AND / OR another_condition
AND / OR …;
```

---

## Exercise: Employees and Buildings Review

This exercise reviews concepts from the last few lessons, including:

* OUTER JOINs
* NULL handling
* WHERE clause conditions

We are using the same **Employees** and **Buildings** tables as before, with a small change:

👉 A few new employees have been hired, but they have **not yet been assigned a building**.

---

## Table: buildings

| building_name | capacity |
| ------------- | -------- |
| 1e            | 24       |
| 1w            | 32       |
| 2e            | 16       |
| 2w            | 20       |

---

## Table: employees (Read-only)

| role     | name       | building | years_employed |
| -------- | ---------- | -------- | -------------- |
| Engineer | Becky A.   | 1e       | 4              |
| Engineer | Dan B.     | 1e       | 2              |
| Engineer | Sharon F.  | 1e       | 6              |
| Engineer | Dan M.     | 1e       | 4              |
| Engineer | Malcom S.  | 1e       | 1              |
| Artist   | Tylar S.   | 2w       | 2              |
| Artist   | Sherman D. | 2w       | 8              |
| Artist   | Jakob J.   | 2w       | 6              |
| Artist   | Lillia A.  | 2w       | 7              |
| Artist   | Brandon J. | 2w       | 7              |
| Manager  | Scott K.   | 1e       | 9              |
| Manager  | Shirlee M. | 1e       | 3              |
| Manager  | Daria O.   | 2w       | 6              |
| Engineer | Yancy I.   | NULL     | 0              |
| Artist   | Oliver P.  | NULL     | 0              |

---

## Exercise Tasks and Solutions

### Task 1: Find the names of employees who have not been assigned a building

```sql
SELECT name
FROM employees
WHERE building IS NULL;
```

---

### Task 2: Find the list of all buildings and the employees assigned to them (including unassigned buildings)

```sql
SELECT b.building_name, e.name
FROM buildings b
LEFT JOIN employees e
ON b.building_name = e.building;
```

---

### Task 3: Find all employees who have been employed for more than 5 years and have a building assigned

```sql
SELECT name, years_employed
FROM employees
WHERE years_employed > 5
AND building IS NOT NULL;
```

---

## Key Takeaways

* NULL represents missing or unknown data
* Avoid NULLs when sensible defaults are safe
* Use NULL when default values would distort analysis
* Always check NULLs using `IS NULL` or `IS NOT NULL`
* NULL values commonly appear in OUTER JOIN results

Understanding NULL handling is critical for writing correct and reliable SQL queries.

---

## What’s Next?

In the next lesson, you will learn more about:

* Constraints
* Advanced filtering logic
* Writing safer queries with NULL-aware conditions

Keep practicing — mastering NULLs is a key SQL skill 🚀
