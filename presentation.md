# Subquery

## Definition:  
Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps. 

## Important rules:

- Subqueries can be used with SELECT, UPDATE, INSERT, and DELETE statements along with the expression operator.
- You can place the Subquery in a number of SQL clauses: WHERE clause, HAVING clause, FROM clause.
- The subquery generally executes <b>first</b> when the subquery doesn’t have any co-relation with the main query, when there is a co-relation the parser takes the decision on the fly on which query to execute on precedence and uses the output of the subquery accordingly.
- Subquery must be enclosed in parentheses.
  
### Types
- Single-row subquery: A subquery that returns only one row of results. It can be used with comparison operators such as =, >, <, etc.
- Multi-row subquery: A subquery that returns multiple rows of results. It can be used with operators such as IN, ANY, ALL, etc.
- Correlated subquery: A subquery that refers to columns from the outer query. Correlated subqueries are evaluated once for each row processed by the outer query.
- Scalar subquery: A subquery that returns a single value (single-row, single-column result). Scalar subqueries are often used within expressions.

### Key Points

### Syntax:
Example 1:
```
SELECT column_name
FROM table_name
WHERE column_name expression operator 
    ( SELECT COLUMN_NAME  from TABLE_NAME   WHERE ... );

```

### Best Practices


### Types
