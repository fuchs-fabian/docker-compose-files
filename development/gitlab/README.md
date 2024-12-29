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

Adjust `Sign-up restrictions` in `Admin` area -> `Settings` -> `General` -> `Sign-up restrictions` to `Sign-up enabled` to allow users to sign up, but also enable `Require admin approval for new sign-ups` to prevent spam.

### Commands

Check the status of the services:

```bash
docker exec -it gitlab gitlab-ctl status
```

Restart and reconfigure `gitlab-rails`:

```bash
docker exec -it gitlab gitlab-ctl restart
```

```bash
docker exec -it gitlab gitlab-ctl reconfigure
```

View current resource usage:

```bash
docker stats gitlab
```

### Runners

Especially in the Homelab, it makes sense to have an instance runner that can generally be used for all projects.

To add this, proceed as follows:

Go to `Admin` area -> `CI/CD` -> `Runners` -> `New instance runner`.

**Tags**: `linux, docker`

**Run untagged jobs**: ☑️

**Runner description**: general

Than click on `Create runner`.

Choose `Linux` as the operating system.

Use the [`docker-compose.yml`](../gitlab-runner/docker-compose.yml) and its [`.env`](../gitlab-runner/.env) file.

Adjust the `.env` file to your needs. This means at least `URL` and `TOKEN`.

After that, simply start the runner.

## TODO

Currently it is not yet possible for GitLab to recognize exactly which IP address has done something. You can only see the IP address of the reverse proxy.

### Known issues

- `keywatcher: pubsub receive: EOF`

  GitLab issue: [`426006`](https://gitlab.com/gitlab-org/gitlab/-/issues/426006#note_2276284129)
