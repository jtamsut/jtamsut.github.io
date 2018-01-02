---
layout: post
title: "An Introduction to Relational Databases"
categories: relational databases SQL
---

I. Table of Contents 

A. Basics of Relational Databases 
B. Relational Databases 
C. Relational Query Language (SQL)

This article will explore the fundamental concepts behind relational databases. In this article we will be concerned mainly with learning the syntax and semantics of the **Structured Query Language** (or SQL which is pronounced "ess-kew-ell") as well as learning how to design relational database schemas.

We will begin by discussing the defining features of a relational database and how relational databases differ from other types of databases such as a document-orientated databases or key-value databases. Once we know *what* a relational database is we will then discuss how to add, delete, update and query data in a relational database using the Structured Query Language or SQL. 

## Brief History of Relational Databases 

 <!-- As computer's became more ubiquitous in the 1960's the need for a way to persist data arose. In 1970 a British computer scientist published a paper entitled [*A relational model of data for large shared data banks*]({{site_url}}/images/relational-data-codd.pdf) where he TODO  -->

## What is a Relational Database?

A **database** is any "technology" that stores data in an organized fashion for an extended period of time. Therefore, we can say that a filing cabinet is a *type* of database because it stores files (the contents of the files are the *data*) in an organized manner (possibly in alphabetical order by file name). Databases store information in a highly structured and searchable way. The data in a database must be organized in such a way that it can logically and quickly be retrieved. This article will discuss **relational databases**, but you should know other types of databases exist.

### Vast Landscape of Databases 

How a database organizes its data determines what type of database it is. Relational databases store data in tables and rows while key-value stores store data in key-value pairs. 

The term *database* is a generic term referring to anything that stores data. A **Database Management Software** (DBMS) is a specific piece of software used to manipulate a database. There are many relational DBMS's. Here are three of them:

