# 📘 SQL Topic: Subqueries

## 🔹 Introduction

Kabhi-kabhi ek single SQL query se hum apne data ke saare questions ka answer nahi nikal sakte. Aise cases me ya to:

* Multiple queries likhkar manually process karein, ya
* Ek hi complex query ke andar **subquery** ka use karein.

👉 **Subquery** ka matlab hota hai: ek query ke andar doosri query.

---

## 🔹 Example: General Subquery

Maan lo tumhari company ke paas **Sales Associates** ki list hai, jisme unka:

* Revenue generated
* Salary

data diya hua hai.

Ab tumhe nikalna hai kaun se associates company ko **average revenue se zyada cost** kar rahe hain.

### Step 1: Average revenue nikalna

```sql
SELECT AVG(revenue_generated)
FROM sales_associates;
```

### Step 2: Subquery use karke compare karna

```sql
SELECT *
FROM sales_associates
WHERE salary >
   (SELECT AVG(revenue_generated)
    FROM sales_associates);
```

### Explanation:

* Inner query pehle average revenue nikalti hai
* Outer query har associate ki salary ko us average se compare karti hai
* Jo salary average revenue se zyada hogi, wo rows return hongi

---

## 🔹 Where Subqueries Can Be Used

Subqueries ko hum normally jahan table ya value use karte hain, wahan use kar sakte hain:

* `FROM` clause me (JOIN ke saath)
* `WHERE` clause me
* `HAVING` clause me
* `SELECT` clause me expressions ke andar

⚠️ Rules:

* Har subquery parentheses `( )` ke andar honi chahiye
* Subqueries kisi bhi table ko reference kar sakti hain
* Kuch databases LIMIT / OFFSET allow nahi karte subquery ke andar

---

## 🔹 Correlated Subqueries

Correlated subquery wo hoti hai jisme:

* Inner query outer query ke column par depend karti hai
* Inner query har row ke liye alag-alag run hoti hai

---

## 🔹 Example: Correlated Subquery

Maan lo tumhare paas **Employees** table hai jisme:

* Department (engineering, sales, etc.)
* Revenue generated
* Salary

Ab tumhe nikalna hai kaun se employees apne department ke average se **worse perform** kar rahe hain.

```sql
SELECT *
FROM employees
WHERE salary >
   (SELECT AVG(revenue_generated)
    FROM employees AS dept_employees
    WHERE dept_employees.department = employees.department);
```

### Explanation:

* Outer query har employee ko check karti hai
* Inner query us employee ke department ka average revenue nikalti hai
* Comparison hota hai: employee salary > department average revenue

---

## 🔹 Notes on Correlated Subqueries

* Ye queries powerful hoti hain
* Lekin samajhna thoda difficult hota hai
* Performance slow ho sakti hai
* Isliye meaningful aliases use karna chahiye

---

## 🔹 Existence Tests (IN / NOT IN with Subquery)

Normal case me:

```sql
WHERE column IN (value1, value2, value3)
```

Dynamic list ke saath (subquery):

```sql
SELECT *
FROM mytable
WHERE column
    IN/NOT IN (SELECT another_column
               FROM another_table);
```

### Explanation:

* Inner query ek list return karti hai
* Outer query check karti hai ki column ki value us list me hai ya nahi

---

## 🎯 Key Points Summary

* Subquery = query ke andar query
* Parentheses mandatory `( )`
* FROM, WHERE, HAVING, SELECT me use ho sakti hai
* Correlated subquery outer query ke data par depend karti hai
* IN / NOT IN ke saath existence test hota hai

---

