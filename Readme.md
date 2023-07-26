# Spring Boot Application - Customer API

This Spring Boot application implements an API that allows you to manage customer information. It provides endpoints for 
retrieving all customers, adding a new customer, updating customer details, retrieving customer information by ID and delete 
customer information y ID.

## Endpoints:

1. **Retrieve all customers** (HTTP GET):
    - Endpoint: `/api/v1/customers`
    - Description: Get a list of all customers.

2. **Add a new customer** (HTTP POST):
    - Endpoint: `/api/v1/customers`
    - Description: Add a new customer to the database. 
    - Request Body (JSON):
   ```json
   {
     "name": "John Doe",
     "email": "johndoe@example.com",
     "age": 30
   }
   ```
3. Update customer information (HTTP PUT):
   - Endpoint: /api/v1/customers/{customerId} 
   - Description: Update information for an existing customer. 
   - Request Body (JSON):
   ```json
   {
   "name": "Updated Name",
   "email": "updatedemail@example.com",
   "age": 35
   }
   ```
4. Retrieve customer by ID (HTTP GET):
    - Endpoint: /api/v1/customers/{customerId} 
    - Description: Get information for a specific customer by their ID.
5. Delete customer by ID (HTTP DELETE)
   - Endpoint: /api/v1/customers/{customerId} 
   - Description: Delete information for a specific customer by their ID

## Getting Started:
- Initialize Docker on your computer. 
- Run the Tomcat app using docker-compose.yml. 
    ```shell
    # Navigate to the directory containing docker-compose.yml
    cd /path/to/your/project
    # Run Docker Compose to start the Tomcat server
    docker-compose up -d
    ```
- Run Main.java. 
  - Make sure you have Java and Maven installed on your system. 
  - Navigate to the project directory and run the following command:
  ```shell
  mvn spring-boot:run
  ```
- Use POSTMAN or any other API client to interact with the API.

## Configure the Connection with the Database:

To configure the connection with the database, find the file called `application.yml` under `src/main/resources`. Now, you
can configure your information here, you need to modify the port, username, and password from the docker-compose.yml file.

```yml
spring:
  datasource:
    url: jdbc:postgresql://localhost:PORT/customer
    username: username
    password: password
```
You can see the full list of options in the official docs.

## Configure Server

To configure a server, create a file called `application.yml` under `src/main/resources`. Now, you can configure your
server here. For example, if you want to change your port, change `PORT`:

```yml
server:
  port: PORT
```

## Useful Commands to manage databases

```shell
# Go into the image bash
docker exec -it postgres bash
# Go into database, change username for the one you create in docker-compose.yml
psql -U username
# List all available databases 
\l to list databases
# Create a new database
CREATE DATABASE customer;
# Exit from database bash
\q
# Exit docker compose bash
ctrl+D
# Connect to the database
\c databeName
```

Please note that you may need to replace 'username' with the actual username you defined in the docker-compose.yml file.