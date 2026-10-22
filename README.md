# Phansible Role: MariaDB

[![CI](https://github.com/phansible/role-mariadb/actions/workflows/ci.yml/badge.svg)](https://github.com/phansible/role-mariadb/actions/workflows/ci.yml)

An Ansible Role that installs [MariaDB](https://mariadb.org/) 11.8 LTS on Ubuntu and Debian specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

- Ubuntu 22.04, 24.04 or 26.04, or Debian 12 or 13.
- Ansible 2.15 or newer.
- The `ansible.mysql` collection (bundled with the `ansible` package, or `ansible-galaxy collection install ansible.mysql`).
- Internet access to `deb.mariadb.org`. MariaDB comes from the upstream MariaDB repository (11.8 LTS) on every platform.

## Role Variables

All variables live under one `mariadb` dictionary in `defaults/main.yml`. Override the whole dictionary, since Ansible does not merge dictionaries by default.

| Variable | Default | Description |
| --- | --- | --- |
| `mariadb.root_password` | `root` | Password set on the `root` accounts (`localhost`, `127.0.0.1`, `::1` and the machine hostname). |
| `mariadb.database` | `phansible` | Database to create. |
| `mariadb.user` | `changme` | User created with all privileges on `database`. |
| `mariadb.password` | `changme` | Password for `user`. |
| `mariadb.dump` | `""` | SQL file under `/vagrant/` imported into `database`. Empty skips the import. |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
    mariadb:
      root_password: secret
      database: app
      user: app
      password: secret
      dump: ""
  roles:
    - role-mariadb
```

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-mariadb/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-mariadb/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
