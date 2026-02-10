# SQL Lesson 11: Queries with Aggregates (Part 2)

## 📘 Introduction

As our SQL queries become more powerful, they also become more complex. By now, we have nearly covered all the **important components of a SELECT query**. In this lesson, we focus on an important question:

> If `WHERE` filters rows **before grouping**, then how do we filter **after grouping**?

The answer is the **HAVING clause**.

---

## 🔍 WHERE vs HAVING (Core Concept)

### 🔹 WHERE Clause

* Filters **individual rows**
* Applied **before** `GROUP BY`
* Cannot be used directly with aggregate results

### 🔹 HAVING Clause

* Filters **grouped rows**
* Applied **after** `GROUP BY`
* Used with **aggregate functions** like `COUNT`, `SUM`, `AVG`, etc.

👉 This makes `HAVING` essential when working with grouped data.

---

## 🧱 Query Order of Execution (Logical)

Understanding this order helps avoid confusion:

1. `FROM`
2. `WHERE`
3. `GROUP BY`
4. `HAVING`
5. `SELECT`
6. `ORDER BY`

---

## 🧮 SELECT Query with HAVING Clause

### General Syntax

```sql
SELECT group_by_column,
       AGG_FUNC(column_expression) AS aggregate_result_alias, ...
FROM mytable
WHERE condition
GROUP BY group_by_column
HAVING group_condition;
```

### Key Points

* `WHERE` filters rows **before grouping**
* `HAVING` filters **after aggregation**
* Conditions in `HAVING` look similar to `WHERE`

---

## 💡 Did You Know?

If you are **not using `GROUP BY`**, then:

* A simple `WHERE` clause is enough
* `HAVING` is **not required**

---

## 📊 Employees Table Overview

We continue working with the `Employees` table.

### Table: `Employees`

| Column Name    | Description                                          |
| -------------- | ---------------------------------------------------- |
| Role           | Job role of the employee (Engineer, Artist, Manager) |
| Name           | Employee name                                        |
| Building       | Building where the employee works                    |
| Years_employed | Number of years employee has worked                  |

---

## 🧪 Exercise: Employee Aggregates (Part 2)

For this exercise, we dive deeper into employee data and apply the correct clauses for each task.

---

### ✅ Task 1: Find the number of Artists in the studio (without using HAVING)

```sql
SELECT COUNT(*) AS artist_count
FROM employees
WHERE role = 'Artist';
```

📌 Explanation: Since no grouping is required, `WHERE` alone is sufficient.

---

### ✅ Task 2: Find the number of Employees of each role in the studio

```sql
SELECT role, COUNT(*) AS total_employees
FROM employees
GROUP BY role;
```

📌 Explanation: Employees are grouped by `role`, and `COUNT(*)` is applied per group.

---

### ✅ Task 3: Find the total number of years employed by all Engineers

```sql
SELECT SUM(years_employed) AS total_engineer_years
FROM employees
WHERE role = 'Engineer';
```

📌 Explanation: Filtering Engineers first using `WHERE`, then summing their years.

---

## 🧠 When to Use HAVING?

Use `HAVING` when:

* You need to filter based on **aggregate results**
* Example: roles having more than 3 employees

```sql
SELECT role, COUNT(*) AS total
FROM employees
GROUP BY role
HAVING COUNT(*) > 3;
```

---

## 🎯 Key Takeaways

* `WHERE` → filters rows
* `GROUP BY` → groups rows
* `HAVING` → filters groups
* `HAVING` is useless without grouping
* Logical execution order matters

---

## 📚 Supported SQL Dialects

These queries work across:

* MySQL
* PostgreSQL
* SQLite
* Microsoft SQL Server

---

## 🚀 Conclusion

The `HAVING` clause completes your understanding of aggregate queries in SQL. With `WHERE`, `GROUP BY`, and `HAVING` together, you can analyze large datasets efficiently.

Happy Querying! 🎉
