# `docker-compose-files`: Docker Compose files with best practices for bind mounts, env...

This repository is a collection of Docker Compose files in which some best practices are incorporated, everything relevant can be set via the `.env` files and nothing more needs to be done to the Docker Compose files themselves.

In addition, bind mounts are used for all Docker Compose containers.

**Reference**: [https://docs.docker.com/compose/compose-file/05-services/#long-syntax-5](https://docs.docker.com/compose/compose-file/05-services/#long-syntax-5)

> This repository also serves as an example for [`domposy`](https://github.com/fuchs-fabian/domposy).

## Categories

| Category (Folder)             | Description                                                                |
|-------------------------------|----------------------------------------------------------------------------|
| [`development`](./development/) | Docker Compose files for setting up and managing development environments  |
| [`homelab`](./homelab/)         | Docker Compose files designed for a homelab environment                    |

### `homelab`

| Category (Folder)               | Description                                                              |
|---------------------------------|--------------------------------------------------------------------------|
| [`basic`](./homelab/basic/)       | Docker Compose files for "basic" homelab usage                           |
| [`advanced`](./homelab/advanced/) | Docker Compose files for "advanced" homelab usage                        |

## Additional Information

Since the reverse proxy [Nginx Proxy Manager](https://nginxproxymanager.com/setup/) is used here to establish secure connections and not have to release so many ports, several Docker networks are used.

Create therefore the following Docker networks:

```bash
docker network create proxy && docker network create sec && docker network create dev
```
