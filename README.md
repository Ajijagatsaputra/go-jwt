# Go JWT Authentication REST API

A robust and scalable RESTful API built in Go for user authentication and authorization, utilizing **JWT (JSON Web Tokens)** for secure, stateless sessions. This project demonstrates best practices in Go backend development, focusing on clean architecture, efficient routing, and database interaction using an ORM.

## 🚀 Key Technologies

* **Language:** Go (Golang)
* **Routing:** [Gorilla Mux](https://github.com/gorilla/mux) - For powerful and flexible routing and URL matching.
* **Database ORM:** [GORM](https://gorm.io/) - The fantastic ORM library for Go, simplifying database operations.
* **Authentication:** [jwt-go/v4](https://github.com/golang-jwt/jwt) - Standard library for generating, signing, and validating JWTs.
* **Database:** Mysql/MariaDB

## ✨ Features

* **User Registration (`/api/register`):** Secure storage of user passwords using hashing (bcrypt).
* **User Login (`/api/login`):** Generates and returns a secure JWT upon successful authentication.
* **User Authorization (`/api/user`):** Protected route requiring a valid JWT in the Authorization header.
* **Logout (`/api/logout`):** Deletes the JWT token (implemented by client-side or server-side token blacklisting).
* **Middleware:** Custom middleware implementation for JWT validation and route protection.
* **Configuration:** Uses environment variables for database credentials and JWT secrets.

## 🛠️ Getting Started

### Prerequisites

Pastikan Anda telah menginstal komponen-komponen berikut:

1.  **Go:** Version 1.21+
2.  **Mysql/MariaDB** 

### Installation and Setup

1.  **Clone Repository:**
    ```bash
    git clone https://github.com/Ajijagatsaputra/go-jwt.git
    cd go-jwt
    ```

2.  **Environment Variables:**
    Buat file `.env` di *root* direktori dan isi dengan konfigurasi Anda.

    ```

3.  **Run Locally:**
    ```bash
    go mod init
    go run .
    ```
    *Pastikan server Mysql Anda sudah berjalan dan terkonfigurasi sesuai

## 📌 API Endpoints

Aplikasi akan berjalan pada `http://localhost:8080`.

| Method | Endpoint | Description | Body Required |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/register` | Membuat akun user baru. | `name`, `email`, `password` |
| `POST` | `/api/login` | Login dan menerima JWT. | `email`, `password` |
| `GET` | `/api/user` | Mendapatkan data user (membutuhkan JWT). | None (JWT di header) |
| `POST` | `/api/logout` | Logout user (opsional, tergantung implementasi). | None |

### Example Request (Login)

**Request:**
```json
POST /api/login
Content-Type: application/json

{
    "email": "test@example.com",
    "password": "password123"
}

{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..." // JWT Token
}
