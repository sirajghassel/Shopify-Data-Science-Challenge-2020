# Shopify-Data-Science-Challenge-2021
Winter 2021 Data Science Intern Challenge

Question 1: Data_Analysis.ipynb

a) Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
      
There are outliers in the dataset which gave an AOV of 3145. This is illustrated by a standard deviation of 41282.53. Some of the major outliers were around 700000. We know this to be true because the IQR was 227. Futhermore, a skew value of 16.67 indicates a major skew to the right. This further proves that our outliers are to the right of our distribution graph. 
   
b) What metric would you report for this dataset?

To treat such outliers, a floor and cap technique of quantiles was used. The floor was set to 10th percentile and the cap at the 90th percentile. At the 10th percentile, a value of 133.0 was produced and 531 for the 90th percentile. After flooring and capping, the new skew is 0.408. This value lies between -1 and +1 indicating a normal distribution of the data. 


c) What is its value?

The value is 296.31. This is a more realistic value for the cost of sneakers. 



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

  SELECT ProductName
  From Products as P
      INNER JOIN 
      OrderDetails as OD
      ON P.ProductID = OD.ProductID
          INNER JOIN
          Orders as O
          ON OD.OrderID = O.OrderID
              INNER JOIN
              Customers as C
              ON O.OrderID = C.CustomerID
                       INNER JOIN  C.CustomerID = C.Country 
  WHERE C.Country= 'Germany';


  Answer: Syntax Error(missing operator). I've tried the query a couple of different ways, but I kept getting the same error. 
