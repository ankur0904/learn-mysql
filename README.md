## Start the session with a predefined user
```bash
$ mysql -u <USERNAME> -p
```
*It'll prompt for the password.*


### Create Database
```bash
CREATE DATABASE <database_name>;
```

### Use Database
```bash
USE <database_name>;
```
*Essential to select a database before use.*

### Create a table
```bash
CREATE TABLE employee(
    -> emp_id INT,
    -> emp_name VARCHAR(50),
    -> department VARCHAR(50),
    -> salary INT
    -> );
```

### Insert into tables

```bash

```

### Basic commands
- ```bash
    show tables;
  ```

- ```bash
    SELECT * FROM employee;
  ```  

- ```bash
    desc employee;
  ```
