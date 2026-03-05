# Metabase Boilerplate

Docker boilerplate for deploying Metabase with an external PostgreSQL database.

## Prerequisites

- [Docker](https://www.docker.com/) (version 20.10 or higher)
- [Docker Compose](https://docs.docker.com/compose/) (version 1.29 or higher)
- External PostgreSQL database

## Quick Start

1. Clone this repository
2. Copy the environment file:
   ```bash
   cp .env.example .env
   ```
3. Configure your database credentials in `.env`
4. Start Metabase:
   ```bash
   docker-compose up -d
   ```
5. Access Metabase at `http://localhost:{SERVER_PORT}`

## Configuration

All configuration is done through the `.env` file:

| Variable | Description | Default |
|----------|-------------|---------|
| `SERVER_PORT` | Host port for Metabase | `3001` |
| `MB_DB_TYPE` | Database type | `postgres` |
| `MB_DB_HOST` | Database host | `host.docker.internal` |
| `MB_DB_PORT` | Database port | `5432` |
| `MB_DB_DBNAME` | Database name | - |
| `MB_DB_USER` | Database username | - |
| `MB_DB_PASS` | Database password | - |
| `JAVA_TIMEZONE` | Java timezone | `Asia/Jakarta` |

### Database Connection

- **MB_DB_HOST**: Use `host.docker.internal` to connect to a database running on the host machine. For other Docker containers, use the service name.
- **MB_DB_PORT**: Default PostgreSQL port is `5432`.

## Commands

```bash
# Start Metabase
docker-compose up -d

# Stop Metabase
docker-compose down

# View logs
docker-compose logs -f

# Restart Metabase
docker-compose restart
```

## Health Check

The container includes a health check that verifies the Metabase API is responding. You can check the status with:

```bash
docker-compose ps
```

## Data Persistence

This configuration uses an external PostgreSQL database. No local volumes are mounted for data persistence. Ensure your external database is properly backed up.

## License

See [LICENSE](LICENSE) file for details.
