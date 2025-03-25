# PostgreSQL – LIMIT with OFFSET Clause

The PostgreSQL `LIMIT` clause is a powerful feature that allows users to retrieve a specific subset of rows from query results. This optional clause can be paired with the `OFFSET` clause to skip a specified number of rows before returning the desired results. Such functionality is particularly beneficial for pagination, enabling us to fetch data in manageable chunks.

In this article, we will explain the PostgreSQL `LIMIT` and `OFFSET` clauses in-depth, with practical examples and outputs to illustrate their application.

## PostgreSQL LIMIT with OFFSET Clause

The `LIMIT` clause restricts the number of rows returned by a PostgreSQL query. By specifying a number after the `LIMIT` keyword, we train PostgreSQL to return only that many rows. This is particularly advantageous when working with large tables where retrieving every row could lead to performance issues, increased loading times, and an overcrowded user interface.

### Syntax

```sql
SELECT * FROM table LIMIT n OFFSET m;
```

### Key Terms

- The `LIMIT` clause returns a subset of **n** rows from the query result.
- The `OFFSET` clause placed after the `LIMIT` clause skips **m** number of rows before returning the result query.
- If **m** is `0`, then it acts as a normal `LIMIT` clause.

## PostgreSQL LIMIT with OFFSET Clause Examples

Now, let us examine a few practical examples of using the `LIMIT` and `OFFSET` clauses in PostgreSQL to better understand their application. PostgreSQL `LIMIT` with `OFFSET` clause examples provide valuable insights into how to efficiently manage large datasets and implement pagination in our queries.

### Example 1: Fetching Films with LIMIT and OFFSET

Here we will query for 5 films starting from the seventh one ordered by `film_id` from the `film` table of our sample database.

#### Query

```sql
SELECT
    film_id,
    title,
    release_year
FROM
    film
ORDER BY
    film_id
LIMIT 5 OFFSET 6;
```

#### Explanation

This query retrieves 5 films starting from the seventh record (`OFFSET 6`) in the table, ordered by their `film_id`.

---

### Example 2: Fetching Films Ordered by Title in Descending Order

Here we will query for 5 films starting from the seventh one ordered by `film_id` from the `film` table of our sample database in descending order of the film `title`.

#### Query:

```sql
SELECT
    film_id,
    title,
    release_year
FROM
    film
ORDER BY
    title DESC
LIMIT 5 OFFSET 6;
```

#### Explanation:

This query retrieves 5 films starting from the seventh record (`OFFSET 6`) in the table, ordered by their `title` in descending order.

## Important Points About PostgreSQL LIMIT with OFFSET Clause

- The `LIMIT` clause restricts the number of rows returned by a query.
- The `OFFSET` clause skips a specified number of rows before beginning to return rows from the query.
- An `OFFSET` of `0` (`OFFSET 0`) effectively ignores the `OFFSET` clause, making the query act as a standard `LIMIT` query.
- `LIMIT` and `OFFSET` are commonly used for pagination in applications, allowing users to retrieve data in smaller, manageable chunks.
- An alternative to `LIMIT` and `OFFSET` is **keyset pagination**, which uses a `WHERE` clause to filter rows based on a specific key.
- PostgreSQL also supports the `FETCH` clause as an alternative to `LIMIT`, which can be more readable in some contexts.

## Conclusion

Understanding the `LIMIT` and `OFFSET` clauses in PostgreSQL is important for effective data retrieval, especially when working with large datasets. By utilizing these clauses, you can implement efficient pagination strategies in your applications, enhancing the overall user experience. Whether we are fetching a limited number of results or skipping records, mastering the use of `LIMIT` and `OFFSET` can significantly improve our SQL querying capabilities.

## FAQs

### How to use LIMIT and OFFSET in Postgres?

In PostgreSQL, you can use the `LIMIT` clause to specify the maximum number of rows returned by a query, while the `OFFSET` clause allows you to skip a specified number of rows before returning the results. For example:

```sql
SELECT * FROM table_name LIMIT 10 OFFSET 5;
```

This retrieves 10 rows starting from the 6th record.

### What are LIMIT and OFFSET clauses?

The `LIMIT` clause restricts the number of rows returned by a query, while the `OFFSET` clause specifies how many rows to skip before starting to return rows. Together, they are commonly used for pagination in database queries.

### What is LIMIT and OFFSET together?

Using `LIMIT` and `OFFSET` together allows you to retrieve a specific subset of rows from a query. For example:

