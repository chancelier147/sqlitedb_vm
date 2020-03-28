**INSTALL AND CONNECT TO SQLITE DATABASE FROM A VIRTUAL MACHINE.**

(Create a Database name &quot;newdatabase&quot; and create 4 tables in it.)

This project is divided into two steps. The first step is to deploy a virtual machine and install sqlite with vagrant. The second step concerns the creation of a new database and four (4) tables inside this database.

**1. Creating a virtual machine and installing sqlite**

The Vagrant file contains the code needed to deploy an ubuntu bionic virtual machine and install sqlite.

**2. Creating a new database**

First you have to connect to our installed virtual machine with the command &quot;**vagrant ssh**&quot; and then execute the following commands.
```
$ sqlite3 newdatabase
```

And now create the 4 tables:

```
create table clients(
   ...> num_client INT NOT NULL PRIMARY KEY,
   ...> lastname VARCHAR(20),
   ...> firstname VARCHAR(20)
   ...> );

create table products(
   ...> num_product INT NOT NULL PRIMARY KEY,
   ...> product_name VARCHAR(20),
   ...> product_price INT NOT NULL,
   ...> product_description TEXT
   ...> );

create table sales(
   ...> num_sale INT NOT NULL PRIMARY KEY,
   ...> date_sale DATE,
   ...> product_num INT,
   ...> client_num INT,
   ...> FOREIGN KEY (product_num) REFERENCES products (num_product),
   ...> FOREIGN KEY (client_num) REFERENCES clients (num_client)
   ...> );

create table best_clients(
   ...> num_best_client INT NOT NULL PRIMARY KEY,
   ...> lastname VARCHAR(20),
   ...> firstname VARCHAR(20)
   ...> );
```
