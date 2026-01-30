# 📘 SQLBolt – Simple SELECT Queries (Complete Notes with Exercises & Solutions)

This README is a beginner-friendly reference for learning **basic SQL SELECT queries** using examples inspired by SQLBolt lessons. It includes:

* Full table structures
* All exercises
* Clear solutions
* Proper SQL syntax

Anyone can study this file and practice SQL from scratch.

---

## 🗂 Table: `movies`

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

# 🟢 Exercise 1 – Basic SELECT

### 1. Find the title of each film

```sql
SELECT title FROM movies;
```

### 2. Find the director of each film

```sql
SELECT director FROM movies;
```

### 3. Find the title and director of each film

```sql
SELECT title, director FROM movies;
```

### 4. Find the title and year of each film

```sql
SELECT title, year FROM movies;
```

### 5. Find all information about each film

```sql
SELECT * FROM movies;
```

---

# 🟢 Exercise 2 – Constraints

### 1. Find the movie with row id = 6

```sql
SELECT * FROM movies WHERE id = 6;
```

### 2. Find movies released between 2000 and 2010

```sql
SELECT * FROM movies WHERE year BETWEEN 2000 AND 2010;
```

### 3. Find movies NOT released between 2000 and 2010

```sql
SELECT * FROM movies WHERE year NOT BETWEEN 2000 AND 2010;
```

### 4. Find first 5 Pixar movies and their release year

```sql
SELECT title, year FROM movies ORDER BY year ASC LIMIT 5;
```

---

# 🟢 Exercise 3 – String Constraints

### 1. Find all Toy Story movies

```sql
SELECT * FROM movies WHERE title LIKE 'Toy Story%';
```

### 2. Find all movies directed by John Lasseter

```sql
SELECT * FROM movies WHERE director = 'John Lasseter';
```

### 3. Find movies not directed by John Lasseter

```sql
SELECT title, director FROM movies WHERE director != 'John Lasseter';
```

### 4. Find all WALL-* movies

```sql
SELECT * FROM movies WHERE title LIKE 'WALL%';
```

---

# 🟢 Exercise 4 – Filtering & Sorting

### 1. List all directors (alphabetically, no duplicates)

```sql
SELECT DISTINCT director FROM movies ORDER BY director ASC;
```

### 2. Last 4 Pixar movies (most recent to least)

```sql
SELECT title, year FROM movies ORDER BY year DESC LIMIT 4;
```

### 3. First 5 Pixar movies sorted alphabetically

```sql
SELECT title FROM movies ORDER BY title ASC LIMIT 5;
```

### 4. Next 5 Pixar movies sorted alphabetically

```sql
SELECT title FROM movies ORDER BY title ASC LIMIT 5 OFFSET 5;
```

---

## 🗂 Table: `north_american_cities`

| City         | Country       | Population | Latitude  | Longitude   |
| ------------ | ------------- | ---------- | --------- | ----------- |
| Guadalajara  | Mexico        | 1500800    | 20.659699 | -103.349609 |
| Toronto      | Canada        | 2795060    | 43.653226 | -79.383184  |
| Houston      | United States | 2195914    | 29.760427 | -95.369803  |
| New York     | United States | 8405837    | 40.712784 | -74.005941  |
| Philadelphia | United States | 1553165    | 39.952584 | -75.165222  |
| Havana       | Cuba          | 2106146    | 23.05407  | -82.345189  |
| Mexico City  | Mexico        | 8555500    | 19.432608 | -99.133208  |
| Phoenix      | United States | 1513367    | 33.448377 | -112.074037 |
| Los Angeles  | United States | 3884307    | 34.052234 | -118.243685 |
| Ecatepec     | Mexico        | 1742000    | 19.601841 | -99.050674  |

---

# 🟢 Review Exercise – Cities

### 1. List all Canadian cities and populations

```sql
SELECT city, population FROM north_american_cities WHERE country = 'Canada';
```

### 2. Order US cities by latitude (north to south)

```sql
SELECT city, latitude FROM north_american_cities
WHERE country = 'United States'
ORDER BY latitude DESC;
```

### 3. Cities west of Chicago (longitude < -87.6298)

```sql
SELECT city, longitude FROM north_american_cities
WHERE longitude < -87.6298
ORDER BY longitude ASC;
```

### 4. Two largest cities in Mexico

```sql
SELECT city, population FROM north_american_cities
WHERE country = 'Mexico'
ORDER BY population DESC
LIMIT 2;
```

### 5. 3rd and 4th largest US cities

```sql
SELECT city, population FROM north_american_cities
WHERE country = 'United States'
ORDER BY population DESC
LIMIT 2 OFFSET 2;
```

---

# 📌 SQL Template

```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column ASC|DESC
LIMIT number OFFSET number;
```

---

✅ This README is suitable for:

* Beginners learning SQL
* Interview revision
* College DBMS practice
* Data Engineering foundations

---

✨ Happy Learning SQL!
