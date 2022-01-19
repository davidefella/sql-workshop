What is SQL ?
=============

SQL stands for Structured Query Language and is a language that you use to manage data in databases. SQL consists of commands and declarative statements that act as instructions to the database so it can perform tasks.

You can use SQL commands to create a table in a database, to add and make changes to large amounts of data, to search through it to quickly find something specific, or to delete a table all together. [1]

[1] <a href="https://it.wikipedia.org/wiki/Structured_Query_Language">https://it.wikipedia.org/wiki/Structured_Query_Language</a>

Starting your journey
---------------------

An SQL database is a collection of related information stored in tables. Each table has columns that describe the data in them, and rows that contain the actual data. A field is a single piece of data within a row. So to fetch the desired data we need to get specific.

A remote company can have multiple databases, a single database can have multiple tables. All tables then consist of different columns that describe the data and also consist of rows, which are individual entries into the table. 

Let's create the structure!
---------------------------

But First, let's create the structure. To create a database named engineering, we can use the following code:

`CREATE DATABASE engineering;`

This query creates a new table inside the database, it gives the table a name, and the different columns we want our table to have are also passed in.

`CREATE TABLE table_name (column1 datatype, column2 datatype, column3 datatype);`

There are a variety of datatypes that we can use. Some of the most common ones are: `INT`, `DECIMAL`, `DATETIME`, `VARCHAR`, `NVARCHAR`, `FLOAT`, and `BIT`. 

From our example above, this could look like the following code: 

`CREATE TABLE engineering (employee_id  int(6) NOT NULL, first_name varchar(20) NOT NULL, last_name varchar(25) NOT NULL, email varchar(255) NOT NULL, country varchar(30), salary decimal(10,2) NOT NULL);`

The table we create from this data would look something similar to this:

| employee_id    | first_name     | first_name | email   | country | salary  |
| -------------  |:-------------: | ---------: | ------: | ------: | ------: |
|                |                |            |         |         |         |

After creating the table, we can modify it by adding another column to it: 

`ALTER TABLE table_name ADD column_name datatype;`

For example, if we wanted we could add a birthday column to our existing table by typing:

`ALTER TABLE engineering ADD birthday date;`

| employee_id    | first_name     | first_name | email   | country | salary  | birthday |
| -------------  |:-------------: | ---------: | ------: | ------: | ------: | ------:  |
|                |                |            |         |         |         |          |

If we want to alter some column: 

`ALTER TABLE table_name ALTER COLUMN datatype;`

So, let's say we want to alter the firt_name column

`ALTER TABLE engineering ALTER COLUMN first_name varchar(25);`

If we want to remove all rows from the table: 

`TRUNCATE TABLE engineering;`

Manipulate the data!
---------------------------
All the operatations that you can do with data follow the `CRUD` acronym. CRUD stands for the 4 main operations we perform when we query a database: `Create`, `Read`, `Update`, and `Delete`.

