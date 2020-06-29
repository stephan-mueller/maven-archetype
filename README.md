# Maven Archetypes

[![GitHub last commit](https://img.shields.io/github/last-commit/stephan-mueller/maven-archetype)](https://github.com/stephan-mueller/maven-archetype/commits) 
[![GitHub](https://img.shields.io/github/license/stephan-mueller/maven-archetype)](https://github.com/stephan-mueller/maven-archetype/blob/master/LICENSE)
[![CircleCI](https://circleci.com/gh/stephan-mueller/maven-archetype.svg?style=shield)](https://app.circleci.com/pipelines/github/stephan-mueller/maven-archetype)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=stephan-mueller_maven-archetype&metric=alert_status)](https://sonarcloud.io/dashboard?id=stephan-mueller_maven-archetype)

This is a collection of Maven archetypes for Enterprise Java projects. Software requirements to run the samples are `maven`, `openjdk-1.8` (or any other 1.8 JDK) and `docker` for the generated projects.


**Available archetypes:**
* openliberty-archetype (Version 1.0)
* quarkus-archetype (Version 1.0)

## How to run

Before using the archetypes they need to be compiled and installed into the local Maven archetype catalog.

```shell script
$ mvn clean install
```

If everything worked you can access the archetypes via Maven. To generate a project based on a archetype use the following command. You will be asked for the details of the generated project:
```shell script
$ mvn archetype:generate -B -DarchetypeCatalog=local                     \ 
                            -DarchetypeGroupId=<archetype-groupId>       \
                            -DarchetypeArtifactId=<archetype-artifactId> \ 
```

If you prefer to generate projects non-interactive you can run the generator in batch-mode:  
```shell script
$ mvn archetype:generate -B -DarchetypeCatalog=local                     \ 
                            -DarchetypeGroupId=<archetype-groupId>       \
                            -DarchetypeArtifactId=<archetype-artifactId> \ 
                            -DgroupId=org.acme                           \ 
                            -DartifactId=looney                          \
                            -Dversion=1.0-SNAPSHOT                       \
                            -Dpackage=org.acme.looney
```

**Please note**: You can specify the archetype-version by adding the property `-Darchetype-version=<archetype-version>`. If you do not specify any version the latest version is used by default.

## Archetypes

### openliberty-archetype

The openliberty-archetype contains a RESTful hello world application, which demonstrates features of Open Libety, Jakarta EE and Eclipse Microprofile.

|                     | openliberty-archetype       |
|---------------------|-----------------------------|
| archetypeGroupId    | de.openknowledge.archetypes |
| archetypeArtifactId | openliberty-archetype       |
| archetype-version   | 1.0                         |


Currently the archetype generates projects with Open Liberty version `20.0.0.7` by default. The version may be overridden by setting the property  `-Dopenliberty-version=<openliberty-version>` 

To create a project based on the archetype:
```shell script
$ mvn archetype:generate -B -DarchetypeCatalog=local                      \ 
                            -DarchetypeGroupId=de.openknowledge.archetype \
                            -DarchetypeArtifactId=quarkus-archetype       \ 
                            -DgroupId=org.acme                            \ 
                            -DartifactId=looney                           \
                            -Dversion=1.0-SNAPSHOT                        \
                            -Dpackage=org.acme.looney                     \
                            -Dopenliberty-version=20.0.0.7
```

Afterwards you can build the project and run the tests: 
```shell script
$ cd looney
$ mvn clean verify
```

### quarkus-archetype

The quarkus-archetype contains a RESTful hello world application, which demonstrates features of Quarkus and Eclipse Microprofile.

|                     | quarkus-archetype           |
|---------------------|-----------------------------|
| archetypeGroupId    | de.openknowledge.archetypes |
| archetypeArtifactId | quarkus-archetype           |
| archetype-version   | 1.0                         |


Currently the archetype generates projects with quarkus version `1.6.0.Final` by default. The version may be overridden by setting the property  `-Dquarkus-version=<quarkus-version>` 

To create a project based on the archetype:
```shell script
$ mvn archetype:generate -B -DarchetypeCatalog=local                      \ 
                            -DarchetypeGroupId=de.openknowledge.archetype \
                            -DarchetypeArtifactId=quarkus-archetype       \ 
                            -DgroupId=org.acme                            \ 
                            -DartifactId=looney                           \
                            -Dversion=1.0-SNAPSHOT                        \
                            -Dpackage=org.acme.looney                     \
                            -Dquarkus-version=1.6.0.Final
```

Afterwards you can build the project and run the tests: 
```shell script
$ cd looney
$ mvn clean verify
```