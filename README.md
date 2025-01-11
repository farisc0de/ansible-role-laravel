# Ansible Role: Laravel Prepare

This Ansible role prepares a directory for Laravel application deployment by ensuring required folders exist, setting appropriate permissions, and creating a placeholder `.env` file. It is designed for use in CI/CD pipelines as a pre-deployment step.

---

## Features

- Creates the main Laravel application directory.
- Creates subdirectories required for Laravel (`storage`, `bootstrap/cache`, etc.).
- Sets correct ownership and permissions for directories.
- Provides a placeholder `.env` file for configuration.

---

## Requirements

- Ansible 2.9 or higher.
- Target host should have a user with permissions to manage Laravel application files.
- Ensure the `geerlingguy.composer` role or Composer is installed separately if required later.

---

## Role Variables

The following variables can be customized in your playbook:

| Variable           | Default Value           | Description                                             |
|--------------------|-------------------------|---------------------------------------------------------|
| `laravel_app_path` | `/var/www/laravel_app`  | Path to the Laravel application folder.                 |
| `laravel_user`     | `www-data`             | User owning the Laravel files.                         |
| `laravel_group`    | `www-data`             | Group owning the Laravel files.                        |

---

## Dependencies

This role has no dependencies but can be used alongside `geerlingguy.composer` for managing Composer installation.

---

## Example Playbook

Here’s how to use this role in your playbook:

```yaml
---
- name: Prepare Laravel deployment folder
  hosts: app_servers
  become: yes
  roles:
    - role: laravel_prepare
      vars:
        laravel_app_path: /opt/laravel_app
        laravel_user: deployer
        laravel_group: deployer
```

---

## Directory Structure

The role follows the standard Ansible Galaxy directory structure:

```
roles/
  laravel_prepare/
    tasks/
      main.yml
    handlers/
      main.yml
    defaults/
      main.yml
    vars/
      main.yml
    meta/
      main.yml
```

---

## License

MIT

---

## Author Information

This role was created by [Faris Alotaibi](https://github.com/farisc0de) and is maintained as part of efforts to automate Laravel deployments with Ansible. Contributions and feedback are welcome!

---

## Contributing

Feel free to open issues or submit pull requests to improve this role. Ensure that any code changes are tested and documented appropriately.
