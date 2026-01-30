# SQL Lesson 3: Queries with Constraints (Part 2)

When writing **WHERE clauses** with columns containing **text data**, SQL provides several useful operators that help with:

* Case-sensitive and case-insensitive comparisons
* Pattern matching using wildcards
* Filtering using lists of values

These operators make queries more flexible and powerful when working with textual data.

---

## Text Data Operators in SQL

| Operator       | Condition                                        | Example                           |
| -------------- | ------------------------------------------------ | --------------------------------- |
| `=`            | Case-sensitive exact string comparison           | `col_name = "abc"`                |
| `!=` or `<>`   | Case-sensitive string inequality                 | `col_name != "abcd"`              |
| `LIKE`         | Case-insensitive string comparison               | `col_name LIKE "ABC"`             |
| `NOT LIKE`     | Case-insensitive string inequality               | `col_name NOT LIKE "ABCD"`        |
| `%`            | Matches zero or more characters (used with LIKE) | `col_name LIKE "%AT%"`            |
| `_`            | Matches exactly one character (used with LIKE)   | `col_name LIKE "AN_"`             |
| `IN (...)`     | Value exists in a given list                     | `col_name IN ("A", "B", "C")`     |
| `NOT IN (...)` | Value does not exist in a list                   | `col_name NOT IN ("D", "E", "F")` |

---

## Wildcard Explanation

* `%` → Matches **any number of characters** (including zero)

  * Example: `%AT%` matches `AT`, `ATTIC`, `CAT`, `BATS`

* `_` → Matches **exactly one character**

  * Example: `AN_` matches `AND`, but not `AN`

---

## Important Note on Strings

All string values in SQL **must be enclosed in quotes** (single or double, depending on DBMS). This helps the SQL parser distinguish string values from SQL keywords.

Example:

```sql
WHERE name = "John"
```

---

## Performance Note

Although these operators are efficient for most use cases, **full-text search** is better handled by specialized tools such as:

* Apache Lucene
* Sphinx

These tools are optimized for large-scale text search, internationalization, and advanced query features.

---

## SQL Syntax: SELECT with Constraints

```sql
SELECT column, another_column, ...
FROM mytable
WHERE condition
  AND/OR another_condition
  AND/OR ...;
```

---

## Summary

* SQL provides multiple operators for filtering text-based data
* `LIKE` with `%` and `_` enables powerful pattern matching
* `IN` and `NOT IN` simplify multiple-value comparisons
* Proper quoting of strings is mandatory
* WHERE clause conditions improve query precision and performance
