
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&height=280&color=0:0B0F19,40:1E293B,100:0F172A&text=📊%20STUDENT%20PERFORMANCE%20TRACKER&fontColor=00F7FF&fontSize=34&animation=twinkle"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=700&size=25&duration=3000&pause=1000&color=38BDF8&center=true&vCenter=true&width=950&lines=Dixit+Maru+%E2%94%82+Data+Engineer;Relational+Database+Architecture;Advanced+SQL+Analytics+%26+Window+Functions;Enterprise+Academic+Data+Modeling+🚀"/>
</p>

<p align="center">
  <a href="https://www.mysql.com/"><img src="https://img.shields.io/badge/MySQL-8.0+-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL"/></a>
  <a href="https://en.wikipedia.org/wiki/SQL"><img src="https://img.shields.io/badge/Language-SQL-F29111?style=for-the-badge&logoColor=white" alt="SQL"/></a>
  <a href="https://github.com/Dixit2307"><img src="https://img.shields.io/badge/Schema-Normalized_3NF-059669?style=for-the-badge" alt="Schema"/></a>
  <a href="https://github.com/Dixit2307"><img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status"/></a>
  <a href="https://mit-license.org"><img src="https://img.shields.io/badge/License-MIT-DC2626?style=for-the-badge" alt="License"/></a>
</p>

---

## 🧠 Project Architecture & Design

The **Student Performance & Attendance Tracker** is an enterprise-grade relational database framework designed for academic analytics[cite: 15]. Engineered directly in MySQL, the schema is structured to eliminate redundancy and maintain referential integrity through foreign key constraints[cite: 15].

It goes far beyond basic CRUD workflows by providing analytical queries, including **multi-table relational joins**, **window functions (`DENSE_RANK`, running totals)**, **time-series tracking**, and **conditional business logic profiling**[cite: 15].

---

## ⚡ System Dashboard & KPIs

```sql
 ┌────────────────────────────────────────────────────────┐
 │           🎓 ACADEMIC ANALYTICS DASHBOARD              │
 ├────────────────────────────────────────────────────────┤
 │  [01] 🏢 Departments    -> Structural Faculty Units    │
 │  [02] 👨‍🎓 Students       -> Demographic & Contact Data │
 │  [03] 👨‍🏫 Faculty        -> Department Mentors & Leads │
 │  [04] 📚 Courses        -> Course-Faculty Allocations  │
 │  [05] 📝 Enrollments    -> Academic Registration Logs  │
 │  [06] ⏱️ Attendance     -> Real-time Presence Metrics  │
 │  [07] 🏆 Grade Engine   -> Performance Metric Scoring  │
 └────────────────────────────────────────────────────────┘

```

---

## 🗄️ Database Entity-Relationship Architecture

```
                  ┌────────────────────────┐
                  │      DEPARTMENTS       │
                  ├────────────────────────┤
                  │ PK  department_id      │
                  │     department_name    │
                  └───────────┬────────────┘
                              │ 1:N
              ┌───────────────┴───────────────┐
              │                               │
              ▼                               ▼
  ┌────────────────────────┐     ┌────────────────────────┐
  │        STUDENTS        │     │        FACULTY         │
  ├────────────────────────┤     ├────────────────────────┤
  │ PK  student_id         │     │ PK  faculty_id         │
  │     name               │     │     name               │
  │     email, phone       │     │     email, phone       │
  │ FK  department_id      │     │ FK  department_id      │
  └───────────┬────────────┘     └───────────┬────────────┘
              │ 1:N                          │ 1:N
              │                              ▼
              │                  ┌────────────────────────┐
              │                  │        COURSES         │
              │                  ├────────────────────────┤
              │                  │ PK  course_id          │
              │                  │     course_name        │
              │                  │ FK  faculty_id         │
              │                  └───────────┬────────────┘
              │                              │
              └──────────────┬───────────────┘
                             │
            ┌────────────────┼────────────────┐
            ▼                ▼                ▼
┌──────────────────┐ ┌───────────────┐ ┌──────────────────┐
│   ENROLLMENTS    │ │  ATTENDANCE   │ │      GRADES      │
├──────────────────┤ ├───────────────┤ ├──────────────────┤
│ PK enrollment_id │ │ PK attend_id  │ │ PK grade_id      │
│ FK student_id    │ │ FK student_id │ │ FK student_id    │
│ FK course_id     │ │ FK course_id  │ │ FK course_id     │
│    enroll_date   │ │    status     │ │    marks, grade  │
└──────────────────┘ └───────────────┘ └──────────────────┘

```

---

## 📂 Project Topology

```directory
Student-Performance-Tracker
├── 📄 Practical_Exam_db.sql     # Complete DDL, DML & Advanced Query File
├── 📄 schema.sql                # Standalone Table Definitions
├── 📄 queries.sql               # Analytical & Diagnostic Query Suite
└── 📜 README.md                 # Professional System Documentation

```

