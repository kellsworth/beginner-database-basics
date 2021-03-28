<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250" align="right">

# Project Summary

In this project we will be practicing inserting and querying data using SQL. We'll make use of a handy online tool provided by DevMountain that will allow us to write SQL in your browser. [Click Me](https://postgres.devmountain.com/)

On the left are the Tables with their fields, the right is where we will be writing our queries, and the bottom is where we will see our results.  

Any new tables or records that we add into the database will be removed after you refresh the page.

## Table - person

### Instructions
1. Create a table called person that records a person's id, name, age, height ( in cm ), city, favorite_color. 
    * id should be an auto-incrementing id/primary key - Use type: SERIAL
2. Add 5 different people into the person database. 
    * Remember to not include the person_id because it should auto-increment.
3. List all the people in the person table by height from tallest to shortest.
4. List all the people in the person table by height from shortest to tallest.
5. List all the people in the person table by age from oldest to youngest.
6. List all the people in the person table older than age 20.
7. List all the people in the person table that are exactly 18.
8. List all the people in the person table that are less than 20 and older than 30.
9. List all the people in the person table that are not 27 (Use not equals).
10. List all the people in the person table where their favorite color is not red.
11. List all the people in the person table where their favorite color is not red and is not blue.
12. List all the people in the person table where their favorite color is orange or green.
13. List all the people in the person table where their favorite color is orange, green or blue (use IN).
14. List all the people in the person table where their favorite color is yellow or purple (use IN).

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
CREATE TABLE person ( person_id SERIAL PRIMARY KEY, name VARCHAR(200), age INTEGER, height INTEGER, city VARCHAR(200), favorite_color VARCHAR(200) );
```
</details>


CREATE TABLE person (
  person_id SERIAL PRIMARY KEY,
  name VARCHAR(200),
  age INTEGER,
  height INTEGER,
  city VARCHAR(200),
  favorite_color VARCHAR(200)
);
  

<details>

<summary> <code> #2 </code> </summary>

```sql
INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'First Last', 21, 182, 'City', 'Color' );
```

</details>


  INSERT INTO person (name, age, height, city, favorite_color)
  VALUES ('Lexi Dutson', 21, 48, 'Salt Lake City', 'pink'),
    ('Ryan Dutson', 23, 50, 'Draper', 'blue'),
    ('Jax Peterson', 15, 55, 'Park City', 'green'),
    ('Cal Peterson', 13, 49, 'Filmore', 'blue'),
    ('Reagan Dutson', 25, 55, 'Sandy', 'aqua')
    ;


<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM person ORDER BY height DESC;
```

</details>
SELECT * FROM person ORDER BY height DESC;

Query Results
Row count: 5

person_id	name	age	height	city	favorite_color
3	Jax Peterson	15	55	    Park City	green
5	Reagan Dutson	25	55	    Sandy	aqua
2	Ryan Dutson	    23	50	    Draper	blue
4	Cal Peterson	13	49	    Filmore	blue
1	Lexi Dutson	    21	48	    Salt Lake City	pink


<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM person ORDER BY height ASC;
```

</details>

SELECT * FROM person ORDER BY height ASC;


person_id	name	age	height	city	favorite_color
1	Lexi Dutson	    21	48	    Salt Lake City	pink
4	Cal Peterson	13	49	    Filmore	blue
2	Ryan Dutson	    23	50	    Draper	blue
3	Jax Peterson	15	55	    Park City	green
5	Reagan Dutson	25	55	    Sandy	aqua



<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT * FROM person ORDER BY age DESC;
```

</details>
SELECT * FROM person ORDER BY age DESC;

Query Results
Row count: 5

person_id	name	age	height	city	favorite_color
5	Reagan Dutson	25	55	Sandy	aqua
2	Ryan Dutson	    23	50	Draper	blue
1	Lexi Dutson	    21	48	Salt Lake City	pink
3	Jax Peterson	15	55	Park City	green
4	Cal Peterson	13	49	Filmore	blue




<details>

<summary> <code> #6 </code> </summary>

```sql
SELECT * FROM person WHERE age > 20;
```

</details>
SELECT * FROM person WHERE age > 20;

Query Results
Row count: 3

person_id	name	age	height	city	favorite_color
1	Lexi Dutson	    21	48	    Salt Lake City	pink
2	Ryan Dutson	    23	50	    Draper	blue
5	Reagan Dutson	25	55	    Sandy	aqua


<details>

<summary> <code> #7 </code> </summary>

