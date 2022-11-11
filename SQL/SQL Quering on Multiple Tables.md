# Query on Multiple Tables
**1.** From the following tables, write a SQL query to find the salespeople and customers who live in the same city. Return customer name, salesperson name and salesperson city
~~~~sql
SELECT c.cust_name,
s.name, s.city
FROM salesman s, customer c
WHERE s.city = c.city
~~~~
**2.** From the following tables, write a SQL query to locate all the customers and the salesperson who works for them. Return customer name, and salesperson name.
~~~~sql
SELECT c.cust_name, s.name
FROM customer c , salesman s
WHERE s.salesman_id = c.salesman_id;
~~~~
**3.** From the following tables, write a SQL query to find those salespeople who generated orders for their customers but are not located in the same city. Return ord_no, cust_name, customer_id (orders table), salesman_id (orders table).
~~~~sql
SELECT o.ord_no, c.cust_name, c.customer_id, s.salesman_id 
FROM salesman s, customer c, orders o
WHERE s.city != c.city
AND o.customer_id = c.customer_id
AND o.salesman_id = s.salesman_id
~~~~
**4.** From the following tables, write a SQL query to locate the orders made by customers. Return order number, customer name.
~~~~sql
SELECT o.ord_no, c.cust_name
FROM customer c, orders o
WHERE c.customer_id = o.customer_id 
~~~~
**5.** From the following tables, write a SQL query to find those customers where each customer has a grade and is served by a salesperson who belongs to a city. Return cust_name as "Customer", grade as "Grade".
~~~~sql
SELECT c.cust_name AS "Customer",
c.grade AS "Grade",
o.ord_no
FROM orders o, salesman s, customer c
WHERE o.customer_id = c.customer_id
AND o.salesman_id = s.salesman_id
AND s.city IS NOT NULL
AND c.grade IS NOT NULL
~~~~
**6.** From the following table, write a SQL query to find those customers who are served by a salesperson and the salesperson earns commission in the range of 12% to 14% (Begin and end values are included.). Return cust_name AS "Customer", city AS "City".
~~~~sql
SELECT c.cust_name AS "Customer",
c.city AS "City",
s.name AS "Salesman",
s.commission
FROM salesman s, customer c
WHERE s.commission BETWEEN 0.12 AND 0.14
AND s.salesman_id = c.salesman_id 

~~~~
**7.** From the following tables, write a SQL query to find all orders executed by the salesperson and ordered by the customer whose grade is greater than or equal to 200. Compute purch_amt*commission as “Commission”. Return customer name, commission as “Commission%” and Commission.
~~~~sql
SELECT o.ord_no, c.cust_name, s.commission,
o.purch_amt * s.commission as "Commission"
FROM orders o, salesman s, customer c
WHERE c.grade>=200
AND o.customer_id = c.customer_id
AND o.salesman_id = s.salesman_id

~~~~
**8.** From the following table, write a SQL query to find those customers who placed orders on October 5, 2012. Return customer_id, cust_name, city, grade, salesman_id, ord_no, purch_amt, ord_date, customer_id and salesman_id.
~~~~sql
SELECT  *  
FROM customer c,orders o
WHERE c.customer_id=o.customer_id 
AND o.ord_date='2012-10-05'
~~~~



