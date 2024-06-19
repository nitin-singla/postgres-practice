1. Write a SQL statement to change the email column of the employees table with 'not available' for all employees.

Sample Solution:

Code:

-- This SQL statement updates the 'email' column in the 'employees' table, setting all values to 'not available'.

UPDATE employees SET email='not available';

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET email='not available' specifies that the value of the 'email' column for all rows should be set to 'not available'. This effectively replaces the existing email addresses with the string 'not available' for all employees in the table.

Output:

See the result. Only two rows have been displayed.

postgres=# SELECT * FROM employees LIMIT 2;
 employee_id | first_name | last_name |     email     | phone_number | hire_date  | job_id  |  salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------------+--------------+------------+---------+----------+----------------+------------+---------------
         100 | Steven     | King      | not available | 515.123.4567 | 1987-06-17 | AD_PRES | 24000.00 |           0.00 |          0 |            90
         101 | Neena      | Kochhar   | not available | 515.123.4568 | 1987-06-18 | AD_VP   | 17000.00 |   


2. Write a SQL statement to change the email and commission_pct column of the employees table with 'not available' and 0.10 for all employees.

Sample Solution:

Code:

-- This SQL statement updates the 'email' and 'commission_pct' columns in the 'employees' table,
-- setting the 'email' column to 'not available' and the 'commission_pct' column to 0.10 for all rows.

UPDATE employees SET email='not available', commission_pct=0.10;

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET email='not available', commission_pct=0.10 specifies that the value of the 'email' column for all rows should be set to 'not available', and the value of the 'commission_pct' column should be set to 0.10. This effectively updates the email addresses to 'not available' and sets the commission percentage to 0.10 for all employees in the table.

Output:

See the result. Only two rows have been displayed.

postgres=# SELECT * FROM employees LIMIT 2;
 employee_id | first_name | last_name |     email     | phone_number | hire_date  |  job_id  | salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------------+--------------+------------+----------+---------+----------------+------------+---------------
         128 | Steven     | Markle    | not available | 650.124.1434 | 1987-07-15 | ST_CLERK | 2200.00 |           0.10 |        120 |            50
         129 | Laura      | Bissot    | not available | 650.124.5234 | 1987-07-16 | ST_CLERK | 3300.00 |           0.10 |        121 |            50



3. Write a SQL statement to change the email and commission_pct column of the employees table with 'not available' and 0.10 for those employees whose department_id is 110.

Sample Solution:

Code:

-- This SQL statement updates the 'email' and 'commission_pct' columns in the 'employees' table
-- for employees belonging to the department with department_id=110.
-- It sets the 'email' column to 'not available' and the 'commission_pct' column to 0.10 for matching rows.

UPDATE employees 
SET email='not available', commission_pct=0.10 
WHERE department_id=110;

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET email='not available', commission_pct=0.10 specifies that the value of the 'email' column should be set to 'not available', and the value of the 'commission_pct' column should be set to 0.10 for the rows that meet the specified condition.
    WHERE department_id=110 restricts the update operation to only those rows where the value of the 'department_id' column is 110. This ensures that only employees belonging to the department with department_id=110 will have their email addresses updated to 'not available' and their commission percentage set to 0.10.

Output:

See the result. Only two rows have been updated.

postgres=# SELECT *
postgres-# FROM employees
postgres-# WHERE department_id=110
postgres-# AND  email='not available';
 employee_id | first_name | last_name |     email     | phone_number | hire_date  |   job_id   |  salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------------+--------------+------------+------------+----------+----------------+------------+---------------
         205 | Shelley    | Higgins   | not available | 515.123.8080 | 1987-09-30 | AC_MGR     | 12000.00 |           0.10 |        101 |           110
         206 | William    | Gietz     | not available | 515.123.8181 | 1987-10-01 | AC_ACCOUNT |  8300.00 |           0.10 |        205 |           110
(2 rows)


4. Write a SQL statement to change the email column of employees table with 'not available' for those employees whose department_id is 80 and gets a commission is less than.20%.

