# SQL Lesson 15: Deleting Rows

This README is a **complete, beginner-friendly explanation** of **SQL Lesson 15 – Deleting Rows** from SQLBolt.

Nothing is skipped. This file includes:

* What DELETE is and when to use it
* DELETE syntax (with and without WHERE)
* Table used in the lesson
* Safety rules (VERY important)
* Exercise 15 tasks
* **Full solutions with explanation**

You can safely use this as:

* Revision notes
* README.md for GitHub
* Interview preparation material

---

## 1. What is DELETE in SQL?

The **DELETE** statement is used to **remove rows** from a table.

Important difference:

* INSERT → adds rows
* UPDATE → modifies rows
* DELETE → permanently removes rows

⚠️ Once deleted, data is **gone** unless you have a backup.

---

## 2. Basic DELETE Syntax

```sql
DELETE FROM mytable
WHERE condition;
```

Explanation:

* `mytable` → table name
* `WHERE` → decides which rows are deleted

---

## 3. DELETE Without WHERE (Danger Zone 🚨)

```sql
DELETE FROM mytable;
```

This deletes **ALL rows** in the table.

✔️ Useful only when you want to completely empty a table.
❌ Extremely dangerous in production databases.

---

## 4. Safety Rule (Must Follow)

Before running DELETE, **always test the condition**:

```sql
SELECT * FROM mytable
WHERE condition;
```

If the SELECT result looks correct, then execute DELETE.

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

## 6. Exercise 15 – Tasks

### Task 1

This database is getting too big.

🗑️ Remove **all movies released before 2005**.

---

### Task 2

Andrew Stanton has left the studio.

🗑️ Remove **all movies directed by Andrew Stanton**.

---

## 7. Exercise 15 – Solutions

### Solution 1: Delete Movies Released Before 2005

```sql
DELETE FROM movies
WHERE Year < 2005;
```

Explanation:

* Deletes only movies older than 2005
* Keeps newer movies safe

---

### Solution 2: Delete Movies Directed by Andrew Stanton

```sql
DELETE FROM movies
WHERE Director = 'Andrew Stanton';
```

Explanation:

* Deletes only rows where director matches
* Other directors remain untouched

---

## 8. Verify Remaining Data

```sql
SELECT * FROM movies;
```

Always verify after DELETE.

---

## 9. Common Mistakes to Avoid ❌

❌ Forgetting WHERE clause
❌ Not testing condition with SELECT
❌ Deleting more rows than intended
❌ Running DELETE directly on production data

---

## 10. Key Takeaways ⭐

* DELETE permanently removes data
* WHERE clause controls what gets deleted
* Always SELECT before DELETE
* Read DELETE queries twice, execute once

---

## 11. Easy Memory Trick 🧠

> INSERT → Add
> UPDATE → Fix
> DELETE → Remove

Accuracy > Speed in SQL 💯

---

**End of README**