---

## ✨ Advanced Query Capabilities

### 1. 🪟 Analytic Window Functions

* **Performance Rank:** Computes continuous student rankings with zero tie-skips using `DENSE_RANK() OVER (ORDER BY marks_obtained DESC)`.


* **Cumulative Course Attendance:** Uses partition-level frame analysis:
```sql
SELECT attendance_id, course_id, student_id,
       ROUND((SUM(CASE WHEN status = 'Present' THEN 1 ELSE 0 END) 
         OVER (PARTITION BY course_id ORDER BY attendance_date) * 100.0) / 
         COUNT(*) OVER (PARTITION BY course_id ORDER BY attendance_date), 2) AS cumulative_attendance_pct
FROM attendance;

```



* **Dynamic Running Totals:** Computes cumulative enrollments over sequential monthly timelines.



---

### 2. 🔗 Complex Multi-Way Relational Joins

* **Full Outer Join Emulation:** Bridges unmatched student profiles and disconnected grade sets across MySQL instances via `UNION` operations across `LEFT JOIN` and `RIGHT JOIN` constructs.


* **Defaulter & Orphan Identification:** Queries courses without assigned faculty members and locates students with zero course enrollments.



---

### 3. 🎯 Rule-Based Student Profiling (`CASE WHEN`)

Categorizes students into dynamic tiers to support automated academic warnings and honors designations:

```sql
SELECT student_id,
       ROUND((SUM(status = 'Present') / COUNT(*)) * 100, 2) AS attendance_pct,
       CASE 
           WHEN (SUM(status = 'Present') / COUNT(*)) * 100 > 80 THEN 'Regular'
           WHEN (SUM(status = 'Present') / COUNT(*)) * 100 BETWEEN 50 AND 80 THEN 'Irregular'
           ELSE 'Defaulter'
       END AS attendance_category
FROM attendance
GROUP BY student_id;

```

---

## 🛠 Engineering Matrix

| Implementation Vector | Engine Feature Set | Purpose |
| --- | --- | --- |
| **Relational Integrity** | `FOREIGN KEY` & `ON DELETE/UPDATE`<br> | Guarantees parent-child consistency across academic entities.

 |
| **Domain Constraints** | `CHECK (status IN ('Present', 'Absent', 'Late'))`<br> | Prevents invalid attendance state entries at the engine layer.

 |
| **Temporal Transformation** | `TIMESTAMPDIFF`, `DATE_FORMAT`, `CURDATE()`<br> | Extracts admission retention spans and standardizes date representations.

 |
| **Data Imputation** | `COALESCE(email, 'Email Not Provided')`<br> | Handles missing data points gracefully in reporting pipelines.

 |

---

## ⚙️️ Quickstart & Deployment

Run the database setup script in your local or hosted MySQL environment:

```bash
# Clone the repository
git clone [https://github.com/Dixit2307/Student-Performance-Tracker.git](https://github.com/Dixit2307/Student-Performance-Tracker.git)

# Navigate to directory
cd Student-Performance-Tracker

# Execute migration script via MySQL client
mysql -u root -p < Practical_Exam_db.sql

```

---

## 📸 Sample Query Execution

```sql
mysql> SELECT s.student_id, s.name, g.marks_obtained,
    ->        DENSE_RANK() OVER (ORDER BY g.marks_obtained DESC) AS marks_rank
    -> FROM students s
    -> JOIN grades g ON s.student_id = g.student_id;
+------------+-----------------+----------------+------------+
| student_id | name            | marks_obtained | marks_rank |
+------------+-----------------+----------------+------------+
|          3 | Kabir Malhotra  |          92.00 |          1 |
|          1 | Aarav Sharma    |          88.50 |          2 |
|          5 | Reyansh Das     |          80.00 |          3 |
|          2 | Ananya Iyer     |          76.00 |          4 |
|          4 | Diya Patel      |          65.50 |          5 |
+------------+-----------------+----------------+------------+

```

---

## 📈 Scalability Roadmap

* [ ] **Indexing Optimization:** Add B-Tree composite indexes on `(student_id, course_id)` for high-throughput join lookups.
* [ ] **Stored Procedures:** Build automated routines for semester-end grade calculation and report generation.
* [ ] **Audit Logging Triggers:** Create triggers to track grade update histories and preserve audit trails.
* [ ] **View Aggregations:** Implement materialized reporting views for dashboard integration.

---

## 📊 Developer Diagnostics

---

## 👨‍💻 System Engineer

### **Dixit Maru**

* 🚀 **AI / ML & Data Science Engineer**
* 📊 **Database Architect & Data Infrastructure Specialist**
* 💻 **Advanced SQL & Python Developer**

---

## ⭐ Show Your Support

If this database architecture was useful for your studies or projects:

* 🌟 **Star** the repository on GitHub
* 🍴 **Fork** the project to add new analytical routines
* 🤝 **Open a Pull Request** to submit optimizations

---
