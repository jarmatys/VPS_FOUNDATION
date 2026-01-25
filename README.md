# Ansible Collection - jarmatys.vps_foundation

Foundation roles for VPS setup - system hardening, Docker, and common services.

## Installation

```bash
ansible-galaxy collection install git+https://github.com/jarmatys/VPS_FOUNDATION.git#vps_foundation
```

Or add to `requirements.yml`:

```yaml
collections:
  - name: jarmatys.vps_foundation
    source: https://github.com/jarmatys/VPS_FOUNDATION.git#vps_foundation
    type: git
```

## Roles

| Role | Description |
|------|-------------|
| `system_hardening` | System hardening (SSH, firewall, fail2ban, users) |
| `docker_engine` | Docker and Docker Compose installation |
| `postgres` | PostgreSQL container deployment (with optional init scripts) |
| `mssql` | Microsoft SQL Server container deployment |
| `rabbitmq` | RabbitMQ container with management UI (with optional config) |
| `caddy` | Caddy reverse proxy (with optional Cloudflare) |
| `seq` | Seq logging server |
| `portainer` | Portainer CE for Docker management |
| `supertokens` | SuperTokens authentication server |

## Playbooks

### VPS Bootstrap

```yaml
- import_playbook: jarmatys.vps_foundation.vps_bootstrap
  vars:
    vps_app_user: myproject
    vps_app_group: myproject
    vps_timezone: "Europe/Warsaw"
```

### VPS Deploy Infrastructure

```yaml
- import_playbook: jarmatys.vps_foundation.vps_deploy_infrastructure
  vars:
    services_network: myproject-network
    postgres_db: myproject_db
    postgres_user: myproject
    postgres_password: "{{ lookup('env', 'POSTGRES_PASSWORD') }}"
    postgres_init_script_path: "{{ playbook_dir }}/files/init.sql"
    rabbitmq_config_path: "{{ playbook_dir }}/files/rabbitmq.conf"
    services_mssql_enabled: true
    mssql_sa_password: "{{ lookup('env', 'MSSQL_SA_PASSWORD') }}"
    services_seq_enabled: true
    services_portainer_enabled: false
    services_supertokens_enabled: true
```

## Quick Start

```yaml
# playbooks/setup.yml
---
- import_playbook: jarmatys.vps_foundation.vps_bootstrap
  vars:
    vps_app_user: myproject

- import_playbook: jarmatys.vps_foundation.vps_deploy_infrastructure
  vars:
    services_network: myproject-network
    postgres_db: myproject_db
    postgres_user: myproject
    postgres_password: secure_password
    rabbitmq_user: myproject
    rabbitmq_password: secure_password
```

Run:

```bash
ansible-galaxy collection install -r requirements.yml
ansible-playbook -i inventory/dev.yml playbooks/setup.yml
```

## Requirements

- Ansible >= 2.14
- Ubuntu 22.04+ (jammy, noble)
- Collections: `community.docker`, `community.general`, `ansible.posix`

## Important

After running `vps_bootstrap`, login using the `vps_app_user` account instead of the default `ubuntu` or `root` from your provider.

## License

MIT
