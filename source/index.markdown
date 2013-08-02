---
layout: page
title: "Introduction"
date: 2013-08-01 16:19
comments: true
sharing: true
footer: true
---
What?
-----
Doxecute is a document based database with basic SQL support such as INSERT, UPDATE, DELETE, and SELECT statement. No more complicated JavaScript filters, expressions, callback functions.
 
Because it is a document based database, you can insert or update your record using JSON format without even issuing CREATE TABLE statement. Instead of a table, you have a collection where you put all kinds of JSON you want to store. 

Doxecute support SQL from version 1.0. JavaScript will be supported from version 2.0.

Why?
----
Popular document based databases support JavaScript as a query language. However, we database guys are familiar with SQL. You can run ad-hoc queries simply by issuing a SQL statement. The SELECT statement supports WHERE, INNER JOIN, GROUP BY, and ORDER BY clause. 

Doxecute separates different kinds of JSON documents into different storage to reduce reading unnecessary data from disk while running your query on a specific kind of JSON document. 

How?
----
Doxecute is carefully designed to support transaction support on a document based database. It automatically categorizes JSON documents based on the similarity between documents to store different kinds of JSON documents on different storage. It results in reduced amount of I/O for running a query on a specific kind of JSON documents.  

Tutorial?
---------
To check out the tutorial deploying Doxecute on Amazon EC2 node, manipulating JSON documents with SQL, click [here](tutorials).
  
When?
-----
The first closed alpha testing starts on 15th Aug. To join the alpha testing, click [here](alpha-testing).
