## Tools and Technologies Used
1. Spring Boot
2. JDK - 1.8 or later
3. Spring Framework
4. Spring Data JPA (Hibernate)
5. Maven
6. IDE - VS Code
7. PostgreSQL

## Steps Taken
### 1 Create a Spring Boot App
  - Use [Spring Initializer](https://start.spring.io/)
  - Create Project Name
  - Project Type: Maven
  - Dependencies:
    - Spring Web
    - Spring Data JPA
    - PostgreSQL
    - Dev Tools
  - Name Package
### 2 Maven Dependencies
  - Check pom.xml file has all dependencies.
### 3 Configure PostgreSQL Database
  - Create database in PostgreSQL
    - ``` CREATE DATABASE empoyees; ```
  - In ``` src/main/resources/application.properties ``` add 
      ```
      spring.datasource.url=jdbc:postgresql://localhost:5432/employees
      spring.datasource.username=postgres
      spring.datasource.password=root
      spring.jpa.show-sql=true

      ## Hibernate Properties
      # The SQL dialect makes Hibernate generate better SQL for the chosen database
      spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect

      # Hibernate ddl auto (create, create-drop, validate, update)
      spring.jpa.hibernate.ddl-auto = update 
      ```
- Note url, username, and password are environment specific
- Hibernate will automatically create database tables
### 4 Create JPA (Java Persistence API) Entity - Employee.java
  - Create package(folder/dir) model
  - Create class Employee
### 5 Create a Spring Data Repository - EmployeeRepository.java
  - Create package repository in ``` src/main/java/net/javaguides/springboot``` 
  - Create interface in EmployeeRepository.java file
### 6 Create Custom Exception - ResourceNotFoundException.java
  - Create package exception
  - Create class ResourceNotFoundException
### 7 Create Spring Rest Controller - EmployeeController.java
  - Create package controller
  - Create class EmployeeController
## 8 Enable CORS on the Server
  - Add following to EmployeeController.java
  ```
    @CrossOrigin(origins = "http://localhost:4200")
    @RestController
    @RequestMapping("/api/v1/")

    public class EmployeeController { 
  ```
### 9 Running Spring Boot Application
  - At command line
    - ``` mvn spring-boot:run ```
### 10 Test CRUD REST APIs via Postman
  - run locally at:
    - http://localhost:8080/api/v1/employees
