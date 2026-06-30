# Users API with PostgreSQL

A simple REST API written in Go for managing users with PostgreSQL as a database.

## Tech Stack

* Go
* net/http
* PostgreSQL
* database/sql
* lib/pq
* godotenv
* Git / GitHub

## Features

* Create user
* Get all users
* Get user by ID
* Update user by ID
* Delete user by ID
* Get users count
* Delete all users
* PostgreSQL storage
* Environment variables for database configuration
* JSON responses

## Project Structure

```text
users-api-postgres
├── internal
│   ├── database
│   │   └── database.go
│   ├── handlers
│   │   └── users_handler.go
│   ├── models
│   │   └── user.go
│   └── response
│       └── response.go
├── main.go
├── go.mod
├── go.sum
├── .gitignore
├── .env.example
├── solution.sql
└── README.md
```

## Environment Variables

Create a `.env` file in the project root:

```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=users_api
DB_SSLMODE=disable
```

The real `.env` file should not be committed to GitHub.

Example file for GitHub:

```text
.env.example
```

## Database Table

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INTEGER CHECK (age >= 0),
    email VARCHAR(255) UNIQUE NOT NULL,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## API Endpoints

### Create user

```http
POST /addUser
```

Example request:

```powershell
Invoke-RestMethod -Method POST http://localhost:8080/addUser `
  -ContentType "application/json" `
  -Body '{"name":"Max","age":29,"email":"max@example.com"}'
```

### Get all users

```http
GET /getUsers
```

Example request:

```powershell
Invoke-RestMethod -Method GET http://localhost:8080/getUsers
```

### Get user by ID

```http
GET /getUser?id=1
```

Example request:

```powershell
Invoke-RestMethod -Method GET "http://localhost:8080/getUser?id=1"
```

### Update user by ID

```http
PUT /updateUser?id=1
```

Example request:

```powershell
Invoke-RestMethod -Method PUT "http://localhost:8080/updateUser?id=1" `
  -ContentType "application/json" `
  -Body '{"name":"Max Updated","age":30,"email":"max.updated@example.com"}'
```

### Delete user by ID

```http
DELETE /deleteUser?id=1
```

Example request:

```powershell
Invoke-RestMethod -Method DELETE "http://localhost:8080/deleteUser?id=1"
```

### Get users count

```http
GET /getCount
```

Example request:

```powershell
Invoke-RestMethod -Method GET http://localhost:8080/getCount
```

### Delete all users

```http
DELETE /clearUsers
```

Example request:

```powershell
Invoke-RestMethod -Method DELETE http://localhost:8080/clearUsers
```

## How to Run

Clone the repository:

```powershell
git clone https://github.com/Vladislav-090/users-api-postgres.git
```

Go to the project folder:

```powershell
cd users-api-postgres
```

Install dependencies:

```powershell
go mod tidy
```

Create `.env` file and configure database connection.

Run the application:

```powershell
go run .
```

Server will start on:

```text
http://localhost:8080
```

## Status

This project is a learning backend API built step by step while practicing:

* HTTP handlers
* JSON decoding and encoding
* PostgreSQL queries
* INSERT RETURNING
* SELECT
* UPDATE RETURNING
* DELETE
* COUNT
* environment variables
* Git workflow
