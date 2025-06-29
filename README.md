# Redis Commander Docker Service

A Docker service configuration for [Redis Commander](https://github.com/joeferner/redis-commander), a web management tool for Redis.

## Overview

Redis Commander is a web-based Redis management application that provides a graphical interface to view, edit, and manage your Redis data. This repository contains a Docker Compose configuration to easily deploy Redis Commander as a containerized service.

## Features

- Web-based Redis management interface
- Connect to multiple Redis instances
- View, edit, and delete Redis keys
- Import/export Redis data
- Execute Redis commands through the CLI
- Resource-limited container for predictable performance

## Requirements

- Docker and Docker Compose
- Access to a Redis instance
- External Caddy network (or modify the configuration to use your preferred network)

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/redis-commander-docker-service.git
   cd redis-commander-docker-service
   ```

2. Create a `.env` file from the example:

   ```bash
   cp .env.example .env
   ```

3. Edit the `.env` file with your Redis connection details:

   ```env
   REDIS_HOST=your-redis-host
   REDIS_PASSWORD=your-redis-password
   ```

## Configuration

### Environment Variables

The following environment variables can be configured in the `.env` file:

- `REDIS_HOST`: The hostname of your Redis server (default: `redis`)
- `REDIS_PASSWORD`: The password for your Redis server (if required)

Additional environment variables supported by Redis Commander can be added to the `.env` file as needed. See the [Redis Commander documentation](https://github.com/joeferner/redis-commander) for more options.

### Docker Compose Configuration

The `docker-compose.yaml` file includes the following configuration:

- Uses the latest Redis Commander image from GitHub Container Registry
- Sets resource limits (0.5 CPU, 512MB memory)
- Runs as the `redis` user for improved security
- Connects to an external network named `caddy_network`

## Usage

### Starting the Service

```bash
docker-compose up -d
```

### Accessing the Web Interface

By default, Redis Commander will be available at `http://localhost:8081`. If you're using a reverse proxy with the Caddy network, configure it to route traffic to the `redis-commander` container.

### Stopping the Service

```bash
docker-compose down
```

## Security Considerations

- The service runs as the `redis` user instead of root for improved security
- Always set a strong Redis password in production environments
- Consider using a reverse proxy with HTTPS for secure access
- Restrict access to the Redis Commander interface in production environments

## Troubleshooting

- If you can't connect to your Redis instance, verify the `REDIS_HOST` and `REDIS_PASSWORD` in your `.env` file
- Check Docker logs for any errors: `docker-compose logs redis-commander`
- Ensure your Redis instance is accessible from the Docker network

## License

See the [LICENSE](LICENSE) file for details.
