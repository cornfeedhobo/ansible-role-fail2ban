# fail2ban [![Ansible Role](https://img.shields.io/ansible/role/d/34101.svg)](https://galaxy.ansible.com/cornfeedhobo/fail2ban)

## Install

```bash
ansible-galaxy install cornfeedhobo.fail2ban
```

## Role Variables

|Name|Default Value|
|-|-|
| `fail2ban_install` | `true` |
| `fail2ban_packages` | `[fail2ban]` |
| `fail2ban_package_state` | `present"` |
| `fail2ban_configure` | `true` |
| `fail2ban_filters` | `{}` |
| `fail2ban_jails` | `{}` |
| `fail2ban_service` | `true` |
| `fail2ban_service_name` | `fail2ban` |
| `fail2ban_service_state` | `started"` |
| `fail2ban_service_enabled` | `true` |

## Example Playbook

```yaml
- hosts: "all"
  roles:
      - role: "cornfeedhobo.fail2ban"
        fail2ban_install: true
        fail2ban_configure: true
        fail2ban_service: true
        fail2ban_jails:
          sshd:
            enabled: true
            filter: "sshd"
```

## Development

### pip

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pip uninstall -y selinux
```

### pipenv

```bash
pipenv sync
pipenv run pip uninstall -y selinux
```

## License

MIT
