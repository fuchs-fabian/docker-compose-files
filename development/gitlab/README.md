# `gitlab`

## Nginx Proxy Manager

> Replace `example.com` with your domain

### GitLab

Domain: `gitlab.example.com`

Proxy Host:

| Scheme | Forward Hostname / IP | Forward Port |
|--------|-----------------------|--------------|
| http   | gitlab                | 80           |

### Registry

Domain: `registry.example.com`

Proxy Host:

| Scheme | Forward Hostname / IP | Forward Port |
|--------|-----------------------|--------------|
| http   | gitlab                | 5050         |

### Pages

Domain: `pages.example.com`

Proxy Host:

| Scheme | Forward Hostname / IP | Forward Port |
|--------|-----------------------|--------------|
| http   | gitlab                | 8090         |

## General tips

Adjust `Sign-up restrictions` in `Admin` Area -> `Settings` -> `General` -> `Sign-up restrictions` to `Sign-up enabled` to allow users to sign up, but also enable `Require admin approval for new sign-ups` to prevent spam.

## TODO

Currently it is not yet possible for gitlab to recognize exactly which IP address has done something. You can only see the IP address of the reverse proxy.
