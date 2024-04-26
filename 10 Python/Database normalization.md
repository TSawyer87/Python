#Database 
Database normalization is the process of structuring a relational database in accordance with a series of so-called normal forms in order to reduce data redundancy and improve data integrity. It was first proposed by British computer scientist Edgar F. Codd as part of his relational model.

Normalization entails organizing the columns (attributes) and tables (relations) of a database to ensure that their dependencies are properly enforced by database integrity constraints. It is accomplished by applying some formal rules either by a process of synthesis (creating a new database design) or decomposition (improving an existing database design). 

## Objectives

A basic objective of the first normal form defined by Codd in 1970 was to permit data to be queried and manipulated using a "universal data sub-language" grounded in [first-order logic](https://en.wikipedia.org/wiki/First-order_logic "First-order logic").[[1]](https://en.wikipedia.org/wiki/Database_normalization#cite_note-1) An example of such a language is [SQL](https://en.wikipedia.org/wiki/SQL "SQL"), though it is one that Codd regarded as seriously flawed.[[2]](https://en.wikipedia.org/wiki/Database_normalization#cite_note-2)

The objectives of normalisation beyond 1NF (first normal form) were stated by Codd as:

> 1. To free the collection of relations from undesirable insertion, update and deletion dependencies.
> 2. To reduce the need for restructuring the collection of relations, as new types of data are introduced, and thus increase the life span of application programs.
> 3. To make the relational model more informative to users.
> 4. To make the collection of relations neutral to the query statistics, where these statistics are liable to change as time goes by.