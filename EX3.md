### Aggregate function
- MAX
- MIN
- COUNT
- SUM
- AVG

- `MAX`
```bash
mysql> SELECT MAX(salary) FROM employee;
+-------------+
| MAX(salary) |
+-------------+
|     1000000 |
+-------------+
1 row in set (0.00 sec)
```

- `MIN`
```bash
mysql> SELECT MIN(salary) FROM employee;
+-------------+
| MIN(salary) |
+-------------+
|       10000 |
+-------------+
1 row in set (0.00 sec)
```
- `COUNT`
```bash
mysql> SELECT COUNT(*) FROM employee;
+----------+
| COUNT(*) |
+----------+
|        4 |
+----------+
1 row in set (0.00 sec)
```
```bash
mysql> SELECT COUNT(salary) FROM employee;
+---------------+
| COUNT(salary) |
+---------------+
|             4 |
+---------------+
1 row in set (0.00 sec)
```

```bash
mysql> SELECT DISTINCT(COUNT(salary)) FROM employee;
+-----------------+
| (COUNT(salary)) |
+-----------------+
|               4 |
+-----------------+
1 row in set (0.00 sec)
```

- `SUM`

```bash
mysql> SELECT SUM(salary) FROM employee;
+-------------+
| SUM(salary) |
+-------------+
|     1210000 |
+-------------+
1 row in set (0.00 sec)
```

- `AVG`

```bash
mysql> SELECT AVG(salary) FROM employee;
+-------------+
| AVG(salary) |
+-------------+
| 302500.0000 |
+-------------+
1 row in set (0.00 sec)
```

```bash
mysql> SELECT DISTINCT(AVG(salary)) FROM employee;
+---------------+
| (AVG(salary)) |
+---------------+
|   302500.0000 |
+---------------+
1 row in set (0.00 sec)
```