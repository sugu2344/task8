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

- #### orders table Data.

```sql
insert into orders values
(1,1,"2024-10-2",50),
(2,2,"2024-10-12",150),
(3,1,"2024-11-6",200),
(4,5,"2024-11-28",350),
(5,5,"2024-10-25",333),
(6,8,"2024-12-5",99),
(7,4,"2024-12-11",66),
(8,3,"2024-11-28",73),
(9,6,"2024-12-21",64),
(10,6,"2024-12-9",82),
(11,7,"2024-11-30",100),
(12,10,"2024-11-10",173);
select * from orders;
```

- #### products Table

```sql
create table products(id int primary key auto_increment,name varchar(20),price int,description varchar(50));

desc products;
```

- #### Products table Data.

```sql
insert into products values
(1,"product A",111,"electronics"),
(2,"product B",222,"groceries"),
(3,"product c",100,"vegetables"),
(4,"product d",555,"cloths"),
(5,"product e",666,"furnuiture"),
(6,"product c",444,"vechies");
select * from products;

```

- #### view table with data.

```sql
select * from products;
select * from orders;
select * from customers;
```



# **Queries **

#### 1) Retrieve all customers who have placed an order in the last 30 days.

```sql
select distinct customers.id, customers.name,customers.email,customers.address
from customers
join orders
on customers.id = orders.customer_id
where order_date >=curdate()- interval 30 day;
```

#### 2) Get the total amount of all orders placed by each customer.

```sql
SELECT customers.id, customers.name, customers.email, customers.address, SUM(orders.total_amount) AS Total_amount
FROM customers
JOIN orders ON customers.id = orders.customer_id
GROUP BY customers.id;
```

#### 3) Update the price of Product C to 45.00.

```sql
select * from products;
update products set price=45 where id=3;
select * from products;
```

#### 4) Add a new column discount to the products table.

```sql
alter table products add column discount int;
select * from products;
```

#### 5) Retrieve the top 3 products with the highest price.

```sql
select * from products;
select * from products order by price desc limit 3;
```

#### 6) Get the names of customers who have ordered Product A.

```sql
-- table list
select * from customers;
select * from products;
select * from orders;
select * from order_items;

SELECT DISTINCT customers.name
FROM customers
JOIN orders ON customers.id = orders.customer_id
JOIN order_items ON orders.id = order_items.order_id
JOIN products ON products.id = order_items.product_id
WHERE products.name = 'Product a';
```

#### 7) Join the orders and customers tables to retrieve the customer's name and order date for each order.

```sql
 select orders.id as order_id ,customers.name as customer_Name,orders.order_date
   from orders
   join customers
   ON
   customers.id = orders.customer_id;

   ```
 #### 8) Retrieve the orders with a total amount greater than 150.00.

 ```sql
select * from orders
where total_amount >150;
 ```

  #### 9) Normalize the database by creating a separate table for order items and updating the orders table to reference the order_items table.

   ```sql
   CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    foreign key (order_id) references orders(id),
    foreign key (product_id) references products(id)
);
desc order_items;
select * from order_items;
```
 #### 10) Retrieve the average total of all orders.

   ```sql
   SELECT AVG(total_amount) as average_total
FROM orders;
```



