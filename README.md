# Product Service

A RESTful microservice built with Spring Boot for managing product information. This service provides a complete CRUD API for product management with an in-memory H2 database and integrated API documentation.

## 📋 Features

- **CRUD Operations**: Create, Read, Update, and Delete products
- **RESTful API**: Well-structured REST endpoints
- **In-Memory Database**: H2 database for quick development and testing
- **API Documentation**: Integrated Swagger/OpenAPI documentation
- **Spring Data JPA**: Simplified database operations with JPA repositories
- **Lightweight & Fast**: Minimal setup with embedded database

## 🛠️ Technologies Used

- **Java 17**
- **Spring Boot 4.0.2**
- **Spring Web MVC**: For building RESTful APIs
- **Spring Data JPA**: For data persistence
- **H2 Database**: In-memory database
- **SpringDoc OpenAPI 2.5.0**: API documentation
- **Maven**: Build and dependency management

## 📋 Prerequisites

Before running this application, ensure you have the following installed:

- **Java Development Kit (JDK) 17** or higher
- **Maven 3.6+** (or use the included Maven wrapper)
- **Git** (for cloning the repository)

## 🚀 Getting Started

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd product-service
   ```

2. **Build the project**

   ```bash
   ./mvnw clean install
   ```

   On Windows:

   ```cmd
   .\mvnw.cmd clean install
   ```

### Running the Application

1. **Start the application**

   ```bash
   ./mvnw spring-boot:run
   ```

   On Windows:

   ```cmd
   .\mvnw.cmd spring-boot:run
   ```

2. The application will start on `http://localhost:8080`

## 📚 API Endpoints

### Product Operations

| Method   | Endpoint         | Description          |
| -------- | ---------------- | -------------------- |
| `POST`   | `/products`      | Create a new product |
| `GET`    | `/products`      | Get all products     |
| `GET`    | `/products/{id}` | Get product by ID    |
| `DELETE` | `/products/{id}` | Delete a product     |

### API Request Examples

#### Create a Product

```bash
curl -X POST http://localhost:8080/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Laptop",
    "price": 999.99
  }'
```

#### Get All Products

```bash
curl http://localhost:8080/products
```

#### Get Product by ID

```bash
curl http://localhost:8080/products/1
```

#### Delete a Product

```bash
curl -X DELETE http://localhost:8080/products/1
```

## 📖 API Documentation

Once the application is running, you can access the interactive API documentation:

- **Swagger UI**: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)
- **OpenAPI JSON**: [http://localhost:8080/v3/api-docs](http://localhost:8080/v3/api-docs)

## 💾 Database Access

### H2 Console

The H2 database console is enabled for easy database inspection:

- **URL**: [http://localhost:8080/h2-console](http://localhost:8080/h2-console)
- **JDBC URL**: `jdbc:h2:mem:testdb`
- **Username**: `sa`
- **Password**: _(leave empty)_

## 🧪 Testing

Run the test suite with:

```bash
./mvnw test
```

On Windows:

```cmd
.\mvnw.cmd test
```

## 📁 Project Structure

```
product-service/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── sliit/
│   │   │           └── product_service/
│   │   │               ├── Product.java                 # Entity model
│   │   │               ├── ProductController.java       # REST controller
│   │   │               ├── ProductRepository.java       # JPA repository
│   │   │               └── ProductServiceApplication.java
│   │   └── resources/
│   │       └── application.properties                   # Configuration
│   └── test/
│       └── java/
│           └── com/
│               └── sliit/
│                   └── product_service/
│                       └── ProductServiceApplicationTests.java
├── pom.xml                                              # Maven configuration
└── README.md
```

## 🏗️ Build & Package

### Create Executable JAR

```bash
./mvnw package
```

The JAR file will be created in the `target/` directory:

```bash
java -jar target/product-service-0.0.1-SNAPSHOT.jar
```

### Skip Tests During Build

```bash
./mvnw package -DskipTests
```

## 🔧 Configuration

Key application properties can be configured in `src/main/resources/application.properties`:

```properties
# Application Name
spring.application.name=product-service

# H2 Database Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

# H2 Console
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# JPA Configuration
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
```

## 🐛 Troubleshooting

### Port Already in Use

If port 8080 is already in use, change it in `application.properties`:

```properties
server.port=8081
```

### Maven Build Issues

Clear Maven cache and rebuild:

```bash
./mvnw clean install -U
```

## 📝 License

This project is created as part of CTSE DevOps Lab 3.