Sample Solution:

Code:

-- This SQL statement updates the 'email' column in the 'employees' table for employees 
-- belonging to the department with department_id=80 and having a commission percentage less than 0.20.
-- It sets the 'email' column to 'not available' for matching rows.

UPDATE employees 
SET email='not available'
WHERE department_id=80 
AND commission_pct<0.20;

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET email='not available' specifies that the value of the 'email' column should be set to 'not available' for the rows that meet the specified conditions.
    WHERE department_id=80 AND commission_pct<0.20 restricts the update operation to only those rows where the value of the 'department_id' column is 80 and the value of the 'commission_pct' column is less than 0.20. This ensures that only employees belonging to the department with department_id=80 and having a commission percentage less than 0.20 will have their email addresses updated to 'not available'.

Output:

See the result. Only the effected rows have been displayed.

postgres=# SELECT *
postgres-# FROM employees
postgres-# WHERE department_id=80
postgres-# AND  email='not available'
postgres-# AND commission_pct<.20;
 employee_id | first_name | last_name |     email     |    phone_number    | hire_date  | job_id | salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------------+--------------------+------------+--------+---------+----------------+------------+---------------
         155 | Oliver     | Tuvault   | not available | 011.44.1344.486508 | 1987-08-11 | SA_REP | 7000.00 |           0.15 |        145 |            80
         163 | Danielle   | Greene    | not available | 011.44.1346.229268 | 1987-08-19 | SA_REP | 9500.00 |           0.15 |        147 |            80
         164 | Mattea     | Marvins   | not available | 011.44.1346.329268 | 1987-08-20 | SA_REP | 7200.00 |           0.10 |        147 |            80
         165 | David      | Lee       | not available | 011.44.1346.529268 | 1987-08-21 | SA_REP | 6800.00 |           0.10 |        147 |            80
         166 | Sundar     | Ande      | not available | 011.44.1346.629268 | 1987-08-22 | SA_REP | 6400.00 |           0.10 |        147 |            80
         167 | Amit       | Banda     | not available | 011.44.1346.729268 | 1987-08-23 | SA_REP | 6200.00 |           0.10 |        147 |            80
         171 | William    | Smith     | not available | 011.44.1343.629268 | 1987-08-27 | SA_REP | 7400.00 |           0.15 |        148 |            80
         172 | Elizabeth  | Bates     | not available | 011.44.1343.529268 | 1987-08-28 | SA_REP | 7300.00 |           0.15 |        148 |            80
         173 | Sundita    | Kumar     | not available | 011.44.1343.329268 | 1987-08-29 | SA_REP | 6100.00 |           0.10 |        148 |            80
         179 | Charles    | Johnson   | not available | 011.44.1644.429262 | 1987-09-04 | SA_REP | 6200.00 |           0.10 |        149 |            80
(10 rows)

5. Write a SQL statement to change the email column of the employees table with 'not available' for those employees who belongs to the 'Accounting' department.

Sample Solution:

Code:

-- This SQL statement updates the 'email' column in the 'employees' table for employees 
-- belonging to the department identified by the department name 'Accounting'.
-- It sets the 'email' column to 'not available' for employees in the specified department.

UPDATE employees 
SET email='not available'
WHERE department_id=(
    SELECT department_id 
    FROM departments 
    WHERE department_name='Accounting'
);

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET email='not available' specifies that the value of the 'email' column should be set to 'not available' for the rows that meet the specified condition.
    WHERE department_id=(SELECT department_id FROM departments WHERE department_name='Accounting') restricts the update operation to only those rows where the value of the 'department_id' column matches the department ID retrieved from the subquery. The subquery retrieves the department ID for the department named 'Accounting' from the 'departments' table. This ensures that only employees belonging to the 'Accounting' department will have their email addresses updated to 'not available'.

Output:

See the result. Only the effected rows have been displayed.

