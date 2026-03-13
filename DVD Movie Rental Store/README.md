# SQL Practice – 200 Queries on Sakila Database

## Overview

This repository contains **200 structured SQL practice queries** written using the **Sakila Sample Database**.
The goal of this project is to practice and demonstrate core SQL concepts ranging from **basic SELECT statements to advanced analytical queries**.

All queries are organized logically by topic so learners can gradually move from beginner to advanced SQL.

This project is useful for:

* SQL beginners practicing real database queries
* Students preparing for technical interviews
* Learning relational database relationships
* Understanding complex SQL concepts through real examples

---

# Database Used

## Sakila Database

The **Sakila Database** is a sample database originally created by MySQL to simulate a **DVD rental store system**.

It contains multiple interconnected tables representing:

* Films
* Actors
* Customers
* Rentals
* Payments
* Stores
* Staff
* Inventory
* Locations

The database demonstrates a **real-world relational schema**, making it ideal for SQL practice.

---

# Database Schema Overview

Key tables and their purpose:

| Table         | Description                                        |
| ------------- | -------------------------------------------------- |
| actor         | Stores actor information                           |
| film          | Stores film details                                |
| film_actor    | Many-to-many relationship between films and actors |
| category      | Film categories                                    |
| film_category | Mapping between films and categories               |
| customer      | Customer details                                   |
| address       | Address information                                |
| city          | City details                                       |
| country       | Country details                                    |
| inventory     | Physical copies of films in stores                 |
| rental        | Records of film rentals                            |
| payment       | Payment transactions                               |
| store         | Store locations                                    |
| staff         | Store staff members                                |
| language      | Film language                                      |

---

# Table Relationships

Main relational structure:

```
country
   │
   └── city
          │
          └── address
                 │
                 ├── customer
                 ├── staff
                 └── store

film
 ├── film_actor ── actor
 ├── film_category ── category
 └── inventory
         │
         └── rental
               │
               └── payment
```

This schema demonstrates important relational database concepts such as:

* **One-to-Many relationships**
* **Many-to-Many relationships**
* **Foreign keys**
* **Data normalization**

---

# Query Categories

The repository contains **200 SQL queries** divided into the following sections.

## 1. Basic SELECT Queries

Basic data retrieval from tables.

Examples:

* Display all actors
* Show film titles and release years
* List customer emails

---

## 2. Filtering Queries

Using conditions to filter records.

Concepts used:

* `WHERE`
* `LIKE`
* `BETWEEN`
* `IN`
* comparison operators

Examples:

* Films longer than 120 minutes
* Customers whose name starts with "S"
* Payments greater than $8

---

## 3. Aggregation Queries

Using aggregate functions to summarize data.

Functions used:

* `COUNT()`
* `SUM()`
* `AVG()`
* `MIN()`
* `MAX()`

Examples:

* Total number of actors
* Average film length
* Total payments received

---

## 4. GROUP BY and HAVING

Grouping records and filtering grouped results.

Concepts used:

* `GROUP BY`
* `HAVING`

Examples:

* Customers with more than 10 rentals
* Categories with more than 50 films
* Films with more than 5 actors

---

## 5. JOIN Queries

Combining data from multiple tables.

Types used:

* `INNER JOIN`
* `LEFT JOIN`
* multi-table joins

Examples:

* Films with their categories
* Customers with full address
* Rentals with customer details

---

## 6. Subqueries

Queries nested inside another query.

Examples:

* Films with rental rate above average
* Customers with highest payments
* Films never rented

---

## 7. CTE (Common Table Expressions)

Temporary result sets used inside queries.

Syntax used:

```
WITH cte_name AS (
    SELECT ...
)
SELECT * FROM cte_name;
```

Examples:

* Total revenue per store
* Customer rental counts
* Top revenue films

---

## 8. Window Functions

Advanced SQL functions used for ranking and analytics.

Functions used:

* `ROW_NUMBER()`
* `RANK()`
* `DENSE_RANK()`
* `PARTITION BY`

Examples:

* Rank films by rental rate
* Rank customers by total payments
* Top films per category

---

# Skills Practiced

This project demonstrates practical usage of:

* SQL Query Writing
* Database Relationships
* Data Aggregation
* Multi-table Joins
* Analytical Queries
* Window Functions
* Query Optimization Thinking

---

# Project Structure

```
sakila-sql-practice
│
├── queries.sql
├── README.md
└── sakila-database-files
```

---

# Total Queries

| Category          | Queries         |
| ----------------- | --------------- |
| SELECT Queries    | 20              |
| Filtering         | 20              |
| Aggregation       | 30              |
| GROUP BY + HAVING | 20              |
| JOIN Queries      | 50              |
| Subqueries        | 20              |
| CTE               | 20              |
| Window Functions  | 20              |
| Total             | **200 Queries** |

---

# Purpose of This Project

This repository was created to:

* Build strong SQL fundamentals
* Practice complex SQL problems
* Understand relational database design
* Create a structured SQL learning resource

---

# Author

Darshan Dudhat
IT Student | SQL Learner
