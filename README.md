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


Problem 9:
Write a solution to find all dates' Id with higher temperatures compared to its previous dates (yesterday).
Return the result table in any order.
The result format is in the following example.

QUERY
Solution:
Select w1.id
from Weather 1,Weather 2
where DATEDIFF(w1.recordDate,w2.recordDate) = 1
AND w1.temperature > w2.temperature


Problem 10:
There is a factory website that has several machines each running the same number of processes. Write a solution to find the average time each machine takes to complete a process.
The time to complete a process is the 'end' timestamp minus the 'start' timestamp. The average time is calculated by the total time to complete every process on the machine divided by the number of processes that were run.The resulting table should have the machine_id along with the average time as processing_time, which should be rounded to 3 decimal places.
Return the result table in any order.

QUERY
Solution
Select a1.machine_id,round(avg(a2.timestamp-a1.timestamp),3) as processing_time
from Activity 1
Join Activity 2
on a1.machine_id = a2.machine_id and
a1.process_id = a2.process_id
and a1.activity_type = 'start'
and a2.activity_type = 'end'
group by a1.machine_id


Problem 11:
Write a solution to report the name and bonus amount of each employee with a bonus less than 1000.
Return the result table in any order.
The result format is in the following example.

QUERY
Solution:
Select Employee.name,Bonus.bonus from Employee
left join Bonus on Employee.empID = Bonus.empID
where bonus <  1000 
or bonus is null;

Problem 12:
Write a solution to find managers with at least five direct reports.
Return the result table in any order.

QUERY 
Solution:
Select name 
From Employee
where managerId In
(Select managerId
From Employee
Group By managerId
Having Count (id) >= 5)

Problem: 13
The confirmation rate of a user is the number of 'confirmed' messages divided by the total number of requested confirmation messages. The confirmation rate of a user that did not request any confirmation messages is 0. Round the confirmation rate to two decimal places.
Write a solution to find the confirmation rate of each user.
Return the result table in any order.
The result format is in the following example.

Solution:
QUERY
select s.user_id, round(avg(if(c.action = "confirmed",1,0)),2) as confirmation_rate
from Signups as s left join Confirmations as c on s.user_id = c.user_id group by user_id


Problem: 14
Write a solution to report the movies with an odd-numbered ID and a description that is not "boring".
Return the result table ordered by rating in descending order.

Solution:
QUERY
Select * from cinema
where id%2 != 0 and description != 0
order by rating desc
 

 
