## Introduction

JPA Buddy allows you to selectively pick tables/views and fields from your database and get them as JPA entities:

<div class="youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/Lr_zg_uhWW4" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<div class="note">
  The first thing you need to do to use the reverse engineering features is to create a DB connection. The correct way to do it and possible issues are described in the separate <a href="https://www.jpa-buddy.com/documentation/database-connections/" target="_blank">documentation</a>. Check it out to learn more. 
</div>

In the **IntelliJ IDEA Community Edition**, you can generate entities from DB via:

* JPA Structure (1) using plus button;
* Project Panel (2) using right-click.

In the **IntelliJ IDEA Ultimate Edition**, you can generate entities from DB via:

* JPA Structure (1) using plus button;
* Project Panel (2) using right-click;
* Database panel (3) using right-click;

![entities-from-db-action](img/entities-from-db-action.png)

## Entities from DB Wizard

![entities-from-db](img/entities-from-db.png)

### Configuration

The menu on the top of the window allows you to configure:

* <a href="https://www.jpa-buddy.com/documentation/database-connections/" target="_blank">DB connection</a>
* <a href="https://www.jpa-buddy.com/documentation/reverse-engineering/#working-with-remote-db" target="_blank">DB schema cache</a>
* Source root and package where the generated entities will be saved
* Whether indexes and constraints need to be migrated
* Whether schema name should be specified in the `@Table` annotation

Also, from the "Other settings" drop-down list, you can move to the <a href="https://www.jpa-buddy.com/documentation/entity-designer/#settings-1" target="_blank">entity declaration</a> and <a href="https://www.jpa-buddy.com/documentation/reverse-engineering/#settings" target="_blank">reverse engineering</a> settings.

### Mapped Relations, Tables and Views

On the left side of the window, you can see:

* Mapped Relations - tables and views mapped to JPA entities
* Tables - tables that exist in the DB but are not mapped to entities
* Views - views that exist in the DB but are not mapped to entities

After selecting any element from the tree, a panel for migrating attributes from columns will appear. Also, you will be able to define a class name in the corresponding field.

### Migrating Attributes

The main part of the window allows you to configure everything related to attributes. You can choose which attributes you want to add and change all their params, except "Column Name". Mapping type and attribute/converter/hibernate types are represented as drop-down lists.

All attributes are divided into 3 categories:

* Migrated Columns - columns that are already present in the entity (available only for mapped relations)
* Columns - new columns that are not yet mapped in the entity or parent @MappedSuperclass
* References - optional associations that are not represented as a column in the observed table

#### Parent Entities

JPA Buddy offers the ability to define a parent entity by selecting a class annotated with `@MappedSuperclass` from the "Parent" drop-down box. This allows the generated entities to extend from the parent class and automatically inherit all attributes that have the same name and type.

In cases where the column name in the `@MappedSuperclass` doesn't match the child entity's table, we can still inherit the attribute using the `@AttributeOverride` annotation. By simply selecting the attribute name and choosing the one to override, JPA Buddy assists in managing the inheritance.

![attribute-override.png](img/attribute-override.png)

During entity generation, JPA Buddy alerts us if any inherited attributes from the `@MappedSuperclass` are missing in the database, to align the model with the database access the "Generate DDL by Entities" action in the JPA Structure menu and select the "Existing DB update" option.

<div class="youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/a-K-53_8Pcg" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

#### Creating Enums

For attributes matching the `String` or `Integer` type, you can change the mapping type from Basic to Enum, and JPA Buddy will create the corresponding Enum class in the project. You need to fill the enum with proper values manually.

#### Dealing With Unknown Types

