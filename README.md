
<div align="center">

# 🎓 University Management System

A relational database system designed to model, organize, and streamline core academic operations, student enrollments, and institutional administration.

[![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](#)
[![Status](https://img.shields.io/badge/Status-In_Development-F5A623?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-3DA639?style=for-the-badge)](#)

<p align="center">
  <a href="#about">About</a> •
  <a href="#database-schema">Database Schema</a> •
  <a href="#quickstart">Quickstart</a> •
  <a href="#roadmap">Roadmap</a> •
  <a href="#license">License</a>
</p>

---

</div>

## 📌 About

The **University Management System** manages entities across higher-education institutions, tracking student records, faculty allocation, course distribution, and academic tracking.

---

## 🗄️ Database Schema

### 1. `Student` Table
Stores primary identifiers and contact information for enrolled learners[cite: 1].

| Column Name | Data Type | Constraints | Description |
| :--- | :--- | :--- | :--- |
| `Student_id`[cite: 1] | `INT`[cite: 1] | `PRIMARY KEY`[cite: 1] | Unique student identification number[cite: 1] |
| `First_name`[cite: 1] | `VARCHAR(50)`[cite: 1] | `NOT NULL` | Legal given name[cite: 1] |
| `Last_name`[cite: 1] | `VARCHAR(50)`[cite: 1] | `NOT NULL` | Legal family name[cite: 1] |
| `Email`[cite: 1] | `VARCHAR(50)`[cite: 1] | `UNIQUE`, `NOT NULL` | Academic or personal contact email[cite: 1] |

---

## 🚀 Quickstart

### Prerequisites
* **MySQL Server** (v8.0+)
* Any standard SQL client or extension (e.g., **SQLBook**, **VS Code MySQL Extension**, **DBeaver**)[cite: 1]

### Installation

1. **Clone the repository**
   ```bash
   git clone [https://github.com/your-username/university-management-system.git](https://github.com/your-username/university-management-system.git)
   cd university-management-system



2. **Initialize Database and Tables**


Execute the migration queries in your MySQL console:
```sql
-- Create Database
CREATE DATABASE IF NOT EXISTS Univarsity_management_System;[cite: 1]
USE Univarsity_management_System;[cite: 1]

-- Create Student Entity
CREATE TABLE IF NOT EXISTS Student (
    Student_id INT PRIMARY KEY,[cite: 1]
    First_name VARCHAR(50) NOT NULL,[cite: 1]
    Last_name VARCHAR(50) NOT NULL,[cite: 1]
    Email VARCHAR(50) NOT NULL UNIQUE[cite: 1]
);

```



---

## 🗺️ Roadmap

* [x] Database initialization


* [x] Initial `Student` entity table


* [ ] Add `Course` entity table (`Course_id`, `Title`, `Credits`, `Department`)
* [ ] Add `Instructor` table (`Instructor_id`, `Name`, `Department`, `Office`)
* [ ] Set up `Enrollment` junction table with foreign keys (`Student_id`, `Course_id`, `Semester`, `Grade`)
* [ ] Implement stored procedures, views, and trigger events for automated GPA calculation

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

```

```
