## Basics

JPA Buddy allows you to granularly pick tables/views and fields from your database and get them as JPA entities:

<div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/Lr_zg_uhWW4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<div class="note">
  The first thing you need to do to use the reverse engineering features is to create a DB connection. The correct way to do it and possible issues are described in the separate <a href="https://www.jpa-buddy.com/documentation/database-connections/">documentation</a>. Check it out to learn more. 
</div>

In the **IntelliJ IDEA Community Edition**, you can generate entities from DB via:

* JPA Structure (1) using plus button;
* Project Panel (2) using right-click.

In the **IntelliJ IDEA Ultimate Edition**, you can generate entities from DB via:

* JPA Structure (1) using plus button;
* Project Panel (2) using right-click;
* Database panel (3) using right-click;

![entities_from_db_action](img/entities_from_db_action.png)

## Entities from DB Wizard

![entities_from_db](img/entities_from_db.png)

### Configuration

The menu on the top of the window allows you to configure:

* <a href="https://www.jpa-buddy.com/documentation/database-connections/">DB connection</a>
* <a href="https://www.jpa-buddy.com/documentation/reverse-engineering/#working-with-remote-db">DB schema cache</a>
* Source root and package to which the generated entities will be saved
* Whether indexes and constraints need to be migrated
* Whether schema name should be specified in the `@Table` annotation

Also, from the "Other settings" drop-down list, you can move to the <a href="https://www.jpa-buddy.com/documentation/entity-designer/#settings-1">entity declaration</a> and <a href="https://www.jpa-buddy.com/documentation/reverse-engineering/#settings">reverse engineering</a> settings.

### Mapped Relations, Tables and Views

On the left side of the window, you can see:

* Mapped Relations - tables and views mapped to JPA entities
* Tables - tables that exist in the DB but are not mapped to entities
* Views - views that exist in the DB but are not mapped to entities

After selecting any element from the tree, a panel for migrating attributes from columns will appear. Also, you will be able to define a class name in the corresponding field.

### Migrating Attributes

The main part of the window allows you to configure everything related to attributes. You can choose which attributes you want to add and change all their params, except "Column Name". Mapping type and attribute/converter/hibernate types are represented as drop-down lists.

All attributes are divided into 3 categories:

* Migrated Columns - the ones already presented in the entity (available only for mapped relations)
* Columns - new, not mapped in the entity or parent @MappedSuperclass yet
* References - optional associations that are not represented as a column in the observing table

#### Creating Enums

For attributes matching the `String` or `Integer` type, you can change the mapping type from Basic to Enum, and JPA Buddy will create the corresponding Enum class in the project. You need to fill the enum with proper values manually.

#### Dealing With Unknown Types

