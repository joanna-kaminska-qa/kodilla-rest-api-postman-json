# kodilla-rest-api-postman-json

![Java](https://img.shields.io/badge/Java-21-blue)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-brightgreen)
![Gradle](https://img.shields.io/badge/Gradle-8-green)
![JUnit](https://img.shields.io/badge/JUnit-5.9.3-purple)
![Mockito](https://img.shields.io/badge/Mockito-5.3.1-orange)
![RestAssured](https://img.shields.io/badge/RestAssured-5.4.0-blueviolet)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Status: Completed](https://img.shields.io/badge/Status-Completed-brightgreen)

---

This project includes exercises and homework tasks completed as part of a module in the Kodilla **Automated Tester** course, focusing on **REST API, Postman and JSON**.  

The repository covers four major areas:

1️⃣ REST API Development (Spring Boot)

2️⃣ REST API Testing (JUnit, MockMvc, RestAssured)

3️⃣ JSON basics & Postman automation

4️⃣ Bonus: Node.js script for sending test emails via MailHog

The project was developed in **IntelliJ IDEA**, using **Java 21** and **Spring Boot 3.2.5** as part of the learning path for future **QA/Test Automation Engineers**.


---

## Description

### ✔ Spring Boot REST API
A simple book-management API with:

- `GET /books`
- `POST /books`
- `PUT /books/{title}`
- `DELETE /books/{title}`

Architecture:

- `BookController`
- `BookService`
- `BookDto`

### ✔ REST API Testing
Using:

- **JUnit 5**
- **Mockito**
- **Spring MockMvc**
- **RestAssured**

Tests verify:

- HTTP status codes (200/201/404)
- JSON structure & serialization
- Controller → Service interactions
- Handling of external APIs

Included test files:

- `BookControllerMvcTest`
- `BookControllerTest`
- `BookControllerRestAssuredTest`
- `ExternalApiRestAssuredTest`
- `ExternalApiTestOfUpdatingAPost`

### ✔ JSON Basics (Module exercises)
Folder: `postman-json/Kodilla-homework/`

Contains:

- JSON structure tasks
- Screenshots from Postman
- JSON formatting exercises

Files:

- `Zadanie 10.1 – podstawy JSON.txt`
- `Zadanie 10.2 – podstawy JSON.png`
- `Zadanie 10.3 – screenshot from Postman`

### ✔ Postman Collections
Stored in: `postman-json/Postman-exercises/`

Included:

- JSONPlaceholder collection
- HTTPBin automated tests
- Course collection

Useful for API exploratory testing and API automation practice.

### ✔ MailHog Email Automation Script (Node.js)
Folder: `mail-mailhog/`

Contents:

- Node.js project using **nodemailer**
- Example script for sending test mail to MailHog (`skrypt.js`)
- Automatically installed `node_modules`
- Supports local testing of email functionalities

> This part is *not* Java-related but belongs to the same module.

---

## Project Structure
```
kodilla-rest-api-postman-json/
│ build.gradle
│ gradlew
│ gradlew.bat
│ LICENSE
│ README.md
│ structure.txt
│
├── src/main/java/com/kodilla/rest
│ ├── KodillaRestApiApplication.java
│ ├── controller/BookController.java
│ ├── domain/BookDto.java
│ └── service/BookService.java
│
├── src/test/java/com/kodilla/rest/controller
│ ├── BookControllerMvcTest.java
│ ├── BookControllerRestAssuredTest.java
│ ├── BookControllerTest.java
│ ├── ExternalApiRestAssuredTest.java
│ └── ExternalApiTestOfUpdatingAPost.java
│
├── postman-json/
│ ├── Kodilla-homework/
│ │ ├── Zadanie 10.1 - podstawy JSON.txt
│ │ ├── Zadanie 10.2 - podstawy JSON.png
│ │ └── Screen z Postmana do zadania 10.3.png
│ └── Postman-exercises/
│ ├── HTTPBIN - automatyzacja.postman_collection.json
│ ├── JSONPlaceholder.postman_collection.json
│ └── Kurs.postman_collection.json
│
└── mail-mailhog/
├── package.json
├── package-lock.json
├── skrypt.js
└── node_modules/...
```
---

## Getting Started

### Requirements

- Java 21
- Gradle (wrapper included)
- IntelliJ IDEA
- Spring Boot 3.2.5
- Node.js (for MailHog script — optional)

---

### Running the Application

**Linux/macOS**
```bash
./gradlew clean build
```
**Windows**
```bash
gradlew clean build
```
### Dependencies (Gradle)
```
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
---
## Test Suites Overview

### ✔ Controller Unit Tests
Validate:

- JSON responses
- Returned lists
- HTTP codes
- Service interactions

Files:

- `BookControllerMvcTest`
- `BookControllerTest`

### ✔ REST Integration Tests (RestAssured)
Covers:

- Real HTTP requests
- JSON structure
- Response validation
- Correct endpoint behavior

File:

- `BookControllerRestAssuredTest`

### ✔ External API Tests
Using RestAssured to test:

- GET requests to public APIs
- PUT requests (updating posts)
- JSON validation

Files:

- `ExternalApiRestAssuredTest`
- `ExternalApiTestOfUpdatingAPost`

---

## Postman Collections
Import collections from:  
`postman-json/Postman-exercises/*.postman_collection.json`

Content includes:

- JSONPlaceholder CRUD tests
- HTTPBin automation tasks
- Course exercises

---

## ✉ MailHog Email Testing
Node.js script:  
`mail-mailhog/skrypt.js`

Run:

```bash
cd mail-mailhog
npm install
node skrypt.js
```
Allows sending a test email to MailHog using nodemailer. Useful for QA exercises related to email testing.

---

## Authors

Created by:

**Joanna Kamińska**  
GitHub: https://github.com/joanna-kaminska-qa

---

## Version History

- **0.3** – Added Postman & JSON tasks + MailHog tests
- **0.2** – README added, improved structure
- **0.1** – Initial upload

---

## License

This project is licensed under the **MIT License**.  
See the `LICENSE` file for details.

---

## Acknowledgments

- Kodilla "Automated Tester" Java course
- Spring Boot documentation
- RestAssured documentation
- JSONPlaceholder API
- Postman Learning Center
- MailHog project
