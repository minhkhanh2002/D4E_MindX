--Lấy danh sách các sản phẩm chiếm 80% lợi nhuận năm 2014
SELECT Product_Name
    FROM [dbo].[ProfitByProduct2014]
    WHERE Percent_Of_Accued_Profit_2014 <= '80%'

--Lấy danh sách các khách hàng mang lại 80% lợi nhuận năm 2015
SELECT Customer_Name
    FROM [dbo].[ProfitByCustomer2015]
    WHERE Percent_Of_Accued_Profit_2015 <= '80%'   

--Tìm ra các khách hàng quan trọng góp phần lớn lợi nhuận của năm 2014 và 2015
WITH Customers2014 AS (
    SELECT Customer_Name
    FROM [dbo].[ProfitByCustomer2014]
    WHERE Percent_Of_Accued_Profit_2014 <= '80%'
),
Customers2015 AS (
    SELECT Customer_Name
    FROM [dbo].[ProfitByCustomer2015]
    WHERE Percent_Of_Accued_Profit_2015 <= '80%'
)
SELECT Customer_Name
FROM Customers2014
INTERSECT
SELECT Customer_Name
FROM Customers2015



--Tìm ra các sản phẩn chủ chốt đều xuất hiện qua các năm từ 2014-2016
WITH Products2014 AS (
    SELECT Product_Name
    FROM [dbo].[ProfitByProduct2014]
    WHERE Percent_Of_Accued_Profit_2014 <= '80%'
),
Products2015 AS (
    SELECT Product_Name
    FROM [dbo].[ProfitByProduct2015]
    WHERE Percent_Of_Accued_Profit_2015 <= '80%'
),
Products2016 AS (
    SELECT Product_Name
    FROM [dbo].[ProfitByProduct2016]
    WHERE Percent_Of_Accued_Profit_2016 <= '80%'
)
SELECT Product_Name
FROM Products2014
INTERSECT
SELECT Product_Name
FROM Products2015
INTERSECT
SELECT Product_Name
FROM Products2016

