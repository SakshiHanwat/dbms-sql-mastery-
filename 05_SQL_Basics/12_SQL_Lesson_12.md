# SQL Lesson 12: Order of Execution of a Query

## 📘 Introduction

Now that we understand **all the major parts of a SELECT query**, it’s time to learn **how SQL actually executes a query internally**.

Although we *write* SQL queries in a certain order, SQL **executes them in a different logical order**. Understanding this execution order is extremely important for:

* Writing correct queries
* Avoiding logical mistakes
* Clearing interview questions

---

## 🧩 Complete SELECT Query Structure

Below is a **complete SELECT query** showing all possible clauses:

```sql
SELECT DISTINCT column, AGG_FUNC(column_or_expression), ...
FROM mytable
    JOIN another_table
      ON mytable.column = another_table.column
WHERE constraint_expression
GROUP BY column
HAVING constraint_expression
ORDER BY column ASC | DESC
LIMIT count OFFSET count;
```

👉 **Important:** This is the *writing order*, NOT the execution order.

---

## 🔄 Why Order of Execution Matters

Each clause is executed **step by step**, and:

* Only results from *previous steps* are available
* Some aliases are **not accessible** in earlier stages
* Knowing this helps avoid errors like:

  * Using aliases in `WHERE`
  * Misusing `HAVING`

---

## ⚙️ Logical Order of Query Execution

### 1️⃣ FROM and JOINs

* SQL first identifies **all tables** involved
* Applies `JOIN` conditions
* Creates a **working dataset** (temporary result)
* Subqueries inside `FROM` are also executed here

---

### 2️⃣ WHERE

* Filters **individual rows** from the working dataset
* Rows that do not match the condition are removed
* Can only access **original table columns**
* ❌ Cannot use SELECT aliases here

---

### 3️⃣ GROUP BY

* Remaining rows are grouped based on column values
* One row per unique group is created
* Mostly used with **aggregate functions**

---

### 4️⃣ HAVING

* Filters **grouped rows**
* Works like `WHERE`, but after aggregation
* ❌ Aliases are usually NOT accessible here

---

### 5️⃣ SELECT

* Final column expressions are calculated
* Aliases are assigned here

---

### 6️⃣ DISTINCT

* Duplicate rows are removed
* Applied after SELECT expressions are computed

---

### 7️⃣ ORDER BY

* Rows are sorted (ASC / DESC)
* ✅ Aliases CAN be used here

---

### 8️⃣ LIMIT / OFFSET

* Restricts the number of rows returned
* OFFSET skips rows before returning results

---

## 🧠 Execution Order Summary (Must Remember)

```
FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT/OFFSET
```

📌 **Very important for interviews & debugging queries**

---

## 📊 Exercise: Final SELECT Practice

This exercise tests your understanding of **GROUP BY, JOINs, and aggregates**.

---

## 🗂️ Table: movies (Read-only)

| id  | title               | director      | year | length_minutes |
| --- | ------------------- | ------------- | ---- | -------------- |
| 1   | Toy Story           | John Lasseter | 1995 | 81             |
| 2   | A Bug's Life        | John Lasseter | 1998 | 95             |
| ... | ...                 | ...           | ...  | ...            |
| 14  | Monsters University | Dan Scanlon   | 2013 | 110            |

---

## 🗂️ Table: boxoffice (Read-only)

| movie_id | rating | domestic_sales | international_sales |
| -------- | ------ | -------------- | ------------------- |
| 1        | 8.3    | 191796233      | 170162503           |
| 2        | 7.2    | 162798565      | 200600000           |
| ...      | ...    | ...            | ...                 |

---

## 🧪 Exercise 12 – Tasks

### ✅ Task 1: Find the number of movies each director has directed

```sql
SELECT director, COUNT(*) AS total_movies
FROM movies
GROUP BY director;
```

---

### ✅ Task 2: Find the total domestic and international sales attributed to each director

```sql
SELECT m.director,
       SUM(b.domestic_sales) AS total_domestic_sales,
       SUM(b.international_sales) AS total_international_sales
FROM movies m
JOIN boxoffice b
  ON m.id = b.movie_id
GROUP BY m.director;
```

---

## 🎯 Key Takeaways

* SQL execution order ≠ SQL writing order
* `WHERE` filters rows, `HAVING` filters groups
* Aliases are available **only after SELECT**
* ORDER BY can use aliases, WHERE cannot

---

## 🏁 Conclusion

Not every query needs all clauses, but SQL’s power lies in allowing flexible data manipulation using these building blocks.

🎉 **Congratulations!** You have completed all SELECT query lessons in SQLBolt.

Next up ➜ **INSERTING ROWS (Lesson 13)** 🚀

Happy SQL Learning! 💙
