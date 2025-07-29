# Spring Boot

* Auto-configurations make setting up Spring project very easy
* Easy to manage dependencies.
* NFR (Non-Functional Requirements)
    * Logging
    * Error handling
    * Monitoring deployed app in prod and observing metrics
    
* Setting up a Spring project and maintaining it without Spring Boot is hard.

## Beware
* /courses endpoint is different from /courses/ and we should be careful when checking the endpoint in the browser

## Benefits of Spring Boot

### Speed:
* Spring Initializr -> Quickly set up Spring projects
* Spring Boot Starter Projects -> Quickly manage dependencies
* Spring Boot Auto Configuration -> Automatic configuration based on dependencies in the class path.
* Spring Boot DevTools -> Don't have to restart the application after making a change

### Production-Ready:
* Logging
* Different configurations for different environments.
* Spring Boot Actuator -> Monitor the app based on several metrics


## Spring Boot Starter Projects
* A set of compatible dependencies that can be used for building an app or a specific feature of an app. These are
  frameworks that aid in implementing the feature.
* Spring Boot Starter Web includes the frameworks Spring Web MVC, Spring Web, Spring Boot Starter Tomcat, Spring Boot
  Starter JSON, etc.
* There are many starter projects offered by Spring Boot.


## Spring Boot Auto Configuration
* Automated configuration is decided based on which frameworks are in the Class path
* Can override defaults by specifying in application.properties file. Example:
    * logging.level.org.springframework=DEBUG -> the package org.springframework will have DEBUG logging level. The
      default logging level is INFO, and it contains much less information than DEBUG.


## Spring Boot Benefits:
* Spring Initializr -> Quickly set up a Spring project
* Spring Boot Starter Projects -> A collection of frameworks with compatible versions, that support a particular
  functionality: Easy dependency management
* Spring Boot Autoconfiguration -> Give good configurations for the frameworks by default, which can also be overriden
  if required,
* Spring Boot DevTools -> Increase productivity (e.g, automatically reload the Spring ApplicationContext when changes to
  the source code have been made.) **NOTE**: Changes to pom.xml file requires manual restart of the app.

* Different environments require different configurations: Dev, QA, Stage, Prod

## Profiles

* We can specify environment-specific configurations using profiles.
* application.properties -> default configurations used by the app.
* application-dev.properties -> configs for dev env (profile)
* application-prod.properties -> configs for prod env (profile)

* If we include spring.profiles.active=prod in application.properties file, then we have configs from both the places,
  and prod profile prop is used if the same prop exists in the default config file.

* What are Profiles? Environment specific configurations.

## Logging Levels

* Trace -> Max.information is shown.
* Debug -> More information is shown than the info level.
* Info -> basic information.
* Warning -> warnings about edge cases or deprecations.
* Error -> only errors and exceptions.

* Off -> no logs shown.

If we set logging level=Trace, then it will also show all the levels (Except Off).  Similarly, for any level we select,
all the levels below it will also be printed.


## Configuration Properties
* If we need to specify many configurations for a specific entity, like:
    currency-service.url=...
    currency-service.username=...
    currency-service.key=...
    ...,
    then the recommended approach is ConfigurationProperties.

* Create a class called CurrencyServiceConfiguration:

``` 
@ConfigurationProperties(prefix = "currency-service") 
@Component // we want Spring to manage this 
public class CurrencyServiceConfiguration {
    private String url;
    private String username;
    private String key;
    // getters & setters
} 
```

## Deployment
* Old way was WAR:
    * Install java, then a webserver and then use the webserver to run the app
* New approach:
    * The created jar file contains an embedded server (tomcat by default).

## Spring Boot Actuator
* Used to monitor and manage the application in production.
* Several endpoints are exposed by the actuator for this purpose:
    * health, mappings, beans, metrics, etc.
* Include the dependency in pom.xml, and access /actuator endpoint
* By default, only the /actuator/health is exposed.
* Expose what we want by specifying in application.properties file:
    * management.endpoints.web.exposure=health,beans

* The /actuator/env endpoint exposes info about the environment. Values are by default masked/hidden. To unmask, do:
  management.endpoint.env.show-values=always // (bad for security! just use this to check the details and then disable)

* The actuator endpoints gather info -> more CPU & memory usage. So use only what you need.


## Spring Boot vs Spring MVC vs Spring
* Spring is all about dependency injection. Define the dependencies via Spring annotations like @Component, identify them using component scan, then inject them via @Autowired.
* Spring modules and spring projects extend the spring ecosystem. They provide good integration with other frameworks like Hibernate/JPA, JUnit, etc.

* Spring MVC is a Spring module. It simplifies the building of web apps and REST APIs.
* Annotations like @Controller, @RestController, @RequestMapping, etc are provided by it.

* Even to build a simple app, a lot of configuration is required when we use Spring and Spring MVC. Spring Boot is a Spring Project that helps with this, We can build production-ready apps quickly using Spring Boot

* Key features of Spring Boot are:
    * Spring Initializr
    * Spring Boot Starter Projects
    * Autoconfigurations
    * DevTools -> automated reloading of Spring ApplicationContext when required.
    * Deployment -> embedded server inside the created jar


## Artifact
* It is the output of a build process (,war, .jar, etc) 
* In Spring Initializr, we define the name of the output file.
* A jar file is a package file format that includes Java class files, metadata and resources.


## What exactly does Spring Boot Autoconfigure?
* Based on what's there in the class path, and the properties defined in the application,properties file, and what is not already defined by us, Spring Boot sets up the necessary Spring Beans.
* Set up Hibernate properties based on application.properties
* Sets up tomcat embedded web server
* Set up actuator endpoints


* Spring Boot also enables non-functional requirements:
    * Actuator
    * Embedded Server
    * Logging and Error handling
    * Profiles and ConfigurationProperties

* @ConfigurationProperties instead of @Value injection is better if we have a group of related properties, and/or if we need type safety, validation and structure.
    * Type mismatch is caught at compile-time, and there won't be silent conversions.
    * Validation -> @NotBlank, @Min(1), @Max(10), etc.


Spring Boot is not a replacement for Spring or Spring MVC. It just helps to use Spring and Spring MVC easily, to build a production-ready apps.
