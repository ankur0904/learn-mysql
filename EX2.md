```Table
employee
+--------+----------+-------------+---------+
| emp_id | emp_name | department  | salary  |
+--------+----------+-------------+---------+
|      1 | a        | HR          | 1000000 |
|      2 | b        | Finance     |  100000 |
|      3 | c        | Engineering |  100000 |
+--------+----------+-------------+---------+

project
+--------+------+--------+----------+
| emp_id | p_id | p_name | location |
+--------+------+--------+----------+
|      1 | p1   | IOT    | Noida    |
|      3 | p2   | AI     | Delhi    |
|      2 | p3   | ML     | Kanpur   |
+--------+------+--------+----------+
3 rows in set (0.01 sec)
```
### `IN`

#### detail of employee whose dapartment is 'HR` or `Finance`
```bash
mysql> SELECT * FROM employee WHERE department IN ('HR', 'Finance');
+--------+----------+------------+---------+
| emp_id | emp_name | department | salary  |
+--------+----------+------------+---------+
|      1 | a        | HR         | 1000000 |
|      2 | b        | Finance    |  100000 |
|      4 | d        | HR         |   10000 |
+--------+----------+------------+---------+
3 rows in set (0.00 sec)
```

### `NOT IN`
```bash
mysql> SELECT * FROM employee WHERE department NOT IN ('HR', 'Finance');
+--------+----------+-------------+--------+
| emp_id | emp_name | department  | salary |
+--------+----------+-------------+--------+
|      3 | c        | Engineering | 100000 |
+--------+----------+-------------+--------+
1 row in set (0.01 sec)
```


### find the name of employee who is working on any project

```bash
mysql> SELECT emp_name FROM employee WHERE emp_id IN (SELECT emp_id FROM project);
+----------+
| emp_name |
+----------+
| a        |
| b        |
| c        |
+----------+
3 rows in set (0.00 sec)
```

### `EXIST and NOT-EXIST`

`corelated`: 
- normal nested query first inner execute then outer execute
- IN CORELATED: first row from the outer table then check for all the row in the inner table.
- inner query return `True`

```bash
mysql> SELECT * FROM employee WHERE EXISTS (SELECT emp_id FROM project WHERE employee.emp_id = project.emp_id);
+--------+----------+-------------+---------+
| emp_id | emp_name | department  | salary  |
+--------+----------+-------------+---------+
|      1 | a        | HR          | 1000000 |
|      2 | b        | Finance     |  100000 |
|      3 | c        | Engineering |  100000 |
+--------+----------+-------------+---------+
3 rows in set (0.00 sec)
```

```bash
mysql> SELECT * FROM employee WHERE NOT EXISTS (SELECT emp_id FROM project WHERE employee.emp_id = project.emp_id);
+--------+----------+------------+--------+
| emp_id | emp_name | department | salary |
+--------+----------+------------+--------+
|      4 | d        | HR         |  10000 |
+--------+----------+------------+--------+
1 row in set (0.00 sec)
```