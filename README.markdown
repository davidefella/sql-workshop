What is SQL ?
=============

SQL stands for Structured Query Language and is a language that you use to manage data in databases. SQL consists of commands and declarative statements that act as instructions to the database so it can perform tasks.

You can use SQL commands to create a table in a database, to add and make changes to large amounts of data, to search through it to quickly find something specific, or to delete a table all together. [1]

[1] <a href="https://it.wikipedia.org/wiki/Structured_Query_Language">https://it.wikipedia.org/wiki/Structured_Query_Language</a>

Starting your journey
---------------------

An SQL database is a collection of related information stored in tables. Each table has columns that describe the data in them, and rows that contain the actual data. A field is a single piece of data within a row. So to fetch the desired data we need to get specific.

A remote company can have multiple databases, a single database can have multiple tables. 

[TABLE PHOTO]


All tables then consist of different columns that describe the data and also consist of rows, which are individual entries into the table. 


Basic SQL Queries
---------------------

All the operatations that you can do with data follow the `CRUD` acronym. CRUD stands for the 4 main operations we perform when we query a database: `Create`, `Read`, `Update`, and `Delete`.

But First, let's create the structure. To create a database named engineering, we can use the following code:

`CREATE DATABASE engineering;`

This query creates a new table inside the database.

`CREATE TABLE table_name (column1 datatype, olumn2 datatype, olumn3 datatype);`




