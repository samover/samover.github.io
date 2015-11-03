---
layout: post
title: Persistent storage: databases 
---

Persistent data storage can simply be defined as the storage of data "long-term". That is to say, it outlives the process or processes that created it.

The most common type of database is relational, one that is constructed from tables where each column within the table represents a single piece of data and each row represents a unique entity. These databases often use Structured Query Language (SQL) to build and query the data they contain. This approach differs to persistent storage using a filesystem as it defines the relationships between data instances rather than just containing them.

While relational databases are the most common they are not always the tool of choice for storing data, particularly when the format of the data may change. As a result there is a plethora of solutions often referred to under the catchall term NoSQL that includes technologies such as Document-Oriented Databases. These allow each data instance to be a wholly unique object and to be stored together with its relationship information as shown in the diagram below.

![SQL-NoSQL](https://kvaes.files.wordpress.com/2015/01/1401269083847.jpg?w=788)

In order to make the most of the data that has been stored a Relational Database Management System (RDBMS) is required and while there are a large number of these available the most popular currently in use are:

SQLite - A powerful embedded RDBMS

MySQL - The most popular RDBMS

PostgreSQL - An open-source, objective RDBMS

Of these PostgreSQL provides a happy medium between relational databases and NoSQL databases as it directly supports object oriented behaviour both in its structure and querying abilities. Making it a powerful tool for any application.
