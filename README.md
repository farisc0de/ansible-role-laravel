# Ansible Role: Laravel

An Ansible role to set up and configure Laravel application directories and permissions.

## Requirements

- Ansible 2.9 or higher
- Ubuntu 20.04 (Focal) or higher
- Debian 10 (Buster) or higher

## Role Variables

### Main Configuration

```yaml
# Application path
laravel_app_path: /var/www/laravel_app

# File ownership
laravel_user: www-data
laravel_group: www-data

# Environment settings
laravel_env: production
laravel_app_key_generate: true
laravel_app_debug: false
laravel_app_url: "http://localhost"
```

### Directory Permissions

```yaml
laravel_storage_dir_mode: "0775"
laravel_storage_file_mode: "0664"
laravel_cache_dir_mode: "0775"
```

### Database Configuration

```yaml
laravel_db_connection: mysql
laravel_db_host: "127.0.0.1"
laravel_db_port: 3306
laravel_db_database: laravel
laravel_db_username: laravel
laravel_db_password: ""  # Should be overridden in vault
```

### Cache Configuration

```yaml
laravel_cache_driver: file
laravel_session_driver: file
laravel_queue_driver: sync
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: webservers
  vars_files:
    - vars/main.yml
  roles:
    - farisc0de.laravel
```

## Tags

- `laravel`: All Laravel-related tasks
- `laravel_directories`: Directory creation tasks
- `laravel_permissions`: Permission-related tasks
- `laravel_config`: Configuration tasks

## License

MIT

## Author Information

This role was created by Faris Alotibi.
