#SQL 
You can request that the returned rows be sorted by one of the fields as follows:

```
SELECT title,plays FROM Track ORDER BY title
```

It is possible to `UPDATE` a column or columns within one or more rows in a table using the [[SQL UPDATE statement]] as follows:

```
UPDATE Track SET plays = 16 WHERE title = 'My Way'
```

The `UPDATE` statement specifies a table and then a list of fields and values to change after the `SET` keyword and then an optional `WHERE` clause to select the rows that are to be updated. A single `UPDATE` statement will change all of the rows that match the `WHERE` clause. If a `WHERE` clause is not specified, it performs the `UPDATE` on all of the rows in the table.

To remove a row, you need a `WHERE` clause on an SQL `DELETE` statement. The `WHERE` clause determines which rows are to be deleted: