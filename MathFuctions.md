# Math Functions in PostgreSQL

PostgreSQL is an advanced relational database system that supports both relational (SQL) and non-relational (JSON) queries. It is free and open-source. One of the most fundamental properties of database systems is mathematical operations, without which a multitude of tasks, from simple arithmetic to complex analysis, are unfeasible.

Math functions are fundamental in performing calculations in PostgreSQL, ensuring that the process is both fast and accurate. In this article, we are going to discuss different math functions in PostgreSQL.

## Introduction to Math Functions

In PostgreSQL, math functions are symbols or keywords used for performing mathematical operations on numerical data types stored in the database. A user can execute such expressions using these functions, including addition, subtraction, multiplication, and division operations, enabling many data manipulation tasks.

## Various Math Functions in PostgreSQL

Given below are the most commonly used math functions in PostgreSQL:

| Operator | Name                | Description                                         |
| -------- | ------------------- | --------------------------------------------------- | ----------------------------------------------- |
| `+`      | Addition            | Adds two values                                     |
| `-`      | Subtraction         | Subtracts right-hand operand from left-hand operand |
| `*`      | Multiplication      | Multiplies two values                               |
| `/`      | Division            | Divides one value by another                        |
| `%`      | Modulo              | Returns the remainder of a division operation       |
| `^`      | Raised To           | Computes the exponent of the right-hand operand     |
| `        | /`                  | Square Root                                         | Calculates the square root                      |
| `!`      | Factorial           | Computes the factorial of a non-negative integer    |
| `@`      | Absolute Value      | Returns the absolute value of a number              |
| `&`      | Bitwise AND         | Performs a bitwise AND operation on two integers    |
| `        | `                   | Bitwise OR                                          | Performs a bitwise OR operation on two integers |
| `#`      | Bitwise XOR         | Performs a bitwise XOR operation on two integers    |
| `~`      | Bitwise NOT         | Performs a bitwise negation operation on an integer |
| `<<`     | Bitwise Shift Left  | Shifts bits of an integer to the left               |
| `>>`     | Bitwise Shift Right | Shifts bits of an integer to the right              |

### Example Database Table: `Sales`

Now, let's see examples of each math function using this table:

### 1. Addition (`+`)

#### Syntax

```sql
SELECT price + 5 AS New_price FROM Sales;
```

#### Output

This query adds 5 to each price and returns a new column named `New_price`.

### 2. Subtraction (`-`)

#### Syntax

```sql
SELECT price - 2 AS New_price FROM Sales;
```

#### Output

This query subtracts 2 from each price and returns a new column named `New_price`.

### 3. Multiplication (`*`)

#### Syntax

```sql
SELECT price * 2 AS New_price FROM Sales;
```

#### Output

This query multiplies each price by 2 and returns a new column named `New_price`.

### 4. Division (`/`)

#### Syntax

```sql
SELECT price / 2 AS New_price FROM Sales;
```

#### Output

This query divides each price by 2 and returns a new column named `New_price`.

### 5. Modulo (`%`)

#### Syntax

```sql
SELECT price % 2 AS New_price FROM Sales;
```

#### Output

This query returns the remainder when each price is divided by 2.

### 6. Exponentiation (`^`)

#### Syntax

```sql
SELECT POWER(price, 2) AS New_price FROM Sales;
```

#### Output

This query calculates the square of each price.

### 7. Square Root (`|/`)

#### Syntax

```sql
SELECT SQRT(price) AS New_price FROM Sales;
```

#### Output

This query calculates the square root of each price.

### Example Database Table: `Numbers`

### 8. Factorial (`!`)

#### Syntax

```sql
SELECT value, factorial(value) AS factorial FROM Numbers;
```

#### Output

This query calculates the factorial of each value.

### 9. Absolute Value (`@`)

#### Syntax

```sql
SELECT value, abs(value) AS absolute_value FROM Numbers;
```

#### Output

This query calculates the absolute value of each value.

### 10. Bitwise AND (`&`)

#### Syntax

```sql
SELECT value, (value & 3) AS bitwise_and_result FROM Numbers;
```

#### Output

This query performs a bitwise AND operation between each value and 3.

### 11. Bitwise OR (`|`)

#### Syntax

```sql
SELECT value, (value | 3) AS bitwise_or_result FROM Numbers;
```

#### Output

This query performs a bitwise OR operation between each value and 3.

### 12. Bitwise XOR (`#`)

#### Syntax

```sql
SELECT value, (value # 3) AS bitwise_xor_result FROM Numbers;
```

#### Output

This query performs a bitwise XOR operation between each value and 3.

### 13. Bitwise NOT (`~`)

#### Syntax

```sql
SELECT value, (~value) AS bitwise_not_result FROM Numbers;
```

#### Output

This query performs a bitwise NOT operation on each value.

### 14. Bitwise Shift Left (`<<`)

#### Syntax

```sql
SELECT value, (value << 1) AS bitwise_shift_left_result FROM Numbers;
```

#### Output

This query shifts all bits of each value one position to the left.

### 15. Bitwise Shift Right (`>>`)

#### Syntax

```sql
SELECT value, (value >> 1) AS bitwise_shift_right_result FROM Numbers;
```

#### Output

This query shifts all bits of each value one position to the right.

## Conclusion

In PostgreSQL, math functions make complex mathematical calculations possible in the database environment. Whether performing simple sums or complex statistical operations, understanding these functions is key to efficient data manipulation and analysis. By mastering math functions, database users can unlock the full potential of PostgreSQL for their data-driven applications and workflows.
