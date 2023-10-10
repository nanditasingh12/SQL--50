# SQL--50
SQL Problems 50

problem 1:
1757. Recyclable and Low Fat Products
Write a solution to find the ids of products that are both low fat and recyclable.
Return the result table in any order.
The result format is in the following example:

Answer:
SQL QUERY:
SELECT product_id
from Products
where low_fats = "Y" and recyclable = "Y"

Problem 2:
Find the names of the customer that are not referred by the customer with id = 2.
Return the result table in any order.
The result format is in the following example.

Answer:
SQL Query
Select name from Customer
where referee_id != 2 or referee_id is null;

Problem 3:
Write a solution to find the name, population, and area of the big countries.
Return the result table in any order.
The result format is in the following example.


Answer:
SQL Query:
Select name,population,area from World
where area >= 3000000 or population >= 25000000;

Problem 4:
Write a solution to find all the authors that viewed at least one of their own articles.
Return the result table sorted by id in ascending order.
The result format is in the following example.

Answer:
SQL Query:
Select distinct author_id as id        // When the primary key is not defined then we use "Distinct" to get the unique identity
from Views
where author_id = viewer_id
order by id asc

Problem 5:
Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.
Return the result table in any order.
The result format is in the following example

Amswer:
SQL Query:
Select tweet_id 
from Tweets
where
char_length(content) > 15;

////////////////////////////////////
TOPIC ON JOINT OPERATION
Problem 6:
Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null.
Return the result table in any order.
The result format is in the following example.

QUERY:
Solution:
Select u.unique_id as unique_id, n.name as name
from Employees n left join EmployeeUNI u
on 
n.id=u.id   

Problem 7:
Write a solution to report the product_name, year, and price for each sale_id in the Sales table.
Return the resulting table in any order.
The result format is in the following example.

QUERY:
Solution:
Select product_name,year,price
from Sales s join product p on s.product_id = p.product_id

Problem 8:
Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.
Return the result table sorted in any order.
The result format is in the following example.

QUERY 
Solution:
Select customer_id
COUNT(v.visit_id) as count_no_trans
from Visits v
LEFT JOIN Transactions t on v.visit_id = t.visit_id
where transaction_id is  null
group by customer_id



 
