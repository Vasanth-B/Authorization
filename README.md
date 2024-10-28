Here's a revised and expanded version of the documentation for the "User Authentication and Authorization with JWT" project:

---

# JWT-Based User Authentication and Authorization System

A secure Node.js application for user authentication and authorization using JSON Web Tokens (JWT). This application is structured following the MVC pattern and employs Express.js for routing, Mongoose for MongoDB interaction, and JWT for secure, token-based session management.

## Live Server
- The application runs locally on: `http://localhost:3000`

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [API Endpoints](#api-endpoints)
  - [User Registration](#user-registration)
  - [User Login](#user-login)
  - [Protected Route Access](#protected-route-access)
- [Postman Collection](#postman-collection)
- [Setup Instructions](#setup-instructions)
- [License](#license)

---

## Project Overview

The **JWT-Based User Authentication and Authorization System** is designed to provide secure access control for web applications, ensuring that only authenticated users can access protected routes. User credentials are securely stored using hashed passwords, and JWTs are issued upon successful login to authorize access to restricted resources.

---

## Features

- **User Registration**: New users can register with unique credentials.
- **User Login**: Registered users authenticate with email and password to receive a JWT.
- **Password Hashing**: Passwords are securely hashed before storage using bcrypt.
- **JWT-Based Authentication**: Secure token-based authentication via Bearer tokens.
- **Protected Routes**: Access to certain routes is restricted to authenticated users only.
- **Detailed API Documentation**: Includes descriptions, request formats, and example responses.
- **Error Handling and Validation**: Proper validation and error handling for input and server-side errors.

---

## Technology Stack

- **Node.js**: JavaScript runtime environment.
- **Express.js**: Framework for server-side routing and API development.
- **MongoDB**: NoSQL database for storing user data.
- **Mongoose**: ODM library for MongoDB.
- **JWT (JSON Web Tokens)**: Token-based user authentication.
- **dotenv**: Manages environment variables for secure configuration.
- **bcrypt**: Library for secure password hashing.
- **Postman**: Tool for API testing and documentation.

---

## API Endpoints

### 1. User Registration

- **URL**: `POST /api/users/register`
- **Description**: Registers a new user and securely stores hashed credentials in the database.

#### Request Example

```json
{
  "username": "Vasanthan",
  "email": "vasanth@gmail.com",
  "password": "password@1234"
}
```

#### Success Response

```json
{
  "message": "User registered successfully"
}
```

#### Error Response

- **409 Conflict**: When email is already registered
  ```json
  {
    "error": "Email is already in use"
  }
  ```
  
- **400 Bad Request**: When input validation fails
  ```json
  {
    "error": "Invalid request data"
  }
  ```

---

### 2. User Login

- **URL**: `POST /api/users/login`
- **Description**: Authenticates a user and returns a JWT token upon successful login.

#### Request Example

```json
{
  "email": "vasanth0@gmail.com",
  "password": "password@1234"
}
```

#### Success Response

```json
{
  "token": "your_jwt_token"
}
```

#### Error Response

- **401 Unauthorized**: Incorrect email or password
  ```json
  {
    "error": "Invalid credentials"
  }
  ```

---

### 3. Protected Route Access

- **Description**: Routes requiring user authentication, accessible only by including a valid JWT in the request headers.
- **Example Route**: `GET /api/protected`
- **Headers**: Requires an `Authorization` header with the value `Bearer your_jwt_token`.

#### Success Response

```json
{
  "message": "Welcome to the protected route!"
}
```

#### Error Response

- **403 Forbidden**: Missing or invalid JWT
  ```json
  {
    "error": "Unauthorized access"
  }
  ```

---

## Postman Collection

- All endpoints can be tested and documented using Postman.
- Import the Postman collection provided with the project or manually set up the requests using the endpoint information above.

---

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/jwt-auth-system.git
   cd jwt-auth-system
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Environment Variables**:
   - Create a `.env` file in the root directory with the following variables:
     ```plaintext
     PORT=3000
     MONGO_URI=your_mongodb_connection_string
     JWT_SECRET=your_jwt_secret_key
     ```
   
4. **Start the Server**:
   ```bash
   npm start
   ```

5. **Testing the API**:
   - Use Postman to test each endpoint using the above examples.

---

## License

This project is licensed under the MIT License.