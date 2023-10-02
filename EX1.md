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
