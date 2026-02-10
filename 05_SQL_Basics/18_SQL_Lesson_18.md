# 📘 SQL Lesson 18: Dropping Tables

## 🔹 Introduction

Kabhi-kabhi hume poori table ko hi database se remove karna padta hai — data ke saath-saath uska structure (schema) bhi delete karna hota hai.
Iske liye SQL me **DROP TABLE** statement use hota hai.

Ye **DELETE** statement se alag hota hai:

* DELETE → sirf rows (data) delete karta hai
* DROP TABLE → poori table + schema delete karta hai

---

## 🔹 Drop Table Statement

### Syntax:

```sql
DROP TABLE IF EXISTS mytable;
```

### Explanation:

* Agar table exist karta hai → delete ho jayega
* Agar table exist nahi karta → normally error aata
* **IF EXISTS** clause error ko suppress (avoid) kar deta hai

---

## 🔹 Dependent Tables (Foreign Key Case)

Agar koi dusri table is table par depend karti hai (jaise FOREIGN KEY relation), to:

* Ya to pehle dependent rows remove karni hongi
* Ya phir dependent table hi drop karni padegi

Nahi to database error throw karega.

---

## 📝 Exercise

We've reached the end of our exercises, so lets clean up by removing all the tables we've worked with.

Tasks:

1. Drop the **Movies** table
2. Drop the **BoxOffice** table

---

## 📊 Table: movies (Read-only)

| id | title               | director       | year | length_minutes |
| -- | ------------------- | -------------- | ---- | -------------- |
| 1  | Toy Story           | John Lasseter  | 1995 | 81             |
| 2  | A Bug's Life        | John Lasseter  | 1998 | 95             |
| 3  | Toy Story 2         | John Lasseter  | 1999 | 93             |
| 4  | Monsters, Inc.      | Pete Docter    | 2001 | 92             |
| 5  | Finding Nemo        | Andrew Stanton | 2003 | 107            |
| 6  | The Incredibles     | Brad Bird      | 2004 | 116            |
| 7  | Cars                | John Lassetter | 2006 | 117            |
| 8  | Ratatouille         | Brad Bird      | 2007 | 115            |
| 9  | WALL-E              | Andrew Stanton | 2008 | 104            |
| 10 | Up                  | Pete Docter    | 2009 | 101            |
| 11 | Toy Story 3         | Lee Unkrich    | 2010 | 103            |
| 12 | Cars 2              | John Lasseter  | 2011 | 120            |
| 13 | Brave               | Brenda Chapman | 2012 | 102            |
| 14 | Monsters University | Dan Scanlon    | 2013 | 110            |

---

## 📊 Table: boxoffice (Read-only)

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

## ✅ Solution

### ✔ Drop Movies table

```sql
DROP TABLE IF EXISTS movies;
```

### ✔ Drop BoxOffice table

```sql
DROP TABLE IF EXISTS boxoffice;
```

---

## 🎯 Summary

* DROP TABLE poori table ko delete karta hai (data + schema)
* IF EXISTS error se bachata hai
* Dependent tables ka dhyaan rakhna zaroori hai
* Ye last lesson tha, isliye cleanup ke liye tables drop ki gayi

---

