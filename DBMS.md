#### 1. What is DB and DBMS ?
	Db is a collection of related data and DBMS is software to manage a DB.

#### 2. What are the Different Languages present in DBMS ?
	- DDL --> CREATE, ALTER, DROP
	- DML --> SELECT, UPDATE, DELETE
	- DCL --> GRANT, REVOKE
	- TCL --> COMMIT, ROLLBACK

#### 3. Explain ACID properties in DBMS .
![](https://github.com/aman0046/LastMinuteRevision-DBMS/raw/main/assets/images/ACID.png)
	- These properties ensure safe and secure transactions.
- **ATOMICITY** --> A transaction must be fully completed or not done at all.
- CONSISTENCY -->Data must remain consistent before and after a transaction.
- ISOLATION --> 1 transaction should not interfere with other transactions.
- DURABILITY --> Data must remain safe even after crashes.
``` sql
BEGIN;
UPDATE accounts SET balance = balance - 500 WHERE id = 'A'; 
UPDATE accounts SET balance = balance + 500 WHERE id = 'B'; 
COMMIT;
```

#### 4. Drop vs Truncate vs Delete .
	- DROP deletes entire Table and Cannot be Rolled Back. [FASTEST]
	- DELETE deletes rows from a table and Can be Rolled Back. [SLOWEST]
	- TRUNCATE deletes all rows from a DB. [FASTER]
``` sql
-- Remove the entire table from DB
DROP TABLE employees;

-- Delete specific rows
DELETE FROM employees WHERE department = 'HR';

-- Remove all rows fast
TRUNCATE TABLE employees;
```

#### 5. Explain Normalization and Denormalization.
- Normalization is the process of organizing a DB by breaking down larger tables into smaller, related table to eliminate Data Redundancy and Ensure Data Integrity.
- Denormalization is the process of combining Normalized tables into a single tables using Joins.
###### 1NF --> Each Column must be Atomic and have a Single Value.

###### ❌ Bad:
```
ID | Name | Courses 
1  | Ram  | Math, Science
```

✅ Good:
```
ID | Name | Course
1  | Ram  | Math
1  | Ram  | Science
```

###### 2NF --> A table is 1NF and has No Partial Dependency in case of Composite Keys ( multiple PKs) .
	Eg. StyudentID StudentName CourseID CourseName 
		These in 1 table give partial dependencies,
		So split into 3 tables -
		StudentId StudentName
		CourseId CourseName
		StudentId CourseID

###### 3NF --> 1NF + 2NF + remove Transitional Dependency (non-key depending on another Non - key)
###### ❌ Bad:
```
StudentID | Name | DeptID | DeptName
```
###### ✅ Good:  
Split into:
``` 
Student(ID, Name, DeptID)
Department(DeptID, DeptName)
```

#### 6. What is an ER diagram ?
	- It is a visual representation fo relationships among entities in a DB.
	- It shows how different tables are connected.
	- Like a flow chart of relationships.

#### 7. Explain Keys .
	- PK --> Unique identifier and cannot be null.
	- UK --> Unique identifier and can be null.
	- FK --> A PK of 1 table related to PK of another table.

#### 8. What are Locks in DB and explain types ?
	- A Lock is a mechanism to control concurrent access of data.
	- Since if multiple users or transactions access the data at the same time, it can lead to Data Inconsistency.
1. Shared Lock : Many people can read at once but no one can write to it.
``` sql
-- Transaction A
SELECT * FROM accounts WHERE id = 101 LOCK IN SHARE MODE;

-- Transaction B (simultaneously)
SELECT * FROM accounts WHERE id = 101 LOCK IN SHARE MODE;
```
2. Exclusive Lock : Only 1 person can edit at a time but no one can even read it.
``` sql
-- Transaction A
UPDATE accounts SET balance = balance - 100 WHERE id = 101;

-- Transaction B
-- will have to wait until A completes
UPDATE accounts SET balance = balance + 100 WHERE id = 101;
```

#### 9. What are Views ? 
	- A View in SQL is a Virtual Table that shows a result of a query.
	- It exposes only specified columns/rows and doesn't store actual data.
	- They just show data from real tables and are like Read-Only tables.
``` sql
Employees
+----+----------+--------+----------+
| ID | Name     | Salary | Dept     |
+----+----------+--------+----------+
| 1  | Alice    | 60000  | HR       |
| 2  | Bob      | 70000  | IT       |
| 3  | Charlie  | 75000  | IT       |
⬇️
CREATE VIEW IT_Employees AS
SELECT Name, Salary FROM Employees WHERE Dept = 'IT';
⬇️
SELECT * FROM IT_Employees;
⬇️
+--------+--------+
| Name   | Salary |
+--------+--------+
| Bob    | 70000  |
| Charlie| 75000  |
```

####  10. What Are Indexes in DBMS ?
	- Indexes are Data Structures that help to improve the Speed of Data Retrieval operations.
	- It is like a lookup guide like the index page in a book.
	- Eg. Creating an Index of Name column helps speed queries that search for a specific name.
``` sql
CREATE INDEX idx_name ON Employees(Name);

-- Now when you do:

SELECT * FROM Employees WHERE Name = 'Alice';

-- Instead of scanning every row, DB directly jumps to names with A, then names with l until it gets 'Alice'.
```
	- However Indexes help in fast data retrieval, they take extra space and can slow down Insert/Delete operations because indexes also change with this operations.

#### 11. What is the Query Execution Order in SQL ?
	1. FROM /JOIN
	2. WHERE
	3. GROUP BY
	4. HAVING
	5. SELECT
	6. DISTINCT
	7. ORDER BY
	8. LIMIT

#### 12. Why PostgreSQL instad of mySQL ?

###### A) Postgres supports JSONB format (binary json) which supports Indexing, making JSON queries faster, but MySQL supports JSON format which doesn't allow indexing/
###### B) Supports Row-Level Security which is better than MySQL, and handles Concurrency better than MySQL.

###### C) Better for Large-Scale Systems.

###### D) BUT MySQL is Faster and Easier to Setup.
# NEED TO ADD WINDOW FUNCTIONS, RANKINGS & PERFORMANCE OPTIMIZATION RELATED STUFF.