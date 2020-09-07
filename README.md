# Shopify-Data-Science-Challenge-2020
Winter 2021 Data Science Intern Challenge

Question 1: Data_Analysis.ipynb


Question 2:

a) 

  SELECT Count(ShipperID)  
  FROM Orders 
  WHERE ShipperID = 
  (SELECT ShipperID 
  FROM Shippers  
  WHERE ShipperName ='Speedy Express');

  Answer: 54

b) 

  SELECT LastName
  FROM Employees
  WHERE employeeID =
    (SELECT MAX(employeeID.num)
        FROM (SELECT count(*) AS num
              FROM Orders) employeeID);

  Answer: It populated 0 records. 
c) 

  SELECT ProductName FROM Products
  WHERE ProductID =
    (SELECT ProductID FROM OrderDetails
  WHERE OrderID =
      (SELECT OrderID FROM Orders
  WHERE CustomerID =
      (SELECT CustomerID FROM Customers
  WHERE Country ='Germany')));

  Answer: 
