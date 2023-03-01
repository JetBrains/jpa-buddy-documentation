# JPA Buddy Documentation

This repository contains the JPA Buddy Documentation. The documentation is published at https://www.jpa-buddy.com/documentation/.

![banner](readme/banner.jpg)

# Reporting Issues

If you notice a mistake, typo or would like us to add more information, feel free to create an issue. We will fix it as soon as possible.

# License
The source code is licensed under Apache 2.0. Hence, all materials located in this repository are allowed to be used for academic purposes as well as public presentations.

# Rules for committers

## Must use simple language

* Sentences should not be started with ing-ending words.
* Sentences should not be started with prepositions. E.g.: and, but and so on...
* Check the wordiness here: https://hemingwayapp.com/
* Check grammar issues here: https://www.grammarly.com/

## List Formatting

* Use * for unordered lists (E.g.: * Name)
* For ordered lists, use numbers followed by a period (E.g.: 1. Name)

## Link Formatting

* If the link leads to an external resource or to another page on our site, it should be formatted as an HTML link using `<a href="..."></a>`
* If the link leads to another section of the documentation, use `[...](link)` 

## Screenshots

* Use only kebab-case for names
* Use only .png format

## Documentation Update

* If the change affects a large part of the documentation, or if screenshots are being updated, it is necessary to branch off from the master branch and make changes there.
* If the changes are related to the release of a new version, the branch should be named according to the new version (E.g.: 2023-1-1)
* After verifying all changes, merge the changes into the master branch.
* Create a tag with the version of the plugin for which the documentation is applicable.
