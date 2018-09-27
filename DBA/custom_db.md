## Custom database support
Custom database can be created for MySQL, PostgreSQL and MongoDB.

### MySQL
Write your sql script to create database(s) and the necessary table(s). Also, populate the table(s) with the necessary data.

Example
```sql
DROP DATABASE IF EXISTS `<database-name>`;
CREATE DATABASE `<database-name>`;
USE `<database-name>`;

# Create table(s) and populate them with data

```

### PostgreSQL
In PostgreSQL, database name will be `DoSelect`. You need to write sql script to create table(s) and populate them with data.

### MongoDB
In Mongodb, database name will be `test` and collection name will be `doselect`. You need to add the json data which will be imported to `doselect` collection.

Example
```json
{ "item": "journal", "qty": 25, "size": { "h": 14, "w": 21, "uom": "cm" }, "status": "A" }
{ "item": "notebook", "qty": 50, "size": { "h": 8.5, "w": 11, "uom": "in" }, "status": "A" }
{ "item": "paper", "qty": 100, "size": { "h": 8.5, "w": 11, "uom": "in" }, "status": "D" }
{ "item": "planner", "qty": 75, "size": { "h": 22.85, "w": 30, "uom": "cm" }, "status": "D" }
{ "item": "postcard", "qty": 45, "size": { "h": 10, "w": 15.25, "uom": "cm" }, "status": "A" }
```
