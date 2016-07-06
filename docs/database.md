# Database

![][1]

Relational DBMS: [Oracle][2], [MySQL][3] <small>([download](http://dev.mysql.com/downloads/windows/installer/5.6.html))</small>, [SQLite][4]

Key-value Stores: [Redis][5], [Memcached][6]

Document stores: [MongoDB][7]

Graph: [Neo4j][8]

Wide column stores: [Cassandra][9], [HBase][10]

### Design and Modeling (a.k.a Data Definition)

#### 1\.1 Schema <sup id="fnref-2159-5"><a href="#fn-2159-5" rel="footnote">1</a></sup>

A database schema of a database system is its structure described in a formal language supported by the database management system (DBMS) and refers to the organization of data as a blueprint of how a database is constructed (divided into database tables in the case of Relational Databases). The formal definition of database schema is a set of formulas (sentences) called integrity constraints imposed on a database. These integrity constraints ensure compatibility between parts of the schema. All constraints are expressible in the same language. A database can be considered a structure in realization of the database language. The states of a created conceptual schema are transformed into an explicit mapping, the database schema. This describes how real world entities are modeled in the database.

![][11]

#### 1\.1.1 Type <sup id="fnref-2159-6"><a href="#fn-2159-6" rel="footnote">2</a></sup> <sup id="fnref-2159-7"><a href="#fn-2159-7" rel="footnote">3</a></sup>

In computer science and computer programming, a data type or simply type is a classification identifying one of various types of data, such as real, integer or Boolean, that determines the possible values for that type; the operations that can be done on values of that type; the meaning of the data; and the way values of that type can be stored.

`TEXT`, `INT`, `ENUM`, `TIMESTAMP`

#### 1.2 Cardinality (a.k.a Relationship) <sup id="fnref-2159-8"><a href="#fn-2159-8" rel="footnote">4</a></sup>

![][12] `Foreign key`, `Primary key`

#### 1\.2 Indexing

A database index is a data structure that improves the speed of data retrieval operations on a database table at the cost of additional writes and storage space to maintain the index data structure. Indexes are used to quickly locate data without having to search every row in a database table every time a database table is accessed. Indexes can be created using one or more columns of a database table, providing the basis for both rapid random lookups and efficient access of ordered records. Why Indexing is important?

![][13] `Indexing in MySQL` <sup id="fnref-2159-14"><a href="#fn-2159-14" rel="footnote">5</a></sup> Indexes are used to find rows with specific column values quickly. Without an index, MySQL must begin with the first row and then read through the entire table to find the relevant rows. The larger the table, the more this costs. If the table has an index for the columns in question, MySQL can quickly determine the position to seek to in the middle of the data file without having to look at all the data. This is much faster than reading every row sequentially. ![][14]

```sql
CREATE INDEX NameIndex ON Employee (name)
SELECT * FROM Employee WHERE name = 'Ashish'
```

### 2. Data Manipulation

#### Create - Read - Update - Delete <sup id="fnref-2159-4"><a href="#fn-2159-4" rel="footnote">6</a></sup>

![][15]

*   Create or add new entries
*   Read, retrieve, search, or view existing entries * Update or edit existing entries * Delete/deactivate existing entries

```sql
/* create */
CREATE TABLE Guests ( id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, firstname VARCHAR(30) NOT NULL, lastname VARCHAR(30) NOT NULL, email VARCHAR(50), reg_date TIMESTAMP )
/* create (insert) */
INSERT INTO Guests (firstname, lastname, email) VALUES ('John', 'Doe', 'john@example.com')
/* read */
SELECT * FROM Guests WHERE id=1 /* update */ UPDATE Guests SET lastname='Doe' WHERE id=1
/* delete */
DELETE FROM Guests WHERE id=1`
```

### 3. Data Retrieve & Transaction

#### 3.1 Data Retrieve

`SELECT`, `WHERE`, `FROM`, `LIMIT`, `JOIN`, `GROUP BY`, `HAVING`

Get user id, user name and number of post of this user

```sql
SELECT user.id, user.name, COUNT(post.*) AS posts
FROM user LEFT OUTER JOIN post ON post.owner_id=user.id GROUP BY user.id`
```

Select user who only order one time.

```sql
SELECT name, COUNT(name) AS c FROM orders GROUP BY name HAVING c = 1;
```

Calculate the longest period (in days) that the company has gone without a hiring or firing anyone.

```sql
SELECT x.date, MIN(y.date) y_date, DATEDIFF(MIN(y.date),x.date) days
FROM ( SELECT hiredate date FROM employees UNION SELECT terminationdate FROM employees ) x
JOIN ( SELECT hiredate date FROM employees UNION SELECT terminationdate FROM employees UNION SELECT CURDATE()) y
ON y.date > x.date GROUP BY x.date ORDER BY days DESC LIMIT 1;
```

**Data Retrieve API**

<table>
<tbody>
<tr>
<td>API</td>
<td>Description</td>
</tr>
<tr>
<td>get</td>
<td>get single item</td>
</tr>
<tr>
<td colspan="2">
<p>Get dog by id</p>
<pre>Dog.get(1)</pre>
</td>
</tr>
<tr>
<td>find</td>
<td>
<p>find items</p>
<p>@see&nbsp;<a href="https://docs.mongodb.com/manual/reference/method/db.collection.find/">collection.find()</a></p>
</td>
</tr>
<tr>
<td colspan="2">&nbsp;&nbsp;
<p>Find dog name "Max"</p>
<pre> Dog.find({"name": "Max"})</pre>
</td>
</tr>
<tr>
<td>sort</td>
<td>
<p>sort items</p>
<p>@see&nbsp;<a href="https://docs.mongodb.com/manual/reference/method/cursor.sort/">cursor.sort</a></p>
</td>
</tr>
<tr>
<td colspan="2">
<p>Get 10 older dogs</p>
<pre>Dog.find().sort("age", {limit: 10})</pre>
</td>
</tr>
<tr>
<td>aggregate</td>
<td>
<p>sum, min, max items</p>
<p>@see&nbsp;<a href="&nbsp;https://docs.mongodb.com/manual/reference/method/db.collection.aggregate/">collection.aggregate</a></p>
</td>
</tr>
<tr>
<td colspan="2">
<p>Get sum of dogs' age</p>
<pre>Dog.find().aggregate({
  "sum_age":  {
     $sum: "age"
   }
})</pre>
</td>
</tr>
</tbody>
</table>

#### 3.2 Transaction

A transaction symbolizes a unit of work performed within a database management system (or similar system) against a database, and treated in a coherent and reliable way independent of other transactions. A transaction generally represents any change in database. Example: Transfer 900$ from Account

`Bob` to `Alice` <sup id="fnref-2159-12"><a href="#fn-2159-12" rel="footnote">7</a></sup>

```sql
start transaction
select balance from Account where Account_Number='Bob';
select balance from Account where Account_Number='Alice';
update Account set balance=balance-900 here Account_Number='Bob' ;
update Account set balance=balance+900 here Account_Number='Alice' ;
commit; //if all sql queries succed rollback; //if any of Sql queries failed or error
```

**ACID Properties** <sup id="fnref-2159-13"><a href="#fn-2159-13" rel="footnote">8</a></sup>

In computer science, ACID (Atomicity, Consistency, Isolation, Durability) is a set of properties that guarantee that database transactions are processed reliably. In the context of databases, a single logical operation on the data is called a transaction.

For example, a transfer of funds from one bank account to another, even involving multiple changes such as debiting one account and crediting another, is a single transaction. ![][16]

### 4\. Backup and Restore <sup id="fnref-2159-3"><a href="#fn-2159-3" rel="footnote">9</a></sup>

Sometimes it is desired to bring a database back to a previous state (for many reasons, e.g., cases when the database is found corrupted due to a software error, or if it has been updated with erroneous data). To achieve this a backup operation is done occasionally or continuously, where each desired database state (i.e., the values of its data and their embedding in database's data structures) is kept within dedicated backup files (many techniques exist to do this effectively). When this state is needed, i.e., when it is decided by a database administrator to bring the database back to this state (e.g., by specifying this state by a desired point in time when the database was in this state), these files are utilized to restore that state.

### 5\. Migration <sup id="fnref-2159-11"><a href="#fn-2159-11" rel="footnote">10</a></sup>

In software engineering, schema migration (also database migration, database change management) refers to the management of incremental, reversible changes to relational database schemas. A schema migration is performed on a database whenever it is necessary to update or revert that database's schema to some newer or older version. Example: Android Migration by droid-migrate

<sup id="fnref-2159-15"><a href="#fn-2159-15" rel="footnote">11</a></sup>

```shell
droid-migrate init -d my_database droid-migrate generate up droid-migrate generate down
```

Example: Database Seeding with Laravel <sup id="fnref-2159-16"><a href="#fn-2159-16" rel="footnote">12</a></sup> ```shell php artisan migrate:make seed_roles_table php artisan migrate:make seed_users_table php artisan migrate:reset php artisan db:seed ```

### 6\. Active record pattern | Object-Relational Mapping (ORM) <sup id="fnref-2159-1"><a href="#fn-2159-1" rel="footnote">13</a></sup>

Object-relational mapping in computer science is a programming technique for converting data between incompatible type systems in object-oriented programming languages. This creates, in effect, a "virtual object database" that can be used from within the programming language. There are both free and commercial packages available that perform object-relational mapping, although some programmers opt to create their own ORM tools.

![][17] **Example**

`php` <sup id="fnref-2159-9"><a href="#fn-2159-9" rel="footnote">14</a></sup>

```php
$employee = new Employee(); $employee->setName("Joe"); $employee->save();
[/code]

`Android` <sup id="fnref-2159-10"><a href="#fn-2159-10" rel="footnote">15</a></sup>

```java
public class User {
  @DatabaseField(id = true) String username;
  @DatabaseField String password;
  @DatabaseField String email;
  @DatabaseField String alias;
  public User() {} }
```

**Implementations**

* Android: [ormlite-android][18] <sup id="fnref-2159-2"><a href="#fn-2159-2" rel="footnote">16</a></sup>
* PHP: [Eloquent][19]

<li id="fn-2159-5">
  <a href="https://en.wikipedia.org/wiki/Database_schema">Database schema</a> <a href="#fnref-2159-5" rev="footnote">↩</a>
</li>
<li id="fn-2159-6">
  <a href="https://en.wikipedia.org/wiki/Data_type">Data type</a> <a href="#fnref-2159-6" rev="footnote">↩</a>
</li>
<li id="fn-2159-7">
  <a href="http://www.w3schools.com/sql/sql_datatypes.asp">SQL Data Types for Various DBs</a> <a href="#fnref-2159-7" rev="footnote">↩</a>
</li>
<li id="fn-2159-8">
  <a href="https://en.wikipedia.org/wiki/Cardinality_(data_modeling)">Cardinality (data modeling)</a> <a href="#fnref-2159-8" rev="footnote">↩</a>
</li>
<li id="fn-2159-14">
  <a href="https://dev.mysql.com/doc/refman/5.0/en/mysql-indexes.html">How MySQL Uses Indexes</a> <a href="#fnref-2159-14" rev="footnote">↩</a>
</li>
<li id="fn-2159-4">
  <a href="https://en.wikipedia.org/wiki/Create,_read,_update_and_delete">Create, read, update and delete</a> <a href="#fnref-2159-4" rev="footnote">↩</a>
</li>
<li id="fn-2159-12">
  <a href="http://javarevisited.blogspot.com/2011/11/database-transaction-tutorial-example.html">Database Transaction Tutorial in SQL with Example for Beginners</a> <a href="#fnref-2159-12" rev="footnote">↩</a>
</li>
<li id="fn-2159-13">
  <a href="https://en.wikipedia.org/wiki/ACID">ACID</a> <a href="#fnref-2159-13" rev="footnote">↩</a>
</li>
<li id="fn-2159-3">
  <a href="https://en.wikipedia.org/wiki/Database">Database</a> <a href="#fnref-2159-3" rev="footnote">↩</a>
</li>
<li id="fn-2159-11">
  <a href="https://en.wikipedia.org/wiki/Schema_migration">Schema migration</a> <a href="#fnref-2159-11" rev="footnote">↩</a>
</li>
<li id="fn-2159-15">
  <a href="https://github.com/aglover/droid-migrate">aglover/droid-migrate</a> <a href="#fnref-2159-15" rev="footnote">↩</a>
</li>
<li id="fn-2159-16">
  <a href="http://laravelbook.com/laravel-database-seeding/">Database Seeding with Laravel</a> <a href="#fnref-2159-16" rev="footnote">↩</a>
</li>
<li id="fn-2159-1">
  <a href="https://en.wikipedia.org/wiki/Object-relational_mapping">Object-relational mapping</a> <a href="#fnref-2159-1" rev="footnote">↩</a>
</li>
<li id="fn-2159-9">
  <a href="http://www.slideshare.net/rob_knight/object-relational-mapping-in-php">Object Relational Mapping in PHP</a> <a href="#fnref-2159-9" rev="footnote">↩</a>
</li>
<li id="fn-2159-10">
  <a href="http://www.b-fil.com/blog/2011/01/20/android-repository-ormlite-existing-sqlite-db">An Android Repository with ORMLite (Using an existing SQLite database)</a> <a href="#fnref-2159-10" rev="footnote">↩</a>
</li>
<li id="fn-2159-2">
  <a href="http://www.sitepoint.com/5-best-android-orms/">5 of the Best Android ORMs</a> <a href="#fnref-2159-2" rev="footnote">↩</a></fn></footnotes></p></p></p></p></p></p></p></p></p> <p>
  </p>

[1]: http://www.netsolutionsindia.com/blog/wp-content/uploads/2014/07/Mongodb-Nosql.jpg
[2]: http://www.oracle.com/index.html
[3]: http://www.mysql.com/
[4]: http://sqlite.org/
[5]: http://redis.io/
[6]: http://memcached.org/
[7]: https://www.mongodb.org/
[8]: http://neo4j.com/
[9]: http://cassandra.apache.org/
[10]: http://hbase.apache.org/
[11]: http://i.imgur.com/uEuEdPv.png
[12]: http://i.stack.imgur.com/Z6tTL.gif
[13]: http://cdn.guru99.com/images/Index.jpg
[14]: http://image.slidesharecdn.com/mysqlindex-091118043907-phpapp02/95/indexing-the-mysql-index-key-to-performance-tuning-17-638.jpg?cb=1357187786
[15]: https://www.pingidentity.com/content/dam/pic/images/glyphs/22_Capabilities_UserProvisioningDeprovisioning_b3_r.png
[16]: https://lh6.googleusercontent.com/y9qoNuNGdd9COo0twXUrefyy6ZKmRs3iFPIMKpJ7UZRXqX7Bc5lXFutzaKLFf0ZPD4Sl7uDj1CvQoCh2kOd9ZNkKokw_-xZ-QUwX8mWkKDexO0I58Oo
[17]: https://symfony-docs-chs.readthedocs.org/en/latest/_images/doctrine_image_1.png
[18]: https://github.com/j256/ormlite-android
[19]: http://laravel.com/docs/4.2/eloquent
