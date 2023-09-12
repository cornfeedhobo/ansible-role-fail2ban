# fail2ban [![Ansible Role](https://img.shields.io/ansible/role/d/61743.svg)](https://galaxy.ansible.com/cornfeedhobo/fail2ban)

install, configure, and manage fail2ban

## Table of content

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [fail2ban_configure](#fail2ban_configure)
  - [fail2ban_filters](#fail2ban_filters)
  - [fail2ban_install](#fail2ban_install)
  - [fail2ban_jails](#fail2ban_jails)
  - [fail2ban_package_state](#fail2ban_package_state)
  - [fail2ban_packages](#fail2ban_packages)
  - [fail2ban_service](#fail2ban_service)
  - [fail2ban_service_enabled](#fail2ban_service_enabled)
  - [fail2ban_service_name](#fail2ban_service_name)
  - [fail2ban_service_state](#fail2ban_service_state)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.5`

## Default Variables

### fail2ban_configure

#### Default value

```YAML
fail2ban_configure: true
```

### fail2ban_filters

name:
before: []
after: []
failregex: []
ignoreregex: []

#### Default value

```YAML
fail2ban_filters: {}
```

#### Example usage

```YAML
nginx-custom:
  init:
    block: >-
      \/?(<webmail>|<phpmyadmin>|<wordpress>|<php>|<misc>)[^,]*
    misc: >-
      (cgi-bin|mysqladmin|admin|aws|credentials|\.aws)
    php: >-
      (phpinfo|test\.php|vendor|laravel|\?XDEBUG_SESSION_START)
    phpmyadmin: >-
      (typo3/|xampp/|admin/|)(pma|(php)?[Mm]y[Aa]dmin)
    webmail: >-
      roundcube|(ext)?mail|horde|(v-?)?webmail
    wordpress: >-
      wp-(login|signup|admin)\.php
  failregex:
    - >-
      \"<HOST>\" \"(\w+|-)\" \"https?\:\/\/.+\" .+ (301|4\d\d)$
    - >-
      \"<HOST>\" \"(\w+|-)\" \"https?\:\/\/[\w\d\.]+<block>\"
    - >-
      \[error\] \d+#\d+: \*\d+ (\S+ )?\"\S+\" (failed|is not found) \(2\: No such file or directory\), client\: <HOST>\, server\: \S*\, request: \"(GET|POST|HEAD).*\"
  ignoreregex: []
```

### fail2ban_install

#### Default value

```YAML
fail2ban_install: true
```

### fail2ban_jails

Jail rules in the form of
name: {key: value, ...}

#### Default value

```YAML
fail2ban_jails: {}
```

#### Example usage

```YAML
nginx-custom:
  enabled: "true"
  filter: "nginx-custom"
  bantime: "72h"
  findtime: "180m"
  maxretry: 3
```

### fail2ban_package_state

#### Default value

```YAML
fail2ban_package_state: present
```

### fail2ban_packages

#### Default value

```YAML
fail2ban_packages: [fail2ban]
```

### fail2ban_service

#### Default value

```YAML
fail2ban_service: true
```

### fail2ban_service_enabled

#### Default value

```YAML
fail2ban_service_enabled: true
```

### fail2ban_service_name

#### Default value

```YAML
fail2ban_service_name: fail2ban
```

### fail2ban_service_state

#### Default value

```YAML
fail2ban_service_state: started
```

## Discovered Tags

**_fail2ban_**

**_fail2ban-configure_**

**_fail2ban-install_**

**_fail2ban-service_**


## Dependencies

None.

## License

MIT

## Author

cornfeedhobo
