# `docker-compose-files`: Docker Compose files with best practices for bind mounts, env...

This repository is a collection of Docker Compose files in which some best practices are incorporated, everything relevant can be set via the `.env` files and nothing more needs to be done to the Docker Compose files themselves.

In addition, bind mounts are used for all Docker Compose containers.

To keep it as simple as possible, the reverse proxy [**Nginx Proxy Manager**](https://nginxproxymanager.com/setup/) was chosen. It enables easy creation of secure connections while minimizing the number of exposed ports.

The Docker Compose files are written in the [**long syntax**](https://docs.docker.com/compose/compose-file/05-services/#long-syntax-5), which is recommended for better readability and maintainability.

There are direct links to the container images in the Docker Compose files, allowing you to easily check for newer versions before starting the container. You can then update the `.env` file accordingly.

> This repository also serves as an example for [`domposbi`](https://github.com/fuchs-fabian/domposbi).

## Services

| Service                                           | Categorization | Official site/repository                                        |
|---------------------------------------------------|----------------|-----------------------------------------------------------------|
| [`defectdojo`](./defectdojo/)                     | 🟣             | [DefectDojo](https://github.com/DefectDojo/django-DefectDojo)   |
| [`gitea`](./gitea/)                               | 🟢             | [Gitea](https://about.gitea.com)                                |
| [`gitea-runner`](./gitea-runner/)                 | 🔵             | [Gitea Runner](https://docs.gitea.com/usage/actions/act-runner) |
| [`gitlab`](./gitlab/)                             | 🟠             | [GitLab](https://about.gitlab.com)                              |
| [`gitlab-runner`](./gitlab-runner/)               | 🟠             | [GitLab Runner](https://docs.gitlab.com/runner)                 |
| [`heimdall`](./heimdall/)                         | 🟢             | [Heimdall](https://github.com/linuxserver/Heimdall)             |
| [`jellyfin`](./jellyfin/)                         | 🟢             | [Jellyfin](https://jellyfin.org)                                |
| [`mongodb`](./mongodb/)                           | 🟣             | [MongoDB](https://www.mongodb.com)                              |
| [`nextcloud`](./nextcloud/)                       | 🟢             | [Nextcloud](https://nextcloud.com)                              |
| [`nginx-proxy-manager`](./nginx-proxy-manager/)   | 🟢             | [Nginx Proxy Manager](https://nginxproxymanager.com)            |
| [`pihole`](./pihole/)                             | 🔵             | [Pi-hole](https://pi-hole.net)                                  |
| [`portainer`](./portainer/)                       | 🔵             | [Portainer](https://www.portainer.io)                           |
| [`stirling-pdf`](./stirling-pdf/)                 | 🟢             | [Stirling PDF](https://www.stirlingpdf.com)                     |
| [`uptime-kuma`](./uptime-kuma/)                   | 🟢             | [Uptime Kuma](https://github.com/louislam/uptime-kuma)          |
| [`vaultwarden`](./vaultwarden/)                   | 🟢             | [Vaultwarden](https://github.com/dani-garcia/vaultwarden)       |

> ***Personal categorization***:
>
> 🟢 **Must-have**: Essential tools for running a homelab – indispensable
>
> 🔵 **Helpful**: Useful tools that make operations easier but are not strictly necessary
>
> 🟠 **Nice to have**: Additional tools that enhance comfort and functionality
>
> 🟣 **For experts/specialists**: Tools designed for advanced users or specific use cases

## Getting started

Create the used (external) Docker networks:

```bash
docker network create proxy && docker network create sec && docker network create dev
```

On your host, navigate to the path where your Docker Compose projects are located.

Download a service:

```bash
SERVICE="<service>" && mkdir -p "$SERVICE" && \
wget -P "$SERVICE" https://raw.githubusercontent.com/fuchs-fabian/docker-compose-files/refs/heads/main/$SERVICE/docker-compose.yml && \
wget -P "$SERVICE" https://raw.githubusercontent.com/fuchs-fabian/docker-compose-files/refs/heads/main/$SERVICE/.env
```

> Replace `<service>` with the desired service, e.g., `gitea`.
