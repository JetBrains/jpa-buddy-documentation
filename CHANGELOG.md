# Changelog

## 2023.2.0 – 2023-05-15

### Liquibase/Flyway/DDL Diff Generator

* To streamline Liquibase changelog generation, we added the ability to specify changeset templates. This new feature automates repetitive tasks, such as generating correct preconditions and empty rollbacks when using the rollback feature in Liquibase <a href="https://issues.jpa-buddy.com/issue/JPAB-1418" target="_blank">JPAB-1418</a>
* The `@Comment` annotation from Hibernate has been supported for the migration script generators <a href="https://issues.jpa-buddy.com/issue/JPAB-1954" target="_blank">JPAB-1954</a>
* Since this release, JPA Buddy allows you to generate diff changes for selected entities only, providing you with more control over your migration process <a href="https://issues.jpa-buddy.com/issue/JPAB-2228" target="_blank">JPAB-2228</a>

### DTO Generator & Coding Assistance

* We supported ModelMapper for code scaffolding, on-the-fly injection, and mapping methods generation <a href="https://issues.jpa-buddy.com/issue/JPAB-2069" target="_blank">JPAB-2069</a>
* Now, JPA Buddy knows how to use the `@Value` annotation from Lombok. Generate immutable DTOs and benefit from concise code <a href="https://issues.jpa-buddy.com/issue/JPAB-2352" target="_blank">JPAB-2352</a>
* Simplify your JSON serialization process by adding the `JsonIgnoreProperties(ignoreUnknown = true)` annotation from Jackson for your DTOs, ensuring effortless compatibility and smoother data handling <a href="https://issues.jpa-buddy.com/issue/JPAB-1218" target="_blank">JPAB-1218</a>
* Kotlin's lovers can now rejoice as we added full Kotlin support for DTO synchronization features <a href="https://issues.jpa-buddy.com/issue/JPAB-2099" target="_blank">JPAB-2099</a>

### Reverse Engineering

* Defining a parent entity during Reverse Engineering is now possible, enabling you to build your entity hierarchy and maintain a well-organized project structure <a href="https://issues.jpa-buddy.com/issue/JPAB-1950" target="_blank">JPAB-1950</a>
* Now, JPA Buddy can migrate database comments using the @Comment annotation from Hibernate or Java Doc <a href="https://issues.jpa-buddy.com/issue/JPAB-1268" target="_blank">JPAB-1268</a>
* JPA Buddy now seamlessly integrates with IntelliJ IDEA Ultimate to read information from the database. This improvement has significantly enhanced the performance of the "JPA Entities from Database" action. Additionally, this allows JPA Buddy to use all the connection settings specified within the IntelliJ IDEA Ultimate interface <a href="https://issues.jpa-buddy.com/issue/JPAB-1296" target="_blank">JPAB-1296</a>

### Entity Designer

* The "Extract to MappedSuperclass" feature has become even better! Now, you can extract both attributes and methods into a MappedSuperclass <a href="https://issues.jpa-buddy.com/issue/JPAB-1692" target="_blank">JPAB-1692</a>
* You can now apply `@SuperBuilder` annotation from Lombok by using JPA Inspector <a href="https://issues.jpa-buddy.com/issue/JPAB-2480" target="_blank">JPAB-2480</a>

### Non-JPA Support

* We expanded our support by adding the ability to include attributes from non-JPA domain entities into your DTOs <a href="https://issues.jpa-buddy.com/issue/JPAB-2338" target="_blank">JPAB-2338</a>
* Also, we enhanced the navigation capabilities, you can now navigate from a DTO to a non-JPA domain entity with ease <a href="https://issues.jpa-buddy.com/issue/JPAB-2337" target="_blank">JPAB-2337</a>
* Generating MapStruct interfaces for non-JPA domain entities is also possible now <a href="https://issues.jpa-buddy.com/issue/JPAB-2372" target="_blank">JPAB-2372</a>

Last but not least, starting from this release, JPA Buddy analyzes not only the entire project for the presence of specific dependencies but also each individual module (in the case of a multi-module project). So, <a href="https://jpa-buddy.com/documentation/#dependencies" target="_blank">certain features</a> will be activated depending on the required dependencies in a module.

We're continuously working to improve your experience with JPA Buddy, and this release is no exception. For a comprehensive list of other improvements and fixes, be sure to check out <a href="https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20232%20State:%20Verified%20" target="_blank">all the resolved issues (65+)</a>.

## 2023.1.5 - 2023-04-24

* The "Generate fluent setters" option now works properly with Lombok `@Setter` annotation <a href="https://issues.jpa-buddy.com/issue/JPAB-2466" target="_blank">JPAB-2466</a>
* Fixed `StackOverflowError` caused by two Embeddable classes including each other <a href="https://issues.jpa-buddy.com/issue/JPAB-2463" target="_blank">JPAB-2463</a>
* JPA Buddy no longer generates redundant `@Table` annotation for entities with specified parent <a href="https://issues.jpa-buddy.com/issue/JPAB-2461" target="_blank">JPAB-2461</a>
* False positive "Can't find inverse attribute" error has been fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2444" target="_blank">JPAB-2444</a>
* The "ID generation" preference is no longer constantly reset to `AUTO` <a href="https://issues.jpa-buddy.com/issue/JPAB-2484" target="_blank">JPAB-2484</a>

For other improvements and fixes, see [all resolved issues (10)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20231%20Bug%20fix:%205).

## 2023.1.4 - 2023-04-10

* The DDL generator now considers final fields with the `@Builder.Default` annotation from Lombok <a href="https://issues.jpa-buddy.com/issue/JPAB-2451" target="_blank">JPAB-2451</a>
* The `@IdClass` annotation is now considered while generating Spring Data JPA repositories <a href="https://issues.jpa-buddy.com/issue/JPAB-2435" target="_blank">JPAB-2435</a>
* JPA Buddy no longer generates redundant getters/setters while performing "Extract to MappedSuperclass" with Lombok enabled <a href="https://issues.jpa-buddy.com/issue/JPAB-2441" target="_blank">JPAB-2441</a>
* The false positive entity attribute warning "This mapping declaration is not efficient and may cause performance issues" has been resolved <a href="https://issues.jpa-buddy.com/issue/JPAB-2427" target="_blank">JPAB-2427</a>
* Spring Auditing attributes are now added correctly <a href="https://issues.jpa-buddy.com/issue/JPAB-2424" target="_blank">JPAB-2424</a>

For other improvements and fixes, see [all resolved issues (9)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%20231%20Bug%20fix:%204%20State:%20-%7BCan%27t%20Reproduce%7D).

