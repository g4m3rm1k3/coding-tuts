# STRUCTRED QUERY LANGAUGE
## Query
what is a query
```sql
SELECT * FROM USER
```
A query is a question, above is an sql query
### degree
The degree of the colums are the titles of the data stored 

### column
the columns store the tables attributes
### constraint
the constraint/domain of the data is the allowable values in the field

### rows
rows contain a tuple of data

### cardinality
the collection of rows/tuples of data

### Working with Postgresql from command line
`psql -U postgres` to connect to the server just enter your password
`\conninfo` to get the connection data
`CREATE TABLE test_table ();` will create a table called test table
`\dt` will list the table relations
```sql
           List of relations
 Schema |    Name    | Type  |  Owner
--------+------------+-------+----------
 public | test_table | table | postgres
```

## Let's get querying
![[Pasted image 20230813143745.png]]

DCL
: data control language
DDL
: data definition language
DQL
: data query language
DML
: data modification language

to rename a colum
```sql
SELECT column as '<new name>'
```
```sql
SELECT emp_no as "Employee #", birth_date as "Birthday", first_name AS "First Name" from "public"."employees"
```

### Concat
single quotes are for characters
```sql
SELECT CONCAT(emp_no, ' ', title) from "public"."titles"
```
![[Pasted image 20230813181510.png]]
```sql
SELECT CONCAT(emp_no, ' is a ', title) from "public"."titles"
```
![[Pasted image 20230813181544.png]]
```sql
SELECT CONCAT(emp_no, ' is a ', title) As "Employee Title" from "public"."titles"

```
see how the title has changed from concat
![[Pasted image 20230813181658.png]]
```sql
SELECT CONCAT (first_name, ' ', last_name) AS "Full Name" from "public"."employees";
```
![[Pasted image 20230813181908.png]]
