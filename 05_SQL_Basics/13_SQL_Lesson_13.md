# SQL Lesson 13: Inserting Rows

This README is a **complete, beginner‑friendly explanation** of **SQL Lesson 13 (Inserting Rows)** from SQLBolt. Nothing is skipped. It includes:

* What a schema is
* Tables used in the lesson
* INSERT syntax (all variations)
* Expressions in INSERT
* Exercises
* **Full solutions** with explanations

This file is written so you can revise later or share with someone who is learning SQL from scratch.

---

## 1. What is a Database Schema?

A **schema** defines the **structure of a table** in a database.

It tells:

* What columns exist
* What datatype each column can store (INT, TEXT, etc.)
* Which columns are required
* Which columns auto‑increment

Think of schema like a **blueprint** of a table.

Example:

* `Year` → Integer only
* `Title` → String/Text only

This strict structure keeps data:

* Fast
* Consistent
* Reliable (even with millions of rows)

---

## 2. Tables Used in This Lesson

### Movies Table (Read‑Only)

| Column Name    | Data Type                | Description     |
| -------------- | ------------------------ | --------------- |
| Id             | INTEGER (Auto Increment) | Unique movie ID |
| Title          | TEXT                     | Movie name      |
| Director       | TEXT                     | Director name   |
| Year           | INTEGER                  | Release year    |
| Length_minutes | INTEGER                  | Movie duration  |

Sample data:

| Id | Title        | Director      | Year | Length_minutes |
| -- | ------------ | ------------- | ---- | -------------- |
| 1  | Toy Story    | John Lasseter | 1995 | 81             |
| 2  | A Bug's Life | John Lasseter | 1998 | 95             |
| 3  | Toy Story 2  | John Lasseter | 1999 | 93             |

---

### Boxoffice Table (Read‑Only)

| Column Name         | Data Type | Description          |
| ------------------- | --------- | -------------------- |
| Movie_id            | INTEGER   | References Movies.Id |
| Rating              | FLOAT     | Movie rating         |
| Domestic_sales      | INTEGER   | US sales             |
| International_sales | INTEGER   | Global sales         |

Sample data:

| Movie_id | Rating | Domestic_sales | International_sales |
| -------- | ------ | -------------- | ------------------- |
| 1        | 8.3    | 191796233      | 170162503           |
| 2        | 7.2    | 162798565      | 200600000           |
| 3        | 7.9    | 245852179      | 239163000           |

---

## 3. INSERT Statement – Basics

To add new data, we use **INSERT INTO**.

### Insert into all columns

```sql
INSERT INTO mytable
VALUES (value1, value2, value3);
```

⚠️ Order of values **must match table columns exactly**.

---

## 4. INSERT with Specific Columns (Recommended)

This is safer and future‑proof.

```sql
INSERT INTO mytable (column1, column2)
VALUES (value1, value2);
```

Benefits:

* Auto‑increment columns can be skipped
* Adding new columns later won’t break old queries

---

## 5. INSERT Multiple Rows at Once

```sql
INSERT INTO mytable (col1, col2)
VALUES (v1, v2),
       (v3, v4),
       (v5, v6);
```

Efficient and clean 👍

---

## 6. INSERT Using Expressions

You can use math and expressions while inserting.

```sql
INSERT INTO boxoffice (movie_id, rating, domestic_sales)
VALUES (1, 9.9, 283742034 / 1000000);
```

This ensures consistent formatting.

---

## 7. Exercise 13 – Tasks

### Task 1

Add the studio's new production **Toy Story 4** to the **Movies** table.

Rules:

* Id is auto‑increment → do NOT insert it
* You can use **any director**

---

### Task 2

Toy Story 4 box office details:

* Rating: **8.7**
* Domestic sales: **340 million**
* International sales: **270 million**

Add this record to the **Boxoffice** table.

---

## 8. Exercise 13 – Solutions

### Solution 1: Insert into Movies

```sql
INSERT INTO movies (Title, Director, Year, Length_minutes)
VALUES ('Toy Story 4', 'Josh Cooley', 2019, 100);
```

Explanation:

* Id skipped (auto‑increment)
* Columns explicitly mentioned
* Clean and safe insertion

---

### Solution 2: Insert into Boxoffice

```sql
INSERT INTO boxoffice (Movie_id, Rating, Domestic_sales, International_sales)
VALUES (15, 8.7, 340000000, 270000000);
```

Explanation:

* `Movie_id` should match Toy Story 4's Id
* Sales entered in full numbers

---

## 9. Verify Inserted Data

```sql
SELECT * FROM movies;
SELECT * FROM boxoffice;
```

This confirms the rows were inserted correctly.

---

## 10. Key Takeaways (Very Important)

* INSERT adds new rows
* Always prefer column‑specific INSERT
* Auto‑increment columns should be skipped
* Expressions can be used while inserting
* Schema controls what data is allowed

---

## 11. Beginner Tip 💡

If SQL ever feels confusing, remember:

> **SELECT = read**
> **INSERT = add**
> **UPDATE = change**
> **DELETE = remove**

You’re doing great. Keep practicing step by step 🚀

---

**End of README**
