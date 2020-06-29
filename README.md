# Maven Archetypes

[![GitHub last commit](https://img.shields.io/github/last-commit/stephan-mueller/maven-archetype)](https://github.com/stephan-mueller/maven-archetype/commits) 
[![GitHub](https://img.shields.io/github/license/stephan-mueller/maven-archetype)](https://github.com/stephan-mueller/maven-archetype/blob/master/LICENSE)
[![CircleCI](https://circleci.com/gh/stephan-mueller/maven-archetype.svg?style=shield)](https://app.circleci.com/pipelines/github/stephan-mueller/maven-archetype)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=stephan-mueller_maven-archetype&metric=alert_status)](https://sonarcloud.io/dashboard?id=stephan-mueller_maven-archetype)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=stephan-mueller_maven-archetype&metric=coverage)](https://sonarcloud.io/dashboard?id=stephan-mueller_maven-archetype)

This is a collection of Maven archetypes for Jakarta EE and Eclipse MicroProfile. Software requirements to run the samples are `maven`, `openjdk-1.8` (or any other 1.8 JDK) and `docker` for the generated projects.


## How to run

Before using the archetypes they need to be compiled and installed into the local Maven archetype catalog.

```shell script
$ mvn clean install
```

If everything worked you can access the archetypes via Maven. To generate a project based on a archetype:  
```shell script
$ mvn archetype:generate -B -DarchetypeCatalog=local                     \ 
                            -DarchetypeGroupId=<archetype-groupId>       \
                            -DarchetypeArtifactId=<archetype-artifactId> \ 
                            -Darchetype-version=<archetype-version>      \
                            -DgroupId=org.acme                           \ 
                            -DartifactId=looney                          \
                            -Dversion=1.0-SNAPSHOT                       \
                            -Dpackage=org.acme.looney
```

Afterwards you can build and run the tests of the generated project: 
```shell script
$ cd looney
$ mvn clean verify
```