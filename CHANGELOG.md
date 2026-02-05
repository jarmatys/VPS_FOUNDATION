# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2025-02-05

### Added
- MSSQL `mssql_max_server_memory_mb` parameter for configuring SQL Server internal memory limit
- RabbitMQ plugins support for enabling custom plugins in container
- Resource configuration options (memory limits, CPU) for various services
- Recreate option to container tasks for all services
- SQLPad role for SQL query tool
- Typesense role for search engine
- Microsoft SQL Server (MSSQL) role
- PostgreSQL initialization scripts support
- RabbitMQ configuration file support

### Changed
- Increased fail2ban maxretry limit for SSH from 3 to 20
- Enhanced SSH hardening with authorized_keys verification
- Updated MSSQL healthcheck command to use CMD format for improved compatibility
- Improved Docker network creation with existing network check

### Fixed
- MSSQL container strict healthcheck comparison
- MSSQL directory ownership and group for data directory
- SSH public key input trimming for proper validation

## [1.0.2] - 2025-01-23

### Fixed
- Added missing permissions for GitHub release workflow

### Added
- LICENSE file (MIT)
- CHANGELOG.md file

## [1.0.1] - 2025-01-23

### Fixed
- Fixed directory paths in release workflow for building and packaging Ansible collection
- Updated release workflow to trigger on published releases instead of tag pushes

## [1.0.0] - 2025-01-23

### Added
- Initial release
- Docker role for container management
- Portainer role for Docker UI
- PostgreSQL role for database deployment
- RabbitMQ role for message queue
- Seq role for centralized logging
- SuperTokens role for authentication
- System hardening role for security configuration
