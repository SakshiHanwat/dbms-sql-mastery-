# SQL Lesson 14: Updating Rows

This README is a **complete and beginner-friendly guide** to **SQL Lesson 14 – Updating Rows** from SQLBolt.

Nothing is skipped. This file includes:

* What UPDATE is and why it’s used
* UPDATE syntax (with and without WHERE)
* Tables used in the lesson
* Common mistakes (VERY important)
* Exercise 14 tasks
* **Full solutions with explanation**

You can use this as:

* Revision notes
* A README.md for GitHub
* Interview prep material

---

## 1. What is UPDATE in SQL?

The **UPDATE** statement is used to **modify existing rows** in a table.

Unlike INSERT (which adds new rows), UPDATE:

* Changes values already stored
* Requires extra care

If done wrong, it can update **all rows** 😬

---

## 2. Basic UPDATE Syntax

```sql
UPDATE mytable
SET column = value_or_expr
WHERE condition;
```

Explanation:

* `mytable` → table name
* `SET` → columns to change
* `WHERE` → which rows to update

⚠️ If you skip `WHERE`, **every row** will be updated.

---

## 3. UPDATE Multiple Columns

```sql
UPDATE mytable
SET column1 = value1,
    column2 = value2
WHERE condition;
```

Multiple columns can be updated at once.

---

## 4. Very Important Safety Tip 🚨

Always do this first:

```sql
SELECT * FROM mytable
WHERE condition;
```

If the SELECT result looks correct, **then** write UPDATE.

This prevents accidental mass updates.

---

## 5. Table Used in This Lesson

### Movies Table

| Column Name    | Data Type | Description     |
| -------------- | --------- | --------------- |
| Id             | INTEGER   | Unique movie ID |
| Title          | TEXT      | Movie title     |
| Director       | TEXT      | Director name   |
| Year           | INTEGER   | Release year    |
| Length_minutes | INTEGER   | Duration        |

---

## 6. Incorrect Data in Movies Table

Some rows contain wrong data and need fixing.

Examples of issues:

* Wrong director
* Wrong year
* Wrong title + director

---

## 7. Exercise 14 – Tasks

### Task 1

The director for **A Bug's Life** is incorrect.

✅ Correct director: **John Lasseter**

---

### Task 2

The release year for **Toy Story 2** is incorrect.

✅ Correct year: **1999**

---

### Task 3

Both the **title and director** for **Toy Story 8** are incorrect.

✅ Correct title: **Toy Story 3**
✅ Correct director: **Lee Unkrich**

---

## 8. Exercise 14 – Solutions

### Solution 1: Fix Director for A Bug's Life

```sql
UPDATE movies
SET Director = 'John Lasseter'
WHERE Title = 'A Bug''s Life';
```

Explanation:

* Only updates A Bug's Life
* Other rows remain untouched

---

### Solution 2: Fix Year for Toy Story 2

```sql
UPDATE movies
SET Year = 1999
WHERE Title = 'Toy Story 2';
```

Explanation:

* Corrects the wrong year (1899 → 1999)

---

### Solution 3: Fix Title and Director for Toy Story 8

```sql
UPDATE movies
SET Title = 'Toy Story 3',
    Director = 'Lee Unkrich'
WHERE Id = 11;
```

Explanation:

* Updates two columns at once
* Uses Id for accuracy

---

## 9. Verify Updates

```sql
SELECT * FROM movies;
```

Always verify after UPDATE.

---

## 10. Common Mistakes to Avoid ❌

❌ Forgetting WHERE clause
❌ Updating wrong rows
❌ Not testing condition with SELECT
❌ Using wrong data types

---

## 11. Key Takeaways ⭐

* UPDATE modifies existing data
* WHERE clause is mandatory for safety
* You can update multiple columns
* Always verify with SELECT

---

## 12. Beginner Memory Trick 🧠

> INSERT → Add new row
> UPDATE → Fix existing row
> DELETE → Remove row

Practice slowly, accuracy matters more than speed 💪

---

**End of README**
