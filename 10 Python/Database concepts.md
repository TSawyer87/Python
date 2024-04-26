#Database 
The primary data structures in a database are tables, rows, and columns
Their technical terms are:

Relation  = (Table)
Tuple       = (Row)
Attribute  = (Column)

![Relational Databases](https://www.py4e.com/images/relational.svg)


A relational database is made up of tables, rows, and columns. The columns generally have a type such as text, numeric, or date data. When we create a table, we indicate the names and types of the columns:

```
CREATE TABLE Track (title TEXT, plays INTEGER)
```

To insert a row into a table, we use the SQL `INSERT` command:

```
INSERT INTO Track (title, plays) VALUES ('My Way', 15)
```

The `INSERT` statement specifies the table name, then a list of the fields/columns that you would like to set in the new row, and then the keyword `VALUES` and a list of corresponding values for each of the fields.