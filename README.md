##  Challenge 3 – Full-Stack Docker Application

### Overview
This project demonstrates the setup and scaling of a full-stack application using Docker Compose. It consists of an Nginx server, a Node.js API service, and a MariaDB database. The application is designed to show how to use Docker in development and production environments, emphasizing the management of environment variables and scaling of services.

### Prerequisites
Before you start, ensure you have the following installed on your system:
- Docker
- Docker Compose

### Configuration Files
- **.env**: Contains all necessary environment variables.
- **docker-compose.yml**: Defines the services, networks, and volumes.

### Environment Variables
The following environment variables need to be set in the `.env` file:
- `MARIADB_ROOT_PASSWORD`: The root password for MariaDB.
- `MARIADB_DATABASE`: The database name.
- `MARIADB_USER`: The database user.
- `MARIADB_PASSWORD`: The password for the database user.

### Setup and Running
1. **Initial Setup**:
   Clone the repository and navigate into the project directory:
   ```bash
   git clone [repository-url]
   cd [project-directory]
   ```

2. **Starting the Application**:
   Use Docker Compose to build and start the application:
   ```bash
   docker-compose up --build
   ```
   This command builds the images and starts the containers as defined in `docker-compose.yml`.

3. **Accessing the Application**:
   - The API can be accessed at: `http://localhost:8080/api/books/`
   - Specific book by ID: `http://localhost:8080/api/books/1`

## Challenge 4 – Scaling the Application
To scale the `node-service` to have 3 running instances:
1. **Modify Docker Compose Configuration**:
   Add the following under the `node-service` service in your `docker-compose.yml`:
   ```yaml
   deploy:
     replicas: 3
   ```

2. **Rebuild and Scale Up**:
   ```bash
   docker-compose up --build
   ```
   This will start 3 instances of `node-service`.

3. **Verify Scaling**:
   - Make requests to `http://localhost:8080/api/stats` and observe different hostnames indicating different instances.
   - Check the running services:
     ```bash
     docker-compose ps
     ```
   This command will list the active instances of `node-service`.

## Benefits of Scaling
Scaling up the `node-service` enhances the application's availability and distributes the load across multiple instances, improving the resilience and performance of the application.

## Conclusion
Thank you for following this guide to set up and scale a full-stack Docker application. We hope this project helps you understand the practical aspects of Docker deployment and management.
