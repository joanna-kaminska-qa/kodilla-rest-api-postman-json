# kodilla-rest-api

![Java](https://img.shields.io/badge/Java-21-blue)
![Spring Boot](https://img.shields.io/badge/SpringBoot-3.2.5-brightgreen)
![Gradle](https://img.shields.io/badge/Gradle-8-green)
![JUnit](https://img.shields.io/badge/JUnit-Platform-purple)
![RestAssured](https://img.shields.io/badge/RestAssured-5.4.0-orange)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

This project includes exercises and homework tasks completed as part of a module in the Kodilla "Automated Tester" Java course, focusing on **REST API**.

The module introduces:
- REST API development with Spring Boot
- building controllers and service layers
- testing using:
    - JUnit
    - Mockito
    - Spring MockMvc
    - RestAssured
- calling external APIs
- validating JSON responses and HTTP status codes

The project was developed in **IntelliJ IDEA** as part of the learning path for future **QA/Test Automation Engineers**.

---

## Description

This repository contains a simple Spring Boot REST API that manages a book collection and demonstrates:

### ✔ REST Controller Development
- `BookController` with GET, POST, PUT, DELETE endpoints
- request/response handling using DTOs
- service layer abstraction (`BookService`)

### ✔ Testing REST APIs
- **MockMvc** tests for verifying controller logic
- **RestAssured** tests for full HTTP integration
- tests for external API interactions
- verifying:
    - response status codes
    - JSON structure
    - serialization/deserialization
    - endpoint behaviors

### ✔ External API Testing
Module includes tests using RestAssured to call public APIs:
- reading posts
- updating posts (`PUT`)
- validating returned fields

All code was developed in **IntelliJ IDEA**, using **Java 21** and **Spring Boot 3.2.5**.

---

## Project Structure
```
kodilla-rest-api/
│ build.gradle
│ gradlew
│ gradlew.bat
│ LICENSE
│ README.md
│ structure.txt
│
├── src/main/java/com/kodilla/rest
│ ├── KodillaRestApiApplication.java
│ │
│ ├── controller/
│ │ └── BookController.java
│ │
│ ├── domain/
│ │ └── BookDto.java
│ │
│ └── service/
│ └── BookService.java
│
└── src/test/java/com/kodilla/rest/controller/
│ BookControllerMvcTest.java
│ BookControllerRestAssuredTest.java
│ BookControllerTest.java
│ ExternalApiRestAssuredTest.java
│ ExternalApiTestOfUpdatingAPost.java
```
---
## Getting Started

### Requirements
- Java 21
- Gradle (wrapper included)
- IntelliJ IDEA
- Spring Boot 3.2.5

### Running the Application

**Linux / macOS**
```bash
./gradlew clean build
```
**Windows**
```bash
gradlew clean build
```
### Dependencies

This project uses **Gradle** for build automation.

Main dependencies from `build.gradle`:

```gradle
plugins {
    id 'java'
    id 'org.springframework.boot' version '3.2.5'
    id 'io.spring.dependency-management' version '1.1.4'
}

group = 'com.kodilla'
version = '0.0.1-SNAPSHOT'

java {
    sourceCompatibility = '21'
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'

    testImplementation 'io.rest-assured:rest-assured:5.4.0'
    testImplementation 'io.rest-assured:spring-mock-mvc:5.4.0'
    testImplementation 'com.google.code.gson:gson:2.8.9'
    testImplementation 'io.rest-assured:json-path:5.4.0'
    testImplementation 'io.rest-assured:xml-path:5.4.0'

    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'

    testImplementation('org.springframework.boot:spring-boot-starter-test') {
        exclude group: 'io.rest-assured'
        exclude group: 'io.rest-assured', module: 'rest-assured-common'
        exclude group: 'io.rest-assured', module: 'spring-mock-mvc'
    }
}

tasks.named('test') {
    useJUnitPlatform()
}
```
## Test Suites Overview

### ✔ Controller Unit Tests (MockMvc, Mockito)

Tests verify:
- correct handling of HTTP requests
- JSON serialization and deserialization
- validation of the returned book list
- proper HTTP status codes (200, 201, 404, etc.)
- correct interactions between controller and service layer

Test files:
- `BookControllerMvcTest`
- `BookControllerTest`


### ✔ REST Integration Tests (RestAssured)

Cover:
- full HTTP request/response flow
- JSON structure validation
- checking list sizes, object fields and HTTP status
- verifying that endpoints behave the same way through real HTTP calls

Test file:
- `BookControllerRestAssuredTest`


### ✔ External API Tests

Using RestAssured to verify public API behavior:
- reading data from external services
- updating posts using PUT requests
- validating updated fields and returned JSON structure

Test files:
- `ExternalApiRestAssuredTest`
- `ExternalApiTestOfUpdatingAPost`


---

### Optional Terminal Commands

- Build the project:

```bash
./gradlew build
```
- Run tests:
```bash
./gradlew test
```
- Clean the project:
```bash
./gradlew clean
```
## Authors

Created by:

**Joanna Kamińska**  
GitHub: [https://github.com/joanna-kaminska-qa](https://github.com/joanna-kaminska-qa)

---

## Version History

- **0.2** – Minor improvements in structure (README added)
- **0.1** – Initial upload

---

## License

This project is licensed under the **MIT License**.  
See the LICENSE file for details.

---

## Acknowledgments
- Kodilla Automated Tester Java course 
- Spring Boot documentation 
- RestAssured documentation 
- JSONPlaceholder API 
- JUnit Platform documentation