Retail Sales Analysis SQL Project
This Project is desgined to increse to sql skill & techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries.
Objectives
Set up a retail sales database: Create and populate a retail sales database with the provided sales data.
Data Cleaning: Identify and remove any records with missing or null values.
Exploratory Data Analysis (EDA): Perform basic exploratory data analysis to understand the dataset.
Business Analysis: Use SQL to answer specific business questions and derive insights from the sales data.
Project Structure
1. Data setup
2. Database cration :-  The Project start with Create a database named called  retils_store
3. Table creation :- A table named retail_sales is created to store the sales data.
4. create table retail_sales
(
transactions_id	int primary key,
sale_date date,
sale_time time,
customer_id int,
gender varchar(15),
age	int,
category varchar(15),
quantiy int,
price_per_unit float,
cogs float,
total_sale float
);
2. Data Exploration & Cleaning
Record Count: Determine the total number of records in the dataset.
Customer Count: Find out how many unique customers are in the dataset.
Category Count: Identify all unique product categories in the dataset.
Null Value Check: Check for any null values in the dataset and delete records with missing data.
select * from retail_sales
where transactions_id is null
or 
sale_date is null
or
sale_time is null
or
customer_id is null
or
gender  is null
or
age	is null
or
category is null
or
  total_sale is null;
  

delete from retail_sales
where transactions_id is null
or 
sale_date is null
or
sale_time is null
or
customer_id is null
or
gender  is null
or
age	is null
or
category is null
or
  total_sale is null;

-------- data exploration 

---- how many sales we have ?

select count(*) as total_sale  from retail_sales

----- how many unique customer we have 
select count(Distinct customer_id) as total_customer from retail_sales


3. data analysis and business problems & answers
------ Q-01 Write a SQL query to retrieve all columns for sales made on '2022-11-05:

select * from retail_sales
where sale_date ='2022-11-05';

----- Q-02 Write a SQL query to retrieve all transactions where the category is
--'Clothing' and the quantity sold is more than 4 in the month of Nov-2022:

SELECT *
FROM retail_sales
WHERE 
category = 'Clothing'
  AND TO_CHAR(sale_date, 'YYYY/MM') = '2022/11'
  AND quantiy >=4;

-------- Q-03 Write a SQL query to calculate the total sales (total_sale) for each category.:

SELECT Category,sum (total_sale) as net_sale
FROM retail_sales
Group by category;

----- Q-04 Write a SQL query to find the average age of customers who purchased items from the
--'Beauty' category.:

SELECT  Round (avg(age),2) as Avg_age
FROM retail_sales
where category = 'Beauty'

----- Q-05 Write a SQL query to find all transactions where the total_sale is greater than 1000.:
SELECT * FROM retail_sales 
Where total_sale > 1000

------ Q-06 Write a SQL query to find the total number of transactions
----(transaction_id) made by each gender in each category.

SELECT category,
		gender,count(*)as total_sale
		FROM retail_sales
		Group by category,
		gender
		order by 1


------ Q-07 Write a SQL query to find the top 5 customers based on the highest total sales **:

		select customer_id, sum(total_sale)as total_sale 
		from retail_sales
		Group by customer_id
		order by total_sale desc
		limit 5 
------- Q-08 Write a SQL query to find the number of unique customers
--who purchased items from each category.:

	SELECT category,
	count( distinct customer_id)as unique_customer 
	FROM retail_sales
	group by category

			
----- end of project 

