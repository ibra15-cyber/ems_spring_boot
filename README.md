# Employee Management System (EMS) Backend

This is the backend of the Employee Management System (EMS) that provides REST APIs for managing employee data. It is built using **Spring Boot** and follows a layered architecture, ensuring separation of concerns between controllers, services, and data repositories.

## Features
- Create a new employee
- Retrieve an employee by ID
- Retrieve all employees
- Update an employee's information
- Delete an employee

## Project Structure

- **`dto/`**: Data Transfer Objects (DTO) for communication between layers.
- **`entity/`**: Employee entity representing the employee table.
- **`exception/`**: Custom exceptions like `ResourceNotFoundException`.
- **`mapper/`**: Utility for mapping between DTOs and entities.
- **`repository/`**: Spring Data JPA repository interfaces.
- **`service/`**: Interfaces for the business logic layer.
- **`service/impl/`**: Implementations of the service interfaces.
- **`controller/`**: REST controllers to handle HTTP requests.

## Technologies
- **Java 11+**
- **Spring Boot**
- **Spring Data JPA**
- **H2 Database (for development) or MySQL/PostgreSQL (for production)**
- **Lombok**: To minimize boilerplate code
- **Maven** or **Gradle**: For project dependency management

## API Endpoints

### Create Employee
- **URL**: `/api/employees`
- **Method**: `POST`
- **Description**: Create a new employee.
- **Request Body**:
  ```json
  {
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
  }
  ```
- **Response**: 201 Created
  ```json
  {
    "id": 1,
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
  }
  ```

### Get Employee by ID
- **URL**: `/api/employees/{id}`
- **Method**: `GET`
- **Description**: Get an employee by their ID.
- **Response**: 200 OK
  ```json
  {
    "id": 1,
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
  }
  ```

### Get All Employees
- **URL**: `/api/employees`
- **Method**: `GET`
- **Description**: Retrieve all employees.
- **Response**: 200 OK
  ```json
  [
    {
      "id": 1,
      "firstName": "John",
      "lastName": "Doe",
      "email": "john.doe@example.com"
    },
    {
      "id": 2,
      "firstName": "Jane",
      "lastName": "Smith",
      "email": "jane.smith@example.com"
    }
  ]
  ```

### Update Employee
- **URL**: `/api/employees/{id}`
- **Method**: `PUT`
- **Description**: Update an employee's details.
- **Request Body**:
  ```json
  {
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@newexample.com"
  }
  ```
- **Response**: 200 OK
  ```json
  {
    "id": 1,
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@newexample.com"
  }
  ```

### Delete Employee
- **URL**: `/api/employees/{id}`
- **Method**: `DELETE`
- **Description**: Delete an employee by ID.
- **Response**: 204 No Content

## Getting Started

### Prerequisites
- Java 11 or higher
- Maven or Gradle
- IDE (e.g., IntelliJ, Eclipse)
- H2 (default development database) or MySQL/PostgreSQL for production

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ems_backend.git
   cd ems_backend
   ```

2. Build the project with Maven:
   ```bash
   mvn clean install
   ```

3. Run the application:
   ```bash
   mvn spring-boot:run
   ```

4. The application will be available at `http://localhost:8080`.

### Database Configuration
By default, the application uses the H2 in-memory database. To use a different database, update the `application.properties` file:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ems_db
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
```

### Testing the API
You can use tools like [Postman](https://www.postman.com/) or [cURL](https://curl.se/) to test the API endpoints.

### Example cURL Requests

- **Create Employee**:
  ```bash
  curl -X POST http://localhost:8080/api/employees \
  -H "Content-Type: application/json" \
  -d '{"firstName": "John", "lastName": "Doe", "email": "john.doe@example.com"}'
  ```

- **Get Employee by ID**:
  ```bash
  curl -X GET http://localhost:8080/api/employees/1
  ```

- **Get All Employees**:
  ```bash
  curl -X GET http://localhost:8080/api/employees
  ```

- **Update Employee**:
  ```bash
  curl -X PUT http://localhost:8080/api/employees/1 \
  -H "Content-Type: application/json" \
  -d '{"firstName": "John", "lastName": "Doe", "email": "john.doe@newexample.com"}'
  ```

- **Delete Employee**:
  ```bash
  curl -X DELETE http://localhost:8080/api/employees/1
  ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any issues or inquiries, feel free to contact the project owner at `your.email@example.com`.