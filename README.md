# Book Extra Chapters - U.2.4: Upgrade to Spring Boot 2.4.0, Cloud 2020, JDK 15

This repository contains the source code of the practical use case described in the book [Learn Microservices with Spring Boot (2nd Edition)](https://tpd.io/book-extra).

The book follows a pragmatic approach to building a Microservice Architecture. You start with a small monolith and examine the _pros_ and _cons_ that come with a move to microservices. 

## Upgrade - Spring Boot 2.4.0, Spring Cloud 2020.0, JDK 15

This extra chapter includes some relevant upgrades for the technology stack used in the book's microservice architecture. 

Note: check the [Book's Web Page](https://tpd.io/book-extra) to see the complete list of chapters and the extra contents.

### Changes - migrating from Spring Boot 2.3.4 to 2.4.0

A summary of the updates included in this package:

* JDK 15
* Spring Boot 2.4.0
* Spring Cloud 2020.0
* Consul 1.9.X
* Version changes in the microservices to align them with the Spring Boot version

#### Default username for embedded databases

Spring Boot 2.4 doesn't use the default `sa` username for the H2 embedded database (check the [docs](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.4-Release-Notes#embedded-database-detection)). To be able to use existing databases, we have to add this line to the configuration of both Multiplication and Gamification microservices (`application.properties` files):

```
spring.datasource.username=sa
```

You can also skip this change if you don't have any previous database files (or if you delete them). Spring Boot will create the databases with the new default credentials.

#### Spring Cloud Bootstrap

When we upgrade to Spring Cloud 2020.0, we lose the _bootstrap_ functionality. In our projects, we use the `bootstrap.properties` file to adjust the settings of the Consul's Config Server. This means our services will fail when running them in Docker containers, because they can't find the `docker` profile configuration, and they'll try to reach the RabbitMQ server locally (from `localhost` - the container's host).

To fix this, we have several options [as documented in the release notes](https://github.com/spring-cloud/spring-cloud-release/wiki/Spring-Cloud-2020.0-Release-Notes#breaking-changes). In this repository, I chose to add an extra dependency to all projects:

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-bootstrap</artifactId>
</dependency>
``` 

#### References

Some additional references:

* [Spring Cloud 2020.0 Release Notes](https://github.com/spring-cloud/spring-cloud-release/wiki/Spring-Cloud-2020.0-Release-Notes)
* [Spring Boot 2.4.0 Release Notes, Embedded Database Detection](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.4-Release-Notes#embedded-database-detection), and the related [pull request](https://github.com/spring-projects/spring-boot/pull/23693#issuecomment-712678254).

## Running the app

You can use Docker to start the complete system, and you can also run the services one by one on your computer. [See the book's last chapter repository](https://github.com/Book-Microservices-v2/chapter08d) for the detailed instructions.

I pushed the new images to the public registry, so you can get the system up and running with the new versions using Docker Compose:

```bash
docker$ docker-compose -f docker-compose-public.yml up
```

## Questions

* Do you have questions about how to make this application work?
* Did you get the book and have questions about any concept explained within this chapter?
* Have you found issues using updated dependencies?

Don't hesitate to create an issue in this repository and post your question/problem there. 

## About the book

Are you interested in building a microservice architecture from scratch? You'll face all the challenges of designing and implementing a distributed system one by one, and will be able to evaluate if it's the best choice for your project.

Visit [https://tpd.io/book-extra](https://tpd.io/book-extra) for all the details about the book.

### Purchase

You can **buy the book online** from these stores:

* [Apress](https://www.kqzyfj.com/click-8535631-14029332?url=https%3A%2F%2Fwww.apress.com%2Fgp%2Fbook%2F9781484261309)
* [Amazon](https://amzn.to/3nADn4q)
* and other online stores, check the IBAN (9781484261309) on [google](https://www.google.com/search?q=9781484261309)

### Source code by chapter (all repositories are available on Github)

* [Chapter 3. A professional 3-tier 3-layer Spring Boot app](https://github.com/Book-Microservices-v2/chapter03)
* [Chapter 4. Building a basic frontend in React (backender-friendly)](https://github.com/Book-Microservices-v2/chapter04)
* [Chapter 5. The Data Layer Concepts and Spring Data JPA](https://github.com/Book-Microservices-v2/chapter05)
* [Chapter 6. Starting with Microservices - Synchronous](https://github.com/Book-Microservices-v2/chapter06)
* [Chapter 7. Event-Driven Architectures - Making our system asynchronous](https://github.com/Book-Microservices-v2/chapter07)
* [Chapter 8 (I). The Gateway Pattern in Microservice Architectures (Spring Cloud Gateway)](https://github.com/Book-Microservices-v2/chapter08a)
* [Chapter 8 (II). Service Discovery and Load Balancing for Spring Boot Microservices (Consul / Spring Cloud Load Balancer)](https://github.com/Book-Microservices-v2/chapter08b)
* [Chapter 8 (III). Centralized Configuration with Consul KV](https://github.com/Book-Microservices-v2/chapter08c)
* [Chapter 8 (IV). Centralized Logs, Distributed Tracing, and Containerization with Docker (Buildpacks) and Docker Compose](https://github.com/Book-Microservices-v2/chapter08d)

Extra chapters:

* [E.1. End-to-End Microservice tests with Cucumber](https://github.com/Book-Microservices-v2/cucumber-tests)
* [U.2.4.0. Upgrade: Spring Boot 2.4.0 and more]()
