----------CLASS 06
USE Northwind
GO
SELECT * FROM Customers
SELECT * FROM Orders
GO
SELECT *
FROM Customers
WHERE CustomerID NOT IN(
SELECT CustomerID
FROM Orders
)

SELECT *
FROM Products
WHERE UnitPrice=(SELECT SUM(UnitPrice)
FROM Products
)
GO

SELECT C.CustomerId,
(
SELECT SUM(OD.UnitPrice * OD.Quantity)
FROM Orders O
INNER JOIN [Order Details] OD
ON O.OrderID=OD.OrderID
WHERE O.CustomerID=O.CustomerID
) AS 'Total order amount'
FROM Customers C
GO

SELECT O.CustomerID,OD.UnitPrice*Quantity 'Total Price'
FROM Orders O
INNER JOIN [Order Details] OD
ON O.OrderID=OD.OrderID
GO
DROP DATABASE Round61
GO
CREATE DATABASE Round61
GO
USE Round61
GO
CREATE TABLE T1
(
Id INT
)
GO
INSERT INTO T1
VALUES
(1),
(2),
(3),
(4)
GO
SELECT * FROM T1
GO
--SOME
IF 4<=SOME(SELECT * FROM T1)
	PRINT 'TRUE'
ELSE
	PRINT 'FALSE'
GO
--ANY
IF 4<ANY(SELECT * FROM T1)
	PRINT 'TRUE'
ELSE
	PRINT 'FALSE'
GO
--ALL
IF 4<=ALL(SELECT * FROM T1)
	PRINT 'TRUE'
ELSE
	PRINT 'FALSE'
GO
USE Northwind
GO

SELECT * FROM Customers
SELECT * FROM Orders
GO
--NOT EXISTS
SELECT * FROM Customers
WHERE NOT EXISTS
(
SELECT * FROM Orders WHERE Customers.CustomerID=Orders.CustomerID
)

DROP DATABASE Round61
GO
CREATE DATABASE Round61
GO
USE Round61
GO
CREATE TABLE Employee
(
Id INT PRIMARY KEY IDENTITY,
Name VARCHAR(30) NOT NULL,
Gender VARCHAR(30) NOT NULL,
Salary INT NOT NULL,
Department VARCHAR(30) NOT NULL
)
GO
INSERT INTO Employee
VALUES
('Rina','FeMale',1000,'HR'),
('Bina','FeMale',1000,'IT'),
('Tina','FeMale',1000,'Salse'),
('Mina','FeMale',1000,'HR'),
('Katrina','FeMale',1000,'HR'),
('Rana','Male',1000,'HR'),
('Rakib','Male',1000,'IT'),
('Runa','FeMale',1000,'HR'),
('Rani','FeMale',1000,'Salse'),
('jina','Male',1000,'HR'),
('Mina','Male',1000,'Accounts')
GO
SELECT * FROM Employee
GO
--WITH
WITH EmployeeCTE
AS
(
SELECT *
FROM Employee
WHERE Department='IT'
)
SELECT * 
FROM EmployeeCTE
GO
--WITH MULTIPLE
WITH
EemployeeCTE_IT AS (SELECT * FROM Employee WHERE Department='IT'),
EemployeeCTE_HR AS (SELECT * FROM Employee WHERE Department='HR')
SELECT * FROM EemployeeCTE_IT
UNION ALL
SELECT * FROM EemployeeCTE_HR
GO

--RECURSIVE CTE
WITH
OddNumberCTE (Id, Number)
AS
(SELECT 1,1
UNION ALL SELECT Id+1, Number + 2 FROM OddNumberCTE
WHERE Id<11
)
SELECT * FROM OddNumberCTE

--RANKING
WITH ExecuteCTE 
AS
(
SELECT Salary,DENSE_RANK() OVER(ORDER  BY Salary) AS MaxSalary 
FROM Employee
)
SELECT * FROM ExecuteCTE
WHERE ExecuteCTE.MaxSalary=1
GO
