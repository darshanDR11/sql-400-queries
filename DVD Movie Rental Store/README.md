# Sakila SQL Practice – 200 Query Project

This project contains **200 SQL practice queries** using the **Sakila Database**.
The goal is to cover essential and advanced SQL concepts including filtering, joins, aggregations, subqueries, CTEs, and window functions.

The repository is structured so that anyone can easily understand the database schema, relationships between tables, and the purpose of each query.

---

# Database Used

**Sakila Database**

Sakila is a sample database representing a **DVD movie rental store**.
It contains data about films, actors, customers, rentals, payments, and stores.

The schema models how a real rental business operates.

---

# SQL Concepts Covered

The 100 queries in this project cover the following SQL concepts:

• Basic SELECT queries
• Filtering with WHERE
• Pattern matching using LIKE
• Aggregation functions (COUNT, SUM, AVG)
• GROUP BY and HAVING
• Multiple table JOINS
• Subqueries
• Common Table Expressions (CTE)
• Window Functions
• Ranking functions (RANK, DENSE_RANK)
• PARTITION BY

---

# Repository Structure

sakila_database

│
├── sakila-schema.sql (database schema)
├── sakila-data.sql (sample data)
├── problem_statements.md (100 SQL questions)
└── solutions.sql (SQL query solutions)

---

# Main Tables in the Sakila Database

The Sakila database contains multiple tables, but the most important ones are listed below.

### Actor

Stores information about actors.

Columns:

* actor_id
* first_name
* last_name
* last_update

---

### Film

Contains information about movies available for rent.

Columns include:

* film_id
* title
* description
* release_year
* rental_rate
* length
* rating

---

### Film_Actor

This table connects actors with films.

Purpose:
A film can have multiple actors, and an actor can appear in multiple films.

Relationship:
actor → film_actor → film

---

### Category

Stores movie genres such as Action, Comedy, Drama, etc.

---

### Film_Category

Connects films with categories.

Relationship:
film → film_category → category

---

### Inventory

Represents physical copies of films available in stores.

Relationship:
film → inventory

A film can have multiple inventory copies.

---

### Rental

Stores rental transactions.

Relationship:
inventory → rental → customer

Each record shows when a film was rented and returned.

---

### Payment

Stores payment information for rentals.

Relationship:
rental → payment

This table tracks the amount paid for each rental.

---

### Customer

Stores customer information.

Columns include:

* customer_id
* first_name
* last_name
* email
* store_id

Customers rent movies from stores.

---

### Store

Represents the physical rental stores.

Each store has staff members and customers.

---

### Staff

Employees working at stores who process rentals and payments.

---

### Address, City, Country

These tables store location information.

Relationship chain:

country → city → address → customer / staff / store

---

# Simplified Relationship Flow

The main business flow of the database looks like this:

Film
↓
Inventory (copies of films)
↓
Rental (customer rents film)
↓
Payment (customer pays for rental)

Customer location structure:

Country → City → Address → Customer

Film relationships:

Actor → Film_Actor → Film
Film → Film_Category → Category

---

# Example Business Question

A typical SQL question using this database might be:

"Which customers generated the highest revenue?"

To answer this, we need to join:

Customer → Rental → Payment

This demonstrates how relational databases connect different tables to answer business questions.

---

# Goal of This Project

The purpose of this repository is to:

• Practice SQL using a real-world relational schema
• Understand relationships between tables
• Improve query writing skills
• Build a structured SQL portfolio on GitHub

---

# Author

Darshan Dudhat
