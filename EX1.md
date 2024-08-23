Table
```
+--------+----------+-------------+---------+
| emp_id | emp_name | department  | salary  |
+--------+----------+-------------+---------+
|      1 | a        | HR          | 1000000 |
|      2 | b        | Finance     |  100000 |
|      3 | c        | Engineering |  100000 |
+--------+----------+-------------+---------+
```
#### find maximum salary from employee table.

```bash
SELECT MAX(salary) FROM employee;
```
O/P: 
```bash
+-------------+
| MAX(salary) |
+-------------+
|     1000000 |
+-------------+
1 row in set (0.00 sec)
```

#### find the name of person who have maximum salary from employee table.
*(NESTED/ Sub query)*

```bash
SELECT emp_name FROM employee WHERE salary=(SELECT MAX(salary) FROM employee);
```
`SELECT MAX(salary) FROM employee` - Inner Query (1)
`SELECT emp_name FROM employee WHERE salary=()` - Outer Query (2)

O/P:

```bash
+----------+
| emp_name |
+----------+
| a        |
+----------+
1 row in set (0.00 sec)
```

### find the second highest salary
Logic: find the (second)highest salary and the salary is not equal to (first)highest. 

```bash
SELECT MAX(salary) FROM employee WHERE salary < (SELECT MAX(salary) FROM employee);
```
O/P:
```bash
+-------------+
| MAX(salary) |
+-------------+
|      100000 |
+-------------+
1 row in set (0.00 sec)
```

### find the name of the person with second highest salary
```bash
SELECT emp_name FROM employee WHERE salary = (SELECT MAX(salary) FROM employee WHERE salary < (SELECT MAX(salary) FROM employee));
```
O/P:

```bash
+----------+
| emp_name |
+----------+
| b        |
| c        |
+----------+
2 rows in set (0.00 sec)
```

### find the third highest salary
```bash
SELECT DISTINCT salary FROM employee ORDER BY salary DESC LIMIT 1 OFFSET 2;
```
O/P:
```bash
+--------+
| salary |
+--------+
|  10000 |
+--------+
1 row in set (0.00 sec)

```

### find the department name with the number of employee
**GROUPBY**

```bash
SELECT ______ FROM employee GROUP BY ______;
```
1. `______` same
2. `______` if different required use `aggregate` function only.

Solution:
```bash
SELECT department,count(department) FROM employee GROUP BY department;
```
or
```bash
SELECT department,count(*) FROM employee GROUP BY department;
```

O/P:
```bash
+-------------+-------------------+
| department  | count(department) |
+-------------+-------------------+
| HR          |                 2 |
| Finance     |                 1 |
| Engineering |                 1 |
+-------------+-------------------+
3 rows in set (0.00 sec)
```
### find the department where the number of employee is less than 2
`GROUP BY` + `WHERE` =  X(no)
`GROUP BY` + `HAVING` = (yes)

```bash
SELECT department FROM employee GROUP BY department HAVING COUNT(*) < 2;
```
O/P:
```bash
+-------------+
| department  |
+-------------+
| Finance     |
| Engineering |
+-------------+
2 rows in set (0.00 sec)
```

Name ???
```bash
SELECT emp_name FROM employee WHERE department IN (SELECT department FROM employee GROUP BY department HAVING COUNT(*) < 2);
```
O/P:
```bash
+----------+
| emp_name |
+----------+
| b        |
| c        |
+----------+
2 rows in set (0.00 sec)
```

### find the highest salary department wise and name the person who is taking the highest salary

```bash
SELECT MAX(salary) FROM employee GROUP BY department;
```
O\P: 
```bash
+-------------+
| MAX(salary) |
+-------------+
|     1000000 |
|      100000 |
|      100000 |
+-------------+
3 rows in set (0.01 sec)
```

```bash
SELECT emp_name FROM employee WHERE salary IN (SELECT MAX(salary) FROM employee GROUP BY department);
```
```bash
+----------+
| emp_name |
+----------+
| a        |
| b        |
| c        |
+----------+
3 rows in set (0.00 sec)
```
