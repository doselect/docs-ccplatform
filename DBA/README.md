## SQL problems
These kind of problems help to assess proficiency of developers in writing SQL queries for data extraction, database admininstration, etc

## Databases
- MySQL
- Oracle (only `SELECT` queries)
- PostgreSQL
- MongoDB

The environment already contains a database named `DoSelect` which is a clone of [Chinook database](https://chinookdatabase.codeplex.com/wikipage?title=Chinook_Schema&referringTitle=Documentation). You can create problems testing `SELECT` queries using the same database.

## Custom database
If you want to create a custom database for the problem, check the [Adding a custom database](custom_db.md) doc.

## Evaluation
For `SELECT` type problems, output of candidate's SQL queries is compared with the output of the expected queries.

And for `DDL/DML` type problems, evaluation can be done using `bash` or `python` scripts. Check the [sample problem](sample.md) for more clarity.
