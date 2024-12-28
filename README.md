# Development Environment Services

This `docker-compose.yml` file sets up a local development environment with essential tools and services for modern application development. Below is an overview of the services included and their purpose.

## Create shared network (usefull to connect with other containers)
      docker network create shared-network


## Services

### 1. MySQL
**Image:** `mysql:8.0`  
**Port:** `3306`  
**Purpose:**
- Provides a relational database management system for your application.
- Preconfigured with a default database (`skyline`) and root password (`rootpassword`).
- Persistent data storage via the `mysql-data` volume.

### 2. Redis
**Image:** `redis:7`  
**Port:** `6379`  
**Purpose:**
- Acts as an in-memory data store.
- Commonly used for caching, session management, and queues.

### 3. Memcached
**Image:** `memcached:latest`  
**Port:** `11211`  
**Purpose:**
- Provides a high-performance, distributed memory caching system.
- Useful for reducing database load and speeding up application performance.

### 4. phpMyAdmin
**Image:** `phpmyadmin/phpmyadmin`  
**Port:** `8080`  
**Purpose:**
- A web-based interface to manage MySQL databases.
- Allows you to execute queries, manage tables, and handle database operations.
- Requires the MySQL service to function.

### 5. Mailhog
**Image:** `mailhog/mailhog`  
**Ports:**
- Web Interface: `8025`
- SMTP: `1025`
**Purpose:**
- Provides a local email testing tool.
- Captures outgoing emails for debugging without actually sending them.
- Features a simple web interface to view and inspect emails.

## Network
All services are connected through a custom Docker network named `tools-network`, ensuring seamless communication between containers.

## Volumes
- **`mysql-data`**: Ensures persistent storage for the MySQL database, so your data is not lost when the container stops.

## Usage
1. **Start the containers:**
   ```bash
   docker-compose up --build
   ```

2. **Access the services:**
   - **MySQL:** Available on port `3306`.
   - **Redis:** Available on port `6379`.
   - **Memcached:** Available on port `11211`.
   - **phpMyAdmin:** Open [http://localhost:8080](http://localhost:8080) in your browser.
   - **Mailhog:** Open [http://localhost:8025](http://localhost:8025) in your browser.

3. **Stop the containers:**
   ```bash
   docker-compose down
   ```

## Customization
- Update environment variables (e.g., database credentials) in the `docker-compose.yml` file to match your application's needs.
- Extend the configuration to add additional services or tools as required.

## Troubleshooting
- Ensure Docker is running and that the required ports are not already in use.
- Use `docker-compose logs` to debug any issues with the containers.

This setup provides a solid foundation for a local development environment with essential services ready to use.

