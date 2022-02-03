# Changelog

## 2022.1.0 - 2022-02-07

### Completely new
JPA Buddy presents - Minimalistic Mode! It's designed to minimize distraction for developers. If you are the one who prefers to have everything at your fingertips – you will definitely like it! [JPAB-1122](https://issues.jpa-buddy.com/issue/JPAB-1122)

### Features
* Database Versioning
  - YAML, SQL and JSON file types are finally supported for the Liquibase diff generator [JPAB-818](https://issues.jpa-buddy.com/issue/JPAB-818)
  - H2 database is now supported [JPAB-673](https://issues.jpa-buddy.com/issue/JPAB-673)
  - Now you can generate a database schema initialization script for any project [JPAB-787](https://issues.jpa-buddy.com/issue/JPAB-787)
* Reverse Engineering
  - JPA Buddy has learned to understand how entities relate to each other more deeply. Now it better suggests cardinality: OneToOne, OneToMany, ManyToOne and ManyToMany! [JPAB-918](https://issues.jpa-buddy.com/issue/JPAB-918)
  - @MapsId attribute generation has been supported [JPAB-995](https://issues.jpa-buddy.com/issue/JPAB-995)
* Spring Data JPA
  - Now it's possible to generate an "Update" JPQL statement via JPA Palette [JPAB-1086](https://issues.jpa-buddy.com/issue/JPAB-1086)

### Improvements
* Database Versioning
  - Now you can deal with the unknown types right at the moment of diff generation [JPAB-1171](https://issues.jpa-buddy.com/issue/JPAB-1171)
  - Join tables are now supported in the wizards [JPAB-1469](https://issues.jpa-buddy.com/issue/JPAB-1469) & [JPAB-1448](https://issues.jpa-buddy.com/issue/JPAB-1448)
* Spring Data
  - Long queries are now much easier to read because they will now be split into multiple lines [JPAB-668](https://issues.jpa-buddy.com/issue/JPAB-668)
  - For modifying query methods, it's now possible to define transactional params [JPAB-1532](https://issues.jpa-buddy.com/issue/JPAB-1532)
* Reverse Engineering
  - Now attributes are divided by type: already migrated, references and columns [JPAB-1487](https://issues.jpa-buddy.com/issue/JPAB-1487)

### Bug-fix
* An issue with incorrectly generated id column for inverse join column in Many to Many table has been fixed [JPAB-1598](https://issues.jpa-buddy.com/issue/JPAB-1598)
* TINYINT(1) DEFAULT 0 as a mapping for Boolean now handles correctly during diff generation [JPAB-1599](https://issues.jpa-buddy.com/issue/JPAB-1599)
* Default timestamps and "on update" statements now handles correctly [JPAB-1600](https://issues.jpa-buddy.com/issue/JPAB-1600)
* Reference to the folder in the Liquibase .xml file now works correctly [JPAB-1603](https://issues.jpa-buddy.com/issue/JPAB-1603)

[All resolved issues (35+)](https://youtrack.haulmont.com/issues/JPAB?q=Milestone:%20221%20Bug%20fix:%200%20State:%20Fixed%20,%20Verified%20tag:%20changelog%20%20%20%20order%20by:%20type%20desc,%20Priority,State%20desc%20-%7BInternal%20improvement%7D%20-Task%20)

## 2021.6.2 - 2022-01-12

### Improvements
* Now plugin can resolve references to changelogs from external libraries [JPAB-1512](https://issues.jpa-buddy.com/issue/JPAB-1512)
* Plugin archive filename on the JB Marketplace now contains the plugin version [JPAB-1556](https://issues.jpa-buddy.com/issue/JPAB-1556)
* Diff for entities with the same names in different schemas is now generated correctly [JPAB-1548](https://issues.jpa-buddy.com/issue/JPAB-1548)

### Bug-fix

* Flyway reserved words are now processed correctly in the migrations [JPAB-1565](https://issues.jpa-buddy.com/issue/JPAB-1565)
* Fixed KotlinIdeaResolutionException during "Convert Java to Kotlin" action [JPAB-1508](https://issues.jpa-buddy.com/issue/JPAB-1508)
* Opening "Edit Persistence Unit dialog" from "Change settings" no longer causes IndexNotReadyException [JPAB-1516](https://issues.jpa-buddy.com/issue/JPAB-1516)
* Unnecessary CascadeTypes are no longer generated along with CascadeType.ALL [JPAB-1552](https://issues.jpa-buddy.com/issue/JPAB-1552)

[All resolved issues (10+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20216%20Bug%20fix:%202%20order%20by:%20Milestone,%20%7BBug%20fix%7D,%20Priority,%20State%20desc,%20type)

## 2021.6.1 - 2021-12-20

### Improvements

* Now @InheritInverseConfiguration is used for MapStruct mappers [JPAB-1246](https://issues.jpa-buddy.com/issue/JPAB-1246)
* "New Association Attribute" dialog improvements [JPAB-1434](https://issues.jpa-buddy.com/issue/JPAB-1434) & [JPAB-1425](https://issues.jpa-buddy.com/issue/JPAB-1425) 
* The configuration file is no longer generated for default settings [JPAB-1423](https://issues.jpa-buddy.com/issue/JPAB-1423)
* The "Help" buttons now lead to the documentation page [JPAB-1016](https://issues.jpa-buddy.com/issue/JPAB-1016) & [JPAB-1478](https://issues.jpa-buddy.com/issue/JPAB-1478)

### Bug-fix

* Changed the approach of generating annotations in Kotlin [JPAB-1151](https://issues.jpa-buddy.com/issue/JPAB-1151)
* Create Repository action is no longer missed if Kotlin is not configured [JPAB-1455](https://issues.jpa-buddy.com/issue/JPAB-1455)
* Missing datasource and subsequent action call no longer causes NullPointerException [JPAB-1455](https://issues.jpa-buddy.com/issue/PAB-1480)
* The search for generic types converters now works correctly [JPAB-1431](https://issues.jpa-buddy.com/issue/JPAB-1431)
* Correctly generates diff for entities with Embedded/Embedded attribute without attributes override [JPAB-1471](https://issues.jpa-buddy.com/issue/JPAB-1471)
* Calling ToString action from JPA Inspector no longer duplicates other annotations [JPAB-1440](https://issues.jpa-buddy.com/issue/JPAB-1440)
* Fixed RuntimeExceptionWithAttachments [JPAB-1479](https://issues.jpa-buddy.com/issue/JPAB-1479)
* The script for renaming columns containing a foreign key is now correctly generated in Liquibase [JPAB-1483](https://issues.jpa-buddy.com/issue/JPAB-1483)
* Throwable exception handled [JPAB-1489](https://issues.jpa-buddy.com/issue/JPAB-1489)
* Add ability to create attribute with ManyToMany and mappedBy [JPAB-1503](https://issues.jpa-buddy.com/issue/JPAB-1503)
* Table name is not generated when creating an entity [JPAB-1504](https://issues.jpa-buddy.com/issue/JPAB-1504)
* Incorrect generation inverse attribute for OneToOne mappedBy attribute [JPAB-1505](https://issues.jpa-buddy.com/issue/JPAB-1505)

[All resolved issues (20+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20216%20Bug%20fix:%201%20order%20by:%20Type%20desc,%20%7BSpent%20time%7D%20desc%20)

## 2021.6.0 - 2021-12-02

### New Features

* DTO Generator [Incubator]*

  - Generate DTOs from entities [JPAB-388](https://issues.jpa-buddy.com/issue/JPAB-388)

  - Generate MapStruct mappers to map entities to DTOs and back [JPAB-1233](https://issues.jpa-buddy.com/issue/JPAB-1233)

  - Validation annotations are automatically migrated to the newly created DTO [JPAB-1148](https://issues.jpa-buddy.com/issue/JPAB-1148)

  - Initialized fields are automatically migrated to the newly created DTO [JPAB-1149](https://issues.jpa-buddy.com/issue/JPAB-1149)

  - Lombok is supported [JPAB-1146](https://issues.jpa-buddy.com/issue/JPAB-1146)

* Liquibase/Flyway diff generator

  - The root node of the changelog shows the contents of the first 20 changesets [JPAB-1169](https://issues.jpa-buddy.com/issue/JPAB-1169)

  - After executing the liquibase/flyway changelogs/migrations, you can navigate to them. For example, you can navigate to the elements that caused the execution to fail [JPAB-590](https://issues.jpa-buddy.com/issue/JPAB-590)

  - Navigation to parent changelogs via gutter icon [JPAB-173](https://issues.jpa-buddy.com/issue/JPAB-173)

  - Support for Map<"X","Y"> with @ElementCollection and with associations [JPAB-808](https://issues.jpa-buddy.com/issue/JPAB-808)

  - Improved windows for Liquibase/Flyway "insert" and "update" actions. You can specify values for attributes via a corresponding table [JPAB-738](https://issues.jpa-buddy.com/issue/JPAB-738)

* Reverse Engineering [Incubator]*

  - You can create immutable entities from database views [JPAB-953](https://issues.jpa-buddy.com/issue/JPAB-953)

  - Added DB schema cache. For slow connections, you can create a snapshot by connecting to the database only once. All subsequent operations related to reverse engineering will receive information from it almost instantly [JPAB-1204](https://issues.jpa-buddy.com/issue/JPAB-1204)

* Spring Data

  - Scaffold JPA Buddy/IDEA Ultimate DB connection properties to application.properties [JPAB-411](https://issues.jpa-buddy.com/issue/JPAB-411)

  - A new inspection for update/delete queries without @Modifying annotation [JPAB-1320](https://issues.jpa-buddy.com/issue/JPAB-1320)

* Entity Designer

  - Annotations of entity attributes are arranged in the order of belonging to packages (Lombok, Hibernate, etc...) [JPAB-998](https://issues.jpa-buddy.com/issue/JPAB-998)

  - Named queries are supported for entities [JPAB-492](https://issues.jpa-buddy.com/issue/JPAB-492)

  - During the creation of associations, you can now see and apply optimization tips [JPAB-1231](https://issues.jpa-buddy.com/issue/JPAB-1231)

  - More Hibernate Validator Constraints are supported [JPAB-684](https://issues.jpa-buddy.com/issue/JPAB-684)

  - Fluent setters generation (with "return this") [JPAB-413](https://issues.jpa-buddy.com/issue/JPAB-413)

### Improvements

* Diff Generator

  - Show SQL results now look like nice-formatted SQL [JPAB-191](https://issues.jpa-buddy.com/issue/JPAB-191)

  - Diff generation now works correctly for attributes with @JoinTable and @ElementCollection annotations [JPAB-1152](https://issues.jpa-buddy.com/issue/JPAB-1152)

  - Supported diff generation for MappedSuperclass with associations [JPAB-1360](https://issues.jpa-buddy.com/issue/JPAB-1360)

  - If your project contains Liquibase/Flyway plugin definition, you can use diff generator features even without maven dependencies [JPAB-1226](https://issues.jpa-buddy.com/issue/JPAB-1226)

* Spring Data

  - Supported UserType inheritors for "Assign JPA converter / Hibernate type" [JPAB-801](https://issues.jpa-buddy.com/issue/JPAB-801)

  - Now you can create @Query method without any conditions [JPAB-1128](https://issues.jpa-buddy.com/issue/JPAB-1128) and [JPAB-1309](https://issues.jpa-buddy.com/issue/JPAB-1309)

* Entity Designer

  - During new entity creation you can immediately create the id for it [JPAB-932](https://issues.jpa-buddy.com/issue/JPAB-932)

  - Attributes with collection type are now initialized to avoid unnecessary null checks [JPAB-1113](https://issues.jpa-buddy.com/issue/JPAB-1113)

  - An entity can now be marked with multiple @TypeDef annotations [JPAB-1408](https://issues.jpa-buddy.com/issue/JPAB-1408)

### Bug-fix

* Diff Generator

  - For JoinTable of the OneToMany association attribute, a primary key is now generated [JPAB-1391](https://issues.jpa-buddy.com/issue/JPAB-1391)

  - Columns are no longer duplicated in the diff if the PhysicalNamingStrategyStandardImpl is used [JPAB-1414](https://issues.jpa-buddy.com/issue/JPAB-1414)

  - MapKeyJoinColumn/MapKeyColumn are now generated correctly for JoinTable [JPAB-1392](https://issues.jpa-buddy.com/issue/JPAB-1392)

* Reverse Engineering
  - Missing drivers no longer causes an error [JPAB-1177](https://issues.jpa-buddy.com/issue/JPAB-1177)

Other improvements and fixes, see [all resolved issues (110+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20216%20%23Resolved%20Bug%20fix:%200)

\* Features in the Incubator are in the active development phase, with major improvements and changes planned in the nearest future. These features will remain free until they are complete. After that, they can become either paid or free, depending on the feature.

## 5.9 - 2021-11-25

- Diff Generator
  - During diff generation, comments left manually on tables and columns are no longer deleted [JPAB-1426](https://issues.jpa-buddy.com/issue/JPAB-1426)
  - The diff generation works correctly for tables with the schema name specified both in camel or upper cases [JPAB-1427](https://issues.jpa-buddy.com/issue/JPAB-1427)
- Lombok
  - Fixed setter method deletion when Lombok @Setter checkbox is unchecked in JPA Inspector [JPAB-1429](https://issues.jpa-buddy.com/issue/JPAB-1429)
  - Getters not backed up by fields are no longer deleted after changing Lombok ToString checkbox in JPA Inspector [JPAB-1430](https://issues.jpa-buddy.com/issue/JPAB-1430)
- Control-flow exception no longer logged in the stack-trace [JPAB-1405](https://issues.jpa-buddy.com/issue/JPAB-1405)
- Now the apply button is disabled after saving the changes in the Database Drivers window [JPAB-1312](https://issues.jpa-buddy.com/issue/JPAB-1312)
- Editing attributes of unknown collection types no longer breaks the code [JPAB-1278](https://issues.jpa-buddy.com/issue/JPAB-1278)

## 5.8 - 2021-11-10

- Made autocompletion for column/table names by default according to the defined naming strategy [JPAB-1367](https://issues.jpa-buddy.com/issue/JPAB-1367)
- Fixed Persistence.xml files with newer namespaces not being detected [JPAB-1353](https://issues.jpa-buddy.com/issue/JPAB-1353)
- Fixed Oracle user validation in the DB connection window [JPAB-1365](https://issues.jpa-buddy.com/issue/JPAB-1365)
- Fixed the following exceptions:
  - UnsupportedOperationException while editing the join column from the "Create Attribute" dialog [JPAB-1361](https://issues.jpa-buddy.com/issue/JPAB-1361)
  - ClassNotFoundException when reverse-engineering the entity from DB [JPAB-1362](https://issues.jpa-buddy.com/issue/JPAB-1362)
  - IllegalStateException while editing several entities from hierarchy in multiple windows [JPAB-1363](https://issues.jpa-buddy.com/issue/JPAB-1363)
  - IllegalStateException when editing an entity with mappedBy attribute, or the entity that is referenced by this attribute [JPAB-1364](https://issues.jpa-buddy.com/issue/JPAB-1364)
  - InvalidVirtualFileAccessException while using Liquibase actions [JPAB-1383](https://issues.jpa-buddy.com/issue/JPAB-1383)

## 5.7 - 2021-10-25

- IDEA 2021.3 support [JPAB-1058](https://issues.jpa-buddy.com/issue/JPAB-1058)
- Improved connection to MSSQL Server with integrated security [JPAB-1262](https://issues.jpa-buddy.com/issue/JPAB-1262)
- Spring Data JPA @Query generator improvements:
  - @Modifying annotation is now generated for @Query 'delete' methods [JPAB-1307](https://issues.jpa-buddy.com/issue/JPAB-1307)
  - The return type of @Modifying queries can now be specified (int/Integer/void) [JPAB-1308](https://issues.jpa-buddy.com/issue/JPAB-1308)
  - Fixed @Query 'find' methods being generated instead of @Query 'delete' methods [JPAB-1305](https://issues.jpa-buddy.com/issue/JPAB-1305)
- Fixed generated hashCode() always returning zero [JPAB-1336](https://issues.jpa-buddy.com/issue/JPAB-1336)
- Improved handling of non-plugin exceptions [JPAB-1269](https://issues.jpa-buddy.com/issue/JPAB-1269)
- Fixed the following exceptions:
  - IllegalArgumentException when applying the "Create entity id attribute" fix [JPAB-1316](https://issues.jpa-buddy.com/issue/JPAB-1316)
  - PsiInvalidElementAccessException when assigning a JPA Converter to an attribute with wrong type [JPAB-1314](https://issues.jpa-buddy.com/issue/JPAB-1314)
  - IllegalArgumentException when changing association cascade in JPA Inspector [JPAB-1304](https://issues.jpa-buddy.com/issue/JPAB-1304)

## 5.6 - 2021-10-05

- Oracle DB SID connection support in IDEA Community [JPAB-1260](https://issues.jpa-buddy.com/issue/JPAB-1260)
- Ability to use Flyway features without a Flyway dependency [JPAB-646](https://issues.jpa-buddy.com/issue/JPAB-646)
- Changed the order of diff changes in Flyway diff scripts when dropping primary key [JPAB-1254](https://issues.jpa-buddy.com/issue/JPAB-1254)
- "Lombok @Data"/"Kotlin data class" inspections are no longer triggered for @Embeddable [JPAB-1266](https://issues.jpa-buddy.com/issue/JPAB-1266)
- Added an id null check to generated equals() method [JPAB-1292](https://issues.jpa-buddy.com/issue/JPAB-1292)
- Fixed no unique constraint being generated for unique associations in Liquibase/Flyway diff generator [JPAB-1275](https://issues.jpa-buddy.com/issue/JPAB-1275)
- "Unsupported type" inspection is not triggered for generic attributes anymore [JPAB-1273](https://issues.jpa-buddy.com/issue/JPAB-1273)
- Fixed the following exceptions:
  - NullPointerException when setting owning side for attribute in JPA Inspector [JPAB-1274](https://issues.jpa-buddy.com/issue/JPAB-1274)
  - ClassCastException when setting converter class in JPA Inspector [JPAB-1272](https://issues.jpa-buddy.com/issue/JPAB-1272)
  - IncorrectOperationException exception when adding validation to an attribute with incorrect type [JPAB-1284](https://issues.jpa-buddy.com/issue/JPAB-1284)
  - "Read access is allowed from inside read-action (or EDT) only" Throwable when generating diff changes [JPAB-1270](https://issues.jpa-buddy.com/issue/JPAB-1270)
  - IllegalStateException when navigating to entity attribute from Liquibase column name [JPAB-1271](https://issues.jpa-buddy.com/issue/JPAB-1271)
  - Exception when opening JPA Buddy settings page from IDEA Welcome Dialog [JPAB-1293](https://issues.jpa-buddy.com/issue/JPAB-1293)
  - Exception when adding "addForeignKeyConstraint" with empty name to SQL file [JPAB-1294](https://issues.jpa-buddy.com/issue/JPAB-1294)

## 5.5 - 2021-09-24

Just clearing out some bugs. Resolved the following issues:

- MSSQL Server connection with Integrated security not working properly [JPAB-1223](https://issues.jpa-buddy.com/issue/JPAB-1223) [JPAB-1252](https://issues.jpa-buddy.com/issue/JPAB-1252)
- Reverse engineering: schema name not being generated for associated entities [JPAB-1244](https://issues.jpa-buddy.com/issue/JPAB-1244)
- "Cancel" button not working for actions with the DB [JPAB-1240](https://issues.jpa-buddy.com/issue/JPAB-1240)
- "Changeset author" setting not being applied to Liquibase changes created via JPA Palette [JPAB-1241](https://issues.jpa-buddy.com/issue/JPAB-1241)
- Liquibase/Flyway diff generator not working for @ElementCollection in entities with generic ids [JPAB-1253](https://issues.jpa-buddy.com/issue/JPAB-1253)
- InvalidPathException when DirectoryModificationTrackerManager is working [JPAB-1242](https://issues.jpa-buddy.com/issue/JPAB-1242)

## 5.4 - 2021-09-13

- Support for non-default schemas in reverse engineering [JPAB-1215](https://issues.jpa-buddy.com/issue/JPAB-1215)
- Fixed the following issues in entity designer:
  - @JoinColumn name not being generated after changing the owning side of association [JPAB-1211](https://issues.jpa-buddy.com/issue/JPAB-1211)
  - Inconsistent owning side behaviour in the "New Association Attribute" window [JPAB-1199](https://issues.jpa-buddy.com/issue/JPAB-1199)
  - JPA converter/Hibernate custom type not being specified after creation in Kotlin [JPAB-1189](https://issues.jpa-buddy.com/issue/JPAB-1189)
  - @Table being removed after generating Lombok @Getter/@Setter above the class [JPAB-1187](https://issues.jpa-buddy.com/issue/JPAB-1187)
  - Lombok @ToString.Exclude not being removed after unchecking "Included into toString" box in JPA Inspector [JPAB-1192](https://issues.jpa-buddy.com/issue/JPAB-1192)
- Liquibase/Flyway diff generator:
  - Fixed the order of diff changes for updating attributes [JPAB-1201](https://issues.jpa-buddy.com/issue/JPAB-1201)
  - Fixed the "Show SQL" action in Liquibase 4.4+ [JPAB-1193](https://issues.jpa-buddy.com/issue/JPAB-1193)
  - Support for ElementCollection with JoinTable [JPAB-1181](https://issues.jpa-buddy.com/issue/JPAB-1181)
  - Changed the SQL type for Currency from "DECIMAL" to "VARCHAR" [JPAB-1209](https://issues.jpa-buddy.com/issue/JPAB-1209)
- Fixed exceptions:
  - IncorrectOperationException when creating a referenced entity via the "Generate" menu [JPAB-1184](https://issues.jpa-buddy.com/issue/JPAB-1184)
  - java.lang.Throwable: "AWT events are not allowed inside write action" when creating some associations [JPAB-1200](https://issues.jpa-buddy.com/issue/JPAB-1200)
  - java.lang.IllegalStateException: Entity PsiClass from SmartPsiElementPointer is null when collect line markers for converters [JPAB-1207](https://issues.jpa-buddy.com/issue/JPAB-1207)
  - java.lang.Throwable: Non-physical PsiElement for AttributeTypeAnnotator [JPAB-1208](https://issues.jpa-buddy.com/issue/JPAB-1208)
- Other improvements and fixes, see [all resolved issues (17)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%205.X%20Bug%20fix:%204).

## 5.3 - 2021-09-01

Fixed exceptions:

- NullPointerException during entity code editing [JPAB-1196](https://issues.jpa-buddy.com/issue/JPAB-1196)
- Process an exception caused when updating a plugin through the notification of recommended plugins [JPAB-1197](https://issues.jpa-buddy.com/issue/JPAB-1197):
  - `com.intellij.diagnostic.PluginException: Key com.haulmont.jpb.generator.JpabObjectMethodsTemplatesManager duplicated [Plugin: com.haulmont.jpab]`
  - `com.intellij.diagnostic.PluginException: Short name 'AssociationFieldHasColumnAnnotation' is not unique`

## 5.2 - 2021-08-30

**Fixed exceptions:**

- PsiInvalidElementAccessException: Element class com.intellij.psi.impl.source.tree.java.FieldElement of type FIELD [JPAB-1179](https://issues.jpa-buddy.com/issue/JPAB-1179)
- ClassCastException: class com.intellij.psi.impl.source.PsiParameterImpl cannot be cast to class com.intellij.psi.PsiClass [JPAB-1180](https://issues.jpa-buddy.com/issue/JPAB-1180)
- PsiInvalidElementAccessException after creating repository method by entity attribute [JPAB-1183](https://issues.jpa-buddy.com/issue/JPAB-1183)

## 5.1 - 2021-08-27

**Fixed exceptions:**

- PsiInvalidElementAccessException: Element class com.intellij.psi.impl.source.tree.java.FieldElement of type FIELD [JPAB-1179](https://issues.jpa-buddy.com/issue/JPAB-1179)
- ClassCastException: class com.intellij.psi.impl.source.PsiParameterImpl cannot be cast to class com.intellij.psi.PsiClass [JPAB-1180](https://issues.jpa-buddy.com/issue/JPAB-1180)
- PsiInvalidElementAccessException after creating repository method by entity attribute [JPAB-1183](https://issues.jpa-buddy.com/issue/JPAB-1183)

## 5.0 - 2021-08-26

- Reverse engineering is finally here!
  - Generate JPA entities from a DB table [JPAB-768](https://issues.jpa-buddy.com/issue/JPAB-768)
  - Add attributes to existing entities from DB columns [JPAB-769](https://issues.jpa-buddy.com/issue/JPAB-769)
  - Migrate indexes and constraints [JPAB-1017](https://issues.jpa-buddy.com/issue/JPAB-1017)
  - Generate entities and associations with composite ids [JPAB-955](https://issues.jpa-buddy.com/issue/JPAB-955) [JPAB-958](https://issues.jpa-buddy.com/issue/JPAB-958)
- Liquibase/Flyway diff generator improvements:
  - Support for composite join columns in associations [JPAB-809](https://issues.jpa-buddy.com/issue/JPAB-809)
  - Better support for types with length and precision [JPAB-385](https://issues.jpa-buddy.com/issue/JPAB-385)
  - @SequenceGenerator above class support [JPAB-649](https://issues.jpa-buddy.com/issue/JPAB-649)
  - Support for GenerationType.AUTO strategy in Hibernate [JPAB-878](https://issues.jpa-buddy.com/issue/JPAB-878)
  - Improved error dialogs [JPAB-936](https://issues.jpa-buddy.com/issue/JPAB-936) [JPAB-980](https://issues.jpa-buddy.com/issue/JPAB-980)
  - Reworked java.lang.LobString type for String with @Lob annotation [JPAB-927](https://issues.jpa-buddy.com/issue/JPAB-927)
  - Support for unique constraints and indexes without an explicit name [JPAB-1088](https://issues.jpa-buddy.com/issue/JPAB-1088)
- Entity designer:
  - Support for @ElementCollection and @CollectionTable [JPAB-107](https://issues.jpa-buddy.com/issue/JPAB-107)
  - Support for @UniqueConstraint [JPAB-121](https://issues.jpa-buddy.com/issue/JPAB-121)
  - Improved equals/hashCode generation [JPAB-1028](https://issues.jpa-buddy.com/issue/JPAB-1028)
  - Ability to specify length and mark the field as Lob for all string types [JPAB-1049](https://issues.jpa-buddy.com/issue/JPAB-1049)
  - New intention: Create Spring Repository by entity class [JPAB-879](https://issues.jpa-buddy.com/issue/JPAB-879)
  - New entities can now be created right in the association creation dialog [JPAB-706](https://issues.jpa-buddy.com/issue/JPAB-706)
- Jakarta Persistence API 3.0 is now supported [JPAB-546](https://issues.jpa-buddy.com/issue/JPAB-546)
- Reworked naming template settings to be a table [JPAB-1046](https://issues.jpa-buddy.com/issue/JPAB-1046)
- Common JPA Buddy intentions and actions are now available in "Actions" dropdown in JPA Inspector and via line markers in IDEA Ultimate [JPAB-725](https://issues.jpa-buddy.com/issue/JPAB-725)
- Improved performance of:
  - Entity designer [JPAB-994](https://issues.jpa-buddy.com/issue/JPAB-994)
  - Liquibase/Flyway diff script generator [JPAB-171](https://issues.jpa-buddy.com/issue/JPAB-171)
- Fixed the following issues:
  - "Create custom type" quick fix not working in Kotlin [JPAB-1098](https://issues.jpa-buddy.com/issue/JPAB-1098)
  - Inability to override standard Spring Data Repository methods [JPAB-1059](https://issues.jpa-buddy.com/issue/JPAB-1059)
  - Quick fix "Mark as Embedded" removing the default value in Kotlin [JPAB-1105](https://issues.jpa-buddy.com/issue/JPAB-1105)
  - "Target type" dropdown being empty in Type Mappings settings in projects without Liquibase [JPAB-914](https://issues.jpa-buddy.com/issue/JPAB-914)
  - "Attribute with unsupported type should either be @Transient or have custom type or converter declaration" inspection triggering for enums [JPAB-729](https://issues.jpa-buddy.com/issue/JPAB-729)
- Other improvements and fixes, see [all resolved issues (70+)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%205.X%20Bug%20fix:%200).

## 4.6 - 2021-08-11

- Liquibase/Flyway diff generator:
  - Fixed diff generation for entity attributes with generic types [JPAB-1087](https://issues.jpa-buddy.com/issue/JPAB-1087)
  - Bidirectional many-to-many associations with implicit join column names are generated in compliance with Hibernate ImplicitNamingStrategyJpaCompliantImpl [JPAB-1089](https://issues.jpa-buddy.com/issue/JPAB-1089)
  - Fixed DTYPE update and create column statements order [JPAB-1081](https://issues.jpa-buddy.com/issue/JPAB-1081)
- JPA Inspector improvements:
  - @DiscriminatorColumn properties are no longer deleted for JOINED inheritance strategy [JPAB-1055](https://issues.jpa-buddy.com/issue/JPAB-1055)
  - Fixed dynamic projection generating without the generic parameter [JPAB-1063](https://issues.jpa-buddy.com/issue/JPAB-1063)
  - Clearing the 'length' field does not cause 'Incorrect length value' validation anymore [JPAB-1078](https://issues.jpa-buddy.com/issue/JPAB-1078)
- Persistence Unit property is no longer ignored during JSON snapshot generation [JPAB-1071](https://issues.jpa-buddy.com/issue/JPAB-1071)
- Fixed '@Table annotation should not be used together with SINGLE_TABLE inheritance strategy.' inspection being shown for wrong inheritance strategies [JPAB-1076](https://issues.jpa-buddy.com/issue/JPAB-1076)
- Search field for JPA Palette now works for the 'Utilities' tab too [JPAB-1070](https://issues.jpa-buddy.com/issue/JPAB-1070)
- Fixed the following exceptions:
  - NullPointerException during line markers processing in some Kotlin projects [JPAB-1073](https://issues.jpa-buddy.com/issue/JPAB-1073)
  - IncorrectOperationException when saving diff changelog file [JPAB-1072](https://issues.jpa-buddy.com/issue/JPAB-1072)
  - IllegalStateException when invoking "Create JPA Entity" fix [JPAB-1074](https://issues.jpa-buddy.com/issue/JPAB-1074)
  - IllegalArgumentException after removing discriminatorType value [JPAB-1090](https://issues.jpa-buddy.com/issue/JPAB-1090)
  - 'java.lang.Throwable: Invalid file' when opening some entity, repository and liquibase files [JPAB-1080](https://issues.jpa-buddy.com/issue/JPAB-1080)
- Other improvements and fixes, see [all resolved issues (15)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%204.X%20Bug%20fix:%205).

## 4.5 - 2021-08-09

- Liquibase/Flyway diff generator:
  - Fixed diff generation for entity attributes with generic types [JPAB-1087](https://issues.jpa-buddy.com/issue/JPAB-1087)
  - Bidirectional many-to-many associations with implicit join column names are generated in compliance with Hibernate ImplicitNamingStrategyJpaCompliantImpl [JPAB-1089](https://issues.jpa-buddy.com/issue/JPAB-1089)
  - Fixed DTYPE update and create column statements order [JPAB-1081](https://issues.jpa-buddy.com/issue/JPAB-1081)
- JPA Inspector improvements:
  - @DiscriminatorColumn properties are no longer deleted for JOINED inheritance strategy [JPAB-1055](https://issues.jpa-buddy.com/issue/JPAB-1055)
  - Fixed dynamic projection generating without the generic parameter [JPAB-1063](https://issues.jpa-buddy.com/issue/JPAB-1063)
  - Clearing the 'length' field does not cause 'Incorrect length value' validation anymore [JPAB-1078](https://issues.jpa-buddy.com/issue/JPAB-1078)
- Persistence Unit property is no longer ignored during JSON snapshot generation [JPAB-1071](https://issues.jpa-buddy.com/issue/JPAB-1071)
- Fixed '@Table annotation should not be used together with SINGLE_TABLE inheritance strategy.' inspection being shown for wrong inheritance strategies [JPAB-1076](https://issues.jpa-buddy.com/issue/JPAB-1076)
- Search field for JPA Palette now works for the 'Utilities' tab too [JPAB-1070](https://issues.jpa-buddy.com/issue/JPAB-1070)
- Fixed the following exceptions:
  - NullPointerException during line markers processing in some Kotlin projects [JPAB-1073](https://issues.jpa-buddy.com/issue/JPAB-1073)
  - IncorrectOperationException when saving diff changelog file [JPAB-1072](https://issues.jpa-buddy.com/issue/JPAB-1072)
  - IllegalStateException when invoking "Create JPA Entity" fix [JPAB-1074](https://issues.jpa-buddy.com/issue/JPAB-1074)
  - IllegalArgumentException after removing discriminatorType value [JPAB-1090](https://issues.jpa-buddy.com/issue/JPAB-1090)
  - 'java.lang.Throwable: Invalid file' when opening some entity, repository and liquibase files [JPAB-1080](https://issues.jpa-buddy.com/issue/JPAB-1080)
- Other improvements and fixes, see [all resolved issues (15)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%204.X%20Bug%20fix:%205).

## 4.4 - 2021-07-27

- Kotlin immutable properties are now generated with "protected set" instead of "private set" [JPAB-1002](https://issues.jpa-buddy.com/issue/JPAB-1002)
- "Repositories" section of JPA Structure tree is displayed only if the Spring Data JPA dependency is detected [JPAB-982](https://issues.jpa-buddy.com/issue/JPAB-982)
- Fixed the JPA Palette search for Liquibase files [JPAB-1003](https://issues.jpa-buddy.com/issue/JPAB-1003)
- Flyway/Liquibase diff generator improvements and fixes:
  - Supported associations for entities with generic ids [JPAB-1030](https://issues.jpa-buddy.com/issue/JPAB-1030)
  - Fixed empty/incorrect DDL being generated for entities with mixed-case table names [JPAB-999](https://issues.jpa-buddy.com/issue/JPAB-999), [JPAB-1000](https://issues.jpa-buddy.com/issue/JPAB-1000)
  - @Lob support for properties with JPA converters and Hibernate types [JPAB-1041](https://issues.jpa-buddy.com/issue/JPAB-1041)
  - Fixed "Include To" field being pre-filled with a deleted changelog file [JPAB-1031](https://issues.jpa-buddy.com/issue/JPAB-1031)
- Fixed the following exceptions:
  - IllegalArgumentException during repository method modification [JPAB-1036](https://issues.jpa-buddy.com/issue/JPAB-1036)
  - Throwable: Slow operations are prohibited on EDT in IntelliJ IDEA 2021.2 EAP [JPAB-1007](https://issues.jpa-buddy.com/issue/JPAB-1007)
  - NullPointerException when using the "Show DDL..." action [JPAB-1012](https://issues.jpa-buddy.com/issue/JPAB-1012)
  - NullPointerException during diff changes generation for entities with JOINED inheritance strategy [JPAB-1033](https://issues.jpa-buddy.com/issue/JPAB-1033)
  - ClassCastException during JPA Inspector "boolean" table cell render [JPAB-1011](https://issues.jpa-buddy.com/issue/JPAB-1011)
  - ClassCastException during when adding equals/hashCode methods from JPA Palette [JPAB-1008](https://issues.jpa-buddy.com/issue/JPAB-1008)
- Other improvements and fixes, see [all resolved issues (26)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%204.X%20Bug%20fix:%204).

## 4.3 - 2021-07-19

Fixed exception for kotlin project:
*NoSuchMethodError occurs when working with kotlin projects after update kotlin plugin to 1.5.21* [JPAB-1029](https://issues.jpa-buddy.com/issue/JPAB-1029)

## 4.2 - 2021-07-08

In this release we mostly focused on cleaning up different bugs. The following issues have been resolved:

- "Drop column" and "Create column" changes showing over and over in Liquibase diff generator for some attribute types [JPAB-964](https://issues.jpa-buddy.com/issue/JPAB-964)
- PsiInvalidElementAccessException: Element class com.intellij.psi.impl.source.tree.java.ClassElement of type CLASS [JPAB-962](https://issues.jpa-buddy.com/issue/JPAB-962)
- JPA Structure not displaying the nodes during code edit in some projects [JPAB-983](https://issues.jpa-buddy.com/issue/JPAB-983)
- Incorrect Liquibase/Flyway diff generation for embedded attributes from @MappedSuperclass parent classes [JPAB-979](https://issues.jpa-buddy.com/issue/JPAB-979)
- Unsupported member type exception when using the "Create Entity" quick-fix [JPAB-961](https://issues.jpa-buddy.com/issue/JPAB-961)
- Incorrect behavior when editing a @Lob attribute using JPA Inspector: length should not be editable [JPAB-940](https://issues.jpa-buddy.com/issue/JPAB-940)
- NullPointerException when generating index name [JPAB-972](https://issues.jpa-buddy.com/issue/JPAB-972)
- ArrayIndexOutOfBoundsException when removing changes from diff generator preview dialog [JPAB-925](https://issues.jpa-buddy.com/issue/JPAB-925)
- ArrayIndexOutOfBoundsException when activating JPA Palette in invalid entity classes [JPAB-971](https://issues.jpa-buddy.com/issue/JPAB-971)
- Unclear error message when generating a repository for entity with no id [JPAB-951](https://issues.jpa-buddy.com/issue/JPAB-951)

## 4.1 - 2021-06-23

- Support Oracle SID connection in IDEA Ultimate [JPAB-949](https://issues.jpa-buddy.com/issue/JPAB-949)
- New setting: which case to generate index and constraint names in [JPAB-480](https://issues.jpa-buddy.com/issue/JPAB-480)
- JPA inspector now shows both the logical names and physical (used in the DB) names of columns and tables [JPAB-889](https://issues.jpa-buddy.com/issue/JPAB-889)
- Supported "Find First" in Spring Data repository method constructors [JPAB-871](https://issues.jpa-buddy.com/issue/JPAB-871)
- "Make X ManyToOne association" and "Create JPA Entity X" quick fixes improvement: JoinColumn is now generated with "name" [JPAB-897](https://issues.jpa-buddy.com/issue/JPAB-897)
- Fixed unnecessary DTYPE column being generated in Hibernate for JOINED inheritance strategy [JPAB-942](https://issues.jpa-buddy.com/issue/JPAB-942)
- Supported entities with an empty @Table annotation in Liquibase/Flyway/SQL generators [JPAB-948](https://issues.jpa-buddy.com/issue/JPAB-948)
- Fixed exceptions:
  - ArrayIndexOutOfBoundsException when generating a table in an SQL file with several DBs enabled [JPAB-921](https://issues.jpa-buddy.com/issue/JPAB-921)
  - "The column type is undefined" exception during diff generation if an @ElementCollection attribute is defined in a @MappedSuperclass entity [JPAB-915](https://issues.jpa-buddy.com/issue/JPAB-915)
  - IllegalArgumentException when adding @Inheritance strategy to an entity [JPAB-920](https://issues.jpa-buddy.com/issue/JPAB-920)
  - IllegalStateException: "Entity PsiClass from SmartPsiElementPointer is null" during plugin update [JPAB-924](https://issues.jpa-buddy.com/issue/JPAB-924)
- Other smaller improvements and fixes, find the full list in our [issue tracker](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%204.X%20Bug%20fix:%201).

## 4.0 - 2021-06-10

- Visual designers for SQL files [JPAB-660](https://issues.jpa-buddy.com/issue/JPAB-660)
- Ability to generate SQL table creation scripts for entities ("Show DDL" action) [JPAB-430](https://issues.jpa-buddy.com/issue/JPAB-430)
- Liquibase and Flyway diff generator improvements:
  - Support for @ElementCollection and @CollectionTable [JPAB-777](https://issues.jpa-buddy.com/issue/JPAB-777)
  - Support for @MapsId [JPAB-446](https://issues.jpa-buddy.com/issue/JPAB-446) [JPAB-855](https://issues.jpa-buddy.com/issue/JPAB-855)
  - Unidirectional @OneToMany without @JoinColumn [JPAB-691](https://issues.jpa-buddy.com/issue/JPAB-691)
  - Smart handling of generated "addNotNullConstraint" [JPAB-460](https://issues.jpa-buddy.com/issue/JPAB-460)
  - Max identifier length setting [JPAB-271](https://issues.jpa-buddy.com/issue/JPAB-271)
  - @EmbeddedId improvements [JPAB-859](https://issues.jpa-buddy.com/issue/JPAB-859) [JPAB-852](https://issues.jpa-buddy.com/issue/JPAB-852)
  - Snapshots are only supported in their main use case now: comparing model to a snapshot. Comparing snapshots and DBs has been disabled as it doesn't have enough information about the data types [JPAB-805](https://issues.jpa-buddy.com/issue/JPAB-805)
- "Diff Changes" action in the JPA Palette for Liquibase changelogs and SQL files [JPAB-783](https://issues.jpa-buddy.com/issue/JPAB-783)
- Flyway callbacks in Java, Kotlin and SQL [JPAB-591](https://issues.jpa-buddy.com/issue/JPAB-591)
- Ability to create Java/Kotlin Flyway migrations [JPAB-635](https://issues.jpa-buddy.com/issue/JPAB-635)
- JPA Palette elements can now be added to the file via drag and drop [JPAB-533](https://issues.jpa-buddy.com/issue/JPAB-533)
- Liquibase changelogs display in JPA Palette is now based on their hierarchy, not the folder structure [JPAB-485](https://issues.jpa-buddy.com/issue/JPAB-485)
- New intentions and action for entities:
  - Create index by attribute intention [JPAB-132](https://issues.jpa-buddy.com/issue/JPAB-132)
  - Generate a repository method from attribute intention [JPAB-295](https://issues.jpa-buddy.com/issue/JPAB-295)
  - "Generate"->"Referenced Entity" action [JPAB-705](https://issues.jpa-buddy.com/issue/JPAB-705)
- Equals() and hashCode() are generated with Objects.equals() and Objects.hash() for Java 1.7+ [JPAB-804](https://issues.jpa-buddy.com/issue/JPAB-804)
- JPA Palette supports entities and repositories in the same Kotlin file [JPAB-851](https://issues.jpa-buddy.com/issue/JPAB-851)
- **Important: table and column names are generated in lower case by default now.** To restore the old behavior, go to Settings -> JPA Buddy -> Entity Declaration and change all the "toLowerCase()" calls to "toUpperCase() in the name templates [JPAB-710](https://issues.jpa-buddy.com/issue/JPAB-710)
- JPA Buddy elements are grouped into categories in the New menu of the project tree [JPAB-727](https://issues.jpa-buddy.com/issue/JPAB-727)
- Support for IDEA 2021.2 [JPAB-863](https://issues.jpa-buddy.com/issue/JPAB-863)
- Other smaller improvements and fixes, find the full list in our [issue tracker](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%204.X%20Bug%20fix:%200).

## 3.2 - 2021-05-26

Another release making JPA Buddy more stable and easy to use!

- Kotlin code generation improvements and fixes
  - Attributes are generated with the *open* modifier if no all-open plugin is detected [JPAB-833](https://issues.jpa-buddy.com/issue/JPAB-833)
  - To-many associations are generated with non-null types [JPAB-835](https://issues.jpa-buddy.com/issue/JPAB-835)
  - toString(), equals() and hashCode() generation fix for data classes [JPAB-841](https://issues.jpa-buddy.com/issue/JPAB-841)
  - Code inspection and quick fix to generate equals() and hashCode() for data classes if there are non-id fields in the primary constructor [JPAB-845](https://issues.jpa-buddy.com/issue/JPAB-845)
- Support for enum types without @Enumerated in Liquibase/Flyway diff generation [JPAB-846](https://issues.jpa-buddy.com/issue/JPAB-846)
- Added support of array types to the "Assign JPA converter" quick fix [JPAB-800](https://issues.jpa-buddy.com/issue/JPAB-800)
- Fixed Velocity error when generating a OneToMany association in an entity with no @Column on @Id [JPAB-834](https://issues.jpa-buddy.com/issue/JPAB-834)
- Fixed exceptions:
  - TraceableDisposable.ObjectNotDisposedException [JPAB-848](https://issues.jpa-buddy.com/issue/JPAB-848)
  - PSI RuntimeExceptionWithAttachments [JPAB-842](https://issues.jpa-buddy.com/issue/JPAB-842)
  - Throwable after trying to update the JPA Buddy plugin with enabled Jmix plugin [JPAB-828](https://issues.jpa-buddy.com/issue/JPAB-828)
- Other bugfixes, the full list can be found in [the issue tracker](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Type:%20Bug,%20Exception%20%20Milestone:%203.X%20Bug%20fix:%202)

## 3.1 - 2021-05-13

This release makes plugin significantly more stable as it introduces [multiple bugfixes](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Type:%20Bug,%20Exception%20%20Milestone:%203.X%20Bug%20fix:%201). **Thanks to all members of the community who are helping us to make JPA Buddy better!**

- **Fixed bug with: \*java.lang.ClassNotFoundException: org.jetbrains.kotlin.psi.KtElement\***
- Supported annotation over getters. All actions including fields creation, Liquibase and Flyway scripts generation work correctly with getter-annotated properties [JPAB-276](https://issues.jpa-buddy.com/issue/JPAB-276)
- Support for JPA properties declared as constructor fields in Kotlin classes [JPAB-268](https://issues.jpa-buddy.com/issue/JPAB-268)
- Support for Spring Data projections in Kotlin [JPAB-614](https://issues.jpa-buddy.com/issue/JPAB-614)
- Added an option to define @OneToOne and @ManyToOne attributes with FetchType.LAZY by default [JPAB-557](https://issues.jpa-buddy.com/issue/JPAB-557)
- Enabled ability to define a scope (All places, Project, Project and libs, Project and tests, Tests only) for diff scripts generation for both Liquibase and Flyway scripts [JPAB-723](https://issues.jpa-buddy.com/issue/JPAB-723)
- toString() method uses getSimpleName instead of fixed literal of the class. Now it works well for inherited entities [JPAB-700](https://issues.jpa-buddy.com/issue/JPAB-700)
- Enabled the @Digits Hibernate validation for String attributes [JPAB-703](https://issues.jpa-buddy.com/issue/JPAB-703)
- Support for JpaSpecificationExecutor in Spring Data repository declaration [JPAB-525](https://issues.jpa-buddy.com/issue/JPAB-525)

## 3.0 - 2021-04-28

- Kotlin support [alpha phase] [JPAB-586](https://issues.jpa-buddy.com/issue/JPAB-586):
  - Visual designers for Kotlin entities and repositories
  - Utility methods generation: equals(), hashCode() and toString()
  - Hibernate Custom Types and JPA Converters support
  - Kotlin entities and repositories in JPA Structure
- Flyway support:
  - Diff versioned migration script generation [JPAB-634](https://issues.jpa-buddy.com/issue/JPAB-634)
  - Empty Flyway script creation [JPAB-587](https://issues.jpa-buddy.com/issue/JPAB-587)
  - Data model snapshots as source/target in diff script generation [JPAB-653](https://issues.jpa-buddy.com/issue/JPAB-653)
- Error monitoring integration with Sentry [JPAB-667](https://issues.jpa-buddy.com/issue/JPAB-667)
- Database Versioning settings reorganization [JPAB-643](https://issues.jpa-buddy.com/issue/JPAB-643)
- Async repository methods [JPAB-416](https://issues.jpa-buddy.com/issue/JPAB-416)
- Unidirectional OneToMany with JoinColumn support [JPAB-156](https://issues.jpa-buddy.com/issue/JPAB-156)
- [Other smaller fixes and improvements](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%203.X%20%20order%20by:%20Type%20,%20Priority)

## 2.2 - 2021-04-07

- Supported IgnoreCase operation for Spring Data conditions [JPAB-458](https://issues.jpa-buddy.com/issue/JPAB-458)
- Limited Wrap type options for methods with Pageable parameter [JPAB-465](https://issues.jpa-buddy.com/issue/JPAB-465)
- Disallowed to select Pageable and Sortable for one method at the same time [JPAB-470](https://issues.jpa-buddy.com/issue/JPAB-470)
- Added inspection for @Builder/@AllArgsConstructor with no @NoArgsConstructor on an entity [JPAB-680](https://issues.jpa-buddy.com/issue/JPAB-680), [JPAB-655](https://issues.jpa-buddy.com/issue/JPAB-655)
- Both nested levels are expanded in the JPA Structure when using "Select in JPA Structure" button [JPAB-677](https://issues.jpa-buddy.com/issue/JPAB-677)
- Renamed "Main changelog" and "Main directory" from liquibase general settings to "Primary changelog" and "Primary directory"
- java.lang.Throwable: Write-unsafe context exception during project initialization in 2021.1 EAP [JPAB-625](https://issues.jpa-buddy.com/issue/JPAB-625)

## 2.1 - 2021-03-24

- Support entity collection attributes for spring data methods [JPAB-601](https://issues.jpa-buddy.com/issue/JPAB-601)
- Generated without business key equals method breaks it's contract [JPAB-636](https://issues.jpa-buddy.com/issue/JPAB-636)
- Improve "Show SQL" action [JPAB-583](https://issues.jpa-buddy.com/issue/JPAB-583)
- Suppress inspection "Equals() method should check the class of its parameter" [JPAB-644](https://issues.jpa-buddy.com/issue/JPAB-644)
- Avoid proxy class compression in equals method [JPAB-629](https://issues.jpa-buddy.com/issue/JPAB-629)
- Deadlock, probably caused by JPA Buddy [JPAB-627](https://issues.jpa-buddy.com/issue/JPAB-627)
- Exception during petclinic inizialization after importing it from vcs (IndexNotReadyException) [JPAB-607](https://issues.jpa-buddy.com/issue/JPAB-607)
- False positive inspection for Embedded Id is shown [JPAB-626](https://issues.jpa-buddy.com/issue/JPAB-626)

## 2.0 - 2021-03-10

* General
  * Lombok support: Lombok annotations for entity/attribute generation; code inspections and intentions
  * Integration with IntelliJ IDEA Ultimate's Data Sources
  * 'Select in JPA Structure' button for navigating to the opened source code file in JPA Structure
  * Entities found via @EntityScan are added to the default persistence unit in JPA Structure
  * 'Detect Connections' action to add DB connections from application.properties to JPA Structure
  * JDBC drivers are now downloaded from the Internet, not bundled with the plugin
* Spring Data
  * @Query method generation for Spring Data repositories
  * Repository methods modification via the JPA Inspector panel
  * Creating Spring Data JPA projections via a special action (New -> Projection) and an intention in a repository class
* JPA
  * mappedBy inspections and intentions for @OneToOne, @OneToMany and @ManyToMany
  * Support for table, entity and column names to be stored in constants
  * Support for @AttributeOverride(s) / @AssociationOverride(s) for embedded attributes in JPA Inspector
* Liquibase
  * Ability to specify the PhysicalNamingStrategy for Liquibase changelog generation
  * Ability to include the newly generated Liquibase changelog or its folder into another changelog during preview
  * Showing Liquibase execution log to the user
  * Ability to set default DB connections for persistence units in the Diff Database Changelog dialog
  * Ability to set the author of the Liquibase changesets during changelog generation
  * Join table names are generated based on the ImplicitNamingStrategy when no @JoinTable is specified for @ManyToMany association
* Other smaller improvements and fixes

## 1.3 - 2021-02-16

- Fixed bug with automatic scanning of data sources
  `com.intellij.openapi.project.IndexNotReadyException: Please change caller according to com.intellij.openapi.project.IndexNotReadyException documentation`

## 1.2 - 2021-01-27

- Fixed bug with building **JPA Structure** tree
  `java.lang.ClassNotFoundException: com.intellij.lang.properties.PropertiesFileType`
- Improve liquibase library search

## 1.1 - 2020-12-29

- Various bug fixes

## 1.0 - 2020-12-15

This is the first release of the JPA Buddy!

- JPA Entity designer
- Liquibase changelog generation: model to DB, model to model through snapshots
- Liquibase changelog designer
- Spring Data Repository designer
- JPA Structure panel displaying hierarchy of entity relations

Take a look at the [Features](https://plugins.jetbrains.com/plugin/15075-jpa-buddy/features) plugin page for more detailed features description.
