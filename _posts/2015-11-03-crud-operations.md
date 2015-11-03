---
layout: post
title: CRUDe databases
---

![crudities](https://www.colourbox.com/preview/2696467-crude-vegetables-on-a-white-background.jpg)

CRUD stands for 'create, read, update and delete'. These four functions are the bare minimum that a database user interface needs to provide. Imagine creating a Bookmark Manager. It should at least allow the user to add a bookmark, show the saved bookmarks, update stored bookmarks and delete unwanted ones.

The four CRUD functions also form the backbone of persistent storage solutions. An example of these are relational database applications like SQL. 

CREATE => INSERT

READ => SELECT

UPDATE => UPDATE

DELETE => DELETE

SQL stands for 'Structured Query Language'. This means that it is a tool with language rules that allow a user to perform a query or read command on a database. First a table has to be created in a database: 

```
CREATE TABLE students ( id SERIAL PRIMARY KEY, name (VARCHAR(80) );
```

Then SQL allows one to insert, update, select and delete data from a table. Here are some examples on how to perform SQL operations on a database: 

```

INSERT INTO students (name) VALUES ('LUKE SKYWALKER');

UPDATE students SET NAME = 'DARTH VADER' WHERE name = 'LUKE SKYWALKER';

DELETE FROM students WHERE name = 'DARTH VADER';

SELECT * FROM students
```

