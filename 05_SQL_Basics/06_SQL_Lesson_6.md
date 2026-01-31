# SQL Lesson 6: Multi-table Queries with JOINs

## Overview

Up to now, we have been working with queries on a **single table**. However, in real-world databases, entity data is usually **split across multiple tables**. This is done using a process called **database normalization**.

In this lesson, we learn how to retrieve data spread across multiple tables using **JOINs**, specifically the **INNER JOIN**.

---

## Database Normalization

### What is Database Normalization?

Database normalization is a design technique used to organize data efficiently by:

* Minimizing **duplicate data** in tables
* Allowing different parts of the database to **grow independently**

### Why Normalization is Useful

* Reduces data redundancy
* Improves data integrity
* Makes updates easier and safer

### Trade-offs of Normalization

* Queries become slightly more **complex**
* Performance issues may arise when joining many **large tables**

---

## Multi-table Queries with JOINs

When data is spread across multiple tables, we use **JOIN clauses** to combine related data.

### Primary Keys

Tables that share information about the same entity must have a **primary key** that uniquely identifies each record.

Common primary key types:

* Auto-incrementing integers (most common)
* Strings
* Hashed values

The key requirement: **it must be unique**.

---

## INNER JOIN

### What is an INNER JOIN?

An **INNER JOIN** returns rows only when there is a **matching value in both tables** based on a specified condition.

### General Syntax

```sql
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table
    ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

### How INNER JOIN Works

* Matches rows from both tables using the `ON` condition
* Combines columns from both tables into a single result
* Applies `WHERE`, `ORDER BY`, `LIMIT`, etc. **after** joining

### Did You Know?

* `JOIN` and `INNER JOIN` mean the same thing
* `INNER JOIN` is preferred for clarity when working with multiple join types

---

## Database Used in This Lesson (Pixar Database)

### Table 1: Movies (Read-Only)

| Id | Title           | Director       | Year | Length_minutes |
| -- | --------------- | -------------- | ---- | -------------- |
| 1  | Toy Story       | John Lasseter  | 1995 | 81             |
| 2  | A Bug's Life    | John Lasseter  | 1998 | 95             |
| 3  | Toy Story 2     | John Lasseter  | 1999 | 93             |
| 4  | Monsters, Inc.  | Pete Docter    | 2001 | 92             |
| 5  | Finding Nemo    | Andrew Stanton | 2003 | 107            |
| 6  | The Incredibles | Brad Bird      | 2004 | 116            |
| 7  | Cars            | John Lasseter  | 2006 | 117            |
| 8  | Ratatouille     | Brad Bird      | 2007 | 115            |
| 9  | WALL-E          | Andrew Stanton | 2008 | 104            |
| 10 | Up              | Pete Docter    | 2009 | 101            |

---

### Table 2: BoxOffice (Read-Only)

| Movie_id | Rating | Domestic_sales | International_sales |
| -------- | ------ | -------------- | ------------------- |
| 5        | 8.2    | 380843261      | 555900000           |
| 14       | 7.4    | 268492764      | 475066843           |
| 8        | 8.0    | 206445654      | 417277164           |
| 12       | 6.4    | 191452396      | 368400000           |
| 3        | 7.9    | 245852179      | 239163000           |
| 6        | 8.0    | 261441092      | 370001000           |

> **Note:** `Movie_id` in the BoxOffice table corresponds to `Id` in the Movies table (1-to-1 relationship).

---

## Exercises

### Exercise 1: Find the domestic and international sales for each movie

#### Query

```sql
SELECT
    movies.title,
    boxoffice.domestic_sales,
    boxoffice.international_sales
FROM movies
INNER JOIN boxoffice
    ON movies.id = boxoffice.movie_id;
```

---

### Exercise 2: Show the sales numbers for each movie that did better internationally than domestically

#### Query

```sql
SELECT
    movies.title,
    boxoffice.domestic_sales,
    boxoffice.international_sales
FROM movies
INNER JOIN boxoffice
    ON movies.id = boxoffice.movie_id
WHERE boxoffice.international_sales > boxoffice.domestic_sales;
```

---

### Exercise 3: List all the movies by their ratings in descending order

#### Query

```sql
SELECT
    movies.title,
    boxoffice.rating
FROM movies
INNER JOIN boxoffice
    ON movies.id = boxoffice.movie_id
ORDER BY boxoffice.rating DESC;
```

---

## Key Takeaways

* Real-world databases use **multiple tables**
* **Normalization** reduces redundancy but increases query complexity
* **INNER JOIN** combines rows that match in both tables
* Always join tables using a **common key**
* Filtering and sorting happen **after** the join

---