```sql
SELECT * FROM person WHERE age = 18;
```

</details>
SELECT * FROM person WHERE age = 18;

Query Results
Query ran successfully. 0 rows to display.

<details>

<summary> <code> #8 </code> </summary>

```sql
SELECT * FROM person WHERE age < 20 OR age > 30;
```

</details>
SELECT * FROM person WHERE age < 20 OR age > 30;

Query Results
Row count: 2

person_id	name	age	height	city	favorite_color
3	Jax Peterson	15	55	    Park City	green
4	Cal Peterson	13	49	    Filmore	    blue
<details>

<summary> <code> #9 </code> </summary>

```sql
SELECT * FROM person WHERE age != 27;
```

</details>

<details>

<summary> <code> #10 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color != 'red';
```

</details>
SELECT * FROM person WHERE age != 27;

Query Results
Row count: 5

person_id	name	age	height	city	favorite_color
1	Lexi Dutson	    21	48	    Salt Lake City	pink
2	Ryan Dutson	    23	50	    Draper	        blue
3	Jax Peterson	15	55	    Park City	    green
4	Cal Peterson	13	49	    Filmore	        blue
5	Reagan Dutson	25	55	    Sandy	        aqua
<details>

<summary> <code> #11 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color != 'red' AND favorite_color != 'blue';
```

</details>
SELECT * FROM person WHERE favorite_color != 'red' AND favorite_color != 'blue';

Query Results
Row count: 3

person_id	name	age	height	city	favorite_color
1	Lexi Dutson	    21	48	    Salt Lake City	pink
3	Jax Peterson	15	55	    Park City	    green
5	Reagan Dutson	25	55	    Sandy	        aqua
<details>

<summary> <code> #12 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color = 'orange' OR favorite_color = 'green';
```

</details>
SELECT * FROM person WHERE favorite_color = 'orange' OR favorite_color = 'green';

Query Results
Row count: 1

person_id	name	age	height	city	favorite_color
3	Jax Peterson	15	55	    Park City	green

<details>

<summary> <code> #13 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color IN ( 'orange', 'green', 'blue' );
```

</details>
SELECT * FROM person WHERE favorite_color IN ( 'orange', 'green', 'blue' );

Query Results
Row count: 3

person_id	name	age	height	city	favorite_color
2	Ryan Dutson	    23	50	Draper	    blue
3	Jax Peterson	15	55	Park City	green
4	Cal Peterson	13	49	Filmore	    blue

<details>

<summary> <code> #14 </code> </summary>

```sql
SELECT * FROM person WHERE favorite_color IN ( 'yellow', 'purple' )
```

</details>
SELECT * FROM person WHERE favorite_color IN ( 'yellow', 'purple' )

Query Results
Query ran successfully. 0 rows to display.

</details>

## Table - orders

### Instructions

1. Create a table called orders that records: order_id, person_id, product_name, product_price, quantity.
2. Add 5 orders to the orders table.
    * Make orders for at least two different people.
    * person_id should be different for different people.
3. Select all the records from the orders table.
4. Calculate the total number of products ordered.
5. Calculate the total order price.
6. Calculate the total order price by a single person_id.

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
CREATE TABLE orders ( order_id SERIAL PRIMARY KEY, person_id INTEGER, product_name VARCHAR(200), product_price NUMERIC, quantity INTEGER );
```

</details>

CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  person_id INTEGER,
  product_name VARCHAR(200),
  product_price NUMERIC,
  quantity INTEGER
  );



<details>

<summary> <code> #2 </code> </summary>

```sql
INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 0, 'Product', 12.50, 2 );
```

</details>

INSERT INTO orders ( person_id, product_name, product_price, quantity ) 
  VALUES ( 100, 'Coffee', 5.12, 1 ),
  (101, 'Lattee', 6.25, 3),
  (102, 'Cafe Misto', 3.25, 1),
  (103, 'Caramel Machiatto', 4.5, 5),
  (104, 'Mocha Frappe', 5.75, 2);

Query Results
Query ran successfully. 0 rows to display.
<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM orders;
```

</details>
SELECT * FROM orders;

Query Results
Row count: 5

order_id	person_id	product_name	product_price	quantity
1	        100	        Coffee	            5.12	    1
2	        101	        Lattee	            6.25	    3
3	        102	        Cafe Misto	        3.25	    1
4	        103	        Caramel Machiatto	4.5	        5
5	        104	        Mocha Frappe	    5.75	    2
<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT SUM(quantity) FROM orders;
```

</details>
SELECT SUM(quantity) FROM orders;

Query Results
Row count: 1

sum
12
<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT SUM(product_price * quantity) FROM orders;
```

