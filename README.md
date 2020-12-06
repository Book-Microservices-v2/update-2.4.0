# Book Extra Chapters - U.2.4: Upgrade to Spring Boot 2.4.0, Cloud 2020, JDK 15

This repository contains the source code of the practical use case described in the book [Learn Microservices with Spring Boot (2nd Edition)](https://amzn.to/3nADn4q).

If you want to know more details about the book and its extra chapters, make sure to [visit this page](https://tpd.io/book-extra).

The book follows a pragmatic approach to building a Microservice Architecture, using a reference implementation that evolves from a small monolith to a full microservice system. 

## Upgrade - Spring Boot 2.4.0, Spring Cloud 2020.0, JDK 15

This extra chapter includes some relevant upgrades for the technology stack used in the book's microservice architecture. 

All these changes are described in detail in a [blog post](https://thepracticaldeveloper.com/book-update-2.4.0/) at The Practical Developer's website. Visit [https://thepracticaldeveloper.com/book-update-2.4.0/](https://thepracticaldeveloper.com/book-update-2.4.0/)

### Changes - migrating from Spring Boot 2.3.4 to 2.4.0

A summary of the updates included in this package:

* The default username for the H2 database is no longer `sa`, so we need to pass this property explicitly or get rid of the old databases.
* Bootstrap is disabled in the new Spring Cloud version, so we have to enable it again to make the config server setup work properly.
* The old MDC key names for Sleuth (Brave) have been removed in favor of the new ones, so we have to change the Logs microservice to use these in the Logback configuration file.

#### References

* [The main post](https://thepracticaldeveloper.com/book-update-2.4.0/) where I explain all these changes.

Some additional references from the official documentation:

* [Spring Cloud 2020.0 Release Notes](https://github.com/spring-cloud/spring-cloud-release/wiki/Spring-Cloud-2020.0-Release-Notes)
* [Spring Boot 2.4.0 Release Notes, Embedded Database Detection](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.4-Release-Notes#embedded-database-detection), and the related [pull request](https://github.com/spring-projects/spring-boot/pull/23693#issuecomment-712678254).
* [Spring Cloud Sleuth - Removed legacy MDC entries](https://github.com/spring-cloud/spring-cloud-sleuth/issues/1221)

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

[Buy the book at Amazon](https://amzn.to/3nADn4q), or visit [https://tpd.io/book-extra](https://tpd.io/book-extra) for all the details.

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
