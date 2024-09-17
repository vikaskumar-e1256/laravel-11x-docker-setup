
# Laravel Docker Setup

This project is a Laravel application using Docker for the development environment. The Docker setup includes a PHP service to run Composer, Artisan commands, and a server for running the Laravel application.

## Prerequisites

Make sure you have the following installed on your system:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Getting Started

Follow these steps to get the Laravel application up and running using Docker Compose.

### 1. Clone the Repository

Clone the project repository (if applicable) or create a new directory for the Laravel project:

```bash
git clone <repository_url>
cd <project_directory>
```

### 2. Create Laravel Project

Run the following Docker Compose command to create a new Laravel project inside the current directory:

```bash
docker-compose run --rm composer create-project laravel/laravel .
```

This will use the `composer` service to create a new Laravel project in the current directory.

### 3. Build and Start the Containers

After creating the Laravel project, build and start the Docker containers:

```bash
docker-compose up -d --build server
```

This will build the Docker images and start the `server` container in detached mode.

### 4. Run Database Migrations

To set up the database and run fresh migrations, execute the following command:

```bash
docker-compose run --rm artisan migrate:fresh
```

This command uses the `artisan` service to run the migrations.

### 5. Access the Application

Once the server is up and running, you can access the Laravel application in your browser:

```
http://localhost:8081
```

If you've customized the port in your `docker-compose.yml`, use that port instead.

## Docker Services

The Docker Compose configuration includes the following services:

- **composer**: Used to run Composer commands.
- **artisan**: Used to run Laravel Artisan commands.
- **server**: The main server that runs the Laravel application.

## Common Commands

### Stop the Containers

To stop the running containers:

```bash
docker-compose down
```

### Rebuild Containers

To rebuild the containers (for example, after updating dependencies or modifying the Dockerfile):

```bash
docker-compose up -d --build
```

### Run Other Artisan Commands

You can run any Artisan command via Docker Compose, for example:

```bash
docker-compose run --rm artisan make:migration create_users_table
```

## Troubleshooting

If you run into issues, here are a few steps you can try:

- Ensure Docker and Docker Compose are running correctly.
- Check your `.env` file for database connection settings.
- Verify that the Docker containers are running using `docker ps`.

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
