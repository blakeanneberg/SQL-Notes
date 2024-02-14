                /***********************************************/
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
    4. Tables: Use tables to make models and predictions, create dashboards, visualize data with other tools, extract data from other sources
    5. NULL represents absence of a value in a column. Not the same as an empty string or value. It means that a particular column in a database does not have any data entered for that specific row.
    6. Addding data to the table 
    ```
    INSERT INTO Shoes
    VALUES  ('14535974'
            ,'Gucci' 
            ,'Slippers'
            ,'Pink'
            ,'695.00'
            ,NULL
            )
    ``` 



