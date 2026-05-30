**1. Introduction to Jenkins**
Jenkins is an open-source automation server used for Continuous Integration (CI) and Continuous Deployment (CD). It helps automate building, testing, and deploying software applications.

Why Jenkins?
Automates repetitive tasks
Faster software delivery
Supports CI/CD pipelines
Integrates with Git, Maven, Docker, and Cloud platforms

**2. Jenkins Architecture**
Jenkins follows a Master-Agent Model.

                Jenkins Master
                      |
        -----------------------------
        |             |             |
     Agent 1       Agent 2       Agent 3
Master Responsibilities
Manages jobs
Schedules builds
Assigns tasks to agents
Agent Responsibilities
Executes build tasks
Runs tests
Performs deployments

**3. Jenkins Installation and UI Overview**
Installation Methods
Windows Installer
Linux Package Manager
Docker Container
WAR File
Access Jenkins
http://localhost:8080

Main Dashboard Features:
Dashboard
Build History
Manage Jenkins
Credentials
Plugins

**4. Jenkins Plugins**
Plugins extend Jenkins functionality.
Popular Plugins:
Plugin	Purpose
Git Plugin	Git integration
Maven Plugin	Maven builds
Docker Plugin	Docker integration
Pipeline Plugin	Pipeline creation
GitHub Plugin	GitHub integration

Benefits: Easy integration, Increased functionality, Automation support

**5. Jenkins Security**
Security features include:
User authentication
Authorization
Role-based access control
Credentials management
Best Practices
Strong passwords
Limited admin access
Secure credentials storage
Regular plugin updates

**6. Jenkins Jobs**
A job is a task performed by Jenkins.
Types: Freestyle Job, Pipeline Job, Multi-Branch Pipeline

**7. Freestyle vs Pipeline Jobs**
Feature	Freestyle	Pipeline
Configuration	GUI Based	Code Based
Flexibility	Limited	High
Version Control	Difficult	Easy
CI/CD Support	Basic	Advanced

Pipeline jobs are preferred in modern DevOps environments.

**8. Jenkins Pipeline**
A Jenkins Pipeline defines the entire CI/CD process as code.

Benefits: Automation, Reusability, Version control, Better maintenance
Pipeline configuration file: Jenkinsfile

**9. Declarative Pipeline Syntax**

Example:

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Application'
            }
        }
    }
}

Advantages:

Easy to read
Structured syntax
Recommended approach

**10. Scripted Pipeline Syntax**
Example:
node {

    stage('Build') {
        echo 'Building Application'
    }

}

Advantages: More flexibility, Advanced scripting

**11. Jenkinsfile Structure**
Basic Structure:
Pipeline
   |
 Agent
   |
 Stages
   |
 Steps

Example:
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build'
            }
        }

        stage('Test') {
            steps {
                echo 'Test'
            }
        }

    }
}

**12. Parameters and Environment Variables**
Parameters
Allow user input during build execution.

Example:
parameters {
    string(name: 'VERSION')
}
Environment Variables

Example:
environment {
    APP_NAME = "DevOpsProject"
}

**13. Multi-Branch Pipelines**
A Multi-Branch Pipeline automatically discovers branches from a Git repository.

Benefits: Branch-specific builds, Better Git integration, Automated branch management

Example:
main
feature-login
feature-payment

Each branch gets its own pipeline.

**14. Pipeline Stages**
Typical CI/CD stages:
Checkout
   ↓
Build
   ↓
Test
   ↓
Package
   ↓
Deploy
Checkout Code

Fetch source code from GitHub.
git 'https://github.com/project/repo.git'
Build Stage
Compile application.

Example:
sh 'mvn compile'
Test Stage

Execute tests.

sh 'mvn test'
Package Stage

Create deployable artifact.

sh 'mvn package'
Post Actions

Actions executed after pipeline completion.
Example:

post {
    always {
        echo 'Pipeline Finished'
    }
}

**15. Managing Artifacts**
Artifacts are generated files such as:
JAR files      WAR files     Reports
Example:
archiveArtifacts 'target/*.jar'

Benefits: Easy access, Version tracking, Deployment support

**16. Docker and Jenkins Integration**
Jenkins can automate Docker operations.

Workflow:
 Source Code
      ↓
 Jenkins Build
      ↓
 Docker Image
      ↓
 Deployment
 
**17. Building Docker Images Using Jenkins**
Example:
sh 'docker build -t myapp .'

Benefits: Automated image creation, Consistent deployments

**18. Docker Inside Jenkins Agents**
Jenkins agents can execute Docker commands.

Example:

agent {
    docker {
        image 'maven:3.9'
    }
}

Advantages: Isolated environments, Consistent builds

**19. Publishing Images to Docker Hub / GHCR**
Example:
sh 'docker push username/myapp'
Deployment Flow:

Build Image
      ↓
Tag Image
      ↓
Push Image

**20. Jenkins and GitHub Integration**
Jenkins can connect directly with GitHub repositories.

Benefits: Automatic builds, Webhook support, Faster CI/CD

Workflow:
GitHub Push
      ↓
Webhook Trigger
      ↓
Jenkins Build

**21. Backup and Restore**
Backup
Important items: Jenkins Home Directory, Job Configurations, Plugins, Credentials, Restore

Restore backup files into Jenkins Home.

Benefits: Disaster recovery, Data protection

**22. Pipeline Best Practices**
Use Jenkinsfile
Keep pipelines simple
Store credentials securely
Use reusable stages
Monitor builds regularly
Backup Jenkins data

**23. Jenkins and Maven Integration**
Jenkins can execute Maven builds automatically.
Configure Maven
Manage Jenkins → Global Tool Configuration
Add Maven installation.
Maven Build Example
sh 'mvn clean install'

Benefits: Automated builds, Dependency management, Faster development.

**24. Code Coverage and Test Reports**
Jenkins can generate:
JUnit Reports
Test Results
Code Coverage Reports

Benefits: Quality assurance, Better monitoring, Defect detection

**25. Triggering Builds**
Poll SCM
Jenkins periodically checks repository changes.
Example:
H/5 * * * *
Checks every 5 minutes.

Webhooks: GitHub instantly notifies Jenkins after code changes.

Benefits: Faster execution, Real-time builds

**26. Jenkins Agents**
Types:
SSH Agents: Connect using SSH protocol.
SFTP Agents: File transfer support.
Container-Based Agents: Docker containers act as Jenkins agents.

Benefits: Scalability, Isolation, Flexibility

**27. CI/CD Deployment Flow**
Complete Jenkins Workflow:

Developer Pushes Code
          ↓
GitHub Repository
          ↓
Jenkins Trigger
          ↓
Build
          ↓
Test
          ↓
Package
          ↓
Docker Image
          ↓
Deployment
Advantages of Jenkins
Open Source
Large Plugin Ecosystem
Strong CI/CD Support
Git Integration
Docker Integration
Maven Support
Cloud Deployment Support



**Summary**
Jenkins is one of the most popular CI/CD automation tools used in DevOps. It supports automated building, testing, packaging, and deployment of applications through pipelines. Jenkins integrates seamlessly with GitHub, Maven, Docker, and cloud platforms, enabling efficient software delivery. Features such as pipelines, plugins, agents, webhooks, and Docker integration make Jenkins a powerful solution for implementing modern CI/CD workflows.
