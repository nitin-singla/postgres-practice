PostgreSQL Alter Table: SOLUTIONS

1. Write a SQL statement to rename the table countries to country_new.

Here is the list of tables.

   tablename   | tableowner
---------------+------------
 orders        | postgres
 employees     | postgres
 job_history   | postgres
 jobs          | postgres
 locations     | postgres
 regions       | postgres
 countries     | postgres
(7 rows)

Sample Solution:

Code:

ALTER TABLE countries RENAME TO country_new;

Output:

Now, after execute the command see the list of tables.

   tablename   | tableowner
---------------+------------
 orders        | postgres
 employees     | postgres
 job_history   | postgres
 jobs          | postgres
 locations     | postgres
 regions       | postgres
 country_new   | postgres
(7 rows)


2. Write a SQL statement to add a column region_id to the table locations.

Here is the structure of the table locations.

postgres=# \d locations
     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE locations
ADD region_id  INT;

Output:

See the structure of the table after alteration.

postgres=# \d locations

     Column     |         Type          | M
----------------+-----------------------+--
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
 region_id      | integer               |


3. Write a SQL statement to change the data type of the column region_id to text in the table locations.

Here is the structure of the table locations.

postgres=# \d locations
     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
 region_id      | integer               |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE locations
ALTER region_id TYPE text;

Output:

Now see the structure of the table locations after alteration.

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
 region_id      | text                  |


4. Write a SQL statement to drop the column city from the table locations.

Here is the structure of the table locations.

postgres=# \d locations
     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
 region_id      | text                  |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE locations
DROP city;

Output:

Now see the structure of the table locations after alteration.

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
 region_id      | text                  |


5. Write a SQL statement to change the name of the column state_province to state, keeping the same size and data type and size.

Here is the structure of the table locations.

postgres=# \d locations
     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
 region_id      | text                  |

Sample Solution:

Code:

ALTER TABLE locations 
RENAME COLUMN state_province TO state;

Output:

Now see the structure of the table locations after alteration.

postgres=# \d locations
     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 country_id     | character varying(2)  |
 region_id      | text                  |
 state          | character varying(25) |


6. Write a SQL statement to add a primary key to the columns location_id in the locations table.

Here is the structure of the table locations.

postgres=# \d locations
     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE locations
ADD PRIMARY KEY(location_id);

Output:

Now see the structure of the table locations after alteration.

postgres=# \d locations

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          | not null
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |
Indexes:
"locations_pkey" PRIMARY KEY, btree (location_id)

7. Write a SQL statement to add a primary key for a combination of columns location_id and country_id.

Here is the structure of the table locations.

postgres=# \d locations

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          |
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE locations
ADD PRIMARY KEY(location_id,country_id);

Output:

Now see the structure of the table locations after alteration.

postgres=# \d locations

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          | not null
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  | not null
Indexes:
    "locations_pkey" PRIMARY KEY, btree (location_id, country_id)


8. Write a SQL statement to drop the existing primary from the table locations on a combination of columns location_id and country_id.

Here is the structure of the table locations.

postgres=# \d locations

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          | not null
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  | not null
Indexes:
    "locations_pkey" PRIMARY KEY, btree (location_id, country_id)

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE locations 
DROP CONSTRAINT locations_pkey;

Output:

Now see the structure of the table locations after alteration.

postgres=# \d locations

     Column     |         Type          | Modifiers
----------------+-----------------------+-----------
 location_id    | numeric(4,0)          | not null
 street_address | character varying(40) |
 postal_code    | character varying(12) |
 city           | character varying(30) |
 state_province | character varying(25) |
 country_id     | character varying(2)  | not null

9. Write a SQL statement to add a foreign key on job_id column of job_history table referencing to the primary key job_id of jobs table.

Here is the structure of the table jobs and job_history.

postgres=# \d jobs

   Column   |         Type          | Modifiers
------------+-----------------------+-----------
 job_id     | character varying(10) | not null
 job_title  | character varying(35) |
 min_salary | numeric(6,0)          |
 max_salary | numeric(6,0)          |
Indexes:
    "jobs_pkey" PRIMARY KEY, btree (job_id)
	

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE job_history
ADD FOREIGN KEY(job_id)
REFERENCES jobs(job_id);

Output:

Now see the structure of the table job_history after being altered.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |
Foreign-key constraints:
    "job_history_job_id_fkey" FOREIGN KEY (job_id) REFERENCES jobs(job_id)


10. Write a SQL statement to add a foreign key constraint named fk_job_id on job_id column of job_history table referencing to the primary key job_id of jobs table.

Here is the structure of the table jobs and job_history.

postgres=# \d jobs

   Column   |         Type          | Modifiers
------------+-----------------------+-----------
 job_id     | character varying(10) | not null
 job_title  | character varying(35) |
 min_salary | numeric(6,0)          |
 max_salary | numeric(6,0)          |
Indexes:
    "jobs_pkey" PRIMARY KEY, btree (job_id)

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE job_history 
ADD CONSTRAINT fk_job_id 
FOREIGN KEY (job_id) 
REFERENCES jobs(job_id) 
ON UPDATE RESTRICT 
ON DELETE CASCADE;

Output:

Now see the structure of the table locations after being altered.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |
Foreign-key constraints:
    "fk_job_id" FOREIGN KEY (job_id) REFERENCES jobs(job_id) ON UPDATE RESTRICT ON DELETE CASCADE


11. Write a SQL statement to drop the existing foreign key fk_job_id from job_history table on job_id column, which is referenced to the job_id of jobs table

Here is the structure of the table job_history.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |
Foreign-key constraints:
    "fk_job_id" FOREIGN KEY (job_id) REFERENCES jobs(job_id) ON UPDATE RESTRICT ON DELETE CASCADE

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE job_history
DROP CONSTRAINT fk_job_id;

Output:

Now see the structure of the table job_history after being altered.

postgres=# \d job_history
 
    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |


12. Write a SQL statement to add an index named index_job_id on job_id column in the table job_history.

Here is the structure of the table job_history.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) |
 department_id | numeric(4,0)          |

Now execute the following statement.

Sample Solution:

Code:

CREATE UNIQUE INDEX CONCURRENTLY index_job_id ON job_history(job_id);
ALTER TABLE job_history ADD CONSTRAINT index_job_id PRIMARY KEY USING INDEX index_job_id;

Output:

Now see the structure of the table job_history after being altered.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) | not null
 department_id | numeric(4,0)          |
Indexes:
    "index_job_id" PRIMARY KEY, btree (job_id)


13. Write a SQL statement to drop the index indx_job_id from job_history table.

Here is the structure of the job_history and index file of the table job_history.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) | not null
 department_id | numeric(4,0)          |
Indexes:
    "index_job_id" PRIMARY KEY, btree (job_id)

Now execute the following statement.

Sample Solution:

Code:

ALTER TABLE job_history DROP CONSTRAINT index_job_id;

Output:

Now see the structure of the table job_history after being altered.

postgres=# \d job_history

    Column     |         Type          | Modifiers
---------------+-----------------------+-----------
 employee_id   | numeric(6,0)          |
 start_date    | date                  |
 end_date      | date                  |
 job_id        | character varying(10) | not null
 department_id | numeric(4,0)          |

Have another way to solve this solution? Contribute your code (and comments