</details>
SELECT SUM(product_price * quantity) FROM orders;

Query Results
Row count: 1

sum
61.12
<details>

<summary> <code> #6 </code> </summary>

```sql
/* The value of person_id depends on what IDs you used. Use a valid ID from your table */
SELECT SUM(product_price * quantity) FROM orders WHERE person_id = 0;
```

</details>
SELECT SUM(product_price * quantity) FROM orders WHERE person_id = 103;

Query Results
Row count: 1

sum
22.5


</details>

## Table - artist

### Instructions

1. Add 3 new artists to the artist table. ( It's already created )
2. Select 10 artists in reverse alphabetical order.
3. Select 5 artists in alphabetical order.
4. Select all artists that start with the word 'Black'.
5. Select all artists that contain the word 'Black'.

### Solution 

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
INSERT INTO artist ( name ) VALUES ( 'artist name' );
```

</details>
INSERT INTO artist ( name ) VALUES ( 'Eloise Didier' );
INSERT INTO artist ( name ) VALUES ( 'Lexi Dutson' );
INSERT INTO artist ( name ) VALUES ( 'Jax Peterson' );

<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT * FROM artist ORDER BY name DESC LIMIT 10;
```

</details>

Query Results
Row count: 10

artist_id	name
155	    Zeca Pagodinho
212	    Yo-Yo Ma
168	    Youssou N'Dour
255	    Yehudi Menuhin
181	    Xis
211	    Wilhelm Kempff
154	    Whitesnake
75	    Vinicius, Toquinho & Quarteto Em Cy
73	    Vinícius E Qurteto Em Cy
74	    Vinícius E Odette Lara

<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT * FROM artist ORDER BY name ASC LIMIT 5;
```

</details>

SELECT * FROM artist ORDER BY name ASC LIMIT 5;

Query Results
Row count: 5

artist_id	name
230	        Aaron Copland & London Symphony Orchestra
202	        Aaron Goldberg
215	        Academy of St. Martin in the Fields Chamber Ensemble & Sir Neville Marriner
222	        Academy of St. Martin in the Fields, John Birch, Sir Neville Marriner & Sylvia McNair
214	        Academy of St. Martin in the Fields & Sir Neville Marriner

<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM artist WHERE name LIKE 'Black%';
```

</details>
SELECT * FROM artist WHERE name LIKE 'Black%';

Query Results
Row count: 3

artist_id	name
11	        Black Label Society
12	        Black Sabbath
169	        Black Eyed Peas
<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT * FROM artist WHERE name LIKE '%Black%';
```

</details>
SELECT * FROM artist WHERE name LIKE '%Black%';

Query Results
Row count: 5

artist_id	name
11	        Black Label Society
12	        Black Sabbath
38	        Banda Black Rio
137	        The Black Crowes
169	        Black Eyed Peas
</details>

## Table - employee

### Instructions

1. List all employee first and last names only that live in Calgary.
2. Find the birthdate for the youngest employee.
3. Find the birthdate for the oldest employee.
4. Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
   * You will need to query the employee table to find the Id for Nancy Edwards
5. Count how many people live in Lethbridge.

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
SELECT first_name, last_name FROM employee WHERE city = 'Calgary';
```

</details>
SELECT first_name, last_name FROM employee WHERE city = 'Calgary';

Query Results
Row count: 5

first_name	last_name
Nancy	    Edwards
Jane	    Peacock
Margaret	Park
Steve	    Johnson
Michael	    Mitchell
<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT MAX(birth_date) from employee;
```

</details>
SELECT MAX(birth_date) from employee;

Query Results
Row count: 1

max
1973-08-29T00:00:00.000Z
<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT MIN(birth_date) from employee;
```

</details>
SELECT MIN(birth_date) from employee;

Query Results
Row count: 1

min
1947-09-19T00:00:00.000Z
<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM employee WHERE reports_to = 2;
```

</details>
SELECT * FROM employee WHERE reports_to = 2;

Query Results
Row count: 3

employee_id	last_name	first_name	title	reports_to	birth_date	hire_date	address	city	state	country	postal_code	phone	fax	email
3	Peacock	Jane	Sales Support Agent	2	1973-08-29T00:00:00.000Z	2002-04-01T00:00:00.000Z	1111 6 Ave SW	Calgary	AB	Canada	T2P 5M5	+1 (403) 262-3443	+1 (403) 262-6712	jane@chinookcorp.com
4	Park	Margaret	Sales Support Agent	2	1947-09-19T00:00:00.000Z	2003-05-03T00:00:00.000Z	683 10 Street SW	Calgary	AB	Canada	T2P 5G3	+1 (403) 263-4423	+1 (403) 263-4289	margaret@chinookcorp.com
5	Johnson	Steve	Sales Support Agent	2	1965-03-03T00:00:00.000Z	2003-10-17T00:00:00.000Z	7727B 41 Ave	Calgary	AB	Canada	T3B 1Y7	1 (780) 836-9987	1 (780) 836-9543	steve@chinookcorp.com
<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT COUNT(*) FROM employee WHERE city = 'Lethbridge';
```

</details>
SELECT COUNT(*) FROM employee WHERE city = 'Lethbridge';

Query Results
Row count: 1

count
2
</details>

## Table - invoice 

### Instructions

1. Count how many orders were made from the USA.
2. Find the largest order total amount.
3. Find the smallest order total amount.
4. Find all orders bigger than $5.
5. Count how many orders were smaller than $5.
6. Count how many orders were in CA, TX, or AZ (use IN).
7. Get the average total of the orders.
8. Get the total sum of the orders.

### Solution

<details>

<summary> <code> SQL Solutions </code> </summary>

<details>

<summary> <code> #1 </code> </summary>

```sql
SELECT COUNT(*) FROM invoice WHERE billing_country = 'USA';
```
</details>
Query Results
Row count: 1

count
91
<details>

<summary> <code> #2 </code> </summary>

```sql
SELECT MAX(total) FROM invoice;
```
</details>
Query Results
Row count: 1

max
26
<details>

<summary> <code> #3 </code> </summary>

```sql
SELECT MIN(total) FROM invoice;
```

</details>
Query Results
Row count: 1

min
1
<details>

<summary> <code> #4 </code> </summary>

```sql
SELECT * FROM invoice WHERE total > 5;
```

</details>
Query Results
Row count: 179

invoice_id	customer_id	invoice_date	billing_address	billing_city	billing_state	billing_country	billing_postal_code	total
3	8	2009-01-03T00:00:00.000Z	Grétrystraat 63	Brussels		Belgium	1000	6
4	14	2009-01-06T00:00:00.000Z	8210 111 ST NW	Edmonton	AB	Canada	T6G 2C7	9
5	23	2009-01-11T00:00:00.000Z	69 Salem Street	Boston	MA	USA	2113	14
10	46	2009-02-03T00:00:00.000Z	3 Chatham Street	Dublin	Dublin	Ireland		6
11	52	2009-02-06T00:00:00.000Z	202 Hoxton Street	London		United Kingdom	N1 5LH	9
12	2	2009-02-11T00:00:00.000Z	Theodor-Heuss-Straße 34	Stuttgart		Germany	70174	14
17	25	2009-03-06T00:00:00.000Z	319 N. Frances Street	Madison	WI	USA	53703	6
18	31	2009-03-09T00:00:00.000Z	194A Chain Lake Drive	Halifax	NS	Canada	B3S 1C5	9
19	40	2009-03-14T00:00:00.000Z	8, Rue Hanovre	Paris		France	75002	14
<details>

<summary> <code> #5 </code> </summary>

```sql
SELECT COUNT(*) FROM invoice WHERE total < 5;
```

</details>
Query Results
Row count: 1

count
233
<details>

<summary> <code> #6 </code> </summary>

```sql
SELECT COUNT(*) FROM invoice WHERE billing_state in ('CA', 'TX', 'AZ');
```

</details>
Query Results
Row count: 1

count
35
<details>

<summary> <code> #7 </code> </summary>

```sql
SELECT AVG(total) FROM invoice;
```

</details>
Query Results
Row count: 1

avg
5.7063106796116505
<details>

<summary> <code> #8 </code> </summary>

```sql
SELECT SUM(total) FROM invoice;
```

</details>
Query Results
Row count: 1

sum
2351
</details>


## Resources

<details>

<summary> <code> SQL </code> </summary>

* [SQL Teaching](http://www.sqlteaching.com/)
* [SQL Bolt](http://sqlbolt.com/)

</details>

## Contributions

If you see a problem or a typo, please fork, make the necessary changes, and create a pull request so we can review your changes and merge them into the master repo and branch.

## Copyright

© DevMountain LLC, 2017. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.

<p align="center">
<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250">
</p>

