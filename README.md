# Redis Docker Service

This project provides a Docker setup for running Redis and Redis Commander, a web-based interface for managing Redis databases.

## Description

This repository contains Docker configurations to easily deploy Redis and Redis Commander. Redis is an in-memory data structure store, used as a database, cache, and message broker. Redis Commander allows you to manage your Redis databases through a user-friendly web interface.

## Services

- **Redis**: The main service that runs the Redis database.
  - **Container Name**: redis
  - **Image**: redis:latest
  - **Ports**: Exposed on the default Redis port (6379)
  - **Health Check**: Ensures Redis is running by pinging the server.

- **Redis Commander**: A web interface for managing Redis.
  - **Container Name**: redis-commander
  - **Image**: ghcr.io/joeferner/redis-commander:latest
  - **Ports**: Accessible on port 8083
  - **Environment Variables**: Loaded from `.env.dev`

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/your-repo.git
   ```

2. Navigate to the project directory:

   ```bash
   cd your-repo
   ```

3. Start the services using Docker Compose:

   ```bash
   docker-compose up -d
   ```

## Usage

- Access Redis Commander at [http://localhost:8083](http://localhost:8083) to manage your Redis databases.
- Use the Redis CLI or any Redis client to connect to the Redis service at `localhost:6379`.

## Contributing

1. Fork the repository.
2. Create a new branch:

   ```bash
   git checkout -b feature/YourFeature
   ```

3. Make your changes and commit them:

   ```bash
   git commit -m "Add your message"
   ```

4. Push to the branch:

   ```bash
   git push origin feature/YourFeature
   ```

5. Open a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
