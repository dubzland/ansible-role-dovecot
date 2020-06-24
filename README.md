# Dubzland: Dovecot
[![Gitlab pipeline status (self-hosted)](https://img.shields.io/gitlab/pipeline/dubzland/ansible-role-dovecot?gitlab_url=https%3A%2F%2Fgit.dubzland.net)](https://git.dubzland.net/dubzland/ansible-role-dovecot/pipelines)

Installs and configures the Dovecot IMAP/POP3 server

## Requirements

Ansible version 2.0 or higher.

## Role Variables

Available variables are listed below, along with their default values (see
    `defaults/main.yml` for more info):

### dubzland_dovecot_virtual_domains

```yaml
dubzland_dovecot_virtual_domains: []
```

List of virtual domains this server will be responsible for.

### dubzland_dovecot_cert_file/dubzland_dovecot_key_file

```yaml
dubzland_dovecot_cert_file: None
dubzland_dovecot_key_file: None
```

Certificate and private key used for TLS authorization.

### dubzland_dovecot_db_driver

```yaml
dubzland_dovecot_db_driver: pgsql
```

Driver to use when connecting to the database.  Possible options are: `mysql`, `pgsql`, and `sqlite`

### dubzland_dovecot_db_host

```yaml
dubzland_dovecot_db_host: 127.0.0.1
```

Database host name/IP.

### dubzland_dovecot_db_username/dubzland_dovecot_db_password

```yaml
dubzland_dovecot_db_username: mailserver
dubzland_dovecot_db_password: notsekret
```

Database server credentials.

### dubzland_dovecot_db_name

```yaml
dubzland_dovecot_db_name: mailserver
```

Database holding credentials.

### dubzland_dovecot_password_query

```yaml
dubzland_dovecot_password_query: "SELECT email AS user, password FROM virtual_users WHERE email='%u'"
```

Database query used to retrieve the creds for a user.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: mailserver
  become: yes
  roles:
    - role: dubzland.dovecot
      vars:
        dubzland_dovecot_virtual_domains:
          - example.com
```

## License

MIT

## Author

* [Josh Williams](https://codingprime.com)
