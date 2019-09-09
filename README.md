1. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id,,.

//CREATE TABLE exercise (country_id int ,country_name varchar(25),region_id int);
-----------------------------------------------------------------------------------

2. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id which is already exists.

//CREATE TABLE IF NOT EXISTS exercise (country_id int ,country_name varchar(25),region_id int);
-----------------------------------------------------------------------------------------------

3. Write a SQL statement to create the structure of a table dup_countries similar to countries.

//create table dup_countries like exercise;
----------------------------------------------------------------------------------------------

4. Write a SQL statement to create a duplicate copy of countries table including structure and data by name dup_countries.

//CREATE TABLE IF NOT EXISTS dup_countries AS SELECT * FROM exercise ; 
----------------------------------------------------------------------------------------------

5. Write a SQL statement to create a table countries set a constraint NOT NULL (all the fields should be not null).
CREATE TABLE

//CREATE TABLE IF NOT EXISTS countries(country_id int NOT NULL,country_name varchar(25) NOT NULL,region_id int NOT NULL); 
----------------------------------------------------------------------------------------------

6. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary, max_salary and check whether the max_salary amount exceeding the upper limit 25000.
 
//CREATE TABLE IF NOT EXISTS jobs(job_id int , job_title varchar(25), min_salary int, max_salary int
CHECK(max_salary<=25000)
);

----------------------------------------------------------------------------------------------
7. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that no countries except Italy, India and China will be entered in the table.

//CREATE TABLE IF NOT EXISTS countries
(country_id int,
 country_name varchar(25) 
 CHECK(country_name IN('Italy','India','China')),
 region_id int);

----------------------------------------------------------------------------------------------

8. Write a SQL statement to create a table named job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.

//CREATE TABLE job_history
(employee_id int,
 start_date date,
 end_date date CHECK (end_date LIKE '--/--/----'),
 job_id int,
 department_id int);
---------------------------------------------------------------------------------------------
9. Write a SQL statement to create a table named countries including columns country_id,country_name and region_id and make sure that no duplicate data against column country_id will be allowed at the time of insertion.

//CREATE TABLE countries(
country_id int,
country_name varchar(25),
region_id int);
---------------------------------------------------------------------------------------------
10. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

//CREATE TABLE  IF NOT EXISTS jobs
(job_id int,
 job_title varchar(25) DEFAULT ' ',
 min_salary int DEFAULT 8000,
 max_salary int DEFAULT NULL);
----------------------------------------------------------------------------------------------
11. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that the country_id column will be a key field which will not contain any duplicate data at the time of insertion.

//create table IF NOT EXISTS countries
(country_id int UNIQUE PRIMARY KEY,
 country_name varchar(25),
 region_id int);

----------------------------------------------------------------------------------------------
12. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the column country_id will be unique and store an auto incremented value.

//CREATE TABLE IF NOT EXISTS countries(
country_id int UNIQUE AUTO_INCREMENT,
country_name varchar(25),
region_id int);

----------------------------------------------------------------------------------------------
13. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the combination of columns country_id and region_id will be unique.

//CREATE TABLE IF NOT EXISTS countries(
country_id int,
country_name varchar(25),
region_id int,
PRIMARY KEY(country_id,region_id)
);

---------------------------------------------------------------------------------------------
14. Write a SQL statement to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.

Here is the structure of the table jobs;



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

//CREATE TABLE IF NOT EXISTS job_history (
employee_id int UNIQUE,
start_date date, 
end_date date, 
job_id int, 
department_id int,
FOREIGN KEY(job_id)REFERENCES jobs(job_id));

-----------------------------------------------------------------------------------------
15. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key columns combined by department_id and manager_id columns contain only those unique combination values, which combinations are exists in the departments table.

Assume the structure of departments table below.

| Field           | Type         | Null | Key | Default | Extra |
|-----------------|--------------|------|-----|---------|-------|
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | NO   | PRI | 0       |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |

//CREATE TABLE IF NOT EXISTS employees(
employee_id  decimal(6,0) PRIMARY KEY, 
first_name varchar(25), 
last_name varchar(25), 
email varchar(25), 
phone_number int,
hire_date date, 
job_id int, 
salary int, 
commission int, 
manager_id decimal(6,0), 
department_id decimal(4,0),
FOREIGN KEY(department_id,manager_id)
REFERENCES departments(department_id,manager_id)
);
--------------------------------------------------------------------------------------------
16. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column department_id, reference by the column department_id of departments table, can contain only those values which are exists in the departments table and another foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables.

"A foreign key constraint is not required merely to join two tables. For storage engines other than InnoDB, it is possible when defining a column to use a REFERENCES tbl_name(col_name) clause, which has no actual effect, and serves only as a memo or comment to you that the column which you are currently defining is intended to refer to a column in another table." - Reference dev.mysql.com

Assume that the structure of two tables departments and jobs.

| Field           | Type         | Null | Key | Default | Extra |
|-----------------|--------------|------|-----|---------|-------|
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  |     | NULL    |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

//CREATE TABLE IF NOT EXISTS  employees(
employee_id  decimal(6,0) PRIMARY KEY, 
first_name varchar(25), 
last_name varchar(25), 
email varchar(25), 
phone_number int,
hire_date date, 
job_id int, 
salary int, 
commission int, 
manager_id decimal(6,0), 
department_id decimal(4,0),
FOREIGN KEY(DEPARTMENT_ID) 
REFERENCES  departments(DEPARTMENT_ID),
FOREIGN KEY(job_id)
REFERENCES jobs(job_id));
------------------------------------------------------------------------------------------------
17. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON UPDATE CASCADE action allows you to perform cross-table update and ON DELETE RESTRICT action reject the deletion. The default action is ON DELETE RESTRICT.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

------------------------------------------------------------------------------------------------
18. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE CASCADE that lets you allow to delete records in the employees(child) table that refer to a record in the jobs(parent) table when the record in the parent table is deleted and the ON UPDATE RESTRICT actions reject any updates.

Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```


| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |

-------------------------------------------------------------------------------------------------
19. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE SET NULL action will set the foreign key column values in the child table(employees) to NULL when the record in the parent table(jobs) is deleted, with a condition that the foreign key column in the child table must accept NULL values and the ON UPDATE SET NULL action resets the values in the rows in the child table(employees) to NULL values when the rows in the parent table(jobs) are updated.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
------------------------------------------------------------------------------------------------
20. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE NO ACTION and the ON UPDATE NO ACTION actions will reject the deletion and any updates.

Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

```CREATE TABLE IF NOT EXISTS jobs ( 
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY, 
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ', 
MIN_SALARY decimal(6,0) DEFAULT 8000, 
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;
```



| Field      | Type         | Null | Key | Default | Extra |
|------------|--------------|------|-----|---------|-------|
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |


