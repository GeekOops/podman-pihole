# podman-pihole

Installs a [pi-hole](https://pi-hole.net/) podman container as system service.

## Requirements

Basic ansible, no further dependencies.

## Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `pihole_cors_hosts` | `''` | List of domains/subdomains on which CORS is allowed. Wildcards are not supported |
| `pihole_password` | `''` | Default web password. If not set, a random one will be set for you |
| `pihole_timezone` | `''` | Timezone, if set |

| `pihole_container_image` | `'docker.io/pihole/pihole:latest'` | Container image to be used |
| `pihole_config_dir` | `'/etc/pihole'` | Configuration directory |
| `pihole_data_dir` | `'/srv/pihole'` | Data directory |
| `pihole_service_name` | `'pihole'` | Systemd service name and podman container name |
| `pihole_auto_update` | `true` | If true, podman auto update label will be set for the container |
| `pihole_container_network` | `'podman'` | If set, the following podman network will be used |
| `pihole_container_ip` | `''` | If set, the following ip address will be used for the container |
| `pihole_mem_limit` | `'512M'` | If set, limit the memory of the container to the following value |
| `pihole_publish` | `127.0.0.1:53:53/udp` and `127.0.0.1:53:53/tcp` and `127.0.0.1:80:80/tcp` | List of published port or port ranges for the container |

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: podman-pihole
           vars:
             pihole_cors_hosts: 'pi.hole,127.0.0.1'
             pihole_password: 'passw0rd'
             pihole_timezone: 'Europe/Amsterdam'
             pihole_publish:
               - '53:53/udp'
               - '[::]:53:53/udp'
               - '53:53/tcp'
               - '[::]:53:53/tcp'
               - '127.0.0.1:80:80/tcp'

## License

[`MIT`](LICENSE)

## Author Information

phoenix
