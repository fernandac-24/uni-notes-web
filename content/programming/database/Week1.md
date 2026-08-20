#database


# Introduction to SQL 

## Links 
* [Grokking Relational Database Design Course](https://github.com/StructuredCS/grokking-relational-database-design)

* [Grokking Relational Database Design Code](https://github.com/Neo-Hao/grokking-relational-database-design)

* [Relational Database Design - Full Course](https://www.youtube.com/watch?v=26ls5lNiijk)


## Tables, Entities, Keys & SQL

What are Relational Databases?
 It is a collection of _tables_. 

* Tables:
-> Is like a spreadsheet where data is organized into rows and columns;
-> used to represent an entire or a relationship between _entities_.

* Entity:
-> is an object or concept that can be described by many _attributes_. 
> [!Image 1]
> ![[Entity.jpeg]]

Insertion Anomaly = occurs when you cannot add vital data to a table because others unrelated or dependent data is missing. 


### Relational Database Management System (RDBMS)
Is a software that: 
-> interacts with the underlying hardware and operating system to physically store and manage data in relational databases. 
 Some common RDBMS - MySQL, MariaDB, PostegreSQL and SQLite
 -> is used to manage and mantain different databases.
* Database:  organizes data into different tables;
> [!Image 2] 
> ![[RDBMS.png | 250x250]]

-> provides tools and functions to manage databases;

* SQL (Structured Query Language) : a programming language that you can use to create, modify, and query data stored in tables in a RDMS. 
	Is the standardized language that most RDMS uses. 

### Firts taste of SQL 
Product table from the Sci-Fi Collective database: 
> [!Image 3]
> ![[sciFiDatabase.png]]

How do we get the product names from the product table whose price is above $20? 

```sql title:code1
SELECT name 
FROM product
WHERE price > 20; 
```
^code1

We are going to use the [[readme1#SQLite online| SQLite Online]] thats a database running on the cloud. 

The firtst SQL command that we'll be running is:

```sql title:code2
SELECT * FROM product ;
```

Wich means select everything (* <=> everything) from the product table. 

This results in showing a table simmilar to the one in [[sciFiDatabase.png]]. 

> [!info]
> ![[SciFiDatabase1.png]]

When we run [[#^code1 | this SQL query]] we receive a "list" of names, of all products wich prices are higher than $20. 
It returns a single column (name), with five rows, in each with a name of one of the products, that has the corresponding characteristic. 
The names are: "Selfie Toaster", "Cat-Poop Coffee", "Inflatable Briefcase", "Lightsabers" and "The Neuralyzer". 

#### SQL clauses:
* `SELECT`: specifies the columns you want to retrieve from a table;
* `FROM`: specifies the source you want to retrieve data from, it can be one or more tables; 
* `WHERE`: allows you to specify conditions to filter the data retrieved by the `SELECT` clause; 
* ` ; ` : indicates the end of the query;

## SQL Filtering & Aggregation

### Filtering 
`WHERE`clause helps you filter only a _subset of data_. In this scenario a subset of data means _rows_. 
So the Where clause filters rows based on the condition that follows. 

If you want, for exemple, that the search retrieves also the description, we can do like this : 
```sql title:'filtering-multiple-columns-with-where'
SELECT name, description
FROM product
WHERE price > 20; 
```
^code3
To get the names of products that are made by 'Mad Inventors Inc.' :
(Comparing the string data types in the manufacter rows)
```sql title:'filtering-by-exact-string-match'
SELECT name
FROM product
WHERE manufacturer 
      = 'Mad Inventors Inc.'; 
```
^code4

#### SQL data types:
- Numeric data types
- String data types ('string')
- Date or time data types
- Unicode character string data types
- Binary data types 
- Miscellaneous data types

#### Logical Operators
- `AND`
- `OR`
- `>`
- `>=`
- `<` 
- `<=` 

Exemple:
Get the products that are made by 'Mad Inventors Inc.' and have a price below 30. 
```sql title:'exemple-logic-operators'
SELECT *
FROM product
WHERE manufacturer = 'Mad Inventors Inc.' 
		AND price < 30; 
```
^code5

>> [!warning]  The result rows 
>>The order of the result rows don't matter, So we shoundn't have any assumptions or 
>> expectations in terms of how the rows are ordered in the results. 

### Aggregation 
 Is about performing calculations on a set of rows to produce a single result. 
 By aggregating data, you can gain insights into the trend and the patterns in the data that may not be visible at the individual record level . 

Exemple: To count the number of rows in the product table. 
We can use the function `COUNT`. 

```sql title:'COUNT exemple'
SELECT COUNT(*)
FROM product;
```
^code6

#### Function
* `COUNT()`: counts the number of rows, and it takes a single parameter;
* `SUM()`: Calculates the _sum_ of the values in a numeric column;
* `AVG()`: Calculates the _average_ value in a numeric column;

Exemple: To get the average price of products that are made by 'Mad Inventors Inc.' 
(Remember [[#^code4| how to filter the products by manufacturer]] ).

```sql title:'AVG exemple'
SELECT AVG(price) AS avg_price 
FROM product
WHERE manufacturer 
      = 'Mad Inventors Inc.'; 
```
^code7
> [!note] 
> The `AS avg_price` simply renames the result column. 

* `MAX()`: Finds the _maximum_ value in a clolumn;
* `MIN()`: Finds the _minimum_ value in a column;

________________________________________________________________________
A new clause to the [[#SQL clauses]]: 
*`GROUP BY`: group rows that have the same values in one or more columns;

_ It allows us to apply functions to each group individually. _

Exemple: To get the number of products per manufacturer 

```sql title:'GOUP BY exemple' 
SELECT COUNT(*) AS product_count, manufacturer
FROM product
GROUP BY manufacturer; 
```
^code8
> [!warning]+ DO NOT FORGET! 
> Remember to include the column following the `GROUP BY`clause in the`SELECT`statement. 
> Why?
> If you forget to do so, you result will come up without the manufacturer column. 

> [!warning]+ DO NOT FORGET!
> Remember to exclude from the `SELECT`clause any column that are neither in the `GROUP BY` clause or the aggregate functions. 
> ```sql title:'Exemple of what you can't do
> SELECT COUNT(*) AS product_count, manufacturer, name
> FROM product
> GROUP BY manufacturer;
> ```
>  _the `name`in line 1 can lead to a error in some SQL engines, and in others the column name will be filled with arbitrarily values from or last row it reads for the group.  _

## SQL Table Commands

### Table management 

#### Create a table 
* `CREATE TABLE`: command handles table creation;

Context: Create the product table for the database supporting The Sci-Fi Collective. 
Remember the struct of the product entity [[Entity.jpeg]]. 
To create the table plus adding a primary key beyond these four different attributes the command will look like this: 

```sql title:'Create a table'
CREATE TABLE product (
	product_id INT PRIMARY KEY,
	name TEXT NOT NULL,
	description TEXT NOT NULL,
	price DECIMAL(5,2) NOT NULL, 
	manufacturer TEXT NOT NULL
);
```

