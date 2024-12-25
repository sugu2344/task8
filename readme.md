# **Sql Task**

## Create a database named ecommerce.

```sql
create database ecommerce;
use ecommerce;
```

- #### Customers table.

```sql
create table customers(id int primary key auto_increment,name varchar(20),email varchar(20),address varchar(50));

desc customers;
```

- #### Customers table Data.

```sql

insert into customers values
(1,"suganesh","suganesh@gmail.com","namakkal"),
(2,"naveen","naveen@gmail.com","salem"),
(3,"gokul","gokul@gmail.com","erode"),
(4,"vignesh","vignesh@gmail.com","namakkal"),
(5,"tamil","tamil@gmail.com","chennai"),
(6,"soundar","soundar@gmail.com","chennai"),
(7,"shankar","shankar@gmail.com","namakkal"),
(8,"muthu","muthu@gmail.com","karraikudi"),
(9,"vijay","vijay@gmail.com","karraikudi"),
(10,"sasi","sasi@gmail.com","salem");
select * from customers;
```

- #### orders Table

```sql
create table  orders(id int primary key auto_increment,customer_id int references customers(id),order_date date ,total_amount int)	;

desc orders;
```

- #### products Table

```sql
create table products(id int primary key auto_increment,name varchar(20),price int,description varchar(50));

desc products;
```
