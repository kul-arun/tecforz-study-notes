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
* A set of compatible dependencies that can be used for building an app or a specific feature of an app. These are frameworks that aid in implementing the feature.
* Spring Boot Starter Web includes the frameworks Spring Web MVC, Spring Web, Spring Boot Starter Tomcat, Spring Boot Starter JSON, etc.
* There are many starter projects offered by Spring Boot.


## Spring Boot Auto Configuration
* Automated configuration is decided based on which frameworks are in the Class path
* Can override defaults by specifying in application.properties file. Example:
    * logging.level.org.springframework=DEBUG -> the package org.springframework will have DEBUG logging level. The default logging level is INFO, and it contains much less information than DEBUG.
