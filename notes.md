            ***********************************************/
            /*                                             */
            /* # Think before you do                       */
            /* - What is the problem your tryung to solve? */
            /*                                             */
            /***********************************************/

# Databases 
- Container (files or set of files) to store organized data
- A set of related info

# Tables
- A structured list of data or a specific type

# Column
- A single field in a table

# Row
- A record in a table

# Data Modeling
- Used to organize info for multiple tables and how they relate to each other together
- Used to represent a business process, or show relationships between business processes

# Types of data models
- Prediction built by data Science 
- Data Model as data tables represented and organized in a Database
- Relational: Conceptual simplicity (structural independence), provides adhoc queries (SQL), set oriented access
- NoSQL: Less semantics in data model, Based on schema less  key value data model, best suited for large sparse data stores. Not only SQL.
- Relational vs Transactional models
    1. Relational: Allows for easy querying and data manipulation in a easy, logical, shows relational databases
    2. Transactional: Operational database like in insuracce and healthcare. 
- Define Entities
    1. Person, place thing or event
    2. Distinguishable, unique and distinct 
- Define attributes
    1. Characteristic of an entity
- Define Relationships
    1. Describes association among entities
- One-One
    1. EX: Manager to store 
- One-Many
    1. EX: Customer to invoices
- Many-Many
    1. EX: Student to classes 
- Primary Keys in DB. 

- ER diagrams documentation and illustrations. 
    1. Composed of entity types and specifices relationships that can exist between instances of thoes entity types. 
    2. Shows relationships
    3. Business process
    4. Represented visually
    5. Show links (primary keys)
    6. Primary Keys
        - A column(s) whose values uniquely identify every row in a table
    7. Foreign Key
        - One or more columns that can be used together to identify a single row in another table
    8. Notation:
        - Chen Notation: One to many (1:M), Many to many (M:N), and one to one (1:1)
        - Crows foot notation: || is one and crows foot is many
        - UML Class Diagram notation: 1.1 is one and 1.* is many


# SQL Queries
- SELECT statements and FROM statements
    1. SELECT either all or particular columns from a table in a query. Needs to specify two pieces of info to use SELECT statemet: what you want, and where you want to select it from
    EX input: 
    ```
    SELECT prod_name
    FROM Products;
    ```
    EX output:
    ```
    prod_name
    Shampoo
    Toothpaste
    Deodorant
    Toothbrush
    ```
    EX Retrieving multiple columns:
    ```
    SELECT prod_name, prod_id, prod_price
    FROM Products;

    SELECT  prod_name
            ,prod_id
            ,prod_price
    FROM Products;
    ```
    EX Retrieving multiple columns using * wildcard
    ```
    SELECT * 
    FROM Products;
    ```
    2. LIMIT to see a sample of the data: 
    EX SQLite limit example
    ```
    SELECT columns you wish to see
    FROM specific table 
    LIMIT number of records
    ```
    EX SQLite 
    ```
    SELECT columns you wish to see
    FROM specific table 
    LIMIT 5; 
    ```
    EX Oracle
    ```
    SELECT columns you wish to see
    FROM specific table 
    LIMIT <=5; 
    ```
    DB2
    ```
    SELECT columns you wish to see
    FROM specific table 
    FETCH FIRST 5 ROWS ONLY; 
    ```
- Creating Tables 
    1. New Tables in an existing database
    ```
    CREATE TABLE Shoes
    (
    Id      char (10)   PRIMARY KEY,
    Brand   char(10)    NOT NULL,
    Type    char(250)   NOT NULL,
    Color   char(250)   NOT NULL,
    Price   decimal(8,2)    NOT NULL,
    Desc    Varchar(750)    NULL
    );
    ```
    2. Write data to a new table 
    3. Defining whether columns can accept NULL values or not
        - Datatypes you can assign a column when creating a new table: Real, Integer, Null, Text
    4. Tables: Use tables to make models and predictions, create dashboards, visualize data with other tools, extract data from other sources
    5. NULL represents absence of a value in a column. Not the same as an empty string or value. It means that a particular column in a database does not have any data entered for that specific row.
    6. Addding data to the table 
    ```
    INSERT INTO Shoes
            (Id, 
            ,Brand
            ,Type
            ,Color
            ,Price
            ,Desc
            )
    VALUES  
            ('14535974'
            ,'Gucci' 
            ,'Slippers'
            ,'Pink'
            ,'695.00'
            ,NULL
            )
    ``` 
