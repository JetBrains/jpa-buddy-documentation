## Introduction

JPA Structure panel is responsible for everything related to DB configurations. To create a new DB connection, click on the “Plus” button and choose “DB Connection”. To use [Reverse Engineering](https://www.jpa-buddy.com/documentation/reverse-engineering/) and [Database Versioning](https://www.jpa-buddy.com/documentation/database-versioning/) features, the first thing you will need to do is create a database connection.

For now, JPA Buddy supports following databases:

- [PostgreSQL](https://www.postgresql.org/)
- [MSSQL](https://www.microsoft.com/sql-server/sql-server-2019?rtc=1)
- [MySQL](https://www.mysql.com/)
- [MariaDB](https://mariadb.org/)
- [Oracle](https://www.oracle.com/database/)
- [HSQLDB](http://hsqldb.org/)
- [H2](https://www.h2database.com/html/main.html)

![jpa_structure_db_connection](img/jpa_structure_db_connection.jpeg)

You can fill the required settings for the connection manually, but if your project contains data source settings in the *application.properties* file, JPA Buddy can get them and paste into corresponding fields automatically. Click on the “Detect Connections” button in the JPA Structure panel and the window will appear with filled fields.

As the IntelliJ IDEA Ultimate provides a large number of options for data sources configurations, there is no needs to create other connections to make JPA Buddy works. You can learn more about it on the corresponding [JetBrains documentation page](https://www.jetbrains.com/help/idea/data-sources-and-drivers-dialog.html). 

![ij_ultimate_data_sources](img/ij_ultimate_data_sources.jpeg)

For the IntelliJ IDEA Community edition, JPA Buddy offers a similar mechanism.

![ij_community_db_connection](img/ij_community_db_connection.jpeg)

## Non-Default Schema Connection

Some of the RDBMSs that JPA Buddy supports provide the possibility to create non-default schemas, but not all of them work well with JDBC. That’s why you can face with some known issues during diff generations, or reverse engineering. For now, these issues can only be solved with some workaround. Below are examples of connecting to non-default schemas for all databases supported by JPA Buddy.

<div class="note">
We show two screenshots for all the examples below: the first from the IntelliJ IDEA Community Edition, the second from the IntelliJ IDEA Ultimate Edition.
</div>

### PostgreSQL

The default PostgreSQL schema is “public”. For other schemes you need to specify desired schema name in the Connection params field via “currentSchema” parameter:

![ij_community_postgres](img/ij_community_postgres.jpeg)

![ij_ultimate_postgres](img/ij_ultimate_postgres.jpeg)

<div class="note">
For IntelliJ IDEA Ultimate, JPA Buddy provides connection creating for the required schema without any actions from you. For example, use a connection with the default schema (public) and try to create an entity from another schema. JPA Buddy will create and configure another DB connection with the parameters as described above.
</div>

### Microsoft SQL Server

The default Microsoft SQL Server schema is “dbo”. To connect to the non-default scheme in Microsoft SQL Server, you should follow the steps described below: 

1. Create a login: 

```sql
create login JohnDoe with password='saPassword1'
```

2. Create a user with default schema from which you want to create an entity: 

```sql
create user JohnDoe for login JohnDoe with default_schema = my_schema 
```

3. Give it owner rights:

```sql
exec sp_addrolemember 'db_owner', 'JohnDoe' 
```

4. Create a new connection with the newly created user’s credentials and add schema name in the database URL field

For JDBC the connection setup will look like this:

![ij_community_mssql_jdbc](img/ij_community_mssql_jdbc.jpeg)

![ij_ultimate_mssql_jdbc](img/ij_ultimate_mssql_jdbc.jpeg)

And for [JTDS](http://jtds.sourceforge.net/faq.html) like this:

![ij_community_mssql_jtdc](img/ij_community_mssql_jtdc.jpeg)

![ij_ultimate_mssql_jtdc](img/ij_ultimate_mssql_jtdc.jpeg)

### Oracle

In Oracle, schema, user and database are the same thing. Hence To connect to the non-default scheme you need to specify schema name in the user field.

For the connection via SID setup will look like this:

![ij_community_oracle_sid](img/ij_community_oracle_sid.jpeg)

![ij_ultimate_oracle_sid](img/ij_ultimate_oracle_sid.jpeg)

And for the connection via service name like this:

![ij_community_oracle_service](img/ij_community_oracle_service.jpeg)

![ij_ultimate_oracle_service](img/ij_ultimate_oracle_service.jpeg)

<div class="note">
Reverse engineering does not work for system tables located in the "SYS” schema.
</div>

### MySQL & MariaDB

To connect to the non-default scheme you need to specify schema name in the Database URL field:

![ij_community_mysql](img/ij_community_mysql.jpeg)

![ij_ultimate_mysql](img/ij_ultimate_mysql.jpeg)

## Database Drivers

Since IntelliJ IDEA CE doesn't allow configuring database drives, JPA Buddy is to the rescue! Open Tools -> JPA Buddy -> Database Drivers window. Here you can configure drivers for each supported RDBMS by selecting one of the proposed driver versions and adding additional files from your local machine.

![database_drivers](img/database_drivers.jpeg)
