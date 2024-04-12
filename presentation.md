# Subquery

## Definition:  
Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps. Very often used for filtering, aggregation, or conditional logic.
## Important rules:

- Subqueries can be used with SELECT, UPDATE, INSERT, and DELETE statements along with the expression operator.
- You can place the Subquery in a number of SQL clauses: WHERE clause, HAVING clause, FROM clause.
- The subquery generally executes <b>first</b> when the subquery doesn’t have any co-relation with the main query, when there is a co-relation the parser takes the decision on the fly on which query to execute on precedence and uses the output of the subquery accordingly.
- Subquery must be enclosed in parentheses.

  ### Syntax:
```
SELECT column_name
FROM table_name
WHERE column_name expression operator 
    ( SELECT COLUMN_NAME  from TABLE_NAME   WHERE ... );
```
  
### Types
- <b>Single-row subquery:</b> A subquery that returns only one row of results. It can be used with comparison operators such as =, >, <, etc.

```
SELECT *
FROM Track
WHERE UnitPrice = (
    SELECT MAX(UnitPrice)
    FROM Track
);

```
(For Track table, we will get all rows, because unit is the same)

- <b>Multi-row subquery: A subquery that returns multiple rows of results. It can be used with operators such as IN, ANY, ALL, etc.

```
  SELECT CustomerID, Company, FirstName, LastName, Phone, Email
  FROM Customer
  WHERE Email IN (SELECT Email FROM Customer WHERE Email LIKE '%gmail.com%')
  ORDER BY Email;
```
- <b>Correlated subquery: A subquery that refers to columns from the outer query. Correlated subqueries are evaluated once for each row processed by the outer query.

```
SELECT CustomerID, Company, FirstName, LastName, Phone, Email,
(SELECT COUNT(*) FROM Customer WHERE Email LIKE '%gmail.com%') AS CustomerCount,
(SELECT COUNT(*) FROM Customer WHERE Email LIKE '%yahoo.com%') AS CustomerCount2
FROM Customer
ORDER BY CustomerCount DESC;

```
  
- <b>Scalar subquery:</b> Returns a single value <b>exactly one row and exactly one column</b>, Scalar subqueries are often used within expressions.
```
SELECT CustomerID, Company, FirstName, LastName, Phone, Email,
(SELECT COUNT(*) FROM Customer WHERE Email LIKE '%gmail.com%') AS CustomerCount
FROM Customer;
```
  


### Best Practices

- Use subqueries judiciously as they can complicate the SQL statements and may lead to performance issues.
- Consider alternatives like joins or temporary tables if the subquery makes the query substantially slower or harder to read.
- Always test subqueries for performance in the context of the larger database system.
