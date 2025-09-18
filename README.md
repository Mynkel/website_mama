# Drupal Docker Project

A containerized Drupal web application with Docker-based development and deployment environment.

## Project Structure

```
mama_project/
├── src/                    # Drupal source code (core, modules, themes)
├── docker/                 # Docker configuration
│   ├── bin/               # Docker utility scripts
│   ├── config/            # Container configuration files
│   └── containers/        # Container definitions
├── persistent-data/       # Database and file storage
├── .env                   # Environment variables (not in git)
└── docker-compose.yml     # Docker orchestration
```

## Prerequisites

- Docker
- Docker Compose
- Git

## Quick Start

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd mama_project
   ```

2. **Create environment file**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Build and start containers**
   ```bash
   docker-compose build
   docker-compose up -d
   ```

4. **Access the application**
   - Drupal site: http://localhost:8000
   - Adminer (database admin): http://localhost:8080

## Development Commands

### Container Management
```bash
# Start development environment
docker-compose up -d

# Stop development environment
docker-compose down

# Rebuild containers
docker-compose build

# View logs
docker-compose logs -f [service-name]
```

### Drupal Management
```bash
# Access Drupal container
docker-compose exec web bash

# Drush commands
docker-compose exec web drush status
docker-compose exec web drush cr          # Clear cache
docker-compose exec web drush updb        # Update database
docker-compose exec web drush config:export  # Export configuration
```

### Database Management
```bash
# Access database container
docker-compose exec db bash

# Create database backup
docker-compose exec dbbackup /backup.sh

# MySQL access
docker-compose exec db mysql -u drupal -p drupal
```

## Services

- **web**: PHP-FPM + Apache/Nginx serving Drupal
- **db**: MySQL/MariaDB database
- **adminer**: Web-based database administration
- **dbbackup**: Automated database backup service

## Development Status

This project is in initial setup phase. Current priorities:

1. ⏳ Drupal installation in `src/`
2. ⏳ Docker configuration setup
3. ⏳ Container definitions
4. ⏳ Environment configuration
5. ⏳ Automated backup scripts

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test in Docker environment
5. Submit a pull request

## Support

For issues and questions, please create an issue in the project repository.