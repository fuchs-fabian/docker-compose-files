# docker-compose-files: Docker Compose files with best practices for bind mounts, env...

This repository is a collection of Docker Compose files in which some best practices are incorporated, everything relevant can be set via the `.env` files and nothing more needs to be done to the Docker Compose files themselves. In addition, bind mounts are used for all Docker Compose containers.

**Reference**: [https://docs.docker.com/compose/compose-file/05-services/#long-syntax-5](https://docs.docker.com/compose/compose-file/05-services/#long-syntax-5)

> To run a container with default values on a test basis, the Docker Compose files work out of the box.

There are the following categories:

| Category (Folder) | Description                                                                |
|-------------------|----------------------------------------------------------------------------|
| [development](./development/)       | Docker Compose files for setting up and managing development environments  |
| [homelab](./homelab/)           | Docker Compose files designed for a homelab environment                    |

> This repository also serves as an example for [`domposy`](https://github.com/fuchs-fabian/domposy).

## Additional Information

Create the docker network:

```bash
docker network create proxy-network
```