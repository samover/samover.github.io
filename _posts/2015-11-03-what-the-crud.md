---
layout: post
title: CRUDe databases
---

![crudities](https://www.colourbox.com/preview/2696467-crude-vegetables-on-a-white-background.jpg)

CRUD stands for 'create, read, update and delete'. These four functions are the bare minimum that a database user interface needs to provide. Imagine creating a Bookmark Manager. It should at least allow the user to add a bookmark, show the saved bookmarks, update stored bookmarks and delete unwanted ones.

The four CRUD functions also form the backbone of persistent storage solutions. An example of thes are relational database applications like SQL. 

CRUD | SQL 
-----| ---
CREATE | INSERT
READ  | SELECT
UPDATE | UPDATE
DELETE | DELETE

SQL stands for 'Structured Query Language'. This means that it is a tool with language rules that allow a user to perform a query or read command on a database. It further allows to create a table into a database, insert, update and delete data. Here are some examples on how to perform SQL operations on a database: 

```
CREATE TABLE STUDENTS ( ID SERIAL PRIMARY KEY, NAME (VARCHAR(80) );

INSERT INTO STUDENTS (NAME) VALUES ('LUKE SKYWALKER');

UPDATE STUDENTS SET NAME = 'DARTH VADER' WHERE NAME = 'LUKE SKYWALKER';

DELETE FROM STUDENTS WEHRE NAME = 'DARTH VADER';
```

