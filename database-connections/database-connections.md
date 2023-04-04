## Introduction

JPA Structure panel is responsible for everything related to DB configurations. To create a new DB connection, click on the "Plus" button and choose "DB Connection". To use [Reverse Engineering](https://www.jpa-buddy.com/documentation/reverse-engineering/) and [Database Versioning](https://www.jpa-buddy.com/documentation/database-versioning/) features, the first thing you will need to do is create a database connection.

For now, JPA Buddy supports the following databases:

* <a href="https://www.postgresql.org/" target="_blank">PostgreSQL</a>
* <a href="https://www.microsoft.com/sql-server/sql-server-2019?rtc=1" target="_blank">MSSQL</a>
* <a href="https://www.mysql.com/" target="_blank">MySQL</a>
* <a href="https://mariadb.org/" target="_blank">MariaDB</a>
* <a href="https://www.oracle.com/database/" target="_blank">Oracle</a>
* <a href="http://hsqldb.org/" target="_blank">HSQLDB</a>
* <a href="https://www.h2database.com/html/main.html" target="_blank">H2</a>
* <a href="https://www.ibm.com/analytics/db2" target="_blank">IBM Db2</a>

![jpa-structure-db-connection](img/jpa-structure-db-connection.png)

You can fill the required settings for the connection manually, but if your project contains data source settings in the *application.properties* or *application.yaml* file, JPA Buddy can get them and paste into corresponding fields automatically. Click on the "Detect Connections" button in the JPA Structure tab and the window will appear with filled fields.

As the IntelliJ IDEA Ultimate provides numerous options for data sources configurations, there is no needs to create other connections to make JPA Buddy works. You can learn more about it on the corresponding <a href="https://www.jetbrains.com/help/idea/data-sources-and-drivers-dialog.html" target="_blank">JetBrains documentation page</a>.

![ij-ultimate-data-sources](img/ij-ultimate-data-sources.jpeg)

For the IntelliJ IDEA Community edition, JPA Buddy offers a similar mechanism.

![ij-community-db-connection](img/ij-community-db-connection.jpeg)

## Non-Default Schema Connection

Some RDBMSs that JPA Buddy supports provide the possibility to create non-default schemas, but not all of them work well with JDBC. That’s why you can face with some known issues during diff generations, or reverse engineering. For now, these issues can only be solved with some workaround. Below are examples of connecting to non-default schemas for all databases supported by JPA Buddy.

<div class="note">
We show two screenshots for all the examples below: the first from the IntelliJ IDEA Community Edition, the second from the IntelliJ IDEA Ultimate Edition.
</div>

### PostgreSQL

The default PostgreSQL schema is "public". For other schemes you need to specify desired schema name in the Connection params field via "currentSchema" parameter:

![ij-community-postgres](img/ij-community-postgres.jpeg)

![ij-ultimate-postgres](img/ij-ultimate-postgres.jpeg)

<div class="note">
For IntelliJ IDEA Ultimate, JPA Buddy provides connection creating for the required schema without any actions from you. For example, use a connection with the default schema (public) and try to create an entity from another schema. JPA Buddy will create and configure another DB connection with the parameters as described above.
</div>

### Microsoft SQL Server

The default Microsoft SQL Server schema is "dbo". To connect to the non-default scheme in Microsoft SQL Server, you should follow the steps described below:

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

![ij-community-mssql-jdbc](img/ij-community-mssql-jdbc.jpeg)

![ij-ultimate-mssql-jdbc](img/ij-ultimate-mssql-jdbc.jpeg)

And for <a href="http://jtds.sourceforge.net/faq.html" target="_blank">JTDS</a> like this:

![ij-community-mssql-jtds](img/ij-community-mssql-jtds.jpeg)

![ij-ultimate-mssql-jtds](img/ij-ultimate-mssql-jtds.jpeg)

### Oracle

In Oracle, schema, user and database are the same thing. Hence, to connect to the non-default scheme you need to specify schema name in the user field.

For the connection via SID setup will look like this:

![ij-community-oracle-sid](img/ij-community-oracle-sid.jpeg)

![ij-ultimate-oracle-sid](img/ij-ultimate-oracle-sid.jpeg)

And for the connection via service name like this:

![ij-community-oracle-service](img/ij-community-oracle-service.jpeg)

![ij-ultimate-oracle-service](img/ij-ultimate-oracle-service.jpeg)

<div class="note">
Reverse engineering does not work for system tables located in the "SYS" schema.
</div>

### MySQL & MariaDB

To connect to the non-default scheme you need to specify schema name in the Database URL field:

![ij-community-mysql](img/ij-community-mysql.jpeg)

![ij-ultimate-mysql](img/ij-ultimate-mysql.jpeg)

## Database Drivers

Since IntelliJ IDEA CE doesn't allow configuring database drives, JPA Buddy is to the rescue! Open Tools -> JPA Buddy -> Database Drivers window. Here you can configure drivers for each supported RDBMS by selecting one of the proposed driver versions and adding additional files from your local machine.

![database-drivers](img/database-drivers.jpeg)

## How to connect via SSH

JPA Buddy uses a different mechanism from what IntelliJ IDEA uses to connect to the database. So, JPA Buddy can't use the SSH tunnel configured in IntelliJ IDEA. To make Buddy works properly in this case, you need to establish an SSH tunnel on the system level. Here is <a href="https://www.linode.com/docs/guides/create-an-ssh-tunnel-for-mysql-remote-access/" target="_blank">an example</a> of how you can do it.
