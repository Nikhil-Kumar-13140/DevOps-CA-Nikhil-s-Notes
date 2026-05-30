**1. Introduction to Microservices**
**What are Microservices?**
Microservices Architecture is a software development approach where an application is divided into small, independent services. Each service performs a specific business function and communicates with other services through APIs.
Unlike a monolithic application, where all functionalities are bundled into a single codebase, microservices separate functionalities into multiple services.

*Example :- An E-commerce Application can be divided into:
User Service
Product Service
Order Service
Payment Service
Notification Service
Each service can be developed, deployed, and scaled independently.

**2. Need for Microservices**
Traditional monolithic applications face several challenges:
Difficult to maintain
Large codebase
Slow deployment
Difficult scaling
Single point of failure
Microservices solve these problems by dividing the application into smaller services.

Benefits
Independent deployment
Better scalability
Faster development
Improved fault isolation
Technology flexibility
Easier maintenance

**3. Monolithic vs Microservices Architecture**
Feature	Monolithic	Microservices
Codebase	Single	Multiple
Deployment	Single unit	Independent services
Scalability	Entire application	Individual service
Maintenance	Difficult	Easier
Fault Isolation	Low	High
Development Speed	Slower	Faster

**4. Advantages of Microservices**
**Scalability :-** Each service can be scaled independently.
*Example: If payment requests increase, only the Payment Service needs scaling.

**Isolation :-** Failure in one service does not affect the entire application.
*Example: If Notification Service crashes, Order Service can continue functioning.

**Agility :-** Development teams can work independently on different services.
This enables faster software releases.

**5. API Gateway**
An API Gateway acts as a single entry point for all client requests.

Functions :- Request routing, Authentication, Authorization, Load balancing, Rate limiting

Architecture:- 
                    Client
                      |
                  API Gateway
                      |
           -----------------------
           |         |           |
          User     Order       Payment

Benefits:
Centralized security
Simplified client communication
Reduced complexity

**6. Docker Compose**
Docker Compose is a tool used to define and run multi-container Docker applications.
Instead of running multiple docker commands manually, Docker Compose allows all configurations inside a YAML file.

File name:- docker-compose.yml

Benefits: Easy deployment, Simplified configuration, Multi-container management, Reproducibility

**7. Docker Compose Architecture**

                docker-compose.yml
                       |
                Docker Compose
                      |
            ---------------------
            |         |         |
        Frontend   Backend   Database

All services start together using a single command. --- **docker compose up**

**8. YAML Structure**
YAML stands for:- YAML Ain't Markup Language
It is a human-readable configuration language.

**Basic Structure:**
version: '3'
services:
  web:
    image: nginx

  database:
    image: mysql
    
**9. Components of docker-compose.yml**
Version: Defines compose file format.
version: '3.8'

Services: Defines application containers.
services:
  web:
    image: nginx
    
Volumes: Used for persistent storage.
volumes:
  mysql_data:
Networks

Allows communication between containers.

networks:
  app-network:
  
**10. Writing docker-compose.yml**

Example:
version: '3.8'
services:

  frontend:
    image: nginx
    ports:
      - "80:80"

  backend:
    image: node

  database:
    image: mysql
    
**11. Environment Variables**
Environment variables store configuration values.
Example:

services:
  database:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root123

Benefits: Security, Flexibility, Easy configuration

**12. Secrets and Configs**
Secrets: Used to store sensitive information.

Examples:
Passwords
API Keys
Tokens

Example:
secrets:
  db_password:
    file: ./password.txt
Configs

Used for non-sensitive configuration files.

Example:

configs:
  app_config:
    file: ./config.txt
    
**13. Build vs Image**
Using Image

Downloads pre-built image.

services:
  app:
    image: nginx
Using Build

Builds image from Dockerfile.

services:
  app:
    build: .

Difference:

Build	Image
Creates image	Uses existing image
Needs Dockerfile	No Dockerfile required

**14. Service Dependency Ordering**

Docker Compose provides:

depends_on

Example:

services:

  backend:
    depends_on:
      - database

  database:
    image: mysql

Backend starts after database.

**15. Multi-Container Applications**

A typical application contains:

Frontend
   |
Backend
   |
Database

Each component runs in a separate container.

Benefits:

Better scalability
Easier management
Independent deployment

**16. WordPress + MySQL Deployment**

Example Compose File:

version: '3'

services:

  wordpress:
    image: wordpress
    ports:
      - "80:80"

  mysql:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root123

Run:

docker compose up -d

**17. Node.js + MongoDB Deployment**
version: '3'

services:

  nodeapp:
    build: .

  mongodb:
    image: mongo

Benefits:

Fast deployment
Service separation
Easy scaling

**18. Java Spring Boot + PostgreSQL**
version: '3'

services:

  springboot:
    build: .

  postgres:
    image: postgres

Environment Variables:

environment:
  POSTGRES_PASSWORD: admin
  
**19. Docker Compose Commands**

Start Services

docker compose up

Run in Background

docker compose up -d

Stop Services

docker compose down

View Containers

docker ps

View Logs

docker compose logs

Restart Services

docker compose restart

**20. Advantages of Docker Compose**
Easy configuration
Faster deployment
Supports multi-container applications
Reproducible environments
Simplified networking
Better DevOps workflow