- Temporary Tables
    ```
    CREATE TEMPORARY TABLE Sandals AS 
    (
        SELECT * 
        FROM shoes
        WHERE shoes_type = 'sandals'
    )

    ```
    1. Use temp tables to simplify by creating a subset and joining to that subset and derive a new calculation 
    2. Faster than creating a real table
    
# Comments in SQL
1. Single line:
```
SELECT shoe_id
--, brand_id
,shoe_name
from shoes
from shoes
from shoes
```
2. Selection
```
SELECT shoe_id
/*,brand_id
,shoe_name
*/
from shoes
```
# Filtering
- Narrows data allowed to retrieve
- REduce number of records you retrieve
- increase query performacne 
- Reduce strain on client app
- Goverence limits

## WHERE 
- Example 1
```
SELECT column_name, column_name
FROM table_name
WHERE column_name, operator value;
```
| Operator  | Description |
|-------------- | ---- |
| = | Equal |
|<> | Not Equal or != |
| > | Greater Than |
| < | Less than |
| >= | Greater than or equal |
| <= | Less than or equal |
| BETWEEN | Between inclusinve range |
| IS NULL | is a null value |

- Example 2
```
SELECT ProductName
,UnitPrice
,SupplierID
FROM  Products
WHERE ProductName = 'Tofu';
```
- Example 3: Filtering on a single value
```
SELECT ProductName
,UnitPrice
,SupplierID
FROM  Products
WHERE UnitPrice >= 75; 
```
- Example 4: Checking for non matches 
```
SELECT ProductName
,UnitPrice
,SupplierID
FROM  Products
WHERE ProductName <> 'Alice Mutton';
```
- Example 5: Filtering no Value 
```
SELECT ProductName
,UnitPrice
,SupplierID
FROM  Products
WHERE ProductName IS NULL;
--Null is no data
```
-NULL tIf you wnat to find something that has a price is zero, then write 0 
-IS NULL means you have no infomration

## BETWEEN 
- Filtering with a range of values
```
SELECT ProductName
,UnitPrice
,SupplierID
,UnitsInStock
FROM Products
WHERE UnitsInStock BETWEEN 15 and 80;
```

## IN
- Specifies a range of conditions
- Comma delimited list of values
- Enclosed in ()
- IN executes faster than OR
- Dont have to think about order with IN
- Can cantain another SELECT
- Example: 
```
SELECT
ProductID
,UnitPrice
,SupplierID
FROM Products
WHERE SupplierID IN (9,10,11);
```

## OR 
- DBMS will not evaluate second conditions in a WHERE clause if the first condition is met
- Use for any rows matching the specific conditions
- Matters which one you put first.
- Dont use if you want to check both values, use AND instaed. 
```
SELECT 
ProductName
,ProductID
,UnitPrice
,SupplierID
,ProductName
From products
Where ProductName = 'Tofu' OR 'Konbu';
```
## OR with AND
- Use () after the WHERE to make the AND portion go first and then the WHERE and OR go last.
- Order of Operations where SQL processes AND before OR
- Dont rely on default order of operations. Better to be specific and getting in habit of usng the ()
```
SELECT 
ProdutID
,UnitPrice
,SupplierID
FROM Products
WHERE (SupplierID = 9 OR supplierID = 11)
AND UnitPrice > 15;
```

## NOT
- Exclude different options
```
SELECT *
FROM Employees
WHERE NOT City='London' AND NOT City='Seattle';
```

## LIKE


# Sorting Data
- allows you to see data logially and help keep info you want on top

