// Name: TSQL HW11
// Author: James Smelser
// Date: September 26, 2019

-------------------------------------------------------------
# Chapter 11
## ISTA-420, T-SQL Fundamentals
1. Why do we use variables in T-SQL? How do you declare and initialize T-SQL variables?
- It is an object that can hold a single data value of a specific type. DECLARE statement @ as the first character, assigning a name, assigning a system-supplied or user-defined data type and a length.
2. Describe what is meant by a batch file in T-SQL? What is the difference between batches and trans-
actions?
- A batch is one or more T-SQL statements sent by a client application to SQL Server for execution as a
single unit. A transaction is an atomic unit of work. A batch can have multiple transactions, and a transaction can be submitted in parts as multiple batches.
3. What is the scope of variables with respect to T-SQL batches?
- A variable is local to the batch in which it’s defined.
4. Write a T-SQL code snippet that returns a data element stating whether the current person can legally
purchase alcohol, that is, has reached his 21st birthday.
```
DROP FUNCTION IF EXISTS dbo.GetAge;
GO
CREATE FUNCTION dbo.GetAge
(
@birthdate AS DATE,
@eventdate AS DATE
)
RETURNS INT
AS
BEGIN
RETURN
DATEDIFF(year, @birthdate, @eventdate)
- CASE WHEN 100 * MONTH(@eventdate) + DAY(@eventdate)
< 100 * MONTH(@birthdate) + DAY(@birthdate)
THEN 1 ELSE 0
END;
END;
GO
```
5. (Not in book) Does T-SQL have a for loop construction?
- There is no FOR loop, in T-SQL the WHILE statement is the most commonly used way to execute a loop.
6. What is a cursor? What is the difference between a relation and a cursor?
- an object called cursor you can use to process rows from a result of a query one at a time and in a requested order.
When you use cursors you pretty much go against the relational model, which is based on set theory.
7. How do you declare a temporary table? Why would you declare a temporary table?
- You create a local temporary table by naming it with a single pound sign as a prefix, such as #T1. All three kinds of temporary tables are created in the tempdb database.
8. What is the difference between a stored procedure, a user defined function, and a trigger?
- Stored procedures are routines that encapsulate code. They can have input and output parameters,
they can return result sets of queries, and they are allowed to have side effects. The purpose of a user-defined function (UDF) is to encapsulate logic that calculates something, possibly based on input parameters, and return a result. A trigger is a special kind of stored procedure—one that cannot be executed explicitly. Instead, it’s attached to an event.
9. Write a user defined function that returns a Booleans as to whether a customer may purchase alcohol
as of the instant that the function runs.
```
DROP FUNCTION IF EXISTS dbo.GetAge;
GO
CREATE FUNCTION dbo.GetAge
(
@birthdate AS DATE,
@eventdate AS DATE
)
RETURNS BOOL
AS
BEGIN
RETURN
DATEDIFF(year, @birthdate, @eventdate)
- CASE WHEN 100 * MONTH(@eventdate) + DAY(@eventdate)
< 100 * MONTH(@birthdate) + DAY(@birthdate)
THEN 1 ELSE 0
END;
END;
GO
```
10. Write a trigger that places a customer in the OFF LIMITS table if he attempt to purchase alcohol
when he is underage.
```
DROP FUNCTION IF EXISTS dbo.GetAge;
GO
CREATE FUNCTION dbo.GetAge
(
@birthdate AS DATE,
@eventdate AS DATE
)
RETURNS BOOL
AS
BEGIN
RETURN
DATEDIFF(year, @birthdate, @eventdate)
- CASE WHEN 100 * MONTH(@eventdate) + DAY(@eventdate)
< 100 * MONTH(@birthdate) + DAY(@birthdate)
THEN 1 ELSE 0
END;
END;
GO
```
11. Write a stored procedure that deletes customers from the OFF LIMITS table when they have reached
their 21st birthday.
```
DROP FUNCTION IF EXISTS dbo.GetAge;
GO
CREATE FUNCTION dbo.GetAge
(
@birthdate AS DATE,
@eventdate AS DATE
)
RETURNS BOOL
AS
BEGIN
RETURN
DATEDIFF(year, @birthdate, @eventdate)
- CASE WHEN 100 * MONTH(@eventdate) + DAY(@eventdate)
< 100 * MONTH(@birthdate) + DAY(@birthdate)
THEN 1 ELSE 0
END;
END;
GO
```
