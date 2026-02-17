# Experiment 1

## Aim
To create an `EMPLOYEE_MASTER` table from the `EMPLOYEE` table and perform SQL operations like **CREATE, DELETE, UPDATE, ALTER, and DROP**.

---

## Theory
SQL (Structured Query Language) is used to manage data in relational databases.

- **DDL Commands**: `CREATE`, `ALTER`, `DROP`
- **DML Commands**: `INSERT`, `UPDATE`, `DELETE`

---

## Queries
```sql
-- 1. Create Employee_master table with data using Employee table
CREATE TABLE employee_master AS
SELECT * FROM employee;

-- 2. Delete all record into Employee_master whose DeptNo is 10
DELETE FROM employee_master
WHERE deptno = 10;

-- 3. Update 10% in salary of employees of DEPTNO 20 into Employee_Master
UPDATE employee_master
SET sal = sal + (sal * 0.10)
WHERE deptno = 20;

-- 4. Alter SAL with size 10,2 in Employee_Master
ALTER TABLE employee_master
MODIFY sal DECIMAL(10,2);

-- 5. Drop Employee master Table
DROP TABLE employee_master;

```
---