# Ansible Configuration Management Framework

Comprehensive Ansible automation framework managing 500+ servers across multiple environments. Created reusable playbooks for common tasks, reducing manual configuration tasks by 90%.

## Features

- **Reusable Playbooks**: Pre-built playbooks for common server configurations
- **Role-Based Structure**: Modular roles for different server types
- **Multi-Environment Support**: Separate configurations for dev, staging, and production
- **Security Hardening**: Automated security configurations and compliance
- **Inventory Management**: Dynamic inventory support for cloud environments

## Playbooks

### Web Server Setup
Configures Nginx with SSL, security headers, and fail2ban protection.

```bash
ansible-playbook playbooks/webserver-setup.yml -i inventory/hosts.yml
```

### Database Setup
Configures MariaDB/MySQL with security hardening and user management.

```bash
ansible-playbook playbooks/database-setup.yml -i inventory/hosts.yml --ask-vault-pass
```

### Common Role
Base system configuration including SSH hardening, firewall, and updates.

## Roles

- **common**: Base system configuration and security hardening
- **webserver**: Nginx/Apache web server configuration
- **database**: MySQL/MariaDB/PostgreSQL database setup
- **monitoring**: Prometheus, Grafana, and monitoring tools
- **security**: Security hardening and compliance checks

## Installation

```bash
git clone https://github.com/dmytrobazeliuk-devops/ansible-automation-framework.git
cd ansible-automation-framework
pip install -r requirements.txt
```

## Usage

### Run a playbook

```bash
ansible-playbook playbooks/webserver-setup.yml -i inventory/hosts.yml
```

### Run with vault password

```bash
ansible-playbook playbooks/database-setup.yml -i inventory/hosts.yml --ask-vault-pass
```

### Check connectivity

```bash
ansible all -i inventory/hosts.yml -m ping
```

## Inventory

Edit `inventory/hosts.yml` to configure your servers:

```yaml
all:
  children:
    webservers:
      hosts:
        web1:
          ansible_host: 192.168.1.10
```

## Vault

Store sensitive data in Ansible Vault:

```bash
ansible-vault create group_vars/all/vault.yml
```

## Testing

Run playbooks in check mode:

```bash
ansible-playbook playbooks/webserver-setup.yml -i inventory/hosts.yml --check
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License

## Author

**Dmytro Bazeliuk**
- Portfolio: https://devsecops.cv
- GitHub: [@dmytrobazeliuk-devops](https://github.com/dmytrobazeliuk-devops)