## 2023.1.3 - 2023-03-27

* The nullability algorithm for database versioning scripts now matches Hibernate's algorithm <a href="https://issues.jpa-buddy.com/issue/JPAB-2387" target="_blank">JPAB-2387</a>
* The column type is now defined if `JoinTable` refers to the parent entity with `TABLE_PER_CLASS` strategy <a href="https://issues.jpa-buddy.com/issue/JPAB-2408" target="_blank">JPAB-2408</a>
* Cosmetic problems with the custom field used for the DTO class in the Entity to DTO mapping dialog have been resolved <a href="https://issues.jpa-buddy.com/issue/JPAB-2401" target="_blank">JPAB-2401</a>
* Automatically selecting *-to-one associations after the corresponding *-to-many association is selected has been implemented <a href="https://issues.jpa-buddy.com/issue/JPAB-2409" target="_blank">JPAB-2409</a>
* The unnecessary schema name for the H2 database has been removed when adding `INSERT` statements to Liqubase script <a href="https://issues.jpa-buddy.com/issue/JPAB-2403" target="_blank">JPAB-2403</a>
* A reference to the new changelog file is now inserted at the beginning of the root changelog <a href="https://issues.jpa-buddy.com/issue/JPAB-2402" target="_blank">JPAB-2402</a>

## 2023.1.2 - 2023-03-13

* The index on view in the database no longer causes `ExecutionException` while reverse engineering <a href="https://issues.jpa-buddy.com/issue/JPAB-2381" target="_blank">JPAB-2381</a>
* You can now adjust the query conditions table size in the "Creating repository methods" wizard <a href="https://issues.jpa-buddy.com/issue/JPAB-2386" target="_blank">JPAB-2386</a>
* The Flyway init migration for MySQL no longer fails with an exception if an entity contains the id with the `SEQUENCE` generation type <a href="https://issues.jpa-buddy.com/issue/JPAB-2339" target="_blank">JPAB-2339</a>
* The improper code scaffolding for "mapTo..." postfix completion has been fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2392" target="_blank">JPAB-2392</a>
* JPA Buddy no longer throws an exception while generating differential scripts with Liquibase 4.19+ <a href="https://issues.jpa-buddy.com/issue/JPAB-2404" target="_blank">JPAB-2404</a>

For other improvements and fixes, see [all resolved issues (15+)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20project:%20%7BJPA%20Buddy%7D%20Milestone:%20231%20Bug%20fix:%202%20-%7BCan%27t%20Reproduce%7D).

## 2023.1.1 - 2023-02-22

* When using `@Type` annotation, JPA Buddy no longer produces an exception while generating Liquibase/Flyway scripts <a href="https://issues.jpa-buddy.com/issue/JPAB-2390" target="_blank">JPAB-2390</a>
* A new option to disable pluralization of entity names during reverse engineering has been added to the settings <a href="https://issues.jpa-buddy.com/issue/JPAB-2385" target="_blank">JPAB-2385</a>
* The `equals()` method now accesses fields through getters <a href="https://issues.jpa-buddy.com/issue/JPAB-2367" target="_blank">JPAB-2367</a>

## 2023.1.0 - 2023-02-20

### DTO Generator & Coding Assistance

* The DTO Generator was untied from entities, so now it's possible to create a DTO for any domain model class, including MongoDB document or even not-annotated POJO. Quick fix for unresolved references also supports such options <a href="https://issues.jpa-buddy.com/issue/JPAB-2064" target="_blank">JPAB-2064</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2336" target="_blank">JPAB-2336</a>
* Now, completion contributor functionality and quick fixes for unresolved references are available in Kotlin <a href="https://issues.jpa-buddy.com/issue/JPAB-2022" target="_blank">JPAB-2022</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2093" target="_blank">JPAB-2093</a>
* Improved settings for more detailed customization of which autocompletion options the user wants to see or hide <a href="https://issues.jpa-buddy.com/issue/JPAB-2240" target="_blank">JPAB-2240</a>

### Liquibase/Flyway/DDL Diff Generator

* Support of `@ForeignKey` annotation was added <a href="https://issues.jpa-buddy.com/issue/JPAB-270" target="_blank">JPAB-270</a>
* Added more options to specify the column data type for the entity attribute type or backward using annotations `@JavaType`, `@Type` or `@JdbcType` <a href="https://issues.jpa-buddy.com/issue/JPAB-1888" target="_blank">JPAB-1888</a>, <a href="https://issues.jpa-buddy.com/issue/JPAB-1887" target="_blank">JPAB-1887</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2340" target="_blank">JPAB-2340</a>
* Now, JPA Buddy correctly generates foreign key constraints for association attributes with generic type <a href="https://issues.jpa-buddy.com/issue/JPAB-860" target="_blank">JPAB-860</a>

### Entity Designer

* Ability to adjust `@Audited` and `@EntityListeners` annotations was added to the inspector <a href="https://issues.jpa-buddy.com/issue/JPAB-2216" target="_blank">JPAB-2216</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2217" target="_blank">JPAB-2217</a>
* Now, the user can specify column length for string enumeration <a href="https://issues.jpa-buddy.com/issue/JPAB-2158" target="_blank">JPAB-2158</a>
* Improved detecting of Lombok dependency to use it in entities <a href="https://issues.jpa-buddy.com/issue/JPAB-2321" target="_blank">JPAB-2321</a>

### Other

* JPA Buddy is now available for IntelliJ IDEA 2023.1 <a href="https://issues.jpa-buddy.com/issue/JPAB-2316" target="_blank">JPAB-2316</a>
* The ability to separate tool windows is back <a href="https://issues.jpa-buddy.com/issue/JPAB-2223" target="_blank">JPAB-2223</a>
* Added support of YAML configuration files as sources to detect connection parameters <a href="https://issues.jpa-buddy.com/issue/JPAB-2134" target="_blank">JPAB-2134</a>

For other improvements and fixes, see <a href="https://issues.jpa-buddy.com/issues?q=%23Resolved%20%20project:%20%7BJPA%20Buddy%7D%20Milestone:%20231" target="_blank">all resolved issues (50+)</a>.

## 2022.5.5 - 2023-13-02

