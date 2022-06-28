## Basics

DTO (data transfer object) is an object that carries data between processes. DTOs for JPA entities generally contain a subset of entity attributes. For example, if you need to expose only a few of the entity attributes via REST API, you can map entities to DTOs with those attributes and serialize only them. Basically, DTOs allow you to decouple presentation/business logic layer from the data access layer.

 JPA Buddy offers DTO generation from JPA entities via a visual designer:

 <div class="youtube" align="center">
   <iframe width="560" height="315" src="https://www.youtube.com/embed/qpnM_k-TGFk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
 </div>

## Mutability

By default, JPA Buddy generates immutable DTOs – all the fields are final, and there are no setters for them. To generate DTOs with simple private fields, setters for them, and no-args constructor, check the "Mutable" box.  

![new_dto_mutable](img/new_dto_mutable.jpeg)

## Inner DTOs for associations

Entities can reference other entities via associations, and JPA Buddy allows you to generate DTOs for the referenced entities from the same window. Just check the referenced entity in the tree, choose the DTO type and pick the required fields. Let’s look at the available DTO types.

### New Class

A new class will be created in a separate file. You can specify the package and name for it.

![new_dto_new_class](img/new_dto_new_class.jpeg)

### New Nested Class

A new public static nested class will be created.

![new_dto_new_nested_class](img/new_dto_new_nested_class.jpeg)

### Existing Class

You can select a DTO class that already exists in the project. After clicking on the Browse button, a window with two tabs will open.

![new_dto_existing_class](img/new_dto_existing_class.jpeg)

On the "Search by Name" tab, you can find classes using keyword search.

![choose_class_search_by_name](img/choose_class_search_by_name.jpeg)

On the "Project" tab, you can view the project tree and find the desired class.

![choose_class_project](img/choose_class_project.jpeg)

### Flat

This type can be applied for `@`ToOne associations and `@`ToMany associations with only one selected field.  

<div class="note">
  New nested class will be created for @ToMany associations with more than one selected field instead.
</div>

For Flat DTOs, all inner class fields will be top-class fields. Their names will consist of the inner class filed name + fields names.

![new_dto_flat](img/new_dto_flat.jpeg)

For the configuration specified above, the following fields will be generated:

```java
private String name;
private LocalDate birthDate;
private String ownerFirstName;
private String ownerLastName;
```

## Java Records Support

If you use SDK version 16 and higher in your project, then JPA Buddy will provide an additional "Java Record" checkbox in the "New DTO" wizard. To check the SDK version of the project, open File -> Project Structure...

![project_structure](img/project_structure.png)

 <div class="youtube" align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/_MtJO4QKr0A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
 </div>

## MapStruct Mappers

[MapStruct](https://mapstruct.org/) is a code generator that greatly simplifies the implementation of mappings. The "Mapper class" field appears in the "New DTO" window if your project contains the corresponding dependency. You can select an existing Mapper or create a new one. 

 <div class="youtube" align="center">
   <iframe width="560" height="315" src="https://www.youtube.com/embed/MKQRRWqNLNk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
 </div>
JPA Buddy analyzes MapStruct mappers and can define which DTO is associated with which entity. Thanks to this, you can see the DTOs in the corresponding section in the JPA Structure and navigate between entity and DTOs through gutter icons.

Also, JPA Buddy can help if you prefer to have a single big mapper interface with methods for all entities. In this case, use IntelliJ IDEA "Generate Menu" (Cmd+N/Alt+Insert) in the open mapper class and create methods for any entity.

 <div class="youtube" align="center">
   <iframe width="560" height="315" src="https://www.youtube.com/embed/XahPsC2TciE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
 </div>

## DTO Declaration Settings

![dto_declarations_preferences](img/dto_declarations_preferences.png)

Each project may follow its own conventions for code writing. In the Tools -> JPA Buddy -> DTO Declaration you can configure:

- Serializable type.
- Class name postfix.
- Whether to use Lombok or not.
- Comment link regexp. It allows JPA Buddy to associate DTO with its JPA Entity. To specify a placeholder for the target entity FQN in a comment use the `(?<entity>.*)` pattern. So, if the regexp is defined as `A DTO for the{@link (?.*)} entity.` it will be resolved in the following comment: `//A DTO for the {@link io.jpabuddy.demo.entities.Project} entity.`. The feature is disabled when the field is empty.
- Name pattern regexp. This option is useful if you use an obligatory naming convention for DTOs. It allows JPA Buddy to associate DTO with its JPA Entity using a DTO name only. To specify a placeholder for the simple class name of the target JPA entity, use the `(?<entity>.)` pattern. E.g., `(?.)Dto` means that the `MyEntityDto` class will be considered as a DTO for `MyEntity`. The feature is disabled when the field is empty.

As soon as JPA Buddy is able to associate DTO class with the entity:
  - The DTO class will appear in the DTOs section in the JPA Structure panel (1)
  - The gutter icon will appear in both entity and DTO to ease the navigation between them (2)
  - The gutter icons will appear to navigate to the entity fields from the DTO fields (3)

![comment_link_regexp](img/comment_link_regexp.png)
