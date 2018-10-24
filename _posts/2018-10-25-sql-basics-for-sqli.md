---
layout: post
title: Learn SQL for SQL Injection in 10 minutes
description: "An easy to follow primer for SQL."
modified: 2018-10-25
tags: [sql injection, basics, cheatsheet]
image:
  path: /images/featured/sql-basics.png
  feature: /featured/sql-basics.png
---

Hi there! This article is focused on whats important and I hope you have read my introductory article about SQL and SQL injection . So lets go!

As we know, data is stored in databases . A server can have many databases. Databases contain tables and tables contain data in the form of rows and columns .

<!--more-->

To save you from confusion, here’s a graphic stating difference between Rows and Columns.

![rows vs columns](/images/row-vs-column.jpg)

Column = Type of Information \
Row = Information

Well this means if you have a table of students of your class and you want to add their phone number in it. You will need to create a column for phone numbers which is a type of information but if you want to add recored of a new student, you would need to add a row to enter his/her information .

So how to enter data into databases? How to edit data? How to add rows and columns.

To manage databases, we take help of a declarative language called SQL (Structured Query Language). Here are some main commands of SQL:

**SELECT** : Retrieve data from table(s) \
**INSERT** : Insert data into db table \
**UPDATE** : Update data in db table \
**DELETE** : Delete data from table \
**CREATE** : Create db object \
**ALTER** : Modify db object \
**DROP** : Delete db object \
**GRANT** : Assign privilege \
**REVOKE** : remove privilege


### Selecting data from a table

To select data from a table, we use the SELECT statement whose syntax is as follows:

```sql
SELECT ColumnList FROM TableName WHERE Condition
```

Lets take the following table into account:

|IdNum|LName|FName|JobCode|Salary|
|-----|-----|-----|-------|------|
|1876|CHIN|JACK|TA1|42400|
|1114|GREENWALD|JANICE|ME3|38000|
|1556|PENNINGTON|MICHAEL|ME1|29860|
|1354|PARKER|MARY|FA3|65800|
|1130|WOOD|DEBORAH|PT2|36514|

Now lets say I have find names of the employees whose salary is more than 40,000. For this purpose I can build this SQL query:
SELECT FName FROM Employees Table WHERE Salary > '40000'
It will print the FName i.e. First name of the employees. To print all the information, we can use an * (asterisk) which selects everything .

```sql
SELECT * FROM Employees Table WHERE Salary > '40000'
```

### Inserting data into a table
To insert new data into a table we use INSERT INTO statement whose syntax is as follows:
```sql
INSERT INTO TableName (ColumnList) VALUES (Values)
```

|IdNum|LName|FName|JobCode|Salary|
|-----|-----|-----|-------|------|
|1876|CHIN|JACK|TA1|42400|
|1114|GREENWALD|JANICE|ME3|38000|
|1556|PENNINGTON|MICHAEL|ME1|29860|
|1354|PARKER|MARY|FA3|65800|
|1130|WOOD|DEBORAH|PT2|36514|

Lets assume that we have to add data of a new employee, so we can do the following:

```sql
INSERT INTO Employees Table (LName, FName, JobCode, Salary) VALUES
('Stark', 'Tony', 'AM2', '70500')
```

### Updating data and Using conditional operators

The INSERT INTO , statement is used to add new data but if we have to modify existing data, we use UPDATE command whose syntax is as follows:

```sql
UPDATE TableName
SET Column1 = Value1, Column2 = Value2, …
WHERE Condition
```

|IdNum|LName|FName|JobCode|Salary|
|-----|-----|-----|-------|------|
|1876|CHIN|JACK|TA1|42400|
|1114|GREENWALD|JANICE|ME3|38000|
|1556|PENNINGTON|MICHAEL|ME1|29860|
|1354|PARKER|MARY|FA3|65800|
|1130|WOOD|DEBORAH|PT2|36514|

So if I have to change the salary of Jack Chin then I can simply do this:

```sql
UPDATE Employees Table
SET Salary = '45000' WHERE LName='CHIN'
```

This query is perfect but what if there are more than two employees whose last name is Chin? Well in such cases we need to use multiple conditions with proper conditional operators. There are three conditional operators in SQL:

AND : Both conditions need to be true
OR : At least one condition needs to be true
NOT : The specified condition should not be true
Now lets select all the employees whose first name is Jack and last name is Chin.

```sql
SELECT * FROM Employees Table WHERE LName='Chin' AND FName='Jack'
```
Now lets select everyone whose Job code is either ME1 or ME3

```sql
SELECT * FROM Employees Table WHERE JobCode='ME1' OR JobCode='ME3'
```
Now lets select all the employees whose JobCode is not ME1

```sql
SELECT * FROM Employees Table WHERE NOT JobCode='ME1'
```

### Deleting data from a table
The syntax for deleting data from a table is a follows:

```sql
DELETE FROM<Table Name> WHERE<Search Condition>
```

WHERE Lets remove all the employees whose salary is more than 50,000

```sql
DELETE FROM Employees Table WHERE Salary > '50000'
```

### Ordering data

To order data, we use the ORDER BY statement whose syntax is as follows:

```sql
SELECT ColumnList
FROM TableName
WHERE Condition
ORDER BY ColumnList
```

|IdNum|LName|FName|JobCode|Salary|
|-----|-----|-----|-------|------|
|1876|CHIN|JACK|TA1|42400|
|1114|GREENWALD|JANICE|ME3|38000|
|1556|PENNINGTON|MICHAEL|ME1|29860|
|1354|PARKER|MARY|FA3|65800|
|1130|WOOD|DEBORAH|PT2|36514|

Now lets say we want to store the names of the employees according to alphabetical order, then we can build this query:
```sql
SELECT * FROM Employees Table ORDER BY FName
```

### Combining two our more queries

To combine multiple queries, we use the UNION statement whose syntax is following:

```sql
SELECT ColumnList FROM Table1 UNION SELECT Column List FROM Table2
```

So if you want to execute multiple queries at once, you can simple add the UNION statement between them.

Well there’s more to SQL but these are the basics which will help in being a good SQL Injector.

Keep Learning! Keep Querying!
