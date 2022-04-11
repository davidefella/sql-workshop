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
CREATE TABLE engineering (employee_id  integer NOT NULL, 
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
ALTER TABLE table_name ALTER COLUMN nome_colonna TYPE datatype;
```

So, let's say we want to alter the firt_name column

```
ALTER TABLE engineering ALTER COLUMN first_name TYPE varchar(25);
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
INSERT INTO engineering(employee_id,first_name,last_name,email,country,salary) 
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

## OPERATORE IN

- L'operatore IN si usa per verificare l'appartenenza di un valore a un insieme. 

- Quando le clausole di ricerca sono molte l'operatore IN è molto più pratico. Evita di ripetere ogni volta il nome del campo, l'operatore uguale e l'operatore logico OR.

```
SELECT [campi] FROM [tabella] WHERE [campo] IN ( [clausole di ricerca] ) ;
```

Ad esempio, il per il nostro progetto una possibile query sarebbe

```
SELECT id FROM ordine WHERE nome_pizza IN ('margherita', 'diavola') ;
```

L'ultima query sarebbe equivalente a 

```
SELECT id FROM ordine WHERE nome_pizza = 'margherita' OR nome_pizza = 'diavola';
```

## LIKE

- Mi permette di analizzare il contenuto **parziale** di una stringa

- Utilizza due caratteri speciali da inserire dentro le stringhe: **%** e **_**

- Il simbolo **%** sostituisce un insieme di caratteri in una stringa 

- Il simbolo **_** mi sostituisce un carattere in una stringa 

La sintassi da utilizzare è la seguente: 

```
SELECT [campi] FROM [tavola] WHERE [campo LIKE stringa] 
```

Ecco alcuni esempi relativi al nostro progetto: 


- Tutti i clienti che hanno 'avi' in mezzo al loro nome 

```
select * from ordine where nome_cliente like '%avi%'; 
```

- Tutti i clienti che inziano per 'Anna' 
```
select * from ordine where nome_cliente like 'Anna%'; 
```

- Tutti i clienti che si chiamano Mario o Maria
```
select * from ordine where nome_cliente like 'Mari_'; 
```

## ISTRUZIONE DROP 

- Usata per rimuovere indici, tabelle e database

```
DROP TABLE table_name
```

```
DROP DATABASE database_name
```

## VINCOLI (CONSTRAINTS)

- Limitare il tipo di dati che possono andare in una tabella.

- Accuratezza, affidabilità ed integrità nei dati perché se c'è una violazione del vincolo, l'operazione viene interrotta. 

- A livello di colonna (dominio), tabella o attributo.

```
CREATE TABLE table_name (column datatype constraint);
```

Questi sono alcuni di quelli più utilizzati: 
- NOT NULL - Assicura che una colonna non contenga valori NULL
- UNIQUE - Assicura che una colonna non abbia valori duplicati
- PRIMARY KEY - Una combinazione NOT NULL + UNIQUE, identifica in maniera univoca una riga in una tabella
- FOREIGN KEY - Assicura la relazione tra tabelle
- CHECK - Assicura che i valori di una colonna rispettino una condizione 
- DEFAULT - Set di un valore di default per un attributo
- CREATE INDEX - Crea un indice che migliora la performance per alcune operazioni


### NOT NULL 

- Di default, una colonna può avere valori NULL. Il vincolo NOT NULL forza un attributo ad essere **diverso da NULL**. 

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```
oppure

```
ALTER TABLE Persons ALTER COLUMN Age SET NOT NULL;
```

### UNIQUE 

- Assicura che tutti i valori di una colonna di una tabella sono differenti. 

```
CREATE TABLE Persons (
    ID int NOT NULL UNIQUE,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
oppure 

```
ALTER TABLE Persons ADD CONSTRAINT age_unique UNIQUE(age);
```

### PRIMARY KEY  

- Una chiave primaria identifica un record in una tabella

- Una chiave primaria deve per forza avere un valore **unico** e **non può contenere valori nulli**

- Una tabella, quindi, può avere una sola chiave primaria 

```
CREATE TABLE po_headers (
	po_no INTEGER PRIMARY KEY,
	vendor_no INTEGER,
	description TEXT,
	shipping_address TEXT
);
```
oppure 

```
ALTER TABLE po_headers ADD PRIMARY KEY (po_no);
```

NOTA: in Postgresql, per rendere una chiave primaria numerica autonumerante: 

```
ALTER TABLE <tabella> ALTER COLUMN <nome_colonna> ADD GENERATED BY DEFAULT AS IDENTITY;
```


### FOREIGN KEY  

- E' un vincolo che mi assicura che le relazioni tra tabelle siano coerenti 

- La chiave esterna è un campo legato ad una **chiave primaria di un'altra relazione** (tabella)

- La tabella con la chiave esterna è chiamata tabella figlia, quella con la chiave primaria è chiamata tabella padre. 

```
CREATE TABLE contacts(
   phone VARCHAR(15),
   email VARCHAR(100),
   contact_id INTEGER PRIMARY KEY,
   customer_id INT,
   CONSTRAINT fk_customer
      FOREIGN KEY(customer_id) 
	  REFERENCES customers(customer_id)
);
```

oppure 

```
ALTER TABLE "contacts" ADD FOREIGN KEY (customer_id) REFERENCES customers(customer_id);
```

### CHECK  

Vincolo utilizzato per garantire che i dati all'interno di una colonna siano coerenti con una determinata condizione

```
DROP TABLE IF EXISTS employees;
CREATE TABLE employees (
	id SERIAL PRIMARY KEY,
	first_name VARCHAR (50),
	last_name VARCHAR (50),
	birth_date DATE CHECK (birth_date > '1900-01-01'),
	joined_date DATE CHECK (joined_date > birth_date),
	salary numeric CHECK(salary > 0)
);
```

oppure 

```
ALTER TABLE po_headers_new_new ADD CONSTRAINT vendor_no_check CHECK (vendor_no >= 0);
```

### DEFAULT  

- Utilizzata per impostare un valore di default nel caso l'istruzione di INSERT non passi il valore

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);
```

Oppure

```
alter table po_headers_new_new alter column description set default 'Sono un valore di default';
```

### OPERAZIONI DI JOIN 

- operazione nei database relazionali che permette di interrogare più tabelle di database mettendone in relazione i dati.

- Il principio del join SQL si basa sull'omonima operazione algebrica relazionale, cioè una combinazione derivata da un prodotto cartesiano e da una selezione. 

- Nota: Il prodotto cartesiano (o unione incrociata) è un'operazione di teoria degli insiemi in cui due o più insiemi sono collegati tra loro. La selezione è un'operazione di algebra relazionale che consente di selezionare specifiche tuple da un set iniziale e di inviarle come risultato.

- Vi sono diversi tipi di join SQL che consentono di eseguire query utilizzando un insieme di tabelle di database. Il prerequisito per fare ciò è che le tabelle selezionate siano collegate tra loro utilizzando relazioni a chiave esterna.

- I tipi di join più importanti sono **inner join** e **outer join** 

![alt text](https://www.ionos.it/digitalguide/fileadmin/DigitalGuide/Screenshots/DE-SQL-Join-Typen.png)


## INNER JOIN

```
SELECT <Elenco campi> FROM tabella_a **INNER JOIN** tabella_b **ON** tabella_a.pk_a = tabella_b.pk_b
```

### LEFT OUTER JOIN 

- Restituisce tutte le righe della prima tabella (nell’esempio Impiegati), anche se non ci sono corrispondenze nella seconda tabella


```
SELECT <Elenco campi> FROM tabella_a **LEFT JOIN** tabella_b **ON** tabella_a.pk_a = tabella_b.pk_b
```

### RIGHT OUTER JOIN 

```
SELECT <Elenco campi> FROM tabella_a **RIGHT JOIN** tabella_b **ON** tabella_a.pk_a = tabella_b.pk_b
```

### FULL OUTER JOIN 

```
SELECT <Elenco campi> FROM tabella_a **FULL JOIN** tabella_b **ON** tabella_a.pk_a = tabella_b.pk_b
```
