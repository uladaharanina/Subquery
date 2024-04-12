# Subquery

## Definition:  
Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps. 

## Important rules:

- Subqueries can be used with SELECT, UPDATE, INSERT, DELETE statements along with expression operator.
- You can place the Subquery in a number of SQL clauses: WHERE clause, HAVING clause, FROM clause.
- The subquery generally executes <b>first</b> when the subquery doesn’t have any co-relation with the main query, when there is a co-relation the parser takes the decision on the fly on which query to execute on precedence and uses the output of the subquery accordingly.

### Types

Scaler
```
SELECT name, age,
       (SELECT AVG(age) FROM employees) AS average_age
FROM employees
WHERE age > (SELECT AVG(age) FROM employees);

```

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