For some SQL types, there is no exact match to Java classes. In this case, JPA Buddy does not set the type to prevent generating non-working code. You will need to choose the attribute type yourself. You can also configure default type mappings for each DBMS in the [settings](#type-mappings).

If you have the <a href="https://github.com/vladmihalcea/hibernate-types" target="_blank">HibernateTypes</a> library in your project dependencies list, JPA Buddy can automatically suggest suitable types from the library for the unsupported SQL types during reverse engineering:

<div class="youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/uBjxdAmVDuI" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

#### // TODO Comments

If you want to postpone an attribute creation for specific columns, you can choose `//todo comment` as the mapping type. JPA Buddy will generate the //todo comment with the corresponding quick-fix actions depending on the column type. You can call these actions via ⌘+B (Ctrl+B) shortcut:

* For known basic and association types you can:
  * Uncomment as is
  * Remove column mapping
* For unknown column type you can:
  * Define target Java type
  * Uncomment as is
  * Remove column mapping

Here is the example of generated //todo comment for the attribute with unknown column type:

```java
/*
  TODO [JPA Buddy] create field to map the 'description' column
   Available actions: Define target Java type | Uncomment as is | Remove column mapping
  @Column(name = "description", columnDefinition = "jsonb")
  private java.lang.Object description;
*/
```

After calling the "Define target Java type" action, the following window will appear:

![mapping-java-type](img/mapping-java-type.png)

JPA Buddy will remember data mappings for the subsequent reverse engineering actions. You can always change them in the [settings](#type-mappings).

### Map DB Views to JPA Entities

JPA Buddy follows all best practices providing the most efficient mapping for DB views while reverse engineering:

1. As DB views do not have a primary key, JPA Buddy allows you to select a field or a set of fields to use as the identifier for the target entity.
2. Most DB views are immutable. So, JPA Buddy adds `@Immutable` annotation to the entity and generates getters only. This helps to improve application performance.
3. JPA Buddy generates only a no-arg protected constructor for entities that are mapped to a DB view, as per JPA specifications, which prevents developers from creating a new instance of such entities in the business logic code

<div class="youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/QUXgJSkBJO8" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Reverse Engineering Columns

Some developers prefer the DB-first application development approach. First, they add columns directly to the database and then update the JPA model. JPA Buddy can automate this process. To add attributes to the existing entity, choose From DB action in JPA Designer (1), Editor Toolbar (2) or from IntelliJ IDEA's "Generate" menu (3):

![reverse-engineering-columns-action](img/reverse-engineering-columns-action.png)

After that, the Reverse Engineering Columns wizard will appear:

![reverse-engineering-columns](img/reverse-engineering-columns.png)

The attributes migration flow here is identical to what was described in the [Entities from DB wizard](#migrating-attributes) section.

## Smart References Detection

JPA Buddy deeply understands your model. In certain cases, it's able to properly detect cardinality: `@`OneToOne, `@`OneToMany, `@`ManyToOne, `@`ManyToMany. The coolest thing is that JPA Buddy can show references even when there are no corresponding columns in the current table

<iframe allowfullscreen="true" title="YouTube video player" src="https://www.youtube.com/embed/VYdpesbhND4" height="315" width="560" allow-top-navigation="false" allow-forms="false" allow-popups="false" sandbox="allow-scripts allow-same-origin allow-popups" style="box-sizing: border-box; margin: 0px auto; max-width: 100%; width: 964px; border: none;"></iframe>

Let's look more closely at each of these cases.

### @OneToOne

There are two situations where we can confidently assume the cardinality of the relation as `@`OneToOne:

1. Table has a column with the unique constraint that refers to the primary key of another table
2. Primary key of the table is a foreign key

**Case №1:**

```sql
CREATE TABLE profiles
(
    id        BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
    join_date date,
    user_id BIGINT,
    status    VARCHAR(255),
    bio       VARCHAR(255),
    CONSTRAINT pk_profiles PRIMARY KEY (id)
);

CREATE TABLE users
(
    id         BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
    last_name  VARCHAR(255),
    first_name VARCHAR(255),
    CONSTRAINT pk_users PRIMARY KEY (id)
);

ALTER TABLE profiles
    ADD CONSTRAINT uc_profiles_user UNIQUE (user_id);

ALTER TABLE profiles
    ADD CONSTRAINT FK_PROFILES_ON_USER FOREIGN KEY (user_id) REFERENCES users (id);
```

![one-to-one-uc-diagram.jpeg](img/one-to-one-uc-diagram.png)

![one-to-one-uc-wizard](img/one-to-one-uc-wizard.jpeg)

JPA Buddy will generate a `@`OneToOne association with a `@`JoinColumn annotation in the User entity, and a `@`OneToOne association with a `mappedBy` parameter in the Profile entity:

```java
@Entity
@Table(name = "users")
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @Column(name = "id", nullable = false)
  private Long id;

  @OneToOne(fetch = FetchType.LAZY)
  @JoinColumn(name = "profile_id")
  private Profile profile;
}

@Entity
@Table(name = "profiles")
public class Profile {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @Column(name = "id", nullable = false)
  private Long id;

  @OneToOne(fetch = FetchType.LAZY, mappedBy = "profile")
  private User users;
}
```

**Case №2:**

```sql
CREATE TABLE users
(
    id         BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
    last_name  VARCHAR(255),
    first_name VARCHAR(255),
    CONSTRAINT pk_users PRIMARY KEY (id)
);

CREATE TABLE profiles
(
    user_id   BIGINT NOT NULL,
    status    VARCHAR(255),
    bio       VARCHAR(255),
    join_date date,
    CONSTRAINT pk_profiles PRIMARY KEY (user_id)
);

ALTER TABLE profiles
    ADD CONSTRAINT FK_PROFILES_ON_USER FOREIGN KEY (user_id) REFERENCES users (id);
```

![one-to-one-pk-fk-diagram.jpeg](img/one-to-one-pk-fk-diagram.png)

![one-to-one-pk-fk-wizard.jpeg](img/one-to-one-pk-fk-wizard.jpeg)

Since `@`Id should not be a persistence entity, JPA Buddy will generate:

- `id` attribute of basic type and mark it with `@`Id annotation
- `users` `@`OneToOne association and mark it with `@`MapsId annotation

```java
@Entity
@Table(name = "profiles")
public class Profile {
  @Id
  @Column(name = "user_id", nullable = false)
  private Long id;

  @MapsId
  @OneToOne(fetch = FetchType.LAZY, optional = false)
  @JoinColumn(name = "user_id", nullable = false)
  private User users;

  //...
}

@Entity
@Table(name = "users")
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @Column(name = "id", nullable = false)
  private Long id;

  @OneToOne(fetch = FetchType.LAZY, mappedBy = "user")
  private Profile profiles;

  //...
}
```

### @OneToMany & @ManyToOne

If a table has the column that refers to the primary key of another table, it is most likely a `@`ManyToOne association. But you are also able to change cardinality to `@`OneToOne if required. So, depending on which table you call the reverse engineering action, JPA Buddy will detect mapping type as  `@`OneToMany or  `@`ManyToOne:

```sql
CREATE TABLE users
(
    id         BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
    last_name  VARCHAR(255),
    first_name VARCHAR(255),
    CONSTRAINT pk_users PRIMARY KEY (id)
);

CREATE TABLE profiles
(
    id        BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
    join_date date,
    status    VARCHAR(255),
    bio       VARCHAR(255),
    user_id   BIGINT,
    CONSTRAINT pk_profiles PRIMARY KEY (id)
);

ALTER TABLE profiles
    ADD CONSTRAINT FK_PROFILES_ON_USER FOREIGN KEY (user_id) REFERENCES users (id);
```

![one-to-many-many-to-one-diagram](img/one-to-many-many-to-one-diagram.png)

![one-to-many-many-to-one-wizard](img/one-to-many-many-to-one-wizard.jpeg)

JPA Buddy will generate the following code:

```java
@Entity
@Table(name = "users")
public class User {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @Column(name = "id", nullable = false)
  private Long id;

  @OneToMany(mappedBy = "user")
  private Set<Profile> profiles = new LinkedHashSet<>();

  //...
}

@Entity
@Table(name = "profiles")
public class Profile {
  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  @Column(name = "id", nullable = false)
  private Long id;

  @ManyToOne(fetch = FetchType.LAZY)
  @JoinColumn(name = "user_id")
  private User user;

  //...
}
```

### @ManyToMany

To establish a many-to-many relationship between two tables, you need to use a junction table. The junction table, in this case, contains only two columns - foreign keys. JPA Buddy can automatically detect such a table and identify the relation cardinality between the two tables whose ids are represented as foreign keys in the junction table as `@`ManyToMany.

```sql
CREATE TABLE users
(
  id         BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
  last_name  VARCHAR(255),
  first_name VARCHAR(255),
  CONSTRAINT pk_users PRIMARY KEY (id)
);

CREATE TABLE profiles
(
  id        BIGINT GENERATED BY DEFAULT AS IDENTITY NOT NULL,
  join_date date,
  status    VARCHAR(255),
  bio       VARCHAR(255),
  CONSTRAINT pk_profiles PRIMARY KEY (id)
);

CREATE TABLE profiles_users
(
    profile_id BIGINT NOT NULL,
    users_id   BIGINT NOT NULL,
    CONSTRAINT pk_profiles_users PRIMARY KEY (profile_id, users_id)
);

ALTER TABLE profiles_users
    ADD CONSTRAINT fk_prouse_on_profile FOREIGN KEY (profile_id) REFERENCES profiles (id);

ALTER TABLE profiles_users
    ADD CONSTRAINT fk_prouse_on_user FOREIGN KEY (users_id) REFERENCES users (id);
```

![many-to-many-diagram](img/many-to-many-diagram.png)

![many-to-many-wizard](img/many-to-many-wizard.jpeg)

If this association does not exist in any of the entities, JPA Buddy will generate it in the entity for which the reverse engineering action was called.

```java
@Entity
@Table(name = "users")
public class User {
   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   @Column(name = "id", nullable = false)
   private Long id;

   @ManyToMany
   @JoinTable(name = "profiles_users",
      joinColumns = @JoinColumn(name = "users_id"),
      inverseJoinColumns = @JoinColumn(name = "profile_id"))
   private Set<Profile> profiles = new LinkedHashSet<>();

   //...
}
```

If this association already exists in one of the entities, then JPA Buddy will generate the `@`ManyToMany attribute with the `mappedBy` parameter.

```java
@Entity
@Table(name = "profiles")
public class Profile {
   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   @Column(name = "id", nullable = false)
   private Long id;

   @ManyToMany(mappedBy = "profiles")
   private Set<User> users = new LinkedHashSet<>();
   
   //...
}
```

## Working With Remote DB

The larger the database and the slower the connection of the database (for example, if it is a remote DB), the longer it will take to load the DB schema. For better usability, JPA Buddy provides a DB schema cache. Once you enable it (1), a snapshot file will be created for the selected DB in the temporary directory. Otherwise, the DB schema will be loaded from the DB on each reverse engineering use. When you need it, you can refresh the saved schema cache (2).

![new-entity-db-schema-cache](img/new-entity-db-schema-cache.png)

## Settings

### General

1. Fetch Type – to follow best practices and avoid potential performance issues, JPA Buddy sets `FetchType.LAZY` for  `@OneToOne` and `@ManyToOne` associations by default.
2. Validation Annotations – validation annotations give you another layer of protection in addition to the DB constraints. By default, JPA Buddy will apply such annotations over entity attributes while reverse engineering.
3. Pluralization - by default, JPA Buddy uses the singular form for entity names. For example, if you have a table called `users`, JPA Buddy will generate a `User` entity. If you disable this option, JPA Buddy will keep the original name of the table and only capitalize the first letter – `Users`.
4. Basic type attribute - when this option is enabled, JPA Buddy will analyze the ORM references in the database schema and generate basic type attributes instead of creating associations or relationships between entities. This can be useful in certain scenarios where you prefer to have simple attribute types instead of complex associations.
5. IDEA Ultimate integration - enable this option to use the database metamodel provided by IntelliJ IDEA Ultimate to generate data related objects instead of using a JDBC driver to obtain meta information. This ensures that the generated objects align perfectly with the database structure. The most amazing part of it is that JPA Buddy can utilize all the connection settings specified within the IntelliJ IDEA Ultimate interface.

![preferences-general](img/preferences-general.png)

### Tables & Column Comments

To preserve comments added to the database objects, JPA Buddy transfers them to the corresponding entity using the Hibernate `@Comment` annotation or JavaDocs, depending on your settings.

![preferences-comments](img/preferences-comments.png)

> Please note that only `@Comment` annotations on entities can be included in the generated DDL scripts, depending on the [settings](https://www.jpa-buddy.com/documentation/database-versioning/#preview-window), JavaDocs will be ignored anyway.

### Naming Rules

#### Via Configs

![preferences-naming-rules](img/preferences-naming-rules.png)

Often, DBA specialists adhere to certain naming conventions for database objects. For example, all table or column names have a specific prefix/suffix. Yet, Java developers usually prefer to drop these prefixes/suffixes for the JPA model. JPA Buddy allows you to specify prefixes and suffixes to skip. 
Assume we set `sys_` and `p_` as prefixes to skip. After that, we apply reverse engineering for `sys_user` and `p_product` tables. As a result, prefixes will not appear in the corresponding entity names. The final entity names will be `User` and `Product` instead of `SysUser` and `PProduct`.
Also, the database column names sometimes match the <a href="https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html" target="_blank">reserved Java keywords</a>. E.g., `public`, `interface`, and so on... In this case, you can configure the field suffix so that JPA Buddy will append it to the original column name. E.g. for the `Field` suffix, the resulting names will be `publicField` and `interfaceField`.

#### Via Algorithm

![preferences-naming-rules](img/preferences-naming-rules-algorithm.png)

Despite the flexible options for configuring prefixes, suffixes, reserved words, and so on, in some cases this may still be insufficient. JPA Buddy does not limit you only to these settings. You can write custom code for processing the names of database tables/columns. Moreover, you can not only write code in the current editor but also import an existing class and use its methods.

It is important to note that JPA Buddy does not track changes in classes used in the naming algorithm in real-time. Therefore, after changing the class used in the algorithm, either update your settings or restart IntelliJ IDEA.

### Type Mappings

![preferences-mapping-types](img/preferences-mapping-types.png)

When the application works with several DBMSs, your schema might have slightly different data types for each of them.

Let's say the application needs to support both PostgreSQL and MS SQL and you need to store Unicode characters in string data. PostgreSQL supports Unicode chars in `VARCHAR`, but MS SQL has a separate `NVARCHAR` data type for it.

JPA Buddy lets you specify type mappings for each DBMS. It is also possible to set mappings for JPA Converters and Hibernate Types:

See how you can configure type mappings for reverse engineering in JPA Buddy to make use of the `@JavaType` annotation from Hibernate 6:

<div class="youtube">
<iframe width="560" height="315" src="https://www.youtube.com/embed/7vGgBHwm_Ck?t=89" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Tags: JPA, Entity generation, Database schema, Hibernate, ORM, Entity mapping, DBMS, Java development, Performance optimization, Best practices, Validation annotations, Fetch type