## ORDER BY
- Allows user to sort data by particular columns. 
- EXAMPLE:
```
SELECT something
FROM database
ORDER BY characteristics
```
- Takes the name of one or more columns
- Add a comma after each additional column name
- Can sort by a column not retrieved
- Must always be the last clause in a select statement

### Sort direction
- `DESC` decending order 
- `ASC` ascending order
- Only applies to the column names it directly prcedes


### Sorting by column position
- Example:
```ORDER by 2,3

```
2 means 2nd column
3 meeans 3rd column, etc. 


## % Wildcards
- Good for string values or text data, cant use in numerical data
- Special character used to match parts of a value
- Search pattern made from literal text, wildcard character, or a combination
- Downsides of using Wildcards
    1. Takes longer to run
    2. Better to use another operator if possible: `=, <, =>` etc.
    3. Statements with wildcards take longer to run if used at he end of search patterns
    4. Placement of wildcard is important
- % wildcard will not match NULLs (NULL represents no value in a column)
- Uses LIKE as an operator (though technically a predicate)
| Wildcard   | Action |
|--------------- | --------------- |
| `%Pizza`   | Grabs anything ending with word pizza |
| `Pizza%`   | Grabs anything after the word pizza |
| `%Pizza%`   | Grabs anything before and after the word pizza  |
| `S%E` | Grabs anything that starts with "S" and ends with "E" Like sadie |
| `t%@gmail.com` | Grabs gmail addresses that start with "t" hoping to find tom |

### Underscore `(_)` wildcard
- Matches a single character 
- IS not supported by DB2
- EXAMPLE 1
```
WHERE size LIKE '_pizza'
    OUTPUT: 
    spizza
    mpizza
```
- EXAMPLE 2
```
WHERE size LIKE '%pizza'
OUTPUT: 
    spizza
    mpizza
```
### Bracket `[]` Wildcard
- Used to speciify a set of characters in a specific location
- Does not work with all DBMS 
- Does not work with SQLite

## Math Operators
- Perform basic math calculations using data
- Order of operations (PEMDAS)
- Analysis possibles of using math opeeratiors and SQL together.

| Operator   | Description |
|--------------- | --------------- |
| + | Addition |
| - | Subtraction |
| * | Multiplication |
| / | Division |

- Example 1: Multiplication
```
SELECT
ProductID
,UnitsOnOrder
,UnitPrice
,UnitsOnOrder * UnitPrice AS Total_Order_Cost
FROM Product
```
- Example 2: Combining Math Operations 
```
SELECT
ProductID
,Quantity
,UnitPrice
,Discount
,(UnitPrice - Discount)*Quantity AS
Total_Cost
FROM OrderDetails; 
```
## Aggregate Functins
- Used to summarize data
- Finding highest and lowest values
- Find total number of rows
- Find average value
- 
| Function | Description |
|--------|-----------|
| AVG () | Aveages of column of values |
|COUNT () | Counts the number of values |
| Min () | Finds the minimum value |
| MAX () | Find the max value |
| SUM () | Sums the column values | 
> 
### AVERAGE
- Rows containing NULL values are ignored by the AVERAGE function
```
SELECT AVG(UnitPrice) AS avg_price
FROM products
```

### COUNT
-`COUNT(*)` countas all rows in a table containing values or NULL values
```
SELECT COUNT (*) AS 
total_customers
FROM Customers;
```
- `COUNT(column)` counts all the rows in a specific column ignoring NULL values
```
SELECT COUNT(CustomerID) AS 
total_customers
FROM Customers
```

### MAX and MIN
- NULL values are ignored in MIN and MAX functions
- Example 1

```
SELECT MAX(UnitPrice) AS max_prod_price
FROM Products
```
- Example 2
```
SELECT MAX(UnitPrice) AS max_prod_price
,MIN(UnitPrice) AS min_prod_price
FROM Products
```

