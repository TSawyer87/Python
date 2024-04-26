#SQL 
The `INSERT` command in [[SQLite]] (accessible through the `sqlite3` module in Python) is used to add new rows of data to a table. Here's a breakdown of its syntax and usage:

**Basic [[Syntax]]:**

SQL

```
INSERT [OR conflict-algorithm] INTO [database-name.]table-name [(column-list)] VALUES (value-list) ...;
```

Use code [with caution.](https://gemini.google.com/faq#coding)

**Explanation of Parts:**

- **`INSERT`:** Keyword indicating the operation you want to perform.
- **`[OR conflict-algorithm]`: (Optional) Specifies an alternative behavior for handling conflicts that might arise during insertion. Common options include `REPLACE` (replace existing data) and `IGNORE` (skip inserting rows that cause conflicts).
- **`INTO`:** Keyword indicating the target table for inserting data.
- **`[database-name.]`:** (Optional) If your database file has a name other than the default (`sqlite.db`), you can specify it here.
- **`table-name`:** The name of the table you want to insert data into.
- **`[(column-list)]`:** (Optional) A list of column names in the table where you want to insert values. If omitted, values must be provided for all columns in the table (in their defined order).
- **`VALUES`:** Keyword introducing the list of values to be inserted.
- **`(value-list)`:** A comma-separated list of values to be inserted into the corresponding columns (specified in `column-list` if provided).
- **`;`:** Semicolon to terminate the SQL statement.

**Examples:**

1. **Inserting data with specified columns:**
    
    SQL
    
    ```
    INSERT INTO customers (name, email) VALUES ("John Doe", "john.doe@example.com");
    ```
    
    Use code [with caution.](https://gemini.google.com/faq#coding)
    

- This inserts a new row into the `customers` table with "John Doe" in the `name` column and "john.doe@example.com" in the `email` column.
    
- **Inserting data without specifying columns:**
    
    SQL
    
    ```
    INSERT INTO customers VALUES ("Jane Smith", "jane.smith@example.com");
    ```
    
    Use code [with caution.](https://gemini.google.com/faq#coding)
    
- Here, assuming `customers` has columns `name` and `email` in that order, this inserts a new row with "Jane Smith" in the `name` column and "jane.smith@example.com" in the `email` column.
    
- **Inserting multiple rows:**
    
    SQL
    
    ```
    INSERT INTO orders (customer_id, product_id, quantity)
    VALUES (1, 10, 2), (2, 5, 1);
    ```
    
    Use code [with caution.](https://gemini.google.com/faq#coding)
    

1. This inserts two new rows into the `orders` table, specifying customer IDs, product IDs, and quantities.
    

**Additional Notes:**

- You can use placeholders (`?`) in the `VALUES` clause and pass the actual values as a separate sequence (tuple or list) to the cursor's `execute` method for safer and more dynamic queries (helps prevent SQL injection vulnerabilities).
- Consider using appropriate data types for the values you're inserting to ensure data integrity.

Remember to execute the `INSERT` command using the `cursor.execute()` method in your Python code and commit the changes using `conn.commit()` to persist the data in the database.
