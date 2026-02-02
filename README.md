# Content <!-- omit in toc -->
{:toc}


<script>
import traefik from './docs/traefik/traefik.md'
</script>


## Information

### Arbeitsverzeichnisse

Für rootful:

- Quadlets: /etc/containers/systemd
- Volumes: /var/lib/containers/storage/volumes

Für rootless:

- Quadlets: ~/.config/containers/systemd
- Volumes: ~/.local/share/containers/storage/volumes


# Quadlets
Home Lab - Podman Systemd Quadlets

## Requirements
This home lab uses podman.

- v4.4.0 or later required for quadlets
- v5.3.0 or later recommended for dns


System with installed systemd-containter package to switch to different user.

- systemd-container


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

Create a new user, e.g. *srv_service*

```shell
sudo useradd srv_service
```


## Server Setup - Quadlets 

Services

- Basics
  - Dynamic DNS [DuckDns](./docs/duckdns/duckdns.md)
  - Proxy-Server [Traefik](./docs/traefik/traefik.md)
- Services

{% capture my_traefik %}{% include /docs/traefik/traefik.md %}{% endcapture %}
{{ my_traefik | markdownify }}

# License
This repository is licensed under the [unlicense](LICENSE).

