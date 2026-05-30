**1. Introduction to Maven**
Apache Maven is a build automation and project management tool primarily used for Java applications. It simplifies project building, dependency management, testing, packaging, and deployment.

Why Maven? Before Maven, developers had to:
Download libraries manually, Configure build scripts manually, Manage dependencies themselves
Maven automates these tasks.

**2. Why Build Tools Exist**
Build tools help automate software development tasks such as:
Compiling source code, Running tests, Managing dependencies, Packaging applications, Deploying software

Benefits:- Faster development, Reduced manual work, Consistent builds, Easy dependency management

**3. Project Object Model (POM)**
The core of Maven is the POM (Project Object Model) file.

File name: pom.xml
It contains: Project information, Dependencies, Plugins, Build configuration
Example:
<project>
    <groupId>com.example</groupId>
    <artifactId>demo-app</artifactId>
    <version>1.0</version>
</project>

**4. Maven Directory Structure**
Standard Maven Project Structure:
Project
│
├── src
│   ├── main
│   │   └── java
│   └── test
│       └── java
│
├── pom.xml
└── target
Folders
Folder	Purpose
src/main/java	Application code
src/test/java	Test code
target	Generated output

**5. Maven Build Lifecycle**
Maven follows predefined lifecycle phases.

Main Phases
Validate
   ↓
Compile
   ↓
Test
   ↓
Package
   ↓
Verify
   ↓
Install
   ↓
Deploy
Validate

Checks project correctness.

mvn validate
Compile

Compiles Java source code.

mvn compile
Test

Runs unit tests.

mvn test
Package

Creates JAR/WAR file.

mvn package
Install

Installs package into local repository.

mvn install
Deploy

Uploads artifact to remote repository.

mvn deploy

**6. Parent POM**
A Parent POM provides common configurations for multiple projects.
Benefits: Reduces duplication, Centralized dependency management, Easier maintenance
Example:
<parent>
    <groupId>com.company</groupId>
    <artifactId>parent-project</artifactId>
    <version>1.0</version>
</parent>

**7. Maven Dependencies**
Dependencies are external libraries required by a project.
Example:
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.13</version>
</dependency>

**8. Dependency Scope**
Defines where a dependency is available.
Scope	Description
compile	Default scope
test	Only during testing
runtime	Needed during execution
provided	Supplied by server
system	Local dependency

Example: <scope>test</scope>

**9. Transitive Dependencies**
When a dependency requires another dependency, Maven automatically downloads it.
Example:
Project
  ↓
Spring
  ↓
Logging Library

This automatic dependency download is called Transitive Dependency.

**10. Version Conflicts**
Sometimes two libraries require different versions of the same dependency.
Maven resolves conflicts using the nearest dependency rule.

Example:
Library A → Version 1
Library B → Version 2
Maven chooses the nearest version in the dependency tree.

**11. Dependency Management**
Used to manage dependency versions centrally.

Example:
<dependencyManagement>
    <dependencies>
        <dependency>
            ...
        </dependency>
    </dependencies>
</dependencyManagement>

Benefits: Version consistency, Easier updates, Better maintenance

**12. Maven Plugins**
Plugins extend Maven functionality.

Examples: Compiler Plugin, Surefire Plugin, Shade Plugin, Maven Compiler Plugin
Used to compile Java code.

Example:
<plugin>
    <artifactId>maven-compiler-plugin</artifactId>
</plugin>
Maven Surefire Plugin

Used to run unit tests.

Example:

<plugin>
    <artifactId>maven-surefire-plugin</artifactId>
</plugin>
Maven Shade Plugin

Creates a single executable JAR file.

Benefits: Bundles dependencies, Easy deployment

**13. Maven Wrapper (mvnw)**
Maven Wrapper allows projects to use Maven without requiring a global installation.

Files:
mvnw
mvnw.cmd

Run command:

./mvnw package

Benefits: Consistent Maven version, Easy project setup

**14. Maven and Docker Integration**
Maven can work together with Docker for containerized applications.

Workflow:

Code
 ↓
Maven Build
 ↓
JAR File
 ↓
Docker Image
 ↓
Container
.
**15. Dockerizing Maven Applications**
Example Dockerfile:

FROM openjdk:17

COPY target/app.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]

Build Application:

mvn package

Build Docker Image:

docker build -t myapp .

**16. Dockerfile Maven Plugin**
This plugin helps Maven build Docker images automatically.
Benefits: Automates Docker builds, Simplifies CI/CD workflows, Reduces manual work

**17. Pushing Artifacts to Registries**
After building applications, artifacts can be pushed to repositories.

Examples: Maven Central, Nexus Repository, Artifactory, Docker Hub

Command:
mvn deploy
Advantages of Maven
Easy dependency management
Automated builds
Standard project structure
Plugin support
CI/CD integration
Docker compatibility


**Summary**
Apache Maven is a powerful build automation tool used for managing Java projects. It automates compilation, testing, packaging, dependency management, and deployment. Maven uses a POM file, predefined lifecycle phases, plugins, and repository management to simplify software development. It also integrates seamlessly with Docker and CI/CD pipelines, making it an essential tool in modern DevOps practices.
