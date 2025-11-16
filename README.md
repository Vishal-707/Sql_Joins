# SQL Joins [INNER LEFT RIGHT OUTER ]
This repository contains the deliverables focusing on demonstrating mastery of various SQL JOIN types [INNER LEFT RIGHT FULL SELF CROSS] using a simulated E-Commerce database.
--- <br>

# 🎯 Objective
To create a relational database structure and populate it with sample data to effectively execute and understand the differences between the four primary SQL join.
 
# 🛠 Tools Used
* Environment : MySQL Workbench
The database structure includes four tables.
1. Customers (Customer_Id, Full_Name, Contact, Email, Address)
2. Products (Product_Id, Product_Name, Category, Price, Stock_quantity)
3. Orders (Order_Id, Customer_Id, Product_Id, Order_Date, Amount, Payment_Type)
4. Payments (Payment_Id, Order_Id, Payment_Status, Payment_Date)
--- 

# JOIN SQL --
JOIN clause is used to combine rows from two or more tables based on a related column between them. This allows for the retrieval of data that is distributed across multiple tables, presenting it as a single, unified result set. Joins are fundamental for working with relational databases, where data is often normalized and spread across various tables to avoid redundancy and maintain data integrity. <br>
There are different types of joins In SQL  <br>

the AS keyword is used to create an alias for a column or a table. An alias is a temporary, alternative name given to a column or table within a specific SQL query. This alias exists only for the duration of that query and is not a permanent change to the database schema.


* 𝐈𝐍𝐍𝐄𝐑 𝐉𝐎𝐈𝐍 <br>
  This is the most common type of join. It returns only the rows that have matching values in both tables. Or based on the specified join condition filter.

  - Syntax 
  ```sql
  SELECT columns FROM table1
  INNER JOIN
  table2 ON table1.column_name = table2.column_name;
  ```
  -- Ex. Retrieve the full name of all customers by orders. 
  ```sql
  SELECT c.Customer_Id, o.Order_Id, c.Full_Name FROM Customers c
  INNER JOIN
  Orders o ON c.Customer_Id = o.Customer_Id ;
  ```

* 𝐌𝐮𝐥𝐭𝐢𝐩𝐥𝐞 𝐈𝐍𝐍𝐄𝐑 𝐉𝐎𝐈𝐍𝐒 <br>
  Multiple INNER JOINs are used when you need to combine three or more tables where you only want the records that have a match across all tables.

  - Syntax
  ```sql
  SELECT A.Column1, B.Column2, C.Column3 FROM TableA A INNER JOIN TableB B ON A.Foreign_Key_B = B.Primary_Key_B  
   INNER JOIN TableC C ON B.Foreign_Key_C = C.Primary_Key_C ; 
  ```
  -- Ex. Find the full name of customers, the product name they ordered, and the payment status for those orders.
  ```sql
  SELECT C.Full_Name, P.Product_Name, Py.Payment_Status FROM Customers C INNER JOIN Orders O ON C.Customer_Id = O.Customer_Id
  INNER JOIN
  Products P ON O.Product_Id = P.Product_Id INNER JOIN Payments Py ON O.Order_Id = Py.Order_Id ;
  ```
* 𝐋𝐄𝐅𝐓 𝐉𝐎𝐈𝐍 <br>
  The LEFT JOIN returns all rows from the left table and the matching rows from the right table. If no match is found in the right table, it fills the missing columns with NULL.

  - Syntax
  ```sql
  SELECT columns FROM table1
  LEFT JOIN
  table2 ON table1.column_name = table2.column_name;
  ```
  -- Ex. Find productid productName price by orders
  ```sql
  SELECT p.Product_Id, p.Product_Name, p.price FROM Products p
   LEFT JOIN
  Orders o ON P.Product_Id = o.Product_Id ;
  ```

* 𝐑𝐈𝐆𝐇𝐓 𝐉𝐎𝐈𝐍 <br>
  The RIGHT JOIN is the opposite of the LEFT JOIN. It returns all rows from the right table and the matching rows from the left table. If no match is found in the left table, it fills the missing columns with NULL.

  - Syntax
  ```sql
  SELECT columns FROM table1
  RIGHT JOIN
  table2 ON table1.common_column = table2.common_column ; 
  ```
  -- Ex. Display the Order ID, the Amount, and the Full Name of the customer associated with it.
  ```sql
  SELECT o.Order_Id, o.Amount, c.Full_Name FROM Customers c
  RIGHT JOIN
  Orders o ON c.Customer_Id =   o.Customer_Id ;
  ```

* 𝐅𝐔𝐋𝐋 𝐉𝐎𝐈𝐍 <br>
  This join returns all rows when there is a match in either the left or the right table. If there's no match for a row in one table, NULL values are returned for the columns of the non-matching table.

  - Syntax 
  ```sql
  SELECT columns FROM table1
  FULL JOIN
  table2 ON table1.column_name = table2.column_name;
  ```
* 𝐔𝐍𝐈𝐎𝐍 <br>
  The UNION operator in MySQL is used to combine the results of two or more SELECT queries into a single result set.
  By default, it eliminates duplicate rows. It is useful when you want to merge rows from different queries into one output.

  - Syntax for remove duplicate value.
  ```sql
  SELECT column1, column2, ...  FROM table1 
  UNION 
  SELECT column1, column2, ...  FROM table2; 
  ```
  - Syntax for duplicate value
  ```sql
  SELECT column1, column2, ...  FROM table1 
  UNION ALL
  SELECT column1, column2, ...  FROM table2; 
  ```
  -- Ex. Retrieve the customers and the Orders
  ```sql
  SELECT c.Customer_Id , o.order_Date FROM Customers c LEFT JOIN Orders o ON c.Customer_id = o.Customer_Id  
  UNION
  SELECT c.Customer_Id , o.Amount  FROM Customers c RIGHT JOIN Orders o ON c.Customer_Id = o.Customer_Id ;
  ```
* 𝐂𝐑𝐎𝐒𝐒 𝐉𝐎𝐈𝐍 <br>
  This join returns the Cartesian product of the two tables, meaning it combines every row from the first table with every row from the second table.
  This type of join does not require a join condition.
  ```sql
  SELECT columns FROM table1 CROSS JOIN table2;
  ```
* 𝐒𝐄𝐋𝐅 𝐉𝐎𝐈𝐍 <br>
  A SELF JOIN is a regular join where a table is joined with itself. It is used when rows in the same table are related to each other
  (e.g., an employee table where each employee has a manager who is also in the same table).

  - Syntax
  ```sql
  SELECT a.column1, b.column2 FROM table_name a 
  JOIN
  table_name b ON a.common_column = b.related_column; 
  ```
---





  

  
  












