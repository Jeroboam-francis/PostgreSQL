# LIMIT, OFFSET AND FETCH

lets say we want to select the very first 10 rows from our table.

we use:

## LIMIT

Used to limit the amount of data returned by the SELECT statement. For example selecting only the first 10 records.
The basic syntax is as follows

```sql
SELECT column1, column2, columnN FROM table_name LIMIT number_of_rows;
```

```sql
SELECT * FROM person LIMIT 10;
```

We will have the record of the first 10 people in that table.

## OFFSET

The OFFSET clause is used to skip a specified number of rows before starting to return rows from the result set.

It is typically used in combination with LIMIT or FETCH to paginate results, allowing you to retrieve data in chunks or skip over parts of the dataset.

```sql
SELECT column1, column2, columnN FROM table OFFSET number_of_rows_to_skip;
```

- Selecting a record of a certain number of people after a certain limit.

```sql
SELECT * FROM person OFFSET 5 LIMIT 5;
```

- It will generate records after 5 rows, the first 5. That is 6-10.

We can remove the limit, to select up to the last record.

```sql
SELECT * FROM person OFFSET 5;
```

## FETCH

`LIMIT` - is not a keyword by SQL standards.

- We use the fetch keyword.

Syntax

```sql
SELECT column1, column2, columnN FROM table_name
FETCH {FIRST | NEXT} row_count {ROW | ROWS} ONLY;
```

example

```sql
SELECT * FROM person OFFSET 5 FETCH FIRST 5 ROW ONLY;
```

It will display from row 6, 5 rows, that will be 6-10.

For 1 row you can write `FIRST 1 ROW` or `FIRST ROW`.

## Important Points About PostgreSQL FETCH Clause

- **Portability:** While both `FETCH` and `LIMIT` are used to retrieve a subset of rows, `FETCH` is part of the SQL standard, making it more portable across different SQL databases.
- **ROW vs. ROWS:** The keywords `ROW` and `ROWS` can be used interchangeably with `FETCH`. `ROW` is more appropriate when fetching a single row, and `ROWS` is semantically better for multiple rows.
.
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