* Now, JPA Buddy generates correct migration scripts for indexes that contain a column with `DESC` keyword <a href="https://issues.jpa-buddy.com/issue/JPAB-2346" target="_blank">JPAB-2346</a>
* Inappropriate actions are not shown anymore for MongoDB files <a href="https://issues.jpa-buddy.com/issue/JPAB-2327" target="_blank">JPAB-2327</a>
* Added validation warning when one tries to create a duplicate of an entity from DB <a href="https://issues.jpa-buddy.com/issue/JPAB-2354" target="_blank">JPAB-2354</a>
* Corrected Kotlin support in DTO generation and interaction with repository methods <a href="https://issues.jpa-buddy.com/issue/JPAB-2365" target="_blank">JPAB-2365</a>, <a href="https://issues.jpa-buddy.com/issue/JPAB-2351" target="_blank">JPAB-2351</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2289" target="_blank">JPAB-2289</a>

For other improvements and fixes, see <a href = "https://issues.jpa-buddy.com/issues/JPAB?q=project:%20JPAB%20%23Resolved%20Milestone:%20225%20Bug%20fix:%205%20State:%20-Duplicate">all resolved issues (8)</a>.

## 2022.5.4 - 2023-30-01

* Now, JPA Buddy provides the correct DDL in the "Show DDL" action for the case when `@ElementCollection` is declared inside an `@Embeddable` entity <a href="https://issues.jpa-buddy.com/issue/JPAB-2310" target="_blank">JPAB-2310</a>
* The `referencedColumnName` parameter of the `@JoinColumn` annotation is now correctly considered when generating migration scripts <a href="https://issues.jpa-buddy.com/issue/JPAB-2301" target="_blank">JPAB-2301</a>
* The wrong generation of the MapStruct mapper in the entity package, not in the specified one, has been fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2313" target="_blank">JPAB-2313</a>
* Redundant `@Getter`/`@Setter` Lombok annotations are no longer generated for M2M associations <a href="https://issues.jpa-buddy.com/issue/JPAB-2282" target="_blank">JPAB-2282</a>
* `PluginException`, `ClassCastException`, `RuntimeExceptionWithAttachments` and `Throwable` exceptions were handled <a href="https://issues.jpa-buddy.com/issue/JPAB-2295" target="_blank">JPAB-2295</a>, <a href="https://issues.jpa-buddy.com/issue/JPAB-2306" target="_blank">JPAB-2306</a>, <a href="https://issues.jpa-buddy.com/issue/JPAB-2328" target="_blank">JPAB-2328</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2329" target="_blank">JPAB-2329</a>


