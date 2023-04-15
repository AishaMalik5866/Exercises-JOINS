# Exercises-JOINS


*these are the query exercies I did from made-up databases from a made-up company*

*the database names for the made-up company are sql_invoicing, sql_store, sql_inventory, sql_hr*

------------------------------------------------------------------------------------------------------

USE sql_store;

*doing exercises from store database*

___________________________________________________________

SELECT order_id, o.customer_id, first_name, last_name

FROM orders o

JOIN customers c

ON o.customer_id=c.customer_id;
	
*inner joining 'orders' table with 'customers' table to see customer details and their order id*

------------------------

SELECT order_id, oi.product_id, quantity, oi.unit_price

FROM order_items oi

JOIN products p

ON oi.product_id=p.product_id;

*inner joining 'order_items' table with 'products' table to see order details, like what product was ordered, how much was ordered, and the price of product at the time of sale*

----------------------

SELECT * 

FROM order_items oi

JOIN sql_inventory.products p

ON oi.product_id=p.product_id;

*joins tables across databases to see information about products that are not available in just one database*

-------------------------

SELECT o.order_id, o.order_date, c.first_name, c.last_name, os.name AS status

FROM orders o

JOIN customers c

ON o.customer_id=c.customer_id

JOIN order_statuses os

ON o.status=os.order_status_id;

*joining 'customers' and 'order_statuses' tables with 'orders' table to see order details and if they've been processed*

---------------------------

SELECT p.product_id, p.name, oi.quantity 

FROM products p

LEFT JOIN order_items oi

ON p.product_id=oi.product_id

*doing an outer join between 'products' and 'order_items' tables to see how many of each product has been orderd regardless of whether they've been ordered or not*

----------------------------------

SELECT  o.order_id, o.order_date, c.first_name, sh.name AS shipper, os.name AS status

FROM orders o

JOIN customers c

ON o.customer_id=c.customer_id

LEFT JOIN shippers sh

ON o.shipper_id=sh.shipper_id

JOIN order_statuses os

ON o.status=os.order_status_id

*outer and inner joining multiple tables to see all the orders, their order dates, who ordered, and whether or not the order has been shipped, which includes the shipper's name if it has been shipped*

-----------------------





USE sql_hr;

*doing exercises from HR database*

----------------

SELECT e.employee_id, e.first_name, m.first_name AS manager

FROM employees e

JOIN employees m

ON e.reports_to=m.employee_id;

*self joining 'employees' table in order to see employee information and who their manager is*

--------------------------------
  
  
  

USE sql_invoicing;

*doing exercises from the invoicing database*

-------------------------------

SELECT c.name, pa.name AS payment_method, p.amount, p.date, p.invoice_id

FROM payments p

JOIN payment_methods pa

ON p.payment_method=pa.payment_method_id

JOIN clients c

ON p.client_id=c.client_id;

 *joins 'payment_methods' and 'clients' tables with 'payments' table in order to see the payments made by clients and their payment details*
 
