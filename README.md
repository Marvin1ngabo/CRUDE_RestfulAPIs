# Product Management REST API

A Spring Boot RESTful API for managing products with full CRUD operations.

## Technologies Used

- Java 17
- Spring Boot 4.0.2
- Spring Data JPA
- PostgreSQL
- Maven

## Prerequisites

- Java 17 or higher
- PostgreSQL 18.0
- Maven (or use included Maven wrapper)

## Database Configuration

Create a PostgreSQL database named `ecommerce_db` and update the credentials in `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce_db
spring.datasource.username=postgres
spring.datasource.password=postgres
```

## Running the Application

Using Maven wrapper:
```bash
./mvnw spring-boot:run
```

Or on Windows:
```bash
mvnw.cmd spring-boot:run
```

The application will start on `http://localhost:8080`

## API Endpoints

### Base URL
```
http://localhost:8080/api/products
```

### 1. Create Product
**POST** `/api/products/addProduct`

**Request Body:**
```json
{
  "id": 1,
  "name": "Laptop",
  "description": "High-performance laptop",
  "price": 999.99,
  "category": "Electronics",
  "stockQuantity": 50
}
```

**Response:** `201 CREATED`
```json
"Product saved successfully."
```

### 2. Get All Products
**GET** `/api/products`

**Response:** `200 OK`
```json
[
  {
    "id": 1,
    "name": "Laptop",
    "description": "High-performance laptop",
    "price": 999.99,
    "category": "Electronics",
    "stockQuantity": 50
  }
]
```

### 3. Get Product by ID
**GET** `/api/products/{id}`

**Example:** `GET /api/products/1`

**Response:** `200 OK`
```json
{
  "id": 1,
  "name": "Laptop",
  "description": "High-performance laptop",
  "price": 999.99,
  "category": "Electronics",
  "stockQuantity": 50
}
```

**Error Response:** `404 NOT FOUND`
```json
"Product with id 1 not found."
```

### 4. Update Product
**PUT** `/api/products/{id}`

**Example:** `PUT /api/products/1`

**Request Body:**
```json
{
  "name": "Gaming Laptop",
  "description": "High-performance gaming laptop",
  "price": 1299.99,
  "category": "Electronics",
  "stockQuantity": 30
}
```

**Response:** `200 OK`
```json
"Product updated successfully."
```

**Error Response:** `404 NOT FOUND`
```json
"Product with id 1 not found."
```

### 5. Delete Product
**DELETE** `/api/products/{id}`

**Example:** `DELETE /api/products/1`

**Response:** `200 OK`
```json
"Product deleted successfully."
```

**Error Response:** `404 NOT FOUND`
```json
"Product with id 1 not found."
```

## Testing the API

### Using cURL

```bash
# Create a product
curl -X POST http://localhost:8080/api/products/addProduct \
  -H "Content-Type: application/json" \
  -d '{"id":1,"name":"Laptop","description":"Gaming laptop","price":1299.99,"category":"Electronics","stockQuantity":10}'

# Get all products
curl http://localhost:8080/api/products

# Get product by ID
curl http://localhost:8080/api/products/1

# Update product
curl -X PUT http://localhost:8080/api/products/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Updated Laptop","description":"New description","price":1499.99,"category":"Electronics","stockQuantity":5}'

# Delete product
curl -X DELETE http://localhost:8080/api/products/1
```

### Using Browser
For GET requests, simply open:
- `http://localhost:8080/api/products` - Get all products
- `http://localhost:8080/api/products/1` - Get product with ID 1

## Project Structure

```
src/main/java/auca/ac/rw/restfullApiAssignment/
├── controller/
│   └── ProductController.java       # REST API endpoints
├── service/
│   └── ProductService.java          # Business logic
├── repository/
│   └── ProductRepository.java       # Database operations
├── modal/
│   └── Product.java                 # Entity model
└── RestfullApiAssignmentApplication.java  # Main application
```

## Author

Marvin Ingabo
