# SQL Lesson 9: Queries with Expressions 

## 📌 Overview

In this lesson, we learn about **SQL expressions**. Expressions allow us to go beyond simply selecting raw column data and instead apply **calculations, transformations, and logic** directly within SQL queries.

Using expressions helps to:

* Make query results easier to understand
* Reduce extra data processing outside the database
* Produce more meaningful and readable outputs

⚠️ Note: While expressions are powerful, overusing complex expressions can make queries harder to read. That’s why it’s recommended to use **aliases (`AS`)** to clearly describe calculated columns.

---

## 🔹 What are SQL Expressions?

An SQL expression can include:

* Mathematical operations (`+`, `-`, `*`, `/`)
* Built-in functions (e.g., `ABS`, `ROUND`)
* Calculations using column values

### Example

```sql
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
```

✔️ Here:

* `particle_speed / 2.0` is an expression
* `AS half_particle_speed` gives the expression a readable alias
* `ABS(particle_position) * 10.0 > 500` is an expression in the `WHERE` clause

---

## 🔹 Why Use Aliases?

Aliases improve readability and make results easier to understand.

### Syntax

```sql
SELECT col_expression AS expr_description
FROM mytable;
```

---

## 🔹 Column and Table Aliases

Not only expressions, but **columns and tables** can also have aliases.

### Example

```sql
SELECT column AS better_column_name
FROM a_long_widgets_table_name AS mywidgets
INNER JOIN widget_sales
  ON mywidgets.id = widget_sales.widget_id;
```

✔️ This helps shorten long table names and keeps queries clean.

---

## 📊 Tables Used in Exercise

### Table: `movies` (Read-only)

| id | title               | director       | year | length_minutes |
| -- | ------------------- | -------------- | ---- | -------------- |
| 1  | Toy Story           | John Lasseter  | 1995 | 81             |
| 2  | A Bug's Life        | John Lassetter | 1998 | 95             |
| 3  | Toy Story 2         | John Lasseter  | 1999 | 93             |
| 4  | Monsters, Inc.      | Pete Docter    | 2001 | 92             |
| 5  | Finding Nemo        | Andrew Stanton | 2003 | 107            |
| 6  | The Incredibles     | Brad Bird      | 2004 | 116            |
| 7  | Cars                | John Lassetter | 2006 | 117            |
| 8  | Ratatouille         | Brad Bird      | 2007 | 115            |
| 9  | WALL-E              | Andrew Stanton | 2008 | 104            |
| 10 | Up                  | Pete Docter    | 2009 | 101            |
| 11 | Toy Story 3         | Lee Unkrich    | 2010 | 103            |
| 12 | Cars 2              | John Lassetter | 2011 | 120            |
| 13 | Brave               | Brenda Chapman | 2012 | 102            |
| 14 | Monsters University | Dan Scanlon    | 2013 | 110            |

---

### Table: `boxoffice` (Read-only)

| movie_id | rating | domestic_sales | international_sales |
| -------- | ------ | -------------- | ------------------- |
| 5        | 8.2    | 380843261      | 555900000           |
| 14       | 7.4    | 268492764      | 475066843           |
| 8        | 8.0    | 206445654      | 417277164           |
| 12       | 6.4    | 191452396      | 368400000           |
| 3        | 7.9    | 245852179      | 239163000           |
| 6        | 8.0    | 261441092      | 370001000           |
| 9        | 8.5    | 223808164      | 297503696           |
| 11       | 8.4    | 415004880      | 648167031           |
| 1        | 8.3    | 191796233      | 170162503           |
| 7        | 7.2    | 244082982      | 217900167           |
| 10       | 8.3    | 293004164      | 438338580           |
| 4        | 8.1    | 289916256      | 272900000           |
| 2        | 7.2    | 162798565      | 200600000           |
| 13       | 7.2    | 237283207      | 301700000           |

---

## 🧪 Exercises & Solutions

### ✅ Exercise 1

**List all movies and their combined sales in millions of dollars**

```sql
SELECT
  m.title,
  (b.domestic_sales + b.international_sales) / 1000000.0 AS total_sales_millions
FROM movies m
JOIN boxoffice b
  ON m.id = b.movie_id;
```

---

### ✅ Exercise 2

**List all movies and their ratings in percent**

```sql
SELECT
  m.title,
  b.rating * 10 AS rating_percent
FROM movies m
JOIN boxoffice b
  ON m.id = b.movie_id;
```

---

### ✅ Exercise 3

**List all movies that were released on even-numbered years**

```sql
SELECT title, year
FROM movies
WHERE year % 2 = 0;
```

---

## 🧠 Key Takeaways

* SQL expressions allow calculations directly in queries
* Use `AS` to give meaningful names to expressions
* Expressions reduce post-query processing
* Readability is important—keep queries clean and understandable

---

✅ This README fully covers **SQL Lesson 9: Queries with Expressions**, including explanations, tables, exercises, and solutions.
