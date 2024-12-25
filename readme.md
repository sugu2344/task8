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
