# <center>Database</center>


how do we structure application data?

In memory        | Durable storage
-----------------|------------------
simple variables:|flat files on disk
int, string...etc|text, xml, json   
Data structure:  |Database:
lists,           | key-value store
dictionaries,    | navigational DB
objects          | relational DB
`temporary`      | `persistent`
___


Python vs SQL:

| SQL clauses+aggregations      | python list operations     |
| :---------------------------- | :------------------------- |
| count(*)                      | len(results)               |
| limit 100 offset 10           | results[10:110]            |
| order by column   | sorted(results,key=lambda x:x[column]) |
___

to run PostgreSQL form terminal type `psql`
but you will get this error

`psql: FATAL:  role "username" is not permitted to log in`

so you need to login to login as postgres user:
``` bash
sudo -u postgres -i #then
psql
```
then you can write sql statements or psql commands.

to list all tables:

* PostgreSQL: `\dt` (`\d table_name` to describe a tabe)
* MySQL: show tables and describe table_name
* SQLite: .tables and .schema table_name

to list all databases `\l`

to connect to a database `\c db_name` or you can write directly `psql db_name`

to get help with sql command type `\h`

to get help with psql command type `\?`

or `\q` to exit.

___

## Normalized Design

* every row should have the same number of columns.
* there is a unique  key, and everything in a row says something about the key.
* facts that don't related to the key belong in different table.
* tables shouldn't imply relationships that don't exist.

___
## sql

to create table
``` sql
create Table Collage
(
    name string primary key,
    state char(2),
    enrollment integer reference course(Id)
);  
```
or you can this line at last ``` primary key (name, state,...)```
to create table using another table:
``` sql
CREATE TABLE new_table_name AS
    SELECT column1, column2,...
    FROM existing_table_name
    WHERE ....;
```

to add row to the table
``` sql
INSERT INTO table_name
VALUES (42, 'staff');
```

if the new values aren't in the same order as the table's columns or you want to leave some columns null:
``` sql
INSERT INTO table_name (col2, col1)
VALUES ('staff', 42);
```

some sql commands

``` sql
-- line comment  
SELECT max(name) FROM animals;
SELECT * FROM animals LIMIT 10;
SELECT * FROM animals WHERE species = 'lama' ORDER BY birthdate DESC;
SELECT name, birthdate FROM animals ORDER BY name LIMIT 10 OFFSET 20;
SELECT species, min(birthdate) FROM animals GROUP BY species;
SELECT name, count(*) as num FROM animals
GROUP BY name
ORDER BY num DESC
LIMIT 5
```



___

some databases APIs
Database system  | DB-API module
-----------------|------------------
SQLite           | sqlite3
PostgreSQL       | psycopg2   
MySQL            | mysql.connector


example of python DB-API
```python
import sqlite3
con = sqlite3.connect('Cookies')
cursor = conn.cursor()
cursor.execute('select host_key form Cookies limit 10')
results = cursor.fetchall()
print(results)
conn.close()
```

for PostgreSQL
``` python
import psycopg2
pg = psycopg2.connect("dbname=somedb")
c = pg.cursor()
c.execute("insert into names values ('ahmed')")
pg.commit()
```

Bobby table:
is a way of hacking the database ex:-

write in a text form ') delete from user; --

this may delete all users in the database.

to curing Bobby tables ex:-
``` python
plant = "pumpkin"
c = conn.cursor()
c.execute("inser into garden values (%s)", (plant,))
```
Spammy Tables: is another way of hacking the database ex:-

put this into a text form
``` html
<script>
setTimeout(function() {
    var tt = document.getElementById('content');
    tt.value = "<h2 style='color: #FF6699; font-family: Comic Sans MS'>Spam, spam, spam, spam,<br>Wonderful spam, glorious spam!</h2>";
    tt.form.submit();
}, 2500);
</script>
```

to clean the database form this script first we need to replace it with other value
``` sql
update table_name
    set col_name = value
    where content like '%spam%';
```
then delete the records that we have changed
``` sql
delete from table_name
    where restriction;
```





### ORM: object relation mapper
An object-relational mapper (ORM) is a code library that automates the transfer of data stored in relational databases tables into objects that are more commonly used in application code.

one of the most commonly user ORMs is sqlalchemy.

#### creating database with sqlalchemy:

to install sqlalchemy
```
pip install sqlalchemy
```

1. configuration
2. class: is the oop representation of a table as a python class
    * make a class and extend the Base class that we created

    * inside this class we will add all the code for table and mapper
    code.

3. table:

    * inside each class we must create a table representation

    * we user special variable `__tablename__` to refer to our table.

    * ex:- __tablename__ = 'some_table'

    * make table name lower case with under score for spaces

4. mapper: maps python objects to columns in our database

    * syntax: col_name = Column(attributes,...)

    * the common attributes:
        * String(250)
        * Integer
        * relationship(Class)
        * nullable = False
        * primary_key = True
        * ForignKey('some_table.id')
