# Subquery

## Definition:  
Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps. Very often used for filtering, aggregation, or conditional logic.
## Important rules:

- Subqueries can be used with SELECT, UPDATE, INSERT, and DELETE statements along with the expression operator.
- You can place the Subquery in a number of SQL clauses: WHERE clause, HAVING clause, FROM clause.
- The subquery generally executes <b>first</b> when the subquery doesn’t have any co-relation with the main query, when there is a co-relation the parser takes the decision on the fly on which query to execute on precedence and uses the output of the subquery accordingly.
- Subquery must be enclosed in parentheses.
  
### Types
- Single-row subquery: A subquery that returns only one row of results. It can be used with comparison operators such as =, >, <, etc.

```
SELECT *
FROM Track
WHERE UnitPrice = (
    SELECT MAX(UnitPrice)
    FROM Track
);

```
(For Track table, we will get all rows, because unit is the same)

- Multi-row subquery: A subquery that returns multiple rows of results. It can be used with operators such as IN, ANY, ALL, etc.

```
  SELECT CustomerID, Company, FirstName, LastName, Phone, Email
  FROM Customer
  WHERE Email IN (SELECT Email FROM Customer WHERE Email LIKE '%gmail.com%')
  ORDER BY Email;
```
- Correlated subquery: A subquery that refers to columns from the outer query. Correlated subqueries are evaluated once for each row processed by the outer query.

```
SELECT CustomerID, Company, FirstName, LastName, Phone, Email,
(SELECT COUNT(*) FROM Customer WHERE Email LIKE '%gmail.com%') AS CustomerCount,
(SELECT COUNT(*) FROM Customer WHERE Email LIKE '%yahoo.com%') AS CustomerCount2
FROM Customer
ORDER BY CustomerCount DESC;

```

  
- Scalar subquery: Returns a single value (single-row, single-column result). Scalar subqueries are often used within expressions.
```
SELECT CustomerID, Company, FirstName, LastName, Phone, Email,
(SELECT COUNT(*) FROM Customer WHERE Email LIKE '%gmail.com%') AS CustomerCount
FROM Customer;
```
  

### Key Points

### Syntax:
```
SELECT column_name
FROM table_name
WHERE column_name expression operator 
    ( SELECT COLUMN_NAME  from TABLE_NAME   WHERE ... );
```

### Best Practices


### Types
