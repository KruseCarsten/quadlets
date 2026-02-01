# Content <!-- omit in toc -->
- [Quadlets](#quadlets)
  - [Requirements](#requirements)
  - [Prepare](#prepare)
    - [Configure *ip\_unprivileged\_port\_start*](#configure-ip_unprivileged_port_start)
  - [Setup Proxy-Server - Traefik](#setup-proxy-server---traefik)
- [License](#license)


<script>
import traefik from '/docs/traefik/traefik.md'
</script>


# Quadlets
Home Lab - Podman Systemd Quadlets

## Requirements
This home lab uses podman.

- v4.4.0 or later required for quadlets
- v5.3.0 or later recommended for dns

## Prepare

### Configure *ip_unprivileged_port_start*

Read the current setting (default 1024)

```shell
cat /proc/sys/net/ipv4/ip_unprivileged_port_start
```

To set a new value (for example 80), create the file 
*/etc/sysctl.d/99-mysettings-ipv4.conf* with the contents:

```shell
echo net.ipv4.ip_unprivileged_port_start=80 > /etc/sysctl.d/99-mysettings-ipv4.conf
```

and reload the configuration

```shell
sudo sysctl --system
```

## Setup Proxy-Server - Traefik

{{traefik}}

# License
This repository is licensed under the [unlicense](LICENSE).

