# PostgresSQL Notes

This [basic tutorial](https://www.postgresqltutorial.com) is very helpful.

## Installation
```shell
brew install postgresql
```

Homebrew installed executables here: '/usr/local/Cellar/postgresql/12.3_1/bin'

## Basic Navigation

- Connect to a database: \connect dbname;
- List databases: \l
- List tables: \dt

## Creating a Database

Create a new databse under postgres owner:
```sql
CREATE DATABASE dbname
WITH OWNER=postgres;
```

## SELECT Statements

- || is a concatenation operator

	example: SELECT first_name || ' ' || last_name
	will output the first and last name into one column, separated by a space


- LENGTH(attr) provides the length of a string