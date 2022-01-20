What is SQL ?
=============

SQL stands for Structured Query Language and is a language that you use to manage data in databases. SQL consists of commands and declarative statements that act as instructions to the database so it can perform tasks.

You can use SQL commands to create a table in a database, to add and make changes to large amounts of data, to search through it to quickly find something specific, or to delete a table all together. [1]

[1] <a href="https://it.wikipedia.org/wiki/Structured_Query_Language">https://it.wikipedia.org/wiki/Structured_Query_Language</a>

Starting your journey
---------------------

An SQL database is a collection of related information stored in tables. Each table has columns that describe the data in them, and rows that contain the actual data. A field is a single piece of data within a row. So to fetch the desired data we need to get specific.

A remote company can have multiple databases, a single database can have multiple tables. All tables then consist of different columns that describe the data and also consist of rows, which are individual entries into the table. 

Let's `create` the structure!
---------------------------

But First, let's create the structure. To create a database named engineering, we can use the following code:

```
CREATE DATABASE engineering;
```

This query creates a new table inside the database, it gives the table a name, and the different columns we want our table to have are also passed in.

```
CREATE TABLE table_name (column1 datatype, column2 datatype, column3 datatype);
```

There are a variety of datatypes that we can use. Some of the most common ones are: `INT`, `DECIMAL`, `DATETIME`, `VARCHAR`, `NVARCHAR`, `FLOAT`, and `BIT`. 

From our example above, this could look like the following code: 

```
CREATE TABLE engineering (employee_id  int(6) NOT NULL, 
                          first_name varchar(20) NOT NULL, 
                          last_name varchar(25) NOT NULL, 
                          email varchar(255) NOT NULL, 
                          country varchar(30), 
                          salary decimal(10,2) NOT NULL);
```

The table we create from this data would look something similar to this:

| employee_id    | first_name     | first_name | email   | country | salary  |
| -------------  |:-------------: | ---------: | ------: | ------: | ------: |
|                |                |            |         |         |         |

After creating the table, we can modify it by adding another column to it: 

```
ALTER TABLE table_name ADD column_name datatype;
```

For example, if we wanted we could add a birthday column to our existing table by typing:

```
ALTER TABLE engineering ADD birthday date;`
```

| employee_id    | first_name     | first_name | email   | country | salary  | birthday |
| -------------  |:-------------: | ---------: | ------: | ------: | ------: | ------:  |
|                |                |            |         |         |         |          |

If we want to alter some column: 

```
ALTER TABLE table_name ALTER COLUMN datatype;
```

So, let's say we want to alter the firt_name column

```
ALTER TABLE engineering ALTER COLUMN first_name varchar(25);
```

If we want to remove all rows from the table: 

```
TRUNCATE TABLE engineering;
```

All the operatations that you can do with data follow the `CRUD` acronym. CRUD stands for the 4 main operations we perform when we query a database: `Create`, `Read`, `Update`, and `Delete`.

SQL `INSERT` Statement
---------------------------

This is how we insert data into tables and create new rows. It's the `C` part in CRUD.

```
INSERT INTO table_name(column1, column2, column3,..) 
VALUES(value1, 'value2', value3,..);
```

In the INSERT INTO part, we can specify the columns we want to fill with information. Inside VALUES goes the information we want to store. This creates a new record in the table which is a new row.

```
INSERT INTO table_name(employee_id,first_name,last_name,email,country,salary) 
VALUES (1,'Timmy','Jones','timmy@gmail.com', 'USA',2500.00);
VALUES (2,'Kelly','Smith','ksmith@gmail.com','UK', 1300.00);
```

| employee_id    | first_name     | first_name |       email        | country  | salary  | birthday |
| -------------  |:-------------: | ---------: | ---------------:   | ------:  | ------: | ------:  |
|       1        |     Timmy      |  Jones     |  timmy@gmail.com   |    USA   | 2500.00 |          | 
|       2        |     Kelly      |  Smith     |  ksmith@gmail.com  |    UK    | 1300.00 |          | 

SQL `SELECT` Statement
---------------------------
This statement fetches data from the database. It is the `R` part of CRUD.

```
SELECT  column1,column2
FROM    table_name;
```
From our example earlier, this would look like the following:

```
SELECT first_name,last_name
FROM   engineering;
```

| first_name   | last_name  |
| :--------- : | ---------: |
|    Timmy     |   Jones    |
|    Kelly     |   Smith    | 


The `SELECT` statement points to the specific column we want to fetch data from that we want shown in the results. The `FROM` part determines the table itself.
Here's another example of `SELECT`:

```
SELECT * FROM table_name;
```

The asterisk `*` will grab all the information from the table we specify.

SQL `WHERE` Statement
--------------------

`WHERE` allows us to get more specific with our queries.

If we wanted to filter through our `Engineering` table to search for employees that have a specific salary, we would use `WHERE`.

```
SELECT *
FROM engineering
WHERE salary > 1500
```

| employee_id    | first_name     | first_name |       email        | country  | salary  | birthday |
| -------------  |:-------------: | ---------: | ---------------:   | ------:  | ------: | ------:  |
|       1        |     Timmy      |  Jones     |  timmy@gmail.com   |    USA   | 2500.00 |          | 


This filters through and shows the results that satisfy the condition – that is, it shows only the rows of the people whose salary is `more than 1500`.


SQL `AND`, `OR`, and `BETWEEN` Operators
-----------------------------------

These operators allow you to make the query even more specific by adding more criteria to the `WHERE` statement. The `AND` operator takes in two conditions and they both must be `true` in order for the row to be shown in the result.


```
SELECT column_name
FROM table_name
WHERE column1 =value1 AND column2 = value2;
```

The `OR` operator takes in two conditions, and either one must be true in order for the row to be shown in the result.

```
SELECT column_name
FROM table_name
WHERE column1 =value1 AND column2 = value2;
```


The `BETWEEN` operator filters out within a specific range of numbers or text.

```
SELECT column1,column2
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

We can also use these operators in combination with each other.

```
SELECT * FROM engineering
WHERE  employee_id BETWEEN 3 AND 7
        AND 
        country = 'Germany';
```

This selects all comlumns that have an `employee_id` between` 3 and 7` `AND` have a country of `Germany`.




