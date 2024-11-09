## Capstone_Project - Sales Data Analysis

![image](https://github.com/user-attachments/assets/6d001534-3da8-4f61-b3ef-4219e77b24a2)
TOTAL SALES BY PRODUCT	
Product	 Total Sales
Gloves	 296,900.00 
Hat	 316,195.00 
Jacket	 208,230.00 
Shirt	 485,600.00 
Shoes	 613,380.00 
Socks	 180,785.00 
Grand Total	 2,101,090.00 
![image](https://github.com/user-attachments/assets/7378c5f0-a345-4fa5-b524-fb31f61815da)
![image](https://github.com/user-attachments/assets/37801fc4-9444-459e-a7bd-9aba94b904b4)



![image](https://github.com/user-attachments/assets/67963caa-14f4-4ada-b287-40afc3aefb0c)
TOTAL SALES BY REGION	
Product	Sum of Total Sales
East	 485,925.00 
North	 387,000.00 
South	 927,820.00 
West	 300,345.00 
Grand Total	 2,101,090.00 
![image](https://github.com/user-attachments/assets/6dc9e424-fdad-40ad-a923-e30df68e04dc)
![image](https://github.com/user-attachments/assets/dc2a2386-87b8-45c2-977d-c77ee0ef4b27)



![image](https://github.com/user-attachments/assets/b877cf44-6e0b-4222-923c-5bc44a301f55)
TOTAL SALES BY MONTH	
Product	 Total Sales
Jan	 248,000.00 
Feb	 546,300.00 
Mar	 107,175.00 
Apr	 46,865.00 
May	 104,280.00 
Jun	 247,600.00 
Jul	 274,800.00 
Aug	 204,180.00 
Sep	 34,720.00 
Oct	 133,920.00 
Nov	 103,950.00 
Dec	 49,300.00 
Grand Total	 2,101,090.00 
![image](https://github.com/user-attachments/assets/9a296e04-ee33-4197-bea0-2c5dc872bf6a)
![image](https://github.com/user-attachments/assets/5977d204-5efe-4482-9cd0-50347c383b63)


##Project 1 Question 1b

AVERAGE SALES BY PRODUCT	
Product	Average Sales
Gloves	200.0673854
Hat	158.8121547
Jacket	139.9395161
Shirt	326.5635508
Shoes	308.6965274
Socks	121.8227763
![image](https://github.com/user-attachments/assets/de918abc-8968-467c-8c01-40fd670997a5)


TOTAL REVENUE BY REGION	
Region	Total Revenue
East	195.7007652
North	155.9854897
South	374.1209677
West	121.2535325
![image](https://github.com/user-attachments/assets/439568a6-a99a-42e6-a0f7-1a6bb8df6714)


TOTAL SALES PER MONTH EACH YEAR		
Year	Month	 Total Sales 
2024	Jan	 451,019,939.00 
	Feb	 451,019,970.00 
	Mar	 451,019,999.00 
	Apr	 451,020,030.00 
	May	 451,020,060.00 
	Jun	 451,020,091.00 
	Jul	 451,020,121.00 
	Aug	 451,020,152.00 
	Sep	 451,020,183.00 
	Oct	 451,020,213.00 
	Nov	 451,020,244.00 
	Dec	 451,020,274.00 
2023	Jan	 451,019,938.00 
	Feb	 451,019,969.00 
	Mar	 451,019,998.00 
	Apr	 451,020,029.00 
	May	 451,020,059.00 
	Jun	 451,020,090.00 
	Jul	 451,020,120.00 
	Aug	 451,020,151.00 
	Sep	 451,020,182.00 
	Oct	 451,020,212.00 
	Nov	 451,020,243.00 
	Dec	 451,020,273.00 
![image](https://github.com/user-attachments/assets/ed34fcab-71a1-4a0f-a071-7e71d9245aec)


## USING STRUCTURED QUERY LANGUAGE

***Total Sales for Each Product Category***

Select Product, SUM (Total_Sales) AS [Total Sales]
FROM dbo.Sales_Data
GROUP BY Product

Product Total Sales
Shoes	613380
Jacket	208230
Hat	    316195
Socks	180785
Shirt	485600
Gloves	296900

select * from dbo.Sales_Data


***Number of Sales Transaction In Each Region***

SELECT Region, COUNT(*) AS [Sales Transaction]
FROM dbo.Sales_Data
GROUP BY Region

Region  Sales Transaction
North	2481
East	2483
South	2480
West	2477

select * from dbo.Sales_Data


***Highest-Selling Product By Total Sales Value***

Select TOP 1 Product, SUM (Total_Sales) AS [Total Sales]
FROM dbo.Sales_Data
GROUP BY Product
ORDER BY [TOTAL SALES] DESC

Product Total Sales
Shoes	613380

select * from dbo.Sales_Data


***Total Revenue Per Product***

Select Product, SUM(Quantity*UnitPrice) AS [Total Revenue]
FROM dbo.Sales_Data
GROUP BY Product
ORDER BY [TOTAL REVENUE] DESC

Product Total Revenue
Shoes	613380
Shirt	485600
Hat	    316195
Gloves	296900
Jacket	208230
Socks	180785

select * from dbo.Sales_Data


***Calculate Monthly Sales Total For The Current Year***

SELECT MONTH(OrderDate) AS MONTH,
SUM(Quantity*UnitPrice) AS [Total Sales]
FROM dbo.Sales_Data
WHERE YEAR(OrderDate) = YEAR(2024)
GROUP BY MONTH(OrderDate)
ORDER BY MONTH

select * from dbo.Sales_Data


***Top 5 Customers By Total Purchase Amount***

SELECT TOP 5 Customer_Id,
SUM (Total_Sales) AS [Total Purchase Amount]
FROM dbo.Sales_Data
GROUP BY Customer_Id
ORDER BY [TOTAL PURCHASE AMOUNT] DESC

Customer_Id   Total Purchase Amount
Cus1431	      4235
Cus1495	      4235
Cus1005	      4235
Cus1115	      4235
Cus1302	      4235

select * from dbo.Sales_Data


***Percentage of Total Sales Contributed By Each Region***

SELECT Region,
SUM (Total_Sales) AS [Total Sales],
(SUM (Total_Sales) * 100.0)/ (SELECT SUM(Total_Sales) 
FROM dbo.Sales_Data) AS [Sales Percentage]
FROM dbo.Sales_Data
GROUP BY Region
ORDER BY [Sales Percentage] DESC

Region  Total Sales  Sales Percentage
South	927820	     44.158984146324
East	485925	     23.127281553860
North	387000	     18.419011084722
West	300345	     14.294723215093

select * from dbo.Sales_Data

***Identifying Products With No Sales In The Last Quarter***

SELECT Product,
SUM(TOTAL_SALES) AS [Total Sales]
FROM dbo.Sales_Data
WHERE Product NOT IN ('quarter')
  AND OrderDate >= DATEADD(quarter,-3,GETDATE()) -- 3 quarters ago
  AND OrderDate >= DATEADD(quarter,-1,GETDATE()) -- Last quarter
GROUP BY Product
ORDER BY [Total Sales] DESC;


select * from dbo.Sales_Data

# FURTHER ANALYSIS OF THE SALES DATA USING POWERBI

![Sales Data--Capstone](https://github.com/user-attachments/assets/d415bb63-d967-4236-b1cd-fdbf422f954d)






