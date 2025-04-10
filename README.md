# Product Management Backend Application

## Introduction

The Product Management Backend Application is a Spring Boot-based RESTful service that allows users to manage product data efficiently. It provides endpoints to create, read, update, and delete product records stored in a MySQL database. This application serves as the backend for any product management system and can be integrated with various front-end applications.

## Features

- **CRUD Operations**: Create, Read, Update, and Delete products with ease.
- **RESTful API**: All endpoints follow REST principles for straightforward integration.
- **Database Management**: Uses MySQL for reliable and scalable data storage.
- **Cross-Origin Support**: Allows requests from different origins with `@CrossOrigin` annotation.

## Technologies

- **Spring Boot**: Framework for building the RESTful API.
- **Spring Data JPA**: For data persistence and repository management.
- **MySQL**: Database for storing product information.
- **Lombok**: To reduce boilerplate code.

## Architecture

The application follows a layered architecture consisting of:

- **Controller**: Handles HTTP requests and responses. Maps incoming requests to the appropriate service methods.
- **Service**: Contains business logic and interacts with the repository layer.
- **Repository**: Handles data access and CRUD operations with the database.
- **Entity**: Represents the data model for persistence in the database.

## Endpoints

- **GET /api/products/all**  
  Retrieves a list of all products.

- **POST /api/products/insert**  
  Inserts a new product into the database.  
  **Request Body**: JSON object representing the product.

- **GET /api/products/find/{id}**  
  Retrieves a product by its ID.

- **PUT /api/products/update/{id}**  
  Updates an existing product's details.  
  **Request Body**: JSON object with updated product details.

- **DELETE /api/products/delete/{id}**  
  Deletes a product by its ID.

## Database Schema

The application uses a MySQL database with the following table:

**Table: `Product`**

| Column    | Type    | Description                   |
|-----------|---------|-------------------------------|
| `id`      | INT     | Primary key, auto-incremented  |
| `name`    | VARCHAR | Name of the product            |
| `price`   | DOUBLE  | Price of the product           |
| `quantity`| INT     | Quantity in stock              |

## Getting Started

### Prerequisites

- JDK 17
- Maven
- MySQL

### Installation and Running the Application

1. **Clone the repository**:

   ```bash
   git clone https://github.com/cybage-devops/ECS-Service-Connect.git

2. **Navigate to the project directory**:

   ```bash
   cd product-management-backend-app

3. **Configure MySQL**:
   - Create a database named productmanagementdb
   - Update the src/main/resources/application.properties file with your database credentials

4. **Build the application**:
   
   ```bash
   mvn clean install

5. **Run the application**:

   ```bash
   mvn spring-boot:run

## Docker

The application can be containerized using Docker. Below are the steps to build and run the Docker image.

### Prerequisites

- Docker installed on your machine

### Steps to followed :

1. **Navigate to the project directory**:

   ```bash
   cd product-management-backend-app

2. **Build the docker image**:

   ```bash
   docker build -t product-management-backend-app .

3. **Run the docker container**:

   ```bash
   docker run -p 8080:8080 product-management-backend-app

4. **Verify the application is running**:
  Open your web browser and navigate to http://localhost:8080 to verify that your Spring Boot application is running in the Docker container.

5. **Authenticate Docker with AWS ECR**:

   ```bash
   aws ecr get-login-password --region your_aws_region | sudo docker login --username AWS --password-stdin your_aws_account_id.dkr.ecr.your_aws_region.amazonaws.com

7. **Tag the Docker Image**:

   ```bash
   docker tag docker_image_name aws_account_id.dkr.ecr.your_aws_region.amazonaws.com/your_ECR_repository:tag

7. **Push the Docker Image to ECR**:

   ```bash
   docker push aws_account_id.dkr.ecr.your_aws_region.amazonaws.com/your_ECR_repository:tag



