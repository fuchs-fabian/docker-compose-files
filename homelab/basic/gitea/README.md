# `gitea`

## Nginx Proxy Manager

> Replace `example.com` with your domain!

Domain: `gitea.example.com`

Proxy Host:

| Scheme | Forward Hostname / IP | Forward Port |
|--------|-----------------------|--------------|
| http   | gitea                 | 3000         |

## General tips

It is not recommended to change the `app.ini` file directly. Change the [`docker-compose.yml`](./docker-compose.yml) instead!
