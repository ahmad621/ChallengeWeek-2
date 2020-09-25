# ChallengeWeek-2
Querries inMysql
What was the challenge?

 Create a Database, that contains 4 tables; using SQL.

write queries for most popular product(s), category and subcategory on a given day, week or month.
We are to create an ERD(Entity Relationship Diagram) to show the relationships between the tables.



1. The Most Popular Product Sold on a Specific Date

select productname from product where ProductID in(select ProductID from sales where DateOfsale='2020-5-17' group by productid having count(*)=(select max(amt_of_sales) from (select Count(*) amt_of_sales  FROM sales where DateOfsale='2020-5-14' group by productid) as table1));


2. The Most Popular Product Sold Last Week

select ProductName from Product where Productid in(select ProductID from sales where week(DateOfsale)=week("2020-09-17"))-1 group by productid having count(*)=(select max(amt_of_sales) from (select Count(*) amt_of_sales  FROM sales where week(DateOfsale)=week("2020-09-17"))-1 group by ProductID) as table1));



3. The Most Popular Product Sold on a Specific Month

select ProductName from Product where ProductID in(select ProductID from sales where month(DateOfsale)=1 group by ProductID having count(*)=(select max(amt_of_sales) from (select Count(*) amt_of_sales  FROM sales where month(DateOfsale)=1 group by ProductID) as table1));
