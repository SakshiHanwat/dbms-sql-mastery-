# SQL Lesson 7: OUTER JOINs

## Overview

In the previous lesson, we used **INNER JOIN**, which only returns rows that have matching records in both tables.

However, in real-world databases, this is often not enough. Sometimes:

* One table contains data
* The related table does not yet have matching records

In such cases, using only an INNER JOIN would cause important data to be excluded from the results.

To solve this problem, SQL provides **OUTER JOINs**.

---

## Why OUTER JOINs Are Needed

When two tables contain **asymmetric data** (data entered at different times or incomplete relationships), INNER JOINs may drop rows that are still important.

To ensure no required data is lost, SQL provides three types of OUTER JOINs:

* **LEFT JOIN**
* **RIGHT JOIN**
* **FULL JOIN**

---

## General Syntax for OUTER JOINs

```sql
SELECT column, another_column, …
FROM mytable
INNER / LEFT / RIGHT / FULL JOIN another_table
    ON mytable.id = another_table.matching_id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

> Note: Unlike INNER JOIN, OUTER JOINs return rows even when there is no matching record in the other table.

---

## Types of OUTER JOINs Explained

### LEFT JOIN

* Returns **all rows from the left table**
* If no matching row exists in the right table, the result contains **NULL** values for the right table columns

### RIGHT JOIN

* Returns **all rows from the right table**
* If no matching row exists in the left table, the result contains **NULL** values for the left table columns

### FULL JOIN

* Returns **all rows from both tables**
* Rows without matches on either side will contain **NULL** values

---

## Handling NULL Values

Because OUTER JOINs include non-matching rows, **NULL values** are common in the result set.

When using OUTER JOINs, you often need to add extra logic to:

* Filter NULLs
* Replace NULL values
* Apply conditions carefully

These topics are covered in detail in the next lesson.

---

## Did You Know?

You may sometimes see JOINs written as:

* LEFT OUTER JOIN
* RIGHT OUTER JOIN
* FULL OUTER JOIN

These forms exist for **SQL-92 compatibility**, but:

* LEFT JOIN = LEFT OUTER JOIN
* RIGHT JOIN = RIGHT OUTER JOIN
* FULL JOIN = FULL OUTER JOIN

They behave exactly the same.

---

## Exercise: Film Studio Database

In this exercise, you will work with fictional data representing employees in a film studio and the office buildings they are assigned to.

Some buildings are new and do not yet have any employees, but we still need information about them.

> Due to browser SQL limitations, **only LEFT JOIN is supported** in this exercise.

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

---

## Exercise Tasks and Solutions

### Task 1: Find the list of all buildings that have employees

```sql
SELECT DISTINCT b.building_name
FROM buildings b
LEFT JOIN employees e
ON b.building_name = e.building
WHERE e.name IS NOT NULL;
```

---

### Task 2: Find the list of all buildings and their capacity

```sql
SELECT building_name, capacity
FROM buildings;
```

---

### Task 3: List all buildings and the distinct employee roles in each building (including empty buildings)

```sql
SELECT DISTINCT b.building_name, e.role
FROM buildings b
LEFT JOIN employees e
ON b.building_name = e.building;
```

> Buildings without employees will show `NULL` in the role column.

---

## Key Takeaways

* INNER JOIN returns only matching rows
* LEFT JOIN keeps all rows from the left table
* RIGHT JOIN keeps all rows from the right table
* FULL JOIN keeps all rows from both tables

OUTER JOINs are essential for working with real-world, incomplete, or evolving datasets.

---

## What’s Next?

In the next lesson, you will learn:

* How to handle NULL values properly
* How constraints affect JOIN results
* More advanced JOIN filtering techniques

Keep practicing — JOINs are a core SQL skill 🚀