* [PostgreSQL](https://www.postgresql.org/)
* [MySQL](https://www.mysql.com/)
* [MariaDB](https://mariadb.com/kb/en/mariadb/introduction-to-relational-databases/)

**Tables** or **relations** are what make relational databases "relational". Relational databases store data in tables. They are unique in this regard. These tables are made up of **rows** or **tuples** and **columns** or **attributes**.

![table]({{site_url}}/images/1280px-Relational_database_terms.svg.png)

All data in a given attribute must be of the same type. Examples of different types you'll see an attribute having are: 

* `varchar(80)` - a string that is 80 characters in length or less
* `int` - a number without a decimal
* `real` - a number with a decimal
* `serial` - an autoincrementing integer (e.g., 1 then 2 then 3 ...)

The number of tuples is the **cardinality** of a relation. The number of attributes is the **arity** of the relation.

As stated before a single relational database is comprised of multiple tables.

![table]({{site_url}}/images/tables_in_db.png)

### An Example: Ole, ole 

Let's take a look at a simple example of a schematic of a simple relational database. Relational databases have a unique name. Let's consider a database with the name: **la-liga-players**. This database has a single table named **player**. This is what the table looks like:

|Player Name (String)|Goals (Integer)|Age (Integer)|
|------------------|-----|---|
|Lionel Messi      |25   |29 |
|Luis Suarez       |23   |30 |
|Cristiano Ronaldo |19   |32 |

This tables has the following attributes: 

* Player Name (String)
* Goals (Integer)
* Age (Integer)

Note that all data in a given attribute has the *same* type. Fpr example, all data under the `Goals` attribute is of type `Integer`.

This table has three tuples and a cardinality of 3. Let's assume that in the data we are considering no two players can have the same name. We can therefore say that `Player Name` uniquely identifies each tuple. All data in a given record should be about the same *thing*. For example, all data in a row is about a single player (e.g., Messi, Saurez, Ronaldo). You shouldn't put the number of goals Ronaldo has scored in Messi's record.
  
Now let's say we also wanted to store data about the teams these players were on. The data we want to store for each team is:
  
  * Team Name 
  * Current League Positions (abbreviated Position)
  * Number of La Liga Titles that a team has won (abbreviated Titles)
  
<center><b>Where should we store this data?</b></center>

A naive approach would be to store a team's data in the player table. If we did this our resulting table would look like this:

|Player Name (String)|Goals (Integer)|Age (Integer)| Team Name (String) | Position (Integer) | Titles (Integer) |
|------------------|-----|---|------------|----------|--------|
|Lionel Messi      |25   |29 |FC Barcelona|    2     |   24   |
|Luis Suarez       |23   |30 |FC Barcelona|    2     |   24   | 
|Cristiano Ronaldo |19   |32 |Real Madrid |    1     |   32   |

We have two records that contain the team information for FC Barcelona. Therefore, when FC Barcelona wins another title we must update two records. This is not optimal because: 

* Having to update two records takes longer than updating one 
* We are more likely to make a mistake when we have data duplicated

Generally we want all data to be stored at most **ONCE** in our database. This makes it easier to update. For example if we wanted to update the number of titles FC Barcelona has won we would have to update 2 rows. What if FC Barcelona had 1,000 players? Updating would be very inefficient.

A better way to store the team data is to construct two tables: 

* a Player Table
* a Team Table

The `Player` table would look like this: 

|Player Name (String)       |Goals|Age|Team         |
|------------------|-----|---|-------------|        
|Lionel Messi      |25   |29 |FC Barcelona |    
|Luis Suarez       |23   |30 |FC Barcelona |
|Cristiano Ronaldo |19   |32 |Real Madrid  |

The `Team` table would look like this:

| Team Name  | Position | Titles |
|------------|----------|--------|
|FC Barcelona|    2     |   24   |
|Real Madrid |    1     |   32   |

All tables in a relational database must have a **primary key**. A primary key is a piece of data that uniquely identifies a record. A primary key is always in the same table as the record it identifies. Assuming no two players can have the same name, the `Player Name` attribute is the primary key in the `Player` table. The `Team Name` attribute is the primary key in the `Team` table because no 2 teams can have the same name.

A **foreign key** is a key that lives in one table but uniquely identifies a record in another table. The foreign key in the `Player` table is the `Team` attribute because it references the primary key in another table: the `Team` table.

We can specify a tables **schema** which is essentially a "blue print" for a table. A schema for a given table is that table's name, all of its attribute names and all of its attribute types. A schema for the `Player` table is: 

| Player               |
|----------------------|
|Player Name (String)  |
| Age (Integer)        |
| Goals (Integer)      |
| Team (String)        |

## Basics of SQL 

<!--NEED TO DEFINE A TERM THAT IS GIVEN AS A RESULT OF A SQL QUERY  -->

The Structured Query Language or SQL is a high-level programming language used for querying and manipulating data in relational databases. SQL is the programming language we use to add data, remove data, update data and delete data from a relational database. Suppose we had a `products` table that looked like this. Let's take a look at what a few SQL queries on this table would look like. 

| product-id | product-name | product-price |
|------------|--------------|---------------|
| 0          | black socks  | 2.50          |
| 1          | white socks  | 3.50          |
| 2          | yellow socks | 1.50          |

### SELECT 

`SELECT` is used to retrieve data - by column - from a database table. To use a `SELECT` statement you must pass as arguments 2 pieces of data: 

1. The name of the column(s) you want to select 
2. From what table you want to select a column from  

```sql
SELECT prod_name FROM products; 
```

You can `SELECT` all columns from a table using the wildcard character: 

```sql 
SELECT * FROM products;
```

Note that by convention all SQL keywords are written in capital letters. 

### WHERE 

Sometimes you want to select records based on some search criterion and you want to filter out all other records. A `WHERE` clause can be used to do this. 

```sql
SELECT product-id, product-name
FROM products 
WHERE product-price > 2.00;
```

The result of this query will be: 

| product-id | product-name | product-price |
|------------|--------------|---------------|
| 0          | black socks  | 2.50          |
| 1          | white socks  | 3.50          |

You can also use the `AND` and `OR` logical operators to filter by more than one column.

```sql
SELECT product-id, product-name
FROM products 
WHERE product-price > 2.00 AND product-name = "black socks";
```


### LIKE 

### JOINS 

SQL allows you to join tables on the fly when performing a query. This is us

Need an example of this.

Product Catalog Table 

Item ID|Item Name|Item Price|Vendor Name|Vendor Location| 
-------|---------|----------|-----------|---------------| 
0 
1
2
3
4
5

Why use a join table? 

* Repeating data is a waste of storage space. Use less storage space you save money which means you make more $.
* Repeating data makes it more likely that when you update it you will make a mistake









---


* How to create databases and tables using `CREATE` 
* How to retrieve data from a single relational database table using a `SELECT` statement
* How to filter the results of a SQL `SELECT` using a `WHERE` clause 

1. The SQL programming language is a special-purpose programming lanugage designed for managing information nit a relational database management system. 


A relational database is a database that stores data in tables. A table is comprised of columns and rows. 

Each table has predefined data. If you want to add information to a table is must fit into one of the tables. This is different thatn Mongo where you can have data in the same document that has a different structure.

Other types of databases.

Key-value pairs 
Document stores

Data definition language

A **relation** or **table** is a multiset of tupes having the attributes specified by the schema. 

A **multiset** is a set where multiple elements are allowed.

A **tuple** is an ordered list of elements.

An **attrinute** or **column** is a typed data entry present in each tuple of a relation.

A **tuple** or **row** is a single entry in the table having the attributes specified by the schema.


The **schema** of a table is the table name, its attributes and their types. 

A **key** is an attribute whose values are unique.

All rows need a key. A key must uniquely identify a row.

`NULL` means we do not know the value of something.

common query is the `SFW` query `SELECT FROM WHERE`

Selection is the operation of filtering a relation's tuples based on some condition.

A **projection** is the operation of producing an output table with tuples that have a subset of their prior attributes. 

**Primary key** 

**Foreign key**

Define the term **entity**

SQL commands are case insensitive. Values are not. Use single quotes for constants. 

`LIKE`: Simple string pattern matching

## History of SQL 

## Introduction to SQL 



### Tables 

### Rows 

## How Do We Query Relational Databases?

We query a relational database using SQL keywords. Every SQL query is composed of one or more keywords. 

SQL statements are case insensitive. So `SELECT` and `select` will also work. 

`CREATE` 
`CREATE TABLE`
`INSERT`
### `SELECT`

`SELECT` is used to retrieve one or more columns of data from a database table. To use select you must at minimum specify two pieces of information: 

1. What you want to select.
2. From where you want to select it.

You should not assume any ordering of the data that is returned from the result of a `SELECT` query.

`DELETE`

The wildcard operator (`*`)

## Glossary 

* table 
* record 
* column 
* keyword - a reserved word that is a part of the SQL language. Never name a table or column using a keyword.
* normalization 
* database query 
* join table


The `WHERE` clause

## INNER JOIN
## LEFT JOIN 
## RIGHT JOIN 
## FULL JOIN

## Quiz

|Player            |Goals|Age|Team         |
|------------------|-----|---|-------------|        
|Lionel Messi      |25   |29 |FC Barcelona |    
|Luis Suarez       |23   |30 |FC Barcelona |
|Cristiano Ronaldo |19   |32 |Real Madrid  |

AND

| Team Name  | Position | Titles |
|------------|----------|--------|
|FC Barcelona|    2     |   24   |
|Real Madrid |    1     |   32   |

**Quiz**: What are the name(s) of the players who play on the second place team AND are older than 29?

A **join** between tables returns all unique combinatiosn of their tuples which meet some specified join condition. 

Resolving ambigous variable names: https://docs.oracle.com/cloud/latest/db112/LNPLS/nameresolution.htm#LNPLS2038

## Aggregation 

## The Entity-Relational Model 

The difference between a relation (i.e., a table) and a relationship (i.e., a connection between 2 tables)

How do we design a database a system. 

An ERD is a graphical representation of entities and their relationships to each other 

## Database Design Process

1 (800) YOU - WISH

Cardinality: Only 2 values are one and many. 

WHY DO WE NEED JOIN TABLES????


## Joins 

A SQL `JOIN` is an instruction to combine data from two tables into one.

There are four basic types of SQL joins: 

* `INNER JOINS`
* `
* 
* 

# Appendix: Common PostgreSQL Commands 

All of these commands can be executed in `psql`:

* `\l` - List all databases 
* `\c <db-name>` - Create a new database with name `<db-name>`
* `\dt` - List all tables
* `\d <table-name>`- List details for a table with name `<table-name>`
* `\?` - List all psql commands 
* `\q` - Quit psql 
* `\h` - List documentation for a SQL command

<!--

    What's left: 

    Explain JOINS
    Explain CREATE, INSERT, DELETE, IN
    Explain one-to-many
    Explain many-to-many 
    Explain ERDs 
    Explain Join Tables 

    Exercises: 


  -->

JOINS 
Sub-queries 
DB Indexing

Transactions 

http://philip.greenspun.com/sql/

Why does a join table exist.

A - Atomicity
C - Consistency
I - Isolation
D - Durability

Cap Theorem 

Relational Algebra

http://robertgreiner.com/2014/08/cap-theorem-revisited/

Commands 
`ORDER BY` 
`UNION` 
`AS` 


## Joins and Subqueries 

Joining allows you to query multiple tables at once. 

Cartesian product