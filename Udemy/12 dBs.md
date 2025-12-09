##### SQL vs NoSQL
**SQL** servers Oracle, MS SQL etc (paid ones) or PostGress (open source), MySQL, SQL-lite
**NoSQL** characterized with data format flexibility such as one record can have different structure of fields in comparison to the other record. The records / fields can be modified on the fly. NoSQL can be looked through key/value pair, json based structure. Therefore, it's easy to modify vertically (number of records) and horizontally (number of fields). 
**NoSQL dB**: Redis (open source), MongoDB, DynamoDB (Amazon). However, for a larger projects there arise issues with consistency and scalability. The SQL provides relational dB queries, which minimize the time to retrieve in a large scale operation.

##### CRUD Operations
Create, Read, Update, Destroy
Create: CREATE TABLE products (id INT NOT NULL, name char(255), price float, PRIMARY KEY (id))
INSERT: INSERT INTO products VALUES (1, "pen", 1.20) and 
		INSERT INTO products (id, name) VALUES (2, "pencil") `to insert selected columns`
Read: SELECT * FROM products; or
	SELECT (name, price) FROM products where id=1; `or .. where price NOT NULL` etc.
Update: UPDATE products SET price=1.5 WHERE name="pencil"
*If we wanna add, delete or modify a column in a table, then use ALTER  TABLE*
 ALTER TABLE table_name ADD column_name datatype; 
 Delete: DELETE FROM products where condition;
##### Relational dBs
```
CREATE TABLE orders (
  id INT not NULL, 
  order_numbers INT, 
  customer_id INT, 
  product_id INT, 
  PRIMARY KEY (id),
  FOREIGN KEY (customer_id) REFERENCES customers(id), 
  FOREIGN KEY (product_id) REFERENCES products(id)
  ) // here customer_id refers to the 'id' in 'customers' table, similarly product_id.
```
JOIN is used to join tables together. The commonly used instruction is "INNER JOIN" out of all other types of JOIN. The inner JOIN selects records that have matching values in both tables. 
```SELECT order_number, customers.first_name, customers.last_name, customers.address
FROM orders
INNER JOIN customers ON orders.customer_id = customers.id;
```
#==Highlighted notes==