SELECT * FROM employees 
WHERE email='not available' AND department_id=
(SELECT department_id 
FROM dep 
WHERE department_name='Accounting');


 employee_id | first_name | last_name |     email     | phone_number | hire_date  |   job_id   |  salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------------+--------------+------------+------------+----------+----------------+------------+---------------
         205 | Shelley    | Higgins   | not available | 515.123.8080 | 1987-09-30 | AC_MGR     | 12000.00 |           0.00 |        101 |           110
         206 | William    | Gietz     | not available | 515.123.8181 | 1987-10-01 | AC_ACCOUNT |  8300.00 |           0.00 |        205 |           110
(2 rows)


6. Write a SQL statement to change the salary of an employee to 8000 whose ID is 105, if the existing salary is less than 5000.

Sample Solution:

Code:

-- This SQL statement updates the 'SALARY' column in the 'employees' table for an employee with employee_id=105 
-- if their current salary is less than 5000. It sets their salary to 8000.

UPDATE employees 
SET SALARY = 8000 
WHERE employee_id = 105 
AND salary < 5000;

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET SALARY = 8000 specifies that the value of the 'SALARY' column should be set to 8000 for the rows that meet the specified condition.
    WHERE employee_id = 105 AND salary < 5000 restricts the update operation to only the row where the value of the 'employee_id' column is 105 and the value of the 'salary' column is less than 5000. This ensures that only the employee with employee_id=105 and a salary less than 5000 will have their salary updated to 8000.

Output:

See the result. Only the effected rows have been displayed.

postgres=# SELECT * FROM  employees 
WHERE  SALARY = 8000 
AND employee_id = 105;

 employee_id | first_name | last_name |  email  | phone_number | hire_date  | job_id  | salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------+--------------+------------+---------+---------+----------------+------------+---------------
         105 | David      | Austin    | DAUSTIN | 590.423.4569 | 1987-06-22 | IT_PROG | 8000.00 |           0.00 |        103 |            60
(1 row)


7. Write a SQL statement to change the job ID of the employee which ID is 118 to SH_CLERK if the employee belongs to a department which ID is 30 and the existing job ID does not start with SH.

Sample Solution:

Code:

-- This SQL statement updates the 'JOB_ID' column in the 'employees' table for an employee with employee_id=118 
-- and department_id=30 if their current job does not start with 'SH'. It sets their job to 'SH_CLERK'.

UPDATE employees 
SET JOB_ID = 'SH_CLERK' 
WHERE employee_id = 118 
AND department_id = 30 
AND NOT JOB_ID LIKE 'SH%';

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    SET JOB_ID = 'SH_CLERK' specifies that the value of the 'JOB_ID' column should be set to 'SH_CLERK' for the rows that meet the specified condition.
    WHERE employee_id = 118 AND department_id = 30 AND NOT JOB_ID LIKE 'SH%' restricts the update operation to only the row where the value of the 'employee_id' column is 118, the value of the 'department_id' column is 30, and the 'JOB_ID' column does not start with 'SH'. This ensures that only the employee with employee_id=118, department_id=30, and a job not starting with 'SH' will have their job updated to 'SH_CLERK'.

Output:

See the result. Only the effected rows have been displayed.

postgres=# SELECT * FROM  employees 
WHERE employee_id=118 
AND department_id=30 
AND JOB_ID LIKE 'SH%';

 employee_id | first_name | last_name |  email  | phone_number | hire_date  |  job_id  | salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+---------+--------------+------------+----------+---------+----------------+------------+---------------
         118 | Guy        | Himuro    | GHIMURO | 515.127.4565 | 1987-07-05 | SH_CLERK | 2600.00 |           0.00 |        114 |            30
(1 row)


8. Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules that, the salary will be increased by 25% of the department 40, 15% for department 90 and 10% of the department 110 and the rest of the department will remain same.

Sample Solution:

Code:

-- This SQL statement updates the 'salary' column in the 'employees' table based on the department_id.
-- It increases the salary for employees in specific departments by a certain percentage and leaves it unchanged otherwise.

