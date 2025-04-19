# SQL-Cheat-Sheet


# ✅ SQL Cheat Sheet for Core Java + SQL Interviews (Freshers Edition)

---

## 📌 1. Basic Table Creation

```sql
-- Create Department Table
CREATE TABLE Department (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);

-- Create Employee Table with Foreign Key
CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    salary DECIMAL(10, 2),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
);
```

## 📌 2. Insert Data

```sql
-- Insert into Department
INSERT INTO Department (dept_id, dept_name) VALUES
(1, 'HR'), (2, 'Engineering'), (3, 'Finance');

-- Insert into Employee
INSERT INTO Employee (emp_id, emp_name, salary, dept_id) VALUES
(101, 'Alice', 60000, 1),
(102, 'Bob', 75000, 2),
(103, 'Charlie', 80000, 2),
(104, 'Daisy', 50000, 3);
```

## 📌 3. JOIN Queries

```sql
-- INNER JOIN
SELECT e.emp_id, e.emp_name, e.salary, d.dept_name
FROM Employee e
INNER JOIN Department d ON e.dept_id = d.dept_id;
```

## 📌 4. Update, Delete, Truncate

```sql
-- Update salary
UPDATE Employee SET salary = 85000 WHERE emp_id = 103;

-- Delete an employee
DELETE FROM Employee WHERE emp_id = 104;

-- Truncate the entire Employee table
TRUNCATE TABLE Employee;
```

## 📌 5. Filtering and Sorting

```sql
-- WHERE clause
SELECT * FROM Employee WHERE salary > 60000;

-- LIKE
SELECT * FROM Employee WHERE emp_name LIKE 'A%';

-- IN
SELECT * FROM Employee WHERE dept_id IN (1, 2);

-- BETWEEN
SELECT * FROM Employee WHERE salary BETWEEN 60000 AND 80000;

-- ORDER BY
SELECT * FROM Employee ORDER BY salary DESC;
```

## 📌 6. Aggregates and Grouping

```sql
-- COUNT total employees
SELECT COUNT(*) FROM Employee;

-- Total salary per department
SELECT d.dept_name, SUM(e.salary) AS total_salary
FROM Employee e
JOIN Department d ON e.dept_id = d.dept_id
GROUP BY d.dept_name;

-- AVG salary
SELECT AVG(salary) FROM Employee;
```

## 📌 7. Table Alteration

```sql
-- Add column
ALTER TABLE Employee ADD joining_date DATE;

-- Drop column
ALTER TABLE Employee DROP COLUMN joining_date;
```

## 📌 8. Other Common Queries

```sql
-- Find duplicate employees (by name)
SELECT emp_name, COUNT(*) 
FROM Employee 
GROUP BY emp_name 
HAVING COUNT(*) > 1;

-- Select top 2 salaries (MySQL)
SELECT * FROM Employee ORDER BY salary DESC LIMIT 2;
```

## 📌 9. Important Theory Questions with Answers

### 🔹 Difference between DELETE, TRUNCATE, and DROP
- `DELETE`: Removes rows based on condition, can be rolled back.
- `TRUNCATE`: Removes all rows, cannot be rolled back (faster).
- `DROP`: Deletes the entire table structure.

### 🔹 What is a Primary Key vs Foreign Key?
- **Primary Key**: Uniquely identifies each record in a table.
- **Foreign Key**: Refers to the primary key in another table to maintain relationship.

### 🔹 Types of JOINs: INNER, LEFT, RIGHT, FULL
- **INNER JOIN**: Only matching rows.
- **LEFT JOIN**: All from left + matched from right.
- **RIGHT JOIN**: All from right + matched from left.
- **FULL JOIN**: All records from both sides.

### 🔹 What is Normalization in DBMS?
- Process of organizing data to reduce redundancy.
- Example: Splitting data into multiple related tables.

### 🔹 Subqueries vs JOINs
- **JOIN**: Combines rows from multiple tables.
- **Subquery**: A query inside another query, used when joining is not needed.

### 🔹 What is a Transaction?
- A sequence of SQL operations treated as a single unit.
- Follows ACID properties: Atomicity, Consistency, Isolation, Durability.

---

🧠 **Tip:** Practice explaining each answer with an example to boost confidence during interviews.

