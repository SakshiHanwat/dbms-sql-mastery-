# 📘 SQL Lesson 17: Altering Tables

## 🔹 Introduction

Jaise-jaise time ke saath data change hota hai, waise-waise hume apne database ka structure (schema) bhi change karna padta hai.
SQL me ye kaam **ALTER TABLE** statement se hota hai.

ALTER TABLE ka use karke hum:

* New column add kar sakte hain
* Column remove kar sakte hain
* Table ka naam change kar sakte hain
* Column constraints aur default values modify kar sakte hain

---

## 🔹 Adding Columns

New column add karne ka syntax CREATE TABLE jaisa hi hota hai.
Hume column ka **data type**, aur agar chahiye to **constraint** ya **default value** bhi deni hoti hai.

### Syntax:

```sql
ALTER TABLE mytable
ADD column DataType OptionalTableConstraint
    DEFAULT default_value;
```

Notes:

* DataType batata hai kis type ka data store hoga (INT, TEXT, FLOAT, etc.)
* DEFAULT value existing rows aur new rows dono par apply hoti hai
* MySQL me FIRST ya AFTER clause hota hai, par ye standard SQL feature nahi hai

---

## 🔹 Removing Columns

Column remove karne ke liye DROP use hota hai.

### Syntax:

```sql
ALTER TABLE mytable
DROP column_to_be_deleted;
```

⚠️ Important:

* Kuch databases jaise **SQLite** DROP COLUMN support nahi karte
* Aise case me nayi table bana ke purana data migrate karna padta hai

---

## 🔹 Renaming the Table

Table ka naam change karne ke liye RENAME TO clause use hota hai.

### Syntax:

```sql
ALTER TABLE mytable
RENAME TO new_table_name;
```

---

## 🔹 Other Changes

Har database (MySQL, PostgreSQL, SQLite, SQL Server) ALTER TABLE ke different features support karta hai.
Isliye hamesha apni database documentation check karni chahiye.

---

## 📊 Table: Movies

| id | title               | director       | year | length_minutes |
| -- | ------------------- | -------------- | ---- | -------------- |
| 4  | Monsters, Inc.      | Pete Docter    | 2001 | 92             |
| 5  | Finding Nemo        | Andrew Stanton | 2003 | 107            |
| 6  | The Incredibles     | Brad Bird      | 2004 | 116            |
| 7  | Cars                | John Lasseter  | 2006 | 117            |
| 8  | Ratatouille         | Brad Bird      | 2007 | 115            |
| 9  | WALL-E              | Andrew Stanton | 2008 | 104            |
| 10 | Up                  | Pete Docter    | 2009 | 101            |
| 11 | Toy Story 3         | Lee Unkrich    | 2010 | 103            |
| 12 | Cars 2              | John Lasseter  | 2011 | 120            |
| 13 | Brave               | Brenda Chapman | 2012 | 102            |
| 14 | Monsters University | Dan Scanlon    | 2013 | 110            |

---

## 📝 Exercise 17 — Tasks

### 1️⃣ Task 1

Add a column named **Aspect_ratio** with a **FLOAT** data type to store the aspect-ratio each movie was released in.

### 2️⃣ Task 2

Add another column named **Language** with a **TEXT** data type to store the language that the movie was released in.
Ensure that the default for this language is **English**.

---

## ✅ Solution

### ✔ Solution for Task 1

```sql
ALTER TABLE movies
ADD Aspect_ratio FLOAT;
```

### ✔ Solution for Task 2

```sql
ALTER TABLE movies
ADD Language TEXT DEFAULT 'English';
```

---

## 🎯 Summary

* ALTER TABLE se hum table ka structure change karte hain
* ADD se new column add hota hai
* DROP se column remove hota hai
* RENAME TO se table ka naam change hota hai
* DEFAULT se default value set hoti hai

---
