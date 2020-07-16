# ${artifactId}

This is a project based on the microservice framework [Quarkus](https://quarkus.io). It contains a hello world application, 
which demonstrates features of Quarkus and Eclipse Microprofile

Software requirements to run the samples are `maven`, `openjdk-1.8` (or any other 1.8 JDK) and `docker`.
When running the Maven lifecycle it will create the war package and use the `quarkus-maven-plugin` to create a runnable 
jar (fat jar) which contains the application and the Quarkus application server. The fat jar will be copied into a
Docker image using Spotify's `dockerfile-maven-plugin` during the package phase.

**Notable Features:**
* Dockerfiles for runnable JAR & Native Executable 
* Integration of MP Health, MP Metrics and MP OpenAPI
* Testcontainer-Tests with Rest-Assured, Cucumber and Postman/newman
* Code-Coverage for Testcontainer-Tests

## How to run

Before running the application it needs to be compiled and packaged using Maven. It creates the required war,
jar and Docker image and can be run via `docker`:

```shell script
$ mvn clean package
$ docker run --rm -p 8080:8080 ${artifactId}
```

If everything worked you can access the OpenAPI UI via http://localhost:8080/swagger-ui.

## How to run a native image 

Before building a native executable and a native image, you have to install the GraalVM on your machine. 
To create a docker image with a native executable you have to build the application with the Maven profile `native` 
```shell script
$ mvn clean package -Pnative
$ docker run --rm -p 8080:8080 ${artifactId}
```

**Please note:**
 
The native executable is tailored for a specific operating system (Linux, macOS, Windows etc). If you build the native executable on 
macOS or Windows, you will not be able to use it inside a Linux based docker container. 

To build a native executable which is usable inside a docker container you have to set the property 
`quarkus.native.container-build=true` (the property is set by default when using the Maven profile `native`). 
Instead of your machine a Linux container runtime is used for the build.    

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