# Containerized Jira Setup

This repository contains a Docker Compose configuration for running Atlassian Jira Software with PostgreSQL database in a containerized environment.

## Prerequisites

- Docker
- Docker Compose
- Git

## Components

- **Jira Software**: Version 10.0.0
- **PostgreSQL**: Version 13
- **Network**: Custom bridge network for secure communication between containers

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/containerized-jira.git
   cd containerized-jira
   ```

2. Create a `.env` file in the root directory with the following variables:
   ```
   POSTGRES_USER=your_postgres_user
   POSTGRES_PASSWORD=your_secure_password
   ```

3. Start the containers:
   ```bash
   docker-compose up -d
   ```

4. Access Jira at `http://localhost:8088`

## Configuration

### Ports
- Jira: 8088 (mapped to container port 8080)
- PostgreSQL: 5432 (internal only)

### Volumes
- `jira_postgres_data`: Persistent storage for PostgreSQL data
- `jira_data`: Persistent storage for Jira application data

### Network
- Custom bridge network `jira_network` for secure container communication

## Maintenance

### Stopping the Services
```bash
docker-compose down
```

### Viewing Logs
```bash
docker-compose logs -f
```

### Backup
The data is persisted in Docker volumes. To backup:
1. Stop the containers
2. Backup the Docker volumes
3. Restart the containers

## Security Notes

- The PostgreSQL database is only accessible within the Docker network
- Sensitive data should be stored in the `.env` file (not committed to version control)
- Regular security updates should be applied to both Jira and PostgreSQL images

## License

This project is licensed under the terms of the included LICENSE file.

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request