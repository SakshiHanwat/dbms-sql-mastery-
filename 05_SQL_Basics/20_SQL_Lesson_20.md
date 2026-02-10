# 📘 SQL Topic: Unions, Intersections & Exceptions

## 🔹 Introduction

Jab hum multiple tables ke saath kaam karte hain, tab kabhi-kabhi unke results ko combine karna padta hai.
Is case me SQL ke **set operators** ka use hota hai:

* UNION
* UNION ALL
* INTERSECT
* EXCEPT

Ye operators tab kaam karte hain jab dono queries:

* Same number of columns return karein
* Same order me columns ho
* Compatible data types ho

---

## 🔹 UNION and UNION ALL

**UNION** aur **UNION ALL** dono ek query ke result ko dusri query ke result ke saath append kar dete hain.

Difference:

* UNION → duplicate rows remove karta hai
* UNION ALL → duplicate rows bhi allow karta hai

---

## 🔹 General Syntax (Set Operators)

```sql
SELECT column, another_column
   FROM mytable
UNION / UNION ALL / INTERSECT / EXCEPT
SELECT other_column, yet_another_column
   FROM another_table
ORDER BY column DESC
LIMIT n;
```

### Important Points:

* UNION, INTERSECT, EXCEPT → ORDER BY aur LIMIT se pehle execute hote hain
* Ye operators JOIN ka alternative ho sakte hain jab tables join nahi ho sakti
* Result set ko ek single table jaisa treat kiya jata hai

---

## 🔹 INTERSECT

INTERSECT operator sirf wahi rows return karta hai jo **dono result sets me common (identical)** hoti hain.

* Common rows only
* Duplicate rows automatically remove ho jati hain

---

## 🔹 EXCEPT

EXCEPT operator:

* Sirf wahi rows return karta hai jo **first query me ho**
* Aur **second query me na ho**

⚠️ EXCEPT **order-sensitive** hota hai (LEFT JOIN / RIGHT JOIN jaisa):

* Query order change karne se result bhi change ho jata hai

---

## 🔹 ALL Variants (Database dependent)

Kuch databases support karte hain:

* INTERSECT ALL
* EXCEPT ALL

Inka matlab:

* Duplicate rows bhi retain (keep) ki ja sakti hain

---

## 🔹 Execution Order (Recall from Lesson 12)

Order of execution me:

1. Pehle UNION / INTERSECT / EXCEPT execute hota hai
2. Uske baad ORDER BY
3. Uske baad LIMIT

---

## 🎯 Summary

* UNION → combine results, duplicates remove
* UNION ALL → combine results, duplicates keep
* INTERSECT → common rows only
* EXCEPT → first result se second result subtract karta hai
* Queries ke columns same count, order aur type ke hone chahiye

---
