#Database 
A _cursor_ is like a file handle that we can use to perform operations on the data stored in the database. Calling `cursor()` is very similar conceptually to calling `open()` when dealing with text files.

![A Database Cursor](https://www.py4e.com/images/cursor.svg)

A Database Cursor

Once we have the cursor, we can begin to execute commands on the contents of the database using the `execute()` method.

Database commands are expressed in a special language that has been standardized across many different database vendors to allow us to learn a single database language. The database language is called _Structured Query Language_ or _[[SQL]]_ for short.