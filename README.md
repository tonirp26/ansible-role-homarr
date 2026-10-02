# Ansible Role: Homarr

This role installs the Homarr application in Debian.

After running the role, the `homarr` service will be available on the server. The application's web interface can be accessed at `http://{your-container-ip}:7575`.

> [!WARNING]
> This repository have the variable `SECRET_ENCRYPTION_KEY` this variable must be secret so change for a secret one. For this first test it is in plain text.

## Requirements

Requires Node 24 or later to be installed on the server (you can use the geerlingguy.nodejs role to install Java if needed).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
app_repository_url: "https://github.com/homarr-labs/homarr.git"
```

URL used in git clone command.

```yaml
app_repository_dir: "/opt/homarr"
```

Set repository destination path, if modified make sure that system user `homarr` have correct rights.

```yaml
app_version: "v1.77.2"
```

Set desired version of the app.

```yaml
environment_file: "homarr.env.j2"
```

Template for homarr environment variables and routes.

```yaml
homarr_template: "homarr.j2"
```

Homarr wrapper for executing the Homarr CLI with environment variables loaded from /opt/homarr.env.

```yaml
systemd_redis_template: "redis.service.j2"
```

Template for Redis systemd service executed by root user.

```yaml
systemd_homarr_template: "homarr.service.j2" 
```

Template for Homarr systemd service executed by root user.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: server
  vars_files:
    - vars/main.yml
  roles:
    - homarr
```

*Inside `vars/main.yml`*:

```yaml
app_version: 1.1.1
```

## License

## Author Information

This role was created in 2026 by [tonirp](https://github.com/tonirp26).