### SUM
- Example 1 
```
SELECT SUM(unitPrice) AS 
    total_prod_price
FROM Products
```
- Example 2
```
SELEECT SUM(UnitPrice*UnitsInStock)
    AS total_price
FROM Products
WHERE SupplierID = 23;

```
### DISTINCT
- If DISTINCT is not specified, ALL is assumed. EX if you want to count customers, you need to specifuiy that you want distinct customers so as not to count the same customers more than once if they are in your data multiple times. 
- Cannot use DISTINCT on `COUNT(*)`
- No values to use with MIN and MAX functions 
- Example 1 
``` 
SEELECT COUNT(DISTINCT CustomerID)
FROM Customers
```


## Grouping Data with SQL

- Group data in order to summarize subsets of data `GOUP BY; HAVING`
- Example 1.
```
SELECT 
Region
,COUNT(CustomerID) AS total_customers
FROM Customers
GROUP BY Region;
```
- `GROUP BY` clauses can contain multiple columns
- Every column in your `SELECT` statement must be present in a `GROUP BY` clause, except for aggregated calculations
- NULLS will be grouped together if your `GROUP BY` column contains NULLs
- `WHERE` does not work for groups, only filters on rows. Use `HAVING` clause to filter for groups. Example: 
```
SELECT
CustomerID
,COUNT (*) AS orders 
FROM Orders 
GROUP BY CustomerID
HAVING COUNT (*) >=2;
```
- `WHERE` vs `HAVING`
    1. `WHERE` filters before data is grouped
    2. `HAVING` filters after data is grouped
    3. Rows eliminated by the `WHERE` clause will not be a inlcuded in the group
- `ORDER BY` with `GROUP BY`
    1. `ORDER BY` sorts data
    2.  `GROUP BY` does not sort data
    EXAMPLE: 
    ```
    SELECT SupplierID
    ,COUNT(*) AS Num_Prod
    FROM Products
    WHERE UnitPrice >= 4
    GROUP BY SupplierID 
    HAVING COUNT (*) >=2;
    ```
## Filtering is Useful
- Narrow down your results
- Increasing query and application performance
- Understand your data
    1. Finding specific values
    2. Finding a range of values
    3. Finding blank values

## Key SQL Clauses
| Clause | Description | Required |
|---------------- | --------------- | --------------- |
| `SELECT `| Columns or expressions to be returned| yes |
| `FROM`   | Table from which to retirve data |Only if sleecting data from a table    |
| `WHERE`   | Row level filtering | no |
| `GROUP BY`| Group specification | Only if calculating aggregates by group |
| `HAVING` | group level filter | no |
| `ORDER BY`| output sort order | no |


# Subqueries and Joines

## Subqueries
### How they work

- Innermost select portion first
```
SELECT
CustomerID
,CompanyName
,Region
FROM Customers
WHERE customerID in (SELECT
customerIDkk
    FROM Orders 
    WHERE Freight > 100 );
```
- Subquery in subquery
```
SELECT Customer_name, Customer_contact
FROM Customers
WHERE cust_in IN 
    SELECT customer_id
    FROM Orders 
    WHERE order_number IN (SELECT order_number
        FROM OrderItems
           WHERE prod_name = 'Toothbrush');
```
- Subqueries for calculations
```
SELECT COUNT (*) AS orders 
FROM Orders 
Where customer_id = '1234425';

SELECT customer_name
    ,Customer_state
    (SELECT COUNT (*) AS orders 
    FROM Orders 
    WHERE Orders.customer_id =
Customer.customer_id) AS orders 
FROM customers
ORDER BY Customer_name
```


### Advantages
- to have 2nd, 3rd or moer queries nested within another query.
- helpful when it comes to getting info from multiple tables 
- used for adding addition critereia like a filtering criteria thats not in current table from another table into your query
- No limit to the number of subqueris you can have

### Disatvanteges
- Perfrmace slows when you nest too deeply
- Subquery selects can only retireve a single column
### Best practies for using subqueries



## Joins

### Revisit Key Fields

### Linking data together with Joins

### Different types of joins




