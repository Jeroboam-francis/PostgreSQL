# PostgreSQL Aggregate Functions

PostgreSQL Aggregate Functions are used to perform calculations on a set of rows and return a single value. They are often used with the `GROUP BY` clause in PostgreSQL to summarize data for each group. Commonly used aggregate functions include `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()`.

Find more on [https://www.postgresql.org/docs/current/functions-aggregate.html](https://www.postgresql.org/docs/current/functions-aggregate.html)

## What Are PostgreSQL Aggregate Functions?

PostgreSQL Aggregate Functions are essential for summarizing and analyzing large datasets. These functions operate on multiple rows of a table, combining them into a single, more meaningful result. PostgreSQL aggregate functions are mostly used with the `GROUP BY` clause of the `SELECT` statement.

### Various Aggregate Functions

- `COUNT()`
- `SUM()`
- `AVG()`
- `MIN()`
- `MAX()`

## Common PostgreSQL Aggregate Functions

Below is the list of PostgreSQL aggregate functions, with examples:

### COUNT()

- `COUNT(*)`: Returns the total number of records, i.e., `6`.
- `COUNT(salary)`: Returns the number of non-null values in the `salary` column, i.e., `5`.
- `COUNT(DISTINCT salary)`: Returns the number of distinct non-null values in the `salary` column, i.e., `5`.

### SUM()

- `SUM(salary)`: Sums all non-null values in the `salary` column, i.e., `3120`.
- `SUM(DISTINCT salary)`: Sums all distinct non-null values in the `salary` column, i.e., `3120`.

### AVG()

- `AVG(salary)`: Calculates the average of the `salary` column:  
  `AVG(salary) = SUM(salary) / COUNT(salary) = 3120 / 5 = 624`
- `AVG(DISTINCT salary)`:  
  `AVG(DISTINCT salary) = SUM(DISTINCT salary) / COUNT(DISTINCT salary) = 3120 / 5 = 624`

### MIN()

- `MIN(salary)`: Returns the minimum value in the `salary` column, excluding NULLs, i.e., `403`.

### MAX()

- `MAX(salary)`: Returns the maximum value in the `salary` column, i.e., `802`.

## PostgreSQL Aggregate Functions with Examples

Let’s consider a demo `Employee` table for our examples. This table contains employee details such as their ID, Name, and Salary.

```postgresql
CREATE TABLE Employee (
  Id SERIAL PRIMARY KEY,
  Name VARCHAR(50),  -- Allows longer names
  Salary DECIMAL(10,2)  -- Handles precision for salaries
);

INSERT INTO Employee (Name, Salary)
VALUES ('A', 802),
       ('B', 403),
       ('C', 604),
       ('D', 705),
       ('E', 606),
       ('F', NULL);
```

In this example, we will use multiple aggregate functions on the data:

```postgresql
-- Count the number of employees
SELECT COUNT(*) AS TotalEmployees FROM Employee;

-- Calculate the total salary
SELECT SUM(Salary) AS TotalSalary FROM Employee;

-- Find the average salary
SELECT AVG(Salary) AS AverageSalary FROM Employee;

-- Get the highest salary
SELECT MAX(Salary) AS HighestSalary FROM Employee;

-- Determine the lowest salary
SELECT MIN(Salary) AS LowestSalary FROM Employee;
```

### Output

| TotalEmployees | TotalSalary | AverageSalary | HighestSalary | LowestSalary |
| -------------- | ----------- | ------------- | ------------- | ------------ |
| 6              | 3120        | 624           | 802           | 403          |

## Using Aggregate Functions with GROUP BY

`GROUP BY` allows you to group rows that share a property, enabling you to perform aggregate calculations on each group. This is commonly used with the `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()` functions.

### Example: Total Salary by Each Employee

```postgresql
SELECT Name, SUM(Salary) AS TotalSalary
FROM Employee
GROUP BY Name;
```

### Output

| Name | TotalSalary |
| ---- | ----------- |
| A    | 802         |
| B    | 403         |
| C    | 604         |
| D    | 705         |
| E    | 606         |
| F    | NULL        |

## Using HAVING with Aggregate Functions

The `HAVING` clause is used to filter results after applying aggregate functions. Unlike `WHERE`, which filters rows before aggregation, `HAVING` filters groups after aggregation.

### Example: Find Employees with Salary Greater Than 600

```postgresql
SELECT Name, SUM(Salary) AS TotalSalary
FROM Employee
GROUP BY Name
HAVING SUM(Salary) > 600;
```

### Output

| Name | TotalSalary |
| ---- | ----------- |
| A    | 802         |
| C    | 604         |
| D    | 705         |
| E    | 606         |

## Key Takeaways about PostgreSQL Aggregate Functions

- Aggregate functions in PostgreSQL operate on a group of values and return a single result.
- They are often used with the `GROUP BY` clause to summarize grouped data.
- Aggregate functions operate on non-null values only (except `COUNT(*)`).
- Commonly used aggregate functions are `MIN()`, `MAX()`, `COUNT()`, `AVG()`, and `SUM()`.

## Conclusion

PostgreSQL Aggregate Functions are crucial for summarizing and analyzing large datasets. Whether you’re calculating totals, averages, or finding extreme values like maximum and minimum, these functions simplify data aggregation and help derive insights.

```

```
