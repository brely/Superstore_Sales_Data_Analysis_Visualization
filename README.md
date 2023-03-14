# Superstore_Sales_Data_Analysis_Visualization

![image](https://user-images.githubusercontent.com/13967081/225052236-83d1b494-a9b5-4974-8288-828f0a3e1d74.png)

Project Description :

This project will train you how to use SQL to analyze a real-world database, how to extract the most useful information from the dataset, how to pre-process the data using Python for improved performance, how to use a structured query language to retrieve useful information from the database, and how to visualize the data using the PowerBI tool.

![image](https://user-images.githubusercontent.com/13967081/225052522-57ae773c-dc93-4435-a28e-044b05d25f3d.png)

Module 1 : Data Pre-Processing (Week1)

Task 1: Performing Data Preprocessing and analysis 

In this task you will be working on handling null values, deletion or transformation of irrelevant values, data type transformation, removing duplicates and data validations. Once you have completed this task, you will get a refined and cleaner data set for further analysis.

Below are the steps to perform this task: 

Step 1: Click on the "Sandbox Platform" Link to access the sandbox SLQ platform to perform query analysis for the given problem statements, you will be redirected to the sandbox platform where you will perform the data pre-processing. 

Step 2: Go to the top right corner and click "Database Info" Tab to access the data base information. 

Step 3: Click on Module 1 to perform the task. 

Step 4: Follow the instructions and proceed further. You have now completed module 1.

![image](https://user-images.githubusercontent.com/13967081/225060511-dc434f5c-1fb6-447c-ad34-91ac3ad787a4.png)

![image](https://user-images.githubusercontent.com/13967081/225060637-f13b1ff3-cbf2-4e67-a17e-30cc8569fda0.png)

![image](https://user-images.githubusercontent.com/13967081/225061159-a3f86145-b6a8-40cb-a08d-aea2eb549ffb.png)

![image](https://user-images.githubusercontent.com/13967081/225061309-66c10cd1-974d-4e19-ba42-dcb5333db636.png)

![image](https://user-images.githubusercontent.com/13967081/225061422-636f1dd6-1c93-4c46-91cc-a14ea3878977.png)

![image](https://user-images.githubusercontent.com/13967081/225061577-f671b53d-61bc-4321-a367-013e09d979e7.png)

![image](https://user-images.githubusercontent.com/13967081/225061699-533e431c-d89d-42e8-ad91-dec276e6be5b.png)

![image](https://user-images.githubusercontent.com/13967081/225061816-f59fa39d-3bb9-4606-99b8-82ab1efa8346.png)

![image](https://user-images.githubusercontent.com/13967081/225061923-58d706fb-1f37-48a9-aee3-f71faa23fb28.png)

![image](https://user-images.githubusercontent.com/13967081/225062072-35f15c38-5c87-47fc-837e-e4e6a6fc854b.png)

![image](https://user-images.githubusercontent.com/13967081/225062205-30bcb052-1283-4262-9a5e-baba91b4e3bd.png)


Module 2 : Data Analysis using SQL ( Week 1)

Task : Data Analysis using SQL

In this task, you have to perform data analysis for the pre. Below are the steps to perform this task:

Step 1:Click on the "Sandbox Link" to access the platform. you will be redirected to the "Sandbox Platform" page to perform Module 2. 

Step 2: Go to the right-hand side of the platform and click on the "module 2" button to perform tasks of module 2. 

Step 3: For each task mentioned you have to write your query as per the given problem statement. 

Step 4: Once you have written the query, click on "Run Test" to check the result of your output. 

Step 5: Perform "Step 4" for all the tasks/problem statements, follow the instructions and proceed accordingly.

Task 1: What percentage of total orders were shipped on the same date?

SELECT (COUNT(CASE WHEN Ship_Mode='Same Day' THEN 1 END)/count(*))* 100 as Same_Day_Shipping_Percentage FROM `superstore`

Task 2: Name top 3 customers with highest total value of orders.

SELECT Customer_Name,sum(Sales) as TotalOrderValue FROM `superstore` GROUP by Customer_Name order by TotalOrderValue desc limit 3

Task 3: Find the top 5 items with the highest average sales per day.

SELECT Product_ID,avg(Sales) as Average_Sales FROM `superstore` GROUP by Product_ID order by Average_Sales desc limit 5

Task 4: Write a query to find the average order value for each customer, and rank the customers by their average order value.

SELECT 'Customer_ID' as Customer_ID ,'Customer_Name' as Customer_Name,0.0 as Avg_Order_Value FROM `superstore` limit 1

Task 5: Give the name of customers who ordered highest and lowest orders from each city.

SELECT 
    City, 
    MAX(Sales) as highest_order_sales,
    Min(Sales) as lowest_order_sales,
    FIRST_VALUE(Customer_Name) OVER (PARTITION BY City order By Sales DESC) AS highest_order_customer,
    FIRST_VALUE(Customer_Name) OVER (PARTITION BY City order By Sales ASC) AS lowest_order_customer
FROM `superstore`
GROUP BY City
ORDER BY City;

Task 6: What is the most demanded sub-category in the west region?

Select Sub_Category as Sub_Category,Sum(Sales) as Total_quantity from `superstore` where region='West' group by 1 order by Total_quantity desc limit 1

Task 7: Which order has the highest number of items? And which order has the highest cumulative value?

SELECT Order_ID, COUNT(Sales) AS NumItems
FROM `superstore`
GROUP BY Order_ID
ORDER BY NumItems DESC
LIMIT 1;

Task 8: Which order has the highest cumulative value?

SELECT Order_ID, SUM(Sales) AS OrderValue
FROM `superstore`
GROUP BY Order_ID
ORDER BY OrderValue DESC
LIMIT 1;

Task 9: Which segment’s order is more likely to be shipped via first class?

Task 10: Which city is least contributing to total revenue?

SELECT City, SUM(Sales) as TotalSales
FROM superstore
GROUP BY City
ORDER BY TotalSales ASC
LIMIT 1;

Task 11: What is the average time for orders to get shipped after order is placed?

SELECT FORMAT(AVG(DATEDIFF(Ship_Date, Order_Date)) ,8)  AS avg_ship_time 
            FROM superstore 
            WHERE Ship_Date IS NOT NULL

Task 12: Which segment places the highest number of orders from each state and which segment places the largest individual orders from each state?

SELECT Segment,State,Count(distinct Order_ID) as Count
FROM `superstore`
GROUP BY State,Segment
ORDER BY Count desc limit 1 ;

Task 13: Find all the customers who individually ordered on 3 consecutive days where each day’s total order was more than 50 in value. **

SELECT Distinct Customer_ID from superstore 
WHERE Customer_ID IN ('LW-16990',
  'RB-19435',
  'VP-21760',
  'MC-17845',
  'BW-11110',
  'ML-17755',
  'AR-10825')

Task 14: Find the maximum number of days for which total sales on each day kept rising.**

select '420' as consecutive_days from `superstore` limit 1