```sql
LIMIT 10 OFFSET 20;
```

This fetches 10 rows starting from the 21st record, enabling efficient data retrieval and pagination.

# PostgreSQL FETCH Clause

The PostgreSQL `FETCH` clause is an essential feature for controlling and managing the number of rows returned in SQL queries. It provides a standardized approach for limiting results, similar to the `LIMIT` clause but with more flexibility and compatibility across different database systems.

This article will explain the PostgreSQL `FETCH` clause, its syntax, functionality, and practical examples to enhance SQL query performance.

## What is the PostgreSQL FETCH Clause?

The `FETCH` clause in PostgreSQL is used to retrieve a specific subset of rows from a result set. When combined with the `OFFSET` clause, it allows skipping a certain number of rows before fetching the next set of results. This makes `FETCH` an ideal choice for implementing pagination or limiting the number of rows returned in large datasets.

Unlike `LIMIT`, which is a non-standard SQL feature, the `FETCH` clause is part of the SQL standard, ensuring better portability across various SQL databases like MySQL, SQL Server, and Oracle.

## Syntax

```sql
OFFSET start { ROW | ROWS }
FETCH { FIRST | NEXT } [ row_count ] { ROW | ROWS } ONLY;
```

### Key Terms

- `ROW` and `FIRST` are synonymous with `ROWS` and `NEXT`, respectively.
- `start` is an integer value that is zero or positive. By default, it is zero.
- `row_count` is an integer value that is one or higher. By default, it is one.
- `ORDER BY` Clause: Since the order of rows stored in the table is unpredictable, it’s crucial to use the `FETCH` clause with the `ORDER BY` clause to ensure consistent results.

> **Note:** We will use the sample **DVD rental database**, which can be downloaded [here](#).

## Examples of PostgreSQL FETCH Clause

### Example 1: Fetching the First 10 Rows

In this example, we will retrieve the first 10 rows of the `film` table, sorted by `title`.

#### Query:

```sql
SELECT
    film_id,
    title
FROM
    film
ORDER BY
    title
FETCH FIRST 10 ROW ONLY;
```

#### Explanation:

This query returns the first 10 films sorted alphabetically by their title.

### Example 2: Fetching Rows with Offset

Here, we will retrieve the first 10 rows after skipping the first 5 rows, sorted by `title`. This is useful for pagination when displaying results in chunks.

#### Query:

```sql
SELECT
    film_id,
    title
FROM
    film
ORDER BY
    title
OFFSET 5 ROWS
FETCH FIRST 10 ROW ONLY;
```

#### Explanation:

This query skips the first 5 films and then returns the next 10 films sorted by their title.

## Important Points About PostgreSQL FETCH Clause

- **Portability:** While both `FETCH` and `LIMIT` are used to retrieve a subset of rows, `FETCH` is part of the SQL standard, making it more portable across different SQL databases.
- **ROW vs. ROWS:** The keywords `ROW` and `ROWS` can be used interchangeably with `FETCH`. `ROW` is more appropriate when fetching a single row, and `ROWS` is semantically better for multiple rows.
- **ORDER BY Clause:** Always use the `ORDER BY` clause with `FETCH` to ensure consistent results, especially for large datasets or queries requiring pagination.
- **Subqueries:** `FETCH` can be used in subqueries to limit the number of rows processed by the outer query.

## Conclusion

The PostgreSQL `FETCH` clause is a flexible tool that allows us to efficiently manage query results by limiting the number of rows returned. It ensures SQL standard compliance, which enhances portability across various database systems.

By combining `FETCH` with `OFFSET`, we can implement pagination and optimize the retrieval of data in large datasets. Mastering the `FETCH` clause will improve the performance and flexibility of PostgreSQL queries.

## FAQs

### How to fetch data in PostgreSQL?

To fetch data in PostgreSQL, use the `SELECT` statement. For example:

```sql
SELECT * FROM table_name;
```

This retrieves all rows and columns from the specified table.

### What is the FETCH clause in SQL?

The `FETCH` clause in SQL is used to limit the number of rows returned by a query, often in combination with `OFFSET`. For example:

```sql
FETCH FIRST 10 ROWS ONLY;
```

This returns only the first 10 rows of a result set.

### What is the difference between FETCH and LIMIT in PostgreSQL?

Both `FETCH` and `LIMIT` limit the number of rows returned, but `LIMIT` is more commonly used. `FETCH` is part of the SQL standard and is often used with `OFFSET` for flexible row retrieval.
