# Question

For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

a. How many orders were shipped by Speedy Express in total?

    54 Orders were shipped by Speedy Express
    The following SQL query was used, returning 54 results:
    SELECT * FROM [Orders] WHERE shipperID = 1

b. What is the last name of the employee with the most orders?
    
    Peacock
    
    The following SQL queries were used to produce the result:
    --------------------------------------------------------------------------------------------------------------
    SELECT       'employeeID',
             COUNT('employeeID') AS 'value_occurrence'
    FROM     'Orders'
    GROUP BY 'employeeID'
    ORDER BY 'value_occurrence' DESC
    LIMIT    1;
    
    RESULT:
    EmployeeID	value_occurrence
    4	        40
    --------------------------------------------------------------------------------------------------------------
    SELECT * FROM [Employees] WHERE EmployeeID = 4
    
    RESULT:
    EmployeeID	LastName	FirstName	BirthDate	Photo	      Notes
    4	        Peacock	        Margaret        1958-09-19      EmpID4.pic    Margaret holds a BA in English literature from Concordia College and an MA from the American Institute of Culinary  Arts. She was temporarily assigned to the London office before returning to her permanent post in Seattle.

    --------------------------------------------------------------------------------------------------------------
    
    

c. What product was ordered the most by customers in Germany?

    Product ordered by most customers in germany: Boston Crab Meat
    
    --------------------------------------------------------------------------------------------------------------
    SELECT ProductID,
    COUNT('ProductID') AS 'value_occurrence'
    FROM [OrderDetails] WHERE OrderID 
    IN(SELECT OrderID FROM [Orders] WHERE CustomerID 
    IN(SELECT CustomerID FROM [Customers] WHERE Country = "Germany"))
    GROUP BY 'ProductID'
    
    RESULT:
    ProductID	value_occurrence
    40	        74
    --------------------------------------------------------------------------------------------------------------
    SELECT * FROM [Products] WHERE ProductID = 40
    
    RESULT:
    ProductID	ProductName	   SupplierID	CategoryID	Unit	        Price
    40              Boston Crab Meat   19	        8	        24 - 4 oz tins	18.4
    --------------------------------------------------------------------------------------------------------------