UPDATE employees 
SET salary = CASE department_id 
                WHEN 40 THEN salary + (salary * 0.25)  -- Increase salary by 25% for department_id 40
                WHEN 90 THEN salary + (salary * 0.15)  -- Increase salary by 15% for department_id 90
                WHEN 110 THEN salary + (salary * 0.10) -- Increase salary by 10% for department_id 110
                ELSE salary  -- Keep salary unchanged for other department_ids
            END
WHERE department_id IN (40,50,50,60,70,80,90,110); -- Update salary for employees in specified department_ids

Explanation:

    The UPDATE statement is used to modify existing records in a table.
    employees is the name of the table being updated.
    The CASE expression evaluates different conditions (department_id) and performs corresponding actions (calculating new salary based on the condition).
    WHEN department_id THEN specifies the conditions for each department_id.
    THEN salary + (salary * 0.25) increases the salary by 25% if the department_id is 40, THEN salary + (salary * 0.15) increases the salary by 15% if the department_id is 90, and THEN salary + (salary * 0.10) increases the salary by 10% if the department_id is 110.
    ELSE salary specifies that the salary remains unchanged for department_ids not mentioned in the CASE expression.
    WHERE department_id IN (40,50,50,60,70,80,90,110) restricts the update operation to only those employees whose department_id is included in the list. It ensures that salary is updated only for employees in specified department_ids.

Output:

See the result before update. Only the effected rows have been displayed.

postgres=# SELECT * FROM emp WHERE department_id IN (40,90,110);
 employee_id | first_name | last_name |  email   | phone_number | hire_date  |   job_id   |  salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+----------+--------------+------------+------------+----------+----------------+------------+---------------
         100 | Steven     | King      | SKING    | 515.123.4567 | 1987-06-17 | AD_PRES    | 24000.00 |           0.00 |          0 |            90
         101 | Neena      | Kochhar   | NKOCHHAR | 515.123.4568 | 1987-06-18 | AD_VP      | 17000.00 |           0.00 |        100 |            90
         102 | Lex        | De Haan   | LDEHAAN  | 515.123.4569 | 1987-06-19 | AD_VP      | 17000.00 |           0.00 |        100 |            90
         203 | Susan      | Mavris    | SMAVRIS  | 515.123.7777 | 1987-09-28 | HR_REP     |  6500.00 |           0.00 |        101 |            40
         205 | Shelley    | Higgins   | SHIGGINS | 515.123.8080 | 1987-09-30 | AC_MGR     | 12000.00 |           0.00 |        101 |           110
         206 | William    | Gietz     | WGIETZ   | 515.123.8181 | 1987-10-01 | AC_ACCOUNT |  8300.00 |           0.00 |        205 |           110
(6 rows)

See the result. Only the effected rows have been displayed.

postgres=# SELECT * FROM emp WHERE department_id IN (40,90,110);

 employee_id | first_name | last_name |  email   | phone_number | hire_date  |   job_id   |  salary  | commission_pct | manager_id | department_id
-------------+------------+-----------+----------+--------------+------------+------------+----------+----------------+------------+---------------
         100 | Steven     | King      | SKING    | 515.123.4567 | 1987-06-17 | AD_PRES    | 27600.00 |           0.00 |          0 |            90
         101 | Neena      | Kochhar   | NKOCHHAR | 515.123.4568 | 1987-06-18 | AD_VP      | 19550.00 |           0.00 |        100 |            90
         102 | Lex        | De Haan   | LDEHAAN  | 515.123.4569 | 1987-06-19 | AD_VP      | 19550.00 |           0.00 |        100 |            90
         203 | Susan      | Mavris    | SMAVRIS  | 515.123.7777 | 1987-09-28 | HR_REP     |  8125.00 |           0.00 |        101 |            40
         205 | Shelley    | Higgins   | SHIGGINS | 515.123.8080 | 1987-09-30 | AC_MGR     | 13200.00 |           0.00 |        101 |           110
         206 | William    | Gietz     | WGIETZ   | 515.123.8181 | 1987-10-01 | AC_ACCOUNT |  9130.00 |           0.00 |        205 |           110
(6 rows)
