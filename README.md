# Library Backend

This is a backend project for a library management system. It is built using
Django and includes Docker configurations for easy deployment. The main
components of the project include Docker setup, Docker Compose configurations,
and a proxy setup.

## Features

- Basic Django project structure
- Docker setup for development and production environments
- Docker Compose configurations for different environments
- PostgreSQL database integration
- Proxy configuration for development

## Getting Started

These instructions will get you a copy of the project up and running on your
local machine for development and testing purposes.

### Prerequisites

You will need to have the following software installed on your system:

- Docker
- Docker Compose
- Git

### Installation

1. Clone the repository:

    ```sh
    git clone <repository-url>
    cd library-backend
    ```

2. Copy the sample environment files and update them with your configurations:

    ```sh
    cp .env.dev.sample .env.dev
    cp .env.prod.sample .env.prod
    ```

3. Build and start the Docker containers:

    For development:

    ```sh
    docker-compose -f docker-compose-dev-deploy.yml up --build
    ```

    For production:

    ```sh
    docker-compose -f docker-compose-prod-deploy.yml up --build
    ```

4. Access the Django application:

    The application will be running at `http://localhost:8000`.

### Development with VS Code

For a better development experience, you can use VS Code to attach to the
running container and execute commands inside it.
Use the `docker-compose-vs-code.yml` file for this setup.

#### Launching the Project in VS Code

1. Build and start the Docker containers using the VS Code specific configuration:
docker-compose -f docker-compose-vs-code.yml up --build

2. Open VS Code and attach to the running container:

 - Open the Command Palette (Ctrl+Shift+P or Cmd+Shift+P on macOS) in VS Code.
 - Select Remote-Containers: Attach to Running Container....
 - Choose the container for your app service (it should be named something like library-backend_app_1).

3. Open a terminal inside VS Code:

 - Go to the Terminal menu and select New Terminal.
 - You should now be inside the terminal of the running container.

4. Run Django management commands:

You can now run any Django management command from within the VS Code terminal.
For example, to create a superuser:

```sh
python manage.py createsuperuser
```

Or, to run the server locally:
```sh
python manage.py runserver 0.0.0.0:8000
```

### Directory Structure

- `.devcontainer/` - Development container configuration.
- `.dockerignore` - Docker ignore file.
- `.env.dev.sample` - Sample environment configuration for development.
- `.env.prod.sample` - Sample environment configuration for production.
- `.gitignore` - Git ignore file.
- `Dockerfile` - Dockerfile for building the Docker image.
- `docker-compose-dev-deploy.yml` - Docker Compose file for development deployment.
- `docker-compose-prod-deploy.yml` - Docker Compose file for production deployment.
- `docker-compose-vs-code.yml` - Docker Compose file for VS Code integration.
- `docker-compose.yml` - Docker Compose file.
- `env/` - Environment configuration directory.
- `library/` - Django project directory.
- `proxy/` - Proxy configuration.
- `requirements.dev.txt` - Development requirements.
- `requirements.txt` - Production requirements.
- `scripts/` - Additional scripts.

### Running Commands inside the Docker Container

To run Django management commands inside the Docker container, use the following command:

```sh
docker-compose exec app <command>
```

For example, to create a superuser:
docker-compose exec app python manage.py createsuperuser

### Stopping the Containers
To stop the Docker containers, use the following command:
```sh
docker-compose down
```
