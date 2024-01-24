# java-DB-sub-queries

1. Return all customers listed in the orders table who placed orders on the most recently recorded day. 
```sql
SELECT 
  c.customer_id,
  c.company_name,
  o.order_date
FROM 
  customers c
JOIN 
  orders o ON c.customer_id = o.customer_id
GROUP BY
  c.customer_id,
  c.company_name,
  o.order_date
HAVING
  o.order_date = (SELECT max(o.order_date) FROM orders o);
```
2. Select all product names and prices that have unit price which is bigger than price of product with name 'Carnarvon Tigers'
```sql
SELECT 
  product_name,
  unit_price
FROM
  products
WHERE
  unit_price > (SELECT unit_price FROM products WHERE product_name = 'Carnarvon Tigers');
```
