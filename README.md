# Project: alns-hexadvw-libmgmnt-app
Project for a simple Library Management following the best practices of TDD/BDD, Clean Code, SOLID, DRY and KISS :: It's a Coding Assignment for a position in Hexad GmbH.

# Coding Assigment :: The Mission

```
Library Management

Notes for Candidate
1. Write code that you would be comfortable pushing to production. Some things
to keep in mind:
  - a. Test Driven Development (TDD): OK! (I also followed the BDD principles);
  - b. Proper modelling of classes/modules: OK!;
  - c. Clean Code: OK;
  - d. Do regular commits: OK!.

2. Some principles to keep in mind when solving the assignment
  - a. KISS: OK! (But kee in mind that I already built a solution with persistence layer, so this brings some complexities and require some expertise to handle them).
  - b. DRY: OK! (Spring helps me a lot here :-)

3. It would be good to include your architectural decisions/thoughts/assumptions
in README so that we can better evaluate the assignment?

4. Don’t put the assignment on a public repo.

## Stories
(See the Stories at *.features files located at "/src/test/features" folder.
```

## The Solution Implemented

I decided to use [Spring Boot Initializer](https://start.spring.io/) to make easier to start a more professional and robust project, similar to what we use in real world. Read the `HELP.md` file to know further details about Spring Boot and its subprojects.

I implemented a simple Backend Spring Boot web application, that provides REST API's to handle data operations around a Library Management domain business. I used the following solutions:

  - Git;
  - Java 8+;
  - Build Tool: Apache Maven 3.6.2+
  - Database: H2 in Disk:
    - (See ``src/main/resources/application.properties`` config file to know where will be created the H2 Database files);
  - IDE: JetBrains IntelliJ Idea (But it's Maven based, so it's suitable for any Java IDE with Maven support);
  - Some useful facilitators, such as: Spring Data JPA, Lombok, Swagger-UI.
  - TDD: 
    - In fact, the Stories suggested in this Coding Assigment are best suited for BDD - Behavior Driven Development, so I used Cucumber for Spring Testing Tool. Read some articles about it:
      - [BDD with Cucumber, JUnit and Spring Boot](https://dreamix.eu/blog/java/behaviour-driven-development-bdd-with-cucumber-junit-and-spring-boot);
      - [TDD Vs BDD - The Keys Differences](https://www.softwaretestinghelp.com/tdd-vs-bdd/);
      - [Cucumber BDD](https://medium.com/agile-vision/starting-with-bdd-for-collaborative-development-in-agile-environments-5fb034078b3c)

Inspect the `pom.xml` file to know which frameworks and dependencies are used. Inspect the webapp code to compreehend what is the package structure, naming conventions, classes and their tests. 

## Classes and Tables Design
As mentioned earlier, I used since the Story-01, persistent Entities and Repositories following the Spring-Data-JPA and Hibernate standard. Inspect the packages:
````
  - de.com.alns.codingtest.hexadvw.librarymgmnt
    - .models
    - .models.enums
    - .repositories
````
These Entities are used:
````
  - de.com.alns.codingtest.hexadvw.librarymgmnt
    - Book
    - BookCopy
    - Library
    - User
    - BorrowableItem
    - BorrowOperation
````
  
At the end of Story-04, the application got not so trivial entity relationships, such as ``@OneToOne`` using ``@MapIds`` annotation. And work with them always require a minimum of expertise, because offen there are some trickies on the way.  
 
## Running the the Application

### Pre-requisites:
 - Java 8+
 - Maven 3.6.2+
 - Git

### Assembling the Environment
In the Development Environment, follow the steps below:

- Unzip the Zip file sent attached to HR e-mail;
- Make sure you are at the right branch (master);   
- To build and run the `alns-hexadvw-libmgmnt-app` Application perform the following steps:
  - Open the project in your lovely IDE and build and run the app throughout that way; OR

### Testing 
Inspect the test and integration tests classes:
````
- Features files with the User Stories:
  - src/test/features/*.feature
- StepDefs Java Classes:
  - "src/test/java", Package:
    - de.com.alns.codingtest.hexadvw.librarymgmnt.cucumber.stepdefs.*
- Cucumber Integration Tests for Spring-Boot Config:
    - de.com.alns.codingtest.hexadvw.librarymgmnt.HexadVWCucumberSpringBootTest.java   
````
  - To run the Cucumber BDD Integration Tests:
    - Open the project in your IDE;
    - Open the class file ``de.com.alns.codingtest.hexadvw.librarymgmnt.HexadVWCucumberSpringBootTest.java`` and run this test, according your IDE procedure;
      - I tried hard to find a way to run the Cucumber Integration Tests through Maven command line, but unfortunately, it didn't work properly;
      - All the 4 Stories are passing atthe Cucumber tests within the IDE.
    

### Using the Application

  - To startup the application, go to the project's root and issue the command:
    - [project-dir]/clear && mvn spring-boot:run

  - By default, when the Application startups at this URL:
    - http://localhost:8080/librarymgmnt
  - Open the Swagger-UI page and test the REST API's:
    - `http://localhost:8080/librarymgmnt/swagger-ui.html`

### Mass of Data:

When the each Story/Feature is run by Cucumber tests, the needed mass data are generated. I implemented some utility methods to populate the H2 Database. After the testes finishes, all database structures are dropped.

## Know Issues

  * The Unit Tests must be improved, but the time is short;
  * Try to discover how to run Cucumber Tests by Maven CLI;
  * Refactor the Services and Controller Classes to make them unique responsibility;
  * Implement a simple FrontApp in Angular or React to consume those API's.