For other improvements and fixes, see [all resolved issues (15+)](https://issues.jpa-buddy.com/issues?q=project:%20JPAB%20%23Resolved%20Milestone:%20225%20Bug%20fix:%204%20).

## 2022.5.3 - 2023-16-01

* Now, JPA Buddy creates the correct sequence for IDs annotated with `@GeneratedValue(strategy = GenerationType.SEQUENCE)` in projects with Hibernate 6 <a href="https://issues.jpa-buddy.com/issue/JPAB-2268" target="_blank">JPAB-2268</a>
* For PostgreSQL, JPABuddy now generates an `OID` column instead of `TEXT` for fields annotated with `@Lob` <a href="https://issues.jpa-buddy.com/issue/JPAB-2276" target="_blank">JPAB-2276</a>
* `RuntimeExceptionWithAttachments` no longer appears at the time of the project opening <a href="https://issues.jpa-buddy.com/issue/JPAB-2270" target="_blank">JPAB-2270</a>
* False negative highlights for the MapStruct `@Mapper` annotation when an entity comes from external dependency was fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2275" target="_blank">JPAB-2275</a>
* A redundant unique constraint for the primary key is no longer generated <a href="https://issues.jpa-buddy.com/issue/JPAB-2273" target="_blank">JPAB-2273</a>

For other improvements and fixes, see [all resolved issues (15+)](https://issues.jpa-buddy.com/issues/JPAB?q=project:%20JPAB%20%23Resolved%20Milestone:%20225%20Bug%20fix:%203%20).


## 2022.5.2 - 2022-20-12

* Smart completions from JPA Buddy no longer appear before most suited IntelliJ IDEA options <a href="https://issues.jpa-buddy.com/issue/JPAB-2239" target="_blank">JPAB-2239</a>
* JPA Buddy no longer skips columns from the `@Embedded` attribute of `@MappedSuperclass` type <a href="https://issues.jpa-buddy.com/issue/JPAB-2247" target="_blank">JPAB-2247</a>
* "The incoming YAML document exceeds the limit" exception during reverse engineering was fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2242" target="_blank">JPAB-2242</a>
* Fixed non-critical but often happening exceptions <a href="https://issues.jpa-buddy.com/issue/JPAB-2253" target="_blank">JPAB-2253</a>, <a href="https://issues.jpa-buddy.com/issue/JPAB-2249" target="_blank">JPAB-2249</a>, <a href="https://issues.jpa-buddy.com/issue/JPAB-2248" target="_blank">JPAB-2248</a>

For other improvements and fixes, see [all resolved issues (10+)](https://issues.jpa-buddy.com/issues/JPAB?q=%23Resolved%20Milestone:%20225%20Bug%20fix:%202%20).

## 2022.5.1 - 2022-07-12

* The exception while calculating Liquibase actions was fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2222" target="_blank">JPAB-2222</a>
* Displaying tool window no longer causes `IndexNotReadyException` <a href="https://issues.jpa-buddy.com/issue/JPAB-2221" target="_blank">JPAB-2221</a>
* The false availability of the "Create DTO..." quick-fix has been fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2219" target="_blank">JPAB-2219</a>
* The Spring Data JPA Repository for inherited entities is now generated properly <a href="https://issues.jpa-buddy.com/issue/JPAB-2210" target="_blank">JPAB-2210</a>
* Now, the MapStruct mapper can link the associated attribute, even after renaming <a href="https://issues.jpa-buddy.com/issue/JPAB-2209" target="_blank">JPAB-2209</a>

## 2022.5.0 - 2022-05-12

### Coding Assistance

JPA Buddy introduces coding assistance features for JPA entities, Spring Data repositories, DTOs and MapStruct mappers that make development more straightforward and transparent:

* Create and inject Spring Data Repositories & MapStruct mappers on the fly <a href="https://issues.jpa-buddy.com/issue/JPAB-2054" target="_blank">JPAB-2054</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2023" target="_blank">JPAB-2023</a>
* Generate Spring Data methods/queries via smart postfix completions <a href="https://issues.jpa-buddy.com/issue/JPAB-2038" target="_blank">JPAB-2038</a>
* Apply mappings via "mapTo..." postfix completion <a href="https://issues.jpa-buddy.com/issue/JPAB-2052" target="_blank">JPAB-2052</a>
* Generate JPA-related objects from unresolved references <a href="https://issues.jpa-buddy.com/issue/JPAB-2141" target="_blank">JPAB-2141</a>

### DTO Generator

* Now, you can generate JPA entities from any java/kotlin class <a href="https://issues.jpa-buddy.com/issue/JPAB-1727" target="_blank">JPAB-1727</a>
* MapStruct mapper can now be generated from separate wizard <a href="https://issues.jpa-buddy.com/issue/JPAB-1913" target="_blank">JPAB-1913</a>
* You can now add fields from the entity to its DTOs and vice versa <a href="https://issues.jpa-buddy.com/issue/JPAB-2001" target="_blank">JPAB-2001</a>
* Generic MapStruct mappers have been supported <a href="https://issues.jpa-buddy.com/issue/JPAB-2055" target="_blank">JPAB-2055</a>

### Entity Designer

* All three JPA Buddy tool windows (Structure, Panel and Inspector) now represent a unified panel <a href="https://issues.jpa-buddy.com/issue/JPAB-1906" target="_blank">JPAB-1906</a>
* You can now view entities hierarchy from Editor Toolbar <a href="https://issues.jpa-buddy.com/issue/JPAB-1989" target="_blank">JPAB-1989</a>
* The "Entity Declaration" settings were improved <a href="https://issues.jpa-buddy.com/issue/JPAB-1899" target="_blank">JPAB-1899</a>

### Liquibase/Flyway/DDL Diff Generator

* `@TimeZoneStorage` and `@TimeZoneColumn` annotations from Hibernate 6 have been supported <a href="https://issues.jpa-buddy.com/issue/JPAB-1893" target="_blank">JPAB-1893</a>
* Now, you can create liquibase changelogs from unresolved references <a href="https://issues.jpa-buddy.com/issue/JPAB-1788" target="_blank">JPAB-1788</a>
* Changes that can be merged are now highlighted with the special icon in the preview dialog <a href="https://issues.jpa-buddy.com/issue/JPAB-1589" target="_blank">JPAB-1589</a>

For other improvements and fixes, see [all resolved issues (60+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20225%20%20State:%20Fixed,%20Verified%20sort%20by:%20Priority).

## 2022.4.7 - 2022-28-11

* Now, the script for the `@ManyToMany` association ID is generated properly <a href="https://issues.jpa-buddy.com/issue/JPAB-2173" target="_blank">JPAB-2173</a>
* The "Navigate to JPA converter" line marker no longer appears outside of the entity classes <a href="https://issues.jpa-buddy.com/issue/JPAB-2171" target="_blank">JPAB-2171</a>
* The "Spring Data Projection" action is no longer available without corresponding Spring dependency <a href="https://issues.jpa-buddy.com/issue/JPAB-2168" target="_blank">JPAB-2168</a>
* Now, JPA Buddy remembers the previously selected `GenerationType` even after deleting the ID attribute <a href="https://issues.jpa-buddy.com/issue/JPAB-2180" target="_blank">JPAB-2180</a>
* The `@GeneratedValue` annotation is no longer mistakenly added to the ID attribute marked with the `@EmbeddedId` annotation <a href="https://issues.jpa-buddy.com/issue/JPAB-2179" target="_blank">JPAB-2179</a>

## 2022.4.6 - 2022-14-11

### Bug-fix

* `@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)` annotation over abstract class no longer causes redundant scripts generation <a href="https://issues.jpa-buddy.com/issue/JPAB-2146" target="_blank">JPAB-2146</a>
* Now, JPA Buddy properly handles `@PrimaryKeyJoinColumn` annotation for Liquibase diff generator <a href="https://issues.jpa-buddy.com/issue/JPAB-2147" target="_blank">JPAB-2147</a>
* Fixed an issue with incorrect scripts generation for tables from non-default database schemas <a href="https://issues.jpa-buddy.com/issue/JPAB-2148" target="_blank">JPAB-2148</a>
* JPA Buddy "Minimalistic Mode" action is now avalable in View menu <a href="https://issues.jpa-buddy.com/issue/JPAB-2151" target="_blank">JPAB-2151</a>
* Fixed incorrect display of the "DB Type Selection" wizard for IntelliJ IDEA EAP 2022.3 <a href="https://issues.jpa-buddy.com/issue/JPAB-2159" target="_blank">JPAB-2159</a>

## 2022.4.5 - 2022-31-10

### Bug-fix

* JPA Buddy is now available for IntelliJ IDEA 2022.3 <a href="https://issues.jpa-buddy.com/issue/JPAB-2090" target="_blank">JPAB-2090</a>
* `ClassCastException` no longer appears while generating Kotlin data class as DTO from the Java entity <a href="https://issues.jpa-buddy.com/issue/JPAB-2128" target="_blank">JPAB-2128</a>
* Fixed `MethodInvocationException` for the case when owning entity does not have a column annotation for the `id` attribute <a href="https://issues.jpa-buddy.com/issue/JPAB-2136" target="_blank">JPAB-2136</a>

## 2022.4.4 - 2022-17-10

### Bug-fix

* Fixed an exception happening while looking for persistence units <a href="https://issues.jpa-buddy.com/issue/JPAB-2129" target="_blank">JPAB-2129</a>

## 2022.4.3 - 2022-17-10

### Bug-fix

* `@OneToMany` association in MappedSuperclass no longer causes exceptions for Liquibase/Flyway/DDL Generators <a href="https://issues.jpa-buddy.com/issue/JPAB-2103" target="_blank">JPAB-2103</a>
* Fixed duplicated `addColumn` change for Liquibase generate diff changelog action <a href="https://issues.jpa-buddy.com/issue/JPAB-2124" target="_blank">JPAB-2124</a>
* DTO line markes collecting no longer produces `NullPointerException` <a href="https://issues.jpa-buddy.com/issue/JPAB-2123" target="_blank">JPAB-2123</a>
* Now, JPA Buddy properly displays all entities in the hierarchy tree for the projects with Micronaut dependencies <a href="https://issues.jpa-buddy.com/issue/JPAB-2102" target="_blank">JPAB-2102</a>
* Fixed non-critical but often happening exceptions <a href="https://issues.jpa-buddy.com/issue/JPAB-2085" target="_blank">JPAB-2085</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2086" target="_blank">JPAB-2086</a>

## 2022.4.2 - 2022-27-09

### Bug-fix
* Redundant `@FetchType.LAZY` no longer generated for the inverse side of the one-to-one association while reverse engineering <a href="https://issues.jpa-buddy.com/issue/JPAB-2059" target="_blank">JPAB-2059</a>
* Fixed `IndexNotReadyException` after creating an ID with `GenerationType.SEQUENCE` <a href="https://issues.jpa-buddy.com/issue/JPAB-2072" target="_blank">JPAB-2072</a>
* Few typos were fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-2060" target="_blank">JPAB-2060</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2062" target="_blank">JPAB-2062</a>
* "Create New Projection" action is now available from the "DTOs and Projection" section in the JPA Structure <a href="https://issues.jpa-buddy.com/issue/JPAB-2063" target="_blank">JPAB-2063</a>

## 2022.4.1 - 2022-12-09

### Improvements

* Linking a DTO to an entity is now possible not only via Javadoc comment, but also using single and multiline comments <a href="https://issues.jpa-buddy.com/issue/JPAB-2035" target="_blank">JPAB-2035</a>
* The `jakarta.persistence.GenerationType#UUID` has been supported for `UUID` entity attribute type <a href="https://issues.jpa-buddy.com/issue/JPAB-1871" target="_blank">JPAB-1871</a>

### Bug-fix
* Fixed often happening `NullPointerException` and `IndexNotReadyException` <a href="https://issues.jpa-buddy.com/issue/JPAB-2046" target="_blank">JPAB-2046</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-2047" target="_blank">JPAB-2047</a>
* Previously mistakenly available "Create JPA Repository" quick-fix for an embeddable entity is no longer available <a href="https://issues.jpa-buddy.com/issue/JPAB-2029" target="_blank">JPAB-2029</a>

For other improvements and fixes, see [all resolved issues (10+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20224%20Bug%20fix:%201).

## 2022.4.0 - 2022-05-09

### Completely new

Most Loved JPA Buddy actions can now be called from the concise Editor Toolbar! You can use it while working with:
* Entity <a href="https://issues.jpa-buddy.com/issue/JPAB-1924" target="_blank">JPAB-1924</a>
* Spring Data Repository <a href="https://issues.jpa-buddy.com/issue/JPAB-1925" target="_blank">JPAB-1925</a>
* XML or SQL files <a href="https://issues.jpa-buddy.com/issue/JPAB-1834" target="_blank">JPAB-1834</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-1943" target="_blank">JPAB-1943</a>

### Liquibase/Flyway/DDL Diff Generator

* The `@JdbcTypeCode` annotation from Hibernate 6 was supported <a href="https://issues.jpa-buddy.com/issue/JPAB-1881" target="_blank">JPAB-1881</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-1884" target="_blank">JPAB-1884</a>
* You can now use the new `CamelCaseToUnderscoresNamingStrategy` from Hibernate 6 <a href="https://issues.jpa-buddy.com/issue/JPAB-1897" target="_blank">JPAB-1897</a>
* Now, you can paste generated DDL right to the database console <a href="https://issues.jpa-buddy.com/issue/JPAB-1851" target="_blank">JPAB-1851</a>

### Reverse Engineering

* You can now choose whether to set the schema name for the entity <a href="https://issues.jpa-buddy.com/issue/JPAB-1903" target="_blank">JPAB-1903</a>
* The `@JdbcTypeCode` annotation from Hibernate 6 was supported <a href="https://issues.jpa-buddy.com/issue/JPAB-1885" target="_blank">JPAB-1885</a>
* Now, you can choose whether to generate the `@NonNull` annotation for `not null` fields <a href="https://issues.jpa-buddy.com/issue/JPAB-1977" target="_blank">JPAB-1977</a>

### DTO Generator

* It is possible now to rename both entity and DTO fields at once <a href="https://issues.jpa-buddy.com/issue/JPAB-2000" target="_blank">JPAB-2000</a>
* Now, you can generate fluent setters for mutable DTOs <a href="https://issues.jpa-buddy.com/issue/JPAB-1176" target="_blank">JPAB-1176</a>
* You can now navigate to Entity class from Projection interface <a href="https://issues.jpa-buddy.com/issue/JPAB-1824" target="_blank">JPAB-1824</a>

### Entity Designer

* Inspection for the non-owning side of the `@OneToOne` associations with the `FetchType.Lazy` attribute was added <a href="https://issues.jpa-buddy.com/issue/JPAB-1818" target="_blank">JPAB-1818</a>
* Now, you can set up JPA Buddy UI according to your needs <a href="https://issues.jpa-buddy.com/issue/JPAB-1953" target="_blank">JPAB-1953</a>
* ID generation wizard has been redesigned <a href="https://issues.jpa-buddy.com/issue/JPAB-1416" target="_blank">JPAB-1416</a>

### Spring Data

* Now you can generate a new DTO or projection and apply it as a return type directly from the query/method wizard <a href="https://issues.jpa-buddy.com/issue/JPAB-1803" target="_blank">JPAB-1803</a>
* The return type of `delete` methods has been redesigned <a href="https://issues.jpa-buddy.com/issue/JPAB-1535" target="_blank">JPAB-1535</a>

For other improvements and fixes, see [all resolved issues (50+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20224%20Bug%20fix:%200%20State:%20Verified,%20Fixed%20).

## 2022.3.6 - 2022-25-08

Fixed incorrect error handling from external plugins <a href="https://issues.jpa-buddy.com/issue/JPAB-2014" target="_blank">JPAB-2014</a>

## 2022.3.5 - 2022-18-08

### Bug-fix

* The `@Nationalized` annotation is now generated while reverse engineering if the field is of type `nvarchar`, `ntext`, etc. <a href="https://issues.jpa-buddy.com/issue/JPAB-1998" target="_blank">JPAB-1998</a>
* After creating the reverse attribute, the class in which this attribute was created opens <a href="https://issues.jpa-buddy.com/issue/JPAB-1966" target="_blank">JPAB-1966</a>
* Fixed a false positive "Embeddable attribute is not marked as `@Embedded`" inspection <a href="https://issues.jpa-buddy.com/issue/JPAB-1870" target="_blank">JPAB-1870</a>
* Enabling DB schema caching no longer resets user selection silently <a href="https://issues.jpa-buddy.com/issue/JPAB-1730" target="_blank">JPAB-1730</a>
* The missed actions for Kotlin users are available again in both: JPA Inspector and Context Actions menu <a href="https://issues.jpa-buddy.com/issue/JPAB-1848" target="_blank">JPAB-1848</a>
* Some spelling errors have been corrected <a href="https://issues.jpa-buddy.com/issue/JPAB-1994" target="_blank">JPAB-1994</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-1955" target="_blank">JPAB-1955</a>

## 2022.3.4 - 2022-01-08

### Bug-fix

* Correct DDL statements are now generated for the edge cases using the `@IdClass` annotation <a href="https://issues.jpa-buddy.com/issue/JPAB-1970" target="_blank">JPAB-1970</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-1985" target="_blank">JPAB-1985</a>
* Table column names autocompletion in the Liquibase files no longer produces `Non-idempotent Computation` exception <a href="https://issues.jpa-buddy.com/issue/JPAB-1969" target="_blank">JPAB-1969</a>
* While Reverse Engineering, JPA Buddy now selects the correct mapping types for the `smallint` and `tinyint` types <a href="https://issues.jpa-buddy.com/issue/JPAB-1975" target="_blank">JPAB-1975</a>
* Reserved characters are now escaped in the Liquibase `include` tags <a href="https://issues.jpa-buddy.com/issue/JPAB-1993" target="_blank">JPAB-1993</a>

For other improvements and fixes, see [all resolved issues (10+)](https://issues.jpa-buddy.com/issues/JPAB?q=project:%20%7BJPA%20Buddy%7D%20Milestone:%20223%20Bug%20fix:%204%20order%20by:%20Priority,%20type,%20State%20desc).

## 2022.3.3 - 2022-21-07

Fix bulk  **StackOverflowError** when calculating DTO line markers for an entity class <a href="https://issues.jpa-buddy.com/issue/JPAB-1986" target="_blank">JPAB-1986</a>
```
java.lang.StackOverflowError: null
    at java.util.Objects.hashCode(Objects.java:116)
    at com.haulmont.jpb.action.creation.entity.JavaDtoClassFinder.A(DtoClassFinder.kt:29)
    at com.haulmont.jpb.action.creation.entity.JavaDtoClassFinder.A(DtoClassFinder.kt:29)
    at com.haulmont.jpb.action.creation.entity.JavaDtoClassFinder.A(DtoClassFinder.kt:29)
```


## 2022.3.2 - 2022-20-07

### Bug-fix

* **Critical Performance Issue!** Code editing performance problems <a href="https://issues.jpa-buddy.com/issue/JPAB-1978" target="_blank">JPAB-1978</a>
* "Invalid order syntax for part Desc!" exception the availability check for *DefineEntityGraphIntention* intention <a href="https://issues.jpa-buddy.com/issue/JPAB-1979" target="_blank">JPAB-1979</a>
* Fix navigation from DTO to Entity <a href="https://issues.jpa-buddy.com/issue/JPAB-1962" target="_blank">JPAB-1962</a>

For other improvements and fixes, see [all resolved issues (5+)](https://issues.jpa-buddy.com/issues/JPAB?q=project:%20JPAB%20%23Resolved%20%20Milestone:%20223%20Bug%20fix:%202).

## 2022.3.1 - 2022-04-07

### Features

* For Liquibase/Flyway diff generator, the Hibernate `@Nationalized` annotation has been supported <a href="https://issues.jpa-buddy.com/issue/JPAB-1867" target="_blank">JPAB-1867</a>
* During Reverse Engineering, JPA Buddy now applies the Hibernate `@OnDelete(action = OnDeleteAction.CASCADE)` for migrated columns, if the foreign key contains CASCADE option <a href="https://issues.jpa-buddy.com/issue/JPAB-1741" target="_blank">JPAB-1741</a>

### Improvements

* Since Hibernate 6, the `TextType` value is no longer applicable for columns with type `oid`/`text` in the database. So now, JPA Buddy is also using a new approach <a href="https://issues.jpa-buddy.com/issue/JPAB-1895" target="_blank">JPAB-1895</a>
* You can now generate EntityGraph for Spring Data queries via the new intention <a href="https://issues.jpa-buddy.com/issue/JPAB-1880" target="_blank">JPAB-1880</a>
* Liquibase autocompletion is getting more advanced. Now, you can use autocompletion to fill in the database schema names <a href="https://issues.jpa-buddy.com/issue/JPAB-1774" target="_blank">JPAB-1774</a>

### Bug-fix

* While Init Schema Changelog generation, incorrect database type is no longer generated for `OffsetDateTime` attributes <a href="https://issues.jpa-buddy.com/issue/JPAB-1936" target="_blank">JPAB-1936</a>
* Fixed the `NullPointerException` exception for the case when the user tried to create a DTO with an empty attribute name <a href="https://issues.jpa-buddy.com/issue/JPAB-1941" target="_blank">JPAB-1941</a>
* Creating a Spring Data Projection from a quick-fix action no longer produces an exception <a href="https://issues.jpa-buddy.com/issue/JPAB-1940" target="_blank">JPAB-1940</a>

For other improvements and fixes, see [all resolved issues (20+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20223%20Bug%20fix:%201%20State:%20Verified,%20Fixed%20).

## 2022.3.0 - 2022-20-06

### Completely new
JPA Buddy presents - **DDL Generator**!

This feature allows developers to convert entities into DDL statements in a few clicks. It can generate both initialization scripts to create a database schema from scratch and differential DDL to update the already existing database to the valid state in accordance with JPA entities <a href="https://issues.jpa-buddy.com/issue/JPAB-1832" target="_blank">JPAB-1832</a> & <a href="https://issues.jpa-buddy.com/issue/JPAB-1833" target="_blank">JPAB-1833</a>

### Liquibase/Flyway Diff Generator

* The number of supported databases has increased! Please welcome, IBM Db2 <a href="https://issues.jpa-buddy.com/issue/JPAB-1251" target="_blank">JPAB-1251</a>
* Comparing entities from different VCS branches via snapshot has become more convenient to use <a href="https://issues.jpa-buddy.com/issue/JPAB-1380" target="_blank">JPAB-1380</a>
* Now JPA Buddy knows that you are using Hibernate Envers in your project and does not generate drop scripts for audit tables <a href="https://issues.jpa-buddy.com/issue/JPAB-1817" target="_blank">JPAB-1817</a>
* You can now configure the generator right from the Flyway/Liquibase wizards <a href="https://issues.jpa-buddy.com/issue/JPAB-1734" target="_blank">JPAB-1734</a>

### Reverse Engineering

* Now, JPA Buddy can automatically remove prefixes from the table and column names <a href="https://issues.jpa-buddy.com/issue/JPAB-1841" target="_blank">JPAB-1841</a>
* Since this release, all reverse engineering actions are also available for IBM Db2 <a href="https://issues.jpa-buddy.com/issue/JPAB-1251" target="_blank">JPAB-1251</a>
* You can now define the ID generation strategy for each entity right from the "Entities from DB" wizard <a href="https://issues.jpa-buddy.com/issue/JPAB-1501" target="_blank">JPAB-1501</a>

### DTO Generator

* Now you can generate mapping methods right into an existing MapStruct mapper class <a href="https://issues.jpa-buddy.com/issue/JPAB-1238" target="_blank">JPAB-1238</a>
* The MapStruct method for updating an entity from the DTO now returns an updated entity instead of `void` <a href="https://issues.jpa-buddy.com/issue/JPAB-1792" target="_blank">JPAB-1792</a>

### Entity Designer

* Normalizing entities has become much easier! Just call the new "Extract to MappedSupperclass entity" action and create entities hierarchy in a few clicks <a href="https://issues.jpa-buddy.com/issue/JPAB-944" target="_blank">JPAB-944</a>
* Incorrect behavior of the Minimalistic Mode has been fixed <a href="https://issues.jpa-buddy.com/issue/JPAB-1915" target="_blank">JPAB-1915</a>

### Spring Data

* The Projection creation dialog has started to look even better <a href="https://issues.jpa-buddy.com/issue/JPAB-1724" target="_blank">JPAB-1724</a>

For other improvements and fixes, see [all resolved issues (65+)](https://issues.jpa-buddy.com/issues/JPAB?q=project:%20JPAB%20Milestone:%20223%20Bug%20fix:%200%20%20-Epic%20-%7BInternal%20improvement%7D%20%20State:%20Fixed%20,%20Verified%20order%20by:%20type,%20Priority).

## 2022.2.5 - 2022-6-06

### Bug-fix

* `IndexOutOfBoundsException` no longer appears during Flyway Versioned Migration generation <a href="https://issues.jpa-buddy.com/issue/JPAB-1853" target="_blank">JPAB-1853</a>
* Mapper for DTOs is now generated without any issues <a href="https://issues.jpa-buddy.com/issue/JPAB-1876" target="_blank">JPAB-1876</a>
* Line markers generation no longer causes an `IllegalStateException` <a href="https://issues.jpa-buddy.com/issue/JPAB-1854" target="_blank">JPAB-1854</a>
* Frequent exceptions that do not affect the plugin functionality will no longer bother you <a href="https://issues.jpa-buddy.com/issue/JPAB-1875" target="_blank">JPAB-1875</a>
* Now, `@ElementCollection` attributes are created correctly in Kotlin <a href="https://issues.jpa-buddy.com/issue/JPAB-1849" target="_blank">JPAB-1849</a>

## 2022.2.4 - 2022-17-05

Fixed a non-critical, but often happening `IllegalArgumentException` [JPAB-1852](https://issues.jpa-buddy.com/issue/JPAB-1852)

## 2022.2.3 - 2022-16-05

### Bug-fix

* Incorrect behavior of Minimalistic Mode has been fixed [JPAB-1771](https://issues.jpa-buddy.com/issue/JPAB-1771) & [JPAB-1800](https://issues.jpa-buddy.com/issue/JPAB-1800)
* Frequently occuring `StringIndexOutOfBoundsException` is fixed [JPAB-1814](https://issues.jpa-buddy.com/issue/JPAB-1814)
* Annotations over getters and setters are now generated correctly [JPAB-1797](https://issues.jpa-buddy.com/issue/JPAB-1797)
* The redundant `precision` attribute is no longer generated for numeric fields when creating an entity from a database table [JPAB-1779](https://issues.jpa-buddy.com/issue/JPAB-1779)
* After changing the owning side of the many-to-many association, JPA Buddy no longer loses the name of the join table and its columns names [JPAB-1804](https://issues.jpa-buddy.com/issue/JPAB-1804)
* Supported an array of primitive types, like `String[]` for the `@ElementCollection` attributes [JPAB-1786](https://issues.jpa-buddy.com/issue/JPAB-1786)

For other improvements and fixes, see [all resolved issues (20+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20222%20Bug%20fix:%203%20order%20by:%20Priority%20,%20Type%20).

## 2022.2.2 - 2022-25-04

### Improvements
* `@IdClass` annotation has been supported for Liquibase/Flyway Diff Generator [JPAB-72](https://issues.jpa-buddy.com/issue/JPAB-72)
* The usability of `//TODO` mapping type in the "Entities from DB" wizard has been improved [JPAB-1707](https://issues.jpa-buddy.com/issue/JPAB-1707)
* JPA Buddy is now generates the correct `bytea` datatype for `org.hibernate.type.BinaryType` columns for PostgreSQL database [JPAB-1743](https://issues.jpa-buddy.com/issue/JPAB-1743)
* `@GenericGenerator` parameters have been supported for Liquibase/Flyway Diff Generator [JPAB-1570](https://issues.jpa-buddy.com/issue/JPAB-1570)

### Bug-fix
* It's now possible to create a connection for the MSSQL database from IJ IDEA Community Edition without any exception [JPAB-1752](https://issues.jpa-buddy.com/issue/JPAB-1752)
* "Create entities from DB" action no longer produces `IllegalStateException` [JPAB-1762](https://issues.jpa-buddy.com/issue/JPAB-1762)
* `@ToOne` reference to an entity with `@EmbeddedId` is now generated correctly [JPAB-1732](https://issues.jpa-buddy.com/issue/JPAB-1732)
* `KotlinExceptionWithAttachments` no longer occurs during query extraction in Kotlin projects [JPAB-1739](https://issues.jpa-buddy.com/issue/JPAB-1739)

For other improvements and fixes, see [all resolved issues (25+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20222%20Bug%20fix:%202%20State:%20Verified%20order%20by:%20Priority,%20type,%20State%20desc).

## 2022.2.1 - 2022-12-04

Fixed a non-critical, but often happening bug with incorrect psi [JPAB-1746](https://issues.jpa-buddy.com/issue/JPAB-1746)

## 2022.2.0 - 2022-11-04

Starting with this version, JPA Buddy provides free and paid functionality.

Most of the features stay free, including all visual designers for entities, Spring Data repositories, SQL and Liquibase changelogs. However, some features are available only under commercial license, e.g., differential migration scripts generation. JPA Buddy remains free for students and academic use (teachers, students, classroom assistance) as well as training courses, coding schools and bootcamps. Also, we offer a 50% discount for universities, educational and non-profit organizations.

Learn more about the commercial subscription [here](https://www.jpa-buddy.com/blog/jpa-buddy-goes-freemium).

### Reverse Engineering [Incubator]*

  - Bulk reverse engineering action is finally here! Generate entities for a dozen of tables at the same time [JPAB-919](https://issues.jpa-buddy.com/issue/JPAB-919)
  - The number of actions in //TODO comments has been increased [JPAB-992](https://issues.jpa-buddy.com/issue/JPAB-992)
  - The `mediumtext` column type no longer causes long entity creation [JPAB-1675](https://issues.jpa-buddy.com/issue/JPAB-1675)

### DTO Generator [Incubator]*

  - It's possible now to create a DTO from unresolved references [JPAB-1150](https://issues.jpa-buddy.com/issue/JPAB-1150)
  - Now, you can see all the DTOs for the entity in the JPA Structure panel [JPAB-1582](https://issues.jpa-buddy.com/issue/JPAB-1582)
  - Java Records have been supported [JPAB-1147](https://issues.jpa-buddy.com/issue/JPAB-1147)

### Entity Designer

  - Now JPA Buddy is able to generate blanks for Hibernate Event Listeners [JPAB-1130](https://issues.jpa-buddy.com/issue/JPAB-1130)
  - @Version attribute has been added to the JPA Palette [JPAB-94](https://issues.jpa-buddy.com/issue/JPAB-94)
  - The Set<> is now used by default for collections [JPAB-1492](https://issues.jpa-buddy.com/issue/JPAB-1492)
  - Cascade.REMOVE is now disabled for ManyToMany associations [JPAB-1494](https://issues.jpa-buddy.com/issue/JPAB-1494)
  - Attribute type refactoring now works correctly in Kotlin projects [JPAB-1632](https://issues.jpa-buddy.com/issue/JPAB-1632)

### Liquibase/Flyway Diff Generator

  - PostgreSQL driver 42.3.3 has been supported [JPAB-1700](https://issues.jpa-buddy.com/issue/JPAB-1700)
  - Support for other liquibase statements has been added [JPAB-1555](https://issues.jpa-buddy.com/issue/JPAB-1555) & [JPAB-133](https://issues.jpa-buddy.com/issue/JPAB-133)


### Spring Data

  - EntityGraph is supported for repository methods [JPAB-493](https://issues.jpa-buddy.com/issue/JPAB-493)
  - You can now create a method for the repository from an unresolved reference [JPAB-1541](https://issues.jpa-buddy.com/issue/JPAB-1541)

Other improvements and fixes, see [all resolved issues (55+)](https://issues.jpa-buddy.com/issues/JPAB?q=project:%20JPAB%20Milestone:%20222%20%20Bug%20fix:%200%20order%20by:%20Subsystem,%20Milestone,%20%7BBug%20fix%7D,%20Priority,%20type,%20State%20desc).

\* Features in the Incubator are in the active development phase, with major improvements and changes planned in the nearest future. These features will remain free until they are complete. After that, they can become either paid or free, depending on the feature.

## 2022.1.3 - 2022-03-28

### Bug-fix
* The "Mark as transient" action no longer produces an exception [JPAB-1651](https://issues.jpa-buddy.com/issue/JPAB-1651)
* The migration script for an entity with reference to an entity with `@EmbeddedId` is now generated correctly [JPAB-1686](https://issues.jpa-buddy.com/issue/JPAB-1686)
* JPA Buddy is no longer worried about transient type field use instead of the `@Transient` annotation [JPAB-1676](https://issues.jpa-buddy.com/issue/JPAB-1676)
* Liqubase/Flyway diff generator is now working correctly with `datetime` and `datetime2` types in MSSQL [JPAB-1665](https://issues.jpa-buddy.com/issue/JPAB-1665)
* The name for the non-owning side of the `@OneToOne` association is now generated in the singular during Reverse Engineering [JPAB-1661](https://issues.jpa-buddy.com/issue/JPAB-1661)
* The "Create Entity from DB" action no longer produces `NullPointerException` [JPAB-1671](https://issues.jpa-buddy.com/issue/JPAB-1671)

[All resolved issues (10+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20221%20Bug%20fix:%203%20)

## 2022.1.2 - 2022-03-03

### Improvements
* Now the template for pk constraint name can be configured [JPAB-1639](https://issues.jpa-buddy.com/issue/JPAB-1639)
* Diff generator is now able to bypass the intermediate classes in the hierarchy of entities that are not marked with JPA annotations [JPAB-1659](https://issues.jpa-buddy.com/issue/JPAB-1659)

### Bug-fix
* NullPointerException no longer appears when you interact with Reverse Engineering actions via //TODO comments [JPAB-1649](https://issues.jpa-buddy.com/issue/JPAB-1649)
* The entity name is now formatted correctly when creating an entity from a database table whose name is in camelcase [JPAB-1657](https://issues.jpa-buddy.com/issue/JPAB-1657)
* Navigation to the column from Liquibase changelog no longer causes IllegalStateException [JPAB-1650](https://issues.jpa-buddy.com/issue/JPAB-1650)

[All resolved issues (5+)](https://issues.jpa-buddy.com/issues?q=project:%20JPAB%20Milestone:%20221%20Bug%20fix:%202%20order%20by:%20Milestone,%20%7BBug%20fix%7D,%20Priority,%20type,%20State%20desc)

## 2022.1.1 - 2022-02-16

### Improvements
* IntelliJ IDEA 2022.1 is now supported [JPAB-1597](https://issues.jpa-buddy.com/issue/JPAB-1597)
* Query extraction is prevented for derived queries with the 'findFirst' condition and Optional return type [JPAB-1636](https://issues.jpa-buddy.com/issue/JPAB-1636)

### Bug-fix
* "Add id attribute" quick fix no longer causes "Incorrect java type of attribute" Exception [JPAB-1634](https://issues.jpa-buddy.com/issue/JPAB-1634)
* UnsupportedOperationException no longer occurs in Liquibase changelogs [JPAB-1633](https://issues.jpa-buddy.com/issue/JPAB-1633)
* Action call from //TODO comment no longer causes RuntimeExceptionWithAttachments [JPAB-1630](https://issues.jpa-buddy.com/issue/JPAB-1630)
* The case with Reverse Engineering action call on database table without primary key now handles correctly [JPAB-1629](https://issues.jpa-buddy.com/issue/JPAB-1629)

[All resolved issues (10+)](https://issues.jpa-buddy.com/issues/JPAB?q=project:%20JPAB%20Milestone:%20221%20Bug%20fix:%201)

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

[All resolved issues (55+)](https://issues.jpa-buddy.com/issues/JPAB?q=Milestone:%20221%20Bug%20fix:%200%20State:%20Fixed%20,%20Verified%20order%20by:%20type%20desc,%20Priority,State%20desc%20-%7BInternal%20improvement%7D%20-Task%20)

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
