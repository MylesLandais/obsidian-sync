Question
Tables with lots of columns, few with any particular rows

Attribute tables that contain tupled data
(foreign_key, attribute name, attribue value)

Dumping structured data such as json or xml as strings into database. 

Does your schema have a large number for many-to-many join tables. or self-referential tables, a foreign key that referse to a different row in the same table (tree-like structure)

Making schema changes to properly represent incoming data.

Are you reaching the write-limitations of your database.

*Document Databases and BigTable*
The bigtable paper written by google spawned a number of additional implementations such as HBase or Cassandra.

*Document Databases* corresponds to a document, typically a tree of objects containing attribues of objects that are changing or not known in advance. 

*Graph Databases*