For some SQL types, there is no exact match to Java classes. In this case, JPA Buddy does not set the type so as not to generate non-working code. You will need to choose the attribute type yourself. You can also configure default type mappings for each DBMS in the [settings](#type-mappings).

If you have the [HibernateTypes](https://github.com/vladmihalcea/hibernate-types) library in your project dependencies list, JPA Buddy can find suitable types in this library and automatically suggests them for the unsupported SQL types during reverse engineering:

<div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/uBjxdAmVDuI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

#### // TODO Comments

If you want to postpone an attribute creation for specific columns, you can choose `//todo comment` as the mapping type. JPA Buddy will generate the //todo comment with the corresponding quick-fix actions depending on the column type. You can call these actions via ⌘+B (Ctrl+B) shortcut:

- For known basic and association types you can:

  * Uncomment as is
  * Remove column mapping
- For unknown column type you can:

  - Define target Java type
  - Uncomment as is
  - Remove column mapping

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

![mapping_java_type](img/mapping_java_type.png)

JPA Buddy will remember data mappings for the subsequent reverse engineering actions. You can always change them in the [settings](#type-mappings).

### Map DB Views to JPA Entities

JPA Buddy follows all best practices providing the most efficient mapping for DB views while reverse engineering:

1. DB views do not have the primary key. Hence, JPA Buddy allows selecting a field or a set of fields to use as the identifier for the target entity.
2. Most of the DB views are immutable. So, JPA Buddy adds `@Immutable` annotation to the entity and generates getters only. This helps to achieve better application performance.
3. If a JPA entity is mapped to a DB view, a developer should not be able to create a new instance of this entity in the business logic code. For such entities, JPA Buddy generates only a no-arg protected constructor to meet the JPA specifications.

<div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/QUXgJSkBJO8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Reverse Engineering Columns

Sometimes, developers use the DB-first application development approach and add columns directly to the DB. After that, they need to update the JPA model. JPA Buddy can automate this process. To add attributes to the existing entity, choose From DB action in JPA Palette (1), Editor Toolbar (2) or from the IntelliJ IDEA "Generate" menu (3):

![reverse_engineering_columns_action](img/reverse_engineering_columns_action.png)

After that, the Reverse Engineering Columns wizard will appear:

![reverse_engineering_columns](img/reverse_engineering_columns.png)

The attributes migration flow here is identical to what was described in the [Entities from DB wizard](#migrating-attributes) section.

## Smart References Detection

JPA Buddy deeply understands your model. In certain cases, it's able to properly detect cardinality: `@`OneToOne, `@`OneToMany, `@`ManyToOne, `@`ManyToMany. The coolest thing is that JPA Buddy can show references for which there are no columns in the current table.

<iframe allowfullscreen="true" title="YouTube video player" src="https://www.youtube.com/embed/VYdpesbhND4" height="315" width="560" allow-top-navigation="false" allow-forms="false" allow-popups="false" sandbox="allow-scripts allow-same-origin allow-popups" style="box-sizing: border-box; margin: 0px auto; max-width: 100%; width: 964px; border: none;"></iframe>

Let's look more closely at each of these cases.

### @OneToOne

There are two situations when we know for 100% that the cardinality of the relation is exactly `@`OneToOne:

1. Table has a column with the unique constraint that refers to the primary key of another table
2. Primary key of the table is a foreign key

**Situation №1:**

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

![one_to_one_uc_diagram.jpeg](img/one_to_one_uc_diagram.png)

![one_to_one_uc_wizard](img/one_to_one_uc_wizard.jpeg)

JPA Buddy will generate `@`OneToOne association with `@`JoinColumn annotation in the User entity, and  `@`OneToOne association with `mappedBy` parameter in the Profile entity:

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

**Situation №2:**

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

![one_to_one_pk_fk_diagram.jpeg](img/one_to_one_pk_fk_diagram.png)

![one_to_one_pk_fk_wizard.jpeg](img/one_to_one_pk_fk_wizard.jpeg)

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

If a table has the column that refers to the primary key of another table, it is highly likely `@`ManyToOne association. But you are also able to change cardinality to `@`OneToOne if required. So, depending on which table you call the reverse engineering action, JPA Buddy will detect mapping type as  `@`OneToMany or  `@`ManyToOne:

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

![one_to_many_many_to_one_diagram](img/one_to_many_many_to_one_diagram.png)

![one_to_many_many_to_one_wizard](img/one_to_many_many_to_one_wizard.jpeg)

JPA Buddy will generate the following code:

```sql
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

To establish a many-to-many relationship between two tables, you need to use a junction table. The junction table, in this case, contains only two columns - foreign keys. Since JPA Buddy found such a table, it can say that the relation cardinality between two tables whose ids are represented in the junction table as foreign keys is `@`ManyToMany.

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

![many_to_many_diagram](img/many_to_many_diagram.png)

![many_to_many_wizard](img/many_to_many_wizard.jpeg)

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

The larger the database and the slower the connection of the database (for example, if it is remote DB), the longer it will take to load DB schema. For better usability, JPA Buddy provides a DB schema cache. Once you enable it (1), a snapshot file will be created for the selected DB in the temporary directory. Otherwise, the DB schema will be loaded from the DB on each reverse engineering use. When you need it, you can refresh saved schema cache (2).

![new_entity_db_schema_cache](img/new_entity_db_schema_cache.png)

## Settings

### General

**Fetch Type**

To follow best practices and don't cause performance issues, JPA Buddy sets `FetchType.LAZY` for  `@OneToOne` and `@ManyToOne` associations by default.

**Validation Annotations**

Validation annotations gives you another layer of protection in addition to the DB constraints. By default, JPA Buddy will apply such annotations over entity attributes while reverse engineering.

![preferences_general](img/preferences_general.png)

### Naming Rules

Often, DBA specialists adhere to certain naming conventions for database objects. For example, all table or column names have a specific prefix. Yet, Java developers usually prefer to drop these prefixes for the JPA model. JPA Buddy allows you to specify prefixes to skip. Assume we set `sys_` and `p_` as prefixes to skip. After that, we apply reverse engineering for `sys_user` and `p_product` tables. As a result, prefixes will not appear in the corresponding entity names. The final entity names will be `User` and `Product` instead of `SysUser` and `PProduct`.
Also, the database column names sometimes match the [reserved Java keywords](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html). E.g., `public`, `interface`, and so on... In this case, you can configure the field suffix so that JPA Buddy will append it to the original column name. E.g. for the `Field` suffix, the resulting names will be `publicField` and `interfaceField`.

![preferences_reverse_engineering](img/preferences_naming_rules.png)

### Type Mappings

When the application works with several DBMSs, your schema might have slightly different data types for each of them.

Let’s say the application needs to support both PostgreSQL and MS SQL and you need to store Unicode characters in string data. PostgreSQL supports Unicode chars in `VARCHAR`, but MS SQL has a separate `NVARCHAR` data type for it.

JPA Buddy lets you specify type mappings for each DBMS. It is also possible to set mappings for JPA Converters and Hibernate Types:

![preferences_mapping_types](img/preferences_mapping_types.png)
