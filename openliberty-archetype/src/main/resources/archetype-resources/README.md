# ${artifactId}

This is a project based on the microservice framework [Open Liberty](https://openliberty.io). It contains a hello world application, which demonstrates features of Open Liberty and Eclipse Microprofile

Software requirements to run the samples are `maven`, `openjdk-1.8` (or any other 1.8 JDK) and `docker`. When running the Maven lifecycle it will create the war package and use the `quarkus-maven-plugin` to create a runnable jar (fat jar) which contains the application and the Quarkus application server. The fat jar will be copied into a Docker image using Spotify's `dockerfile-maven-plugin` during the package phase.

**Notable Features:**
* Dockerfiles for runnable JAR & Server
* Integration of MP Health and MP OpenAPI
* Testcontainer-Tests with Rest-Assured, Cucumber and Postman/newman

## How to run

Before running the application it needs to be compiled and packaged using Maven. It creates the required war,
jar and Docker image and can be run via `docker`:

```shell script
$ mvn clean package
$ docker run --rm -p 9080:9080 ${artifactId}
```

Wait for a message log similar to this:

> service_1   | [3/5/20 16:36:02:145 UTC] 0000001b id=         com.ibm.ws.kernel.feature.internal.FeatureManager            A CWWKF0011I: The defaultServer server is ready to run a smarter planet. The defaultServer server started in 13.006 seconds.

If everything worked you can access the OpenAPI UI via http://localhost:9080/openapi/ui.

## Resolving issues

Sometimes it may happen that the containers did not stop as expected when trying to stop the pipeline early. This may
result in running containers although they should have been stopped and removed. To detect them you need to check
Docker:

```shell script
$ docker ps -a | grep ${artifactId}
```

If there are containers remaining although the application has been stopped you can remove them:

```shell script
$ docker rm <ids of the containers>
```