# MySQL Docker

Docker Compose setup for MySQL 8.0

## Prerequisites

- Docker & Docker Compose
- Docker network `app-net` (create with `docker network create app-net`)

## Setup

1. Copy the environment file:
   ```bash
   cp .env.example .env
   ```

2. Update `.env` with your desired passwords

3. Create the Docker network if it doesn't exist:
   ```bash
   docker network create app-net
   ```

4. Start MySQL:
   ```bash
   docker-compose up -d
   ```

## Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `MYSQL_ROOT_PASSWORD` | Root user password | - |
| `MYSQL_DATABASE` | Database to create on startup | `appdb` |
| `MYSQL_USER` | Application user | `appuser` |
| `MYSQL_PASSWORD` | Application user password | - |

## Usage

Connect to MySQL:
```bash
docker exec -it mysql mysql -u root -p
```

View logs:
```bash
docker-compose logs -f mysql
```

Stop:
```bash
docker-compose down
```

## Data Persistence

MySQL data is persisted to `/opt/mysql/data` on the host. Ensure the directory exists and has proper permissions before starting.

## Security

- Never commit `.env` to version control
- Use strong passwords in production
