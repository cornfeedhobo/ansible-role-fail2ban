fail2ban [![Ansible Role](https://img.shields.io/ansible/role/d/34101.svg)](https://galaxy.ansible.com/cornfeedhobo/fail2ban)
========

Install and configure fail2ban.

    ansible-galaxy install cornfeedhobo.fail2ban

Role Variables
--------------

|Name|Default Value|
|-|-|
| `fail2ban_install` | `false` |
| `fail2ban_package_state` | `present"` |
| `fail2ban_packages` | `{{ __fail2ban_packages }}"` |
| `fail2ban_service` | `false` |
| `fail2ban_service_name` | `{{ __fail2ban_service_name }}"` |
| `fail2ban_service_state` | `started"` |
| `fail2ban_service_enabled` | `true` |
| `fail2ban_configure` | `false` |
| `fail2ban_jails` | <pre>- sshd:<br/>    enabled: true<br/>    port: "ssh"<pre> |

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: cornfeedhobo.fail2ban
           fail2ban_install: true
           fail2ban_configure: true
           fail2ban_service: true
           fail2ban_jails:
             - sshd:
                 enabled: true
                 filter: "sshd"

License
-------

MIT
