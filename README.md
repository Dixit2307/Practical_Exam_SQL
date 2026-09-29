
::: {align="center"}
# 🎓 University Management System

### `SQL` • `Database Design` • `MySQL`

**A database project focused on organizing university student
information.**

[![SQL](https://img.shields.io/badge/SQL-Database-blue?style=for-the-badge&logo=mysql&logoColor=white)]()
[![Status](https://img.shields.io/badge/Status-In%20Progress-orange?style=for-the-badge)]()
[![Project](https://img.shields.io/badge/Type-Academic%20Project-purple?style=for-the-badge)]()
:::

------------------------------------------------------------------------

## ✨ About the Project

The **University Management System** is a SQL-based project that begins
with creating a university database and defining a structure for student
records. It is intended as a practical exercise in relational database
creation and SQL.

> **Current scope:** The provided SQLBook contains database
> creation/selection and the beginning of a `Student` table. Additional
> tables, relationships, sample data, and queries can be added as the
> project develops.

## 🧰 Tech Stack

  Technology    Purpose
  ------------- ----------------------------------
  MySQL / SQL   Database creation and management
  SQLBook       Organizing SQL notes and code

## 🗂️ Database Structure

### `Student`

  Column         Type            Description
  -------------- --------------- ---------------------------------
  `Student_id`   `INT`           Student identifier; primary key
  `First_name`   `VARCHAR(50)`   Student's first name
  `Last_name`    `VARCHAR(50)`   Student's last name
  `Email`        `VARCHAR(50)`   Student email address

## 🚀 Getting Started

1.  Open MySQL Workbench or another MySQL client.
2.  Open the project SQL file.
3.  Review and complete the table definition before running it.
4.  Execute the database creation and `USE` statements.
5.  Create and test the student table.

### Database setup

``` sql
CREATE DATABASE Univarsity_management_System;
USE Univarsity_management_System;
```

**Note:** The uploaded SQL currently has an unfinished
`CREATE TABLE Student` statement (a trailing comma and missing statement
terminator). Fix the syntax before executing the table creation.

## 🧠 Concepts Practiced

-   Creating and selecting a database
-   Defining tables and columns
-   Choosing SQL data types
-   Using a primary key
-   Structuring data for a management system

## 🛠️ Roadmap

-   [ ] Complete and validate the `Student` table
-   [ ] Add other university entities as needed
-   [ ] Define relationships and foreign keys
-   [ ] Insert sample records
-   [ ] Practice `SELECT`, filtering, sorting, and joins
-   [ ] Add constraints and test data integrity

## 👨‍💻 Author

::: {align="center"}
**Dixit Maru**

[![GitHub](https://img.shields.io/badge/GitHub-Dixit2307-181717?style=for-the-badge&logo=github)](https://github.com/Dixit2307)

*Aspiring AI/ML & Data Science Developer \| SQL Learner*
:::

------------------------------------------------------------------------

::: {align="center"}
**⭐ If you're exploring this project, feel free to fork it and build on
it.**
:::
