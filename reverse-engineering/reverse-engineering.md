## Basics

JPA Buddy allows you to granularly pick tables/views and fields from your database and get them as JPA entities: 

<div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/a-YjeNdvpPk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<div class="note">
  The first thing you need to do to use the reverse engineering features is to create a DB connection. The correct way to do it and possible issues are described in the separate <a href="https://www.jpa-buddy.com/documentation/database-connections/">documentation</a>. Check it out to learn more. 
</div>

In the **IntelliJ IDEA Community Edition**, you can generate entities from DB via JPA Structure: 

![jpa_structure_entities_from_db](img/jpa_structure_entities_from_db.png)

In the **IntelliJ IDEA Ultimate Edition**, you can generate entities from DB via JPA Structure and from the Database panel: 

![database_entities_from_db](img/database_entities_from_db.png)

## Entities from DB Wizard

![entities_from_db](img/entities_from_db.png)

### Configuration

At the top of the window, you can configure:

* <a href="https://www.jpa-buddy.com/documentation/database-connections/">DB connection</a>
* <a href="https://www.jpa-buddy.com/documentation/reverse-engineering/#working-with-remote-db">DB schema cache</a>
* Source root and package to which the generated entities will be saved
* Whether indexes and constains need to be migrated by ticking the corresponding checkbox

Also, from "Other settings" drop-down list, you can move to the <a href="https://www.jpa-buddy.com/documentation/entity-designer/#settings-1">entity declaration</a> and <a href="https://www.jpa-buddy.com/documentation/reverse-engineering/#settings">reverse engineering</a> settings.

### Mapped Relations, Tables and Views

On the left of the window, you can see:

* Mapped Relations - those tables and views for which there are entities in the project
* Tables - those tables for which there are no entities yet
* Views - those views for which there are no entities yet

After selecting any element from the tree, a panel for migrating attributes from columns will appear. Also, you will be able to define a class name in the corresponding field.

### Migrating Attributes

The main part of the window allows you to configure everything related to attributes. You can choose which attributes you want to add and change all their params, except "Column Name". Mapping type and attribute/converter/hibernate types are represented as drop-down lists.

All attributes are divided into 3 categories:

* Migrated Columns - the ones already presented in the entity (available only for mapped relations)
* Columns - new, not mapped in the entity or parent @MappedSuperclass yet
* References - optional associations that are not represented as a column in the observing table

#### Creating Enums 

For those attributes that match `String` or `Integer` type, you can change the mapping type from Basic to Enum, and JPA Buddy will create the corresponding Enum class in the project, which will need to be filled in with values manually. 

#### Dealing With Unknown Types 

For some SQL types, there is no exact match to Java classes. In this case, JPA Buddy does not set the type so as not to generate non-working code. You will need to choose the attribute type yourself. You can also configure default type mappings for each DBMS in the [settings](#type-mappings). 

At the same time, some of the unsupported SQL types can be mapped via the [HibernateTypes](https://github.com/vladmihalcea/hibernate-types) library. And if you have it in your project, JPA Buddy finds suitable types and automatically suggests them during reverse engineering: 

<div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/uBjxdAmVDuI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

#### // TODO Comments

If you want to postpone the creation of attributes for certain columns, you can choose `//todo comment` as the mapping type. After that, depending on column type, JPA Buddy will generate the //todo comment with the corresponding quick-fix actions that you can call via ⌘+B (Cntl+B) shortcut:

* For known basic and association types you can:

  * Uncomment as is

  - Remove column mapping

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

Configuring it once, JPA Buddy will remember the choice for following reverse engineering actions. You can always change it in the [settings](#type-mappings).

### Map DB Views to JPA Entities

JPA Buddy follows all best practices providing the most efficient mapping for DB views while reverse engineering:  	
1. DB views do not have primary keys. Hence, JPA Buddy allows selecting a field or (often) a set of fields that can play the role of identifier for the target entity. 
2. Most of the DB views are immutable. So, JPA Buddy adds @Immutable annotation to the entity and generates only getters. And this will help to win a few points in the application performance.  	
3. Entities representing DB views can only come from the database. To ensure developers don't create new instances in the business logic, JPA Buddy generates only a protected constructor with no parameters for the entity to meet the JPA specifications.

<div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/QUXgJSkBJO8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
## Reverse Engineering Columns

During development, new columns can be added directly to the database table. JPA Buddy determines which columns already have the appropriate attributes and which do not. To add attributes to the existing entity, choose Columns action in the Reverse Engineering section in JPA Palette.  

![jpa_palette_reverse_engineering_columns](img/jpa_palette_reverse_engineering_columns.png)

After that, the Reverse Engineering Columns wizard will appear:

![reverse_engineering_columns](img/reverse_engineering_columns.png)

The attributes migration flow here is identical to what was described in the [Entities from DB wizard](#migrating-attributes) section.

## Smart References Detection

JPA Buddy deeply understands your model. In certain cases, it's able to properly detect cardinality: `@`OneToOne, `@`OneToMany, `@`ManyToOne, `@`ManyToMany. The coolest thing is that JPA Buddy can show references for which there are no columns in the current table. 

<iframe allowfullscreen="true" title="YouTube video player" src="https://www.youtube.com/embed/VYdpesbhND4" height="315" width="560" allow-top-navigation="false" allow-forms="false" allow-popups="false" sandbox="allow-scripts allow-same-origin allow-popups" style="box-sizing: border-box; margin: 0px auto; max-width: 100%; width: 964px; border: none;"></iframe>



Let's look more precisely at each of these cases.

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

![one_to_one_uc_diagram.jpeg](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/one_to_one_uc_diagram.jpeg?lastModify=1651229099)

![one_to_one_uc_wizard](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/one_to_one_uc_wizard.jpeg?lastModify=1651229099)

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



![one_to_one_pk_fk_diagram.jpeg](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/one_to_one_pk_fk_diagram.jpeg?lastModify=1651229099)

 ![one_to_one_pk_fk_wizard.jpeg](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/one_to_one_pk_fk_wizard.jpeg?lastModify=1651229099)

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

![one_to_many_many_to_one_diagram](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/one_to_many_many_to_one_diagram.jpeg?lastModify=1651229099)

![one_to_many_many_to_one_wizard](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/one_to_many_many_to_one_wizard.jpeg?lastModify=1651229099)

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

![many_to_many_diagram](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/many_to_many_diagram.jpeg?lastModify=1651229099)

![many_to_many_wizard](file:///Users/vlasov/Documents/GitHub/documentation/reverse-engineering/img/many_to_many_wizard.jpeg?lastModify=1651229099)

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

### Fetch Type

To follow best practices and don't cause performance issues, JPA Buddy sets `FetchType.LAZY` for  `@`OneToOne and `@`ManyToOne associations by default. But you can change the default value in any time. Open Preferences -> Tools -> JPA Buddy -> Reverse Engineering:

![fetch_type](img/fetch_type.jpeg)

### Type Mappings

When the application works with several DBMSs, your schema might have slightly different data types for each of them. 

Let’s say the application needs to support both PostgreSQL and MS SQL. And you want to store Unicode characters in your strings. PostgreSQL supports Unicode chars in VARCHAR, but MS SQL has a separate NVARCHAR data type for it. 

JPA Buddy lets you specify type mappings for each DBMS. It is also possible to set mappings for JPA Converters and Hibernate Types: 

![preferences_reverse_engineering](img/preferences_reverse_engineering.jpeg)
