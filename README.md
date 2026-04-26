# SayGenFix

Saygenfix is an AI-powered online examination platform designed to streamline the process of creating, distributing, and grading exams. Built with Go, it provides a clean, role-based interface for both teachers and students.

## Table of Contents

- [About The Project](#about-the-project)
- [Key Features](#key-features)
- [Built With](#built-with)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [License](#license)

## About The Project

This project is a server-side rendered web application that serves as a robust platform for online exams. It features a clear separation of concerns using a layered architecture, making the codebase maintainable and scalable.

The system supports two main roles:
*   **Teachers:** Can create exams, write questions, review student submissions, and view overall results.
*   **Students:** Can view their assigned exams, submit their answers, and check their scores upon completion.

A key feature is the integration with Google's Gemini API, leveraging AI to assist with exam-related tasks.

## Key Features

- **General**
  - Secure User Authentication (Login/Register)
  - Role-based access control (Teacher vs. Student)

- **Teacher Portal**
  - Dashboard with an overview of created exams
  - Create, Edit, and Manage Exams
  - Review and Grade Student Submissions
  - View Detailed Exam Results

- **Student Portal**
  - Dashboard listing available and completed exams
  - Clean interface for taking exams
  - View personal scores and results history

- **AI-Powered Assistance**
  - Utilizes the Google Gemini API for advanced functionalities.

## Built With

*   [Go (Golang)](https://go.dev/)
*   [PostgreSQL](https://www.postgresql.org/) (via `pgx`)
*   [Google Gemini API](https://ai.google.dev/)
*   HTML & CSS (Server-Side Rendered)
*   [Docker](https://www.docker.com/)

## Project Structure

The project follows a standard layered architecture to separate concerns:

```
/
├── cmd/web/              # Main application entry point
├── internal/
│   ├── config/           # Environment, logger, validator setup
│   ├── database/         # Database connection and migrations
│   ├── handler/          # HTTP request handlers
│   ├── middleware/       # HTTP middleware
│   ├── model/            # Domain and DTO data structures
│   ├── repository/       # Data access layer (database operations)
│   ├── router/           # HTTP route definitions
│   └── service/          # Business logic
├── templates/            # HTML templates for the frontend
├── go.mod                # Go module dependencies
└── Dockerfile            # Container definition
```

## Getting Started

To get a local copy up and running, follow these steps.

### Prerequisites

- **Go**: Version 1.24 or newer.
- **PostgreSQL**: A running instance.
- **Database Migration Tool**: A tool like [golang-migrate/migrate](https://github.com/golang-migrate/migrate) is needed to run the SQL migrations.

### Installation

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/mhaatha/go-template-saygenfix.git
    cd go-template-saygenfix
    ```

2.  **Install dependencies:**
    ```sh
    go mod tidy
    ```

3.  **Configure environment variables:**
    Create a `.env` file in the root directory by copying the example (if one exists) or creating it from scratch. It should contain database credentials, session keys, and your Google Gemini API key.
    ```env
    # Example .env
    DB_HOST=localhost
    DB_PORT=5432
    DB_USER=your_db_user
    DB_PASSWORD=your_db_password
    DB_NAME=saygenfix
    DB_SSL_MODE=disable

    GEMINI_API_KEY=your_api_key
    ```

4.  **Run database migrations:**
    Use a migration tool to apply the SQL files located in `internal/database/migrations/`. For example, using `golang-migrate/migrate`:
    ```sh
    migrate -database 'postgres://user:password@host:port/dbname?sslmode=disable' -path internal/database/migrations up
    ```

5.  **Run the application:**
    ```sh
    go run ./cmd/web/main.go
    ```
    The application should now be running on your local server.

## License

Distributed under the MIT License. See `LICENSE` file for more information.
