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
