# `gitlab`

## Nginx Proxy Manager

> Replace `example.com` with your domain!

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

### Useful commands

#### Check the status of the services

```bash
docker exec -it gitlab gitlab-ctl status
```

#### Restart and reconfigure `gitlab-rails`

```bash
docker exec -it gitlab gitlab-ctl restart
```

```bash
docker exec -it gitlab gitlab-ctl reconfigure
```

#### View current resource usage

```bash
docker stats gitlab
```

#### Grep for error logs

```bash
docker logs gitlab | grep error
```

### Sign-up restrictions

Adjust `Sign-up restrictions` in `Admin` area -> `Settings` -> `General` -> `Sign-up restrictions` to `Sign-up enabled` to allow users to sign up, but also enable `Require admin approval for new sign-ups` to prevent spam.

### Auto DevOps

It is recommended to disable `Auto DevOps` in `Admin` area -> `Settings` -> `CI/CD` -> `Auto DevOps` -> `Default to Auto DevOps pipeline for all projects` to prevent unnecessary pipelines.

### Runners

> It is recommended to deploy the runners on a different host!

Especially in the Homelab, it makes sense to have an instance runner that can generally be used for all projects.

> Reference: https://docs.gitlab.com/ee/ci/runners/runners_scope.html#create-an-instance-runner-with-a-runner-authentication-token

To add this, proceed as follows:

Go to `Admin` area -> `CI/CD` -> `Runners` -> `New instance runner`.

> **Tags**: `linux, docker`
>
> **Run untagged jobs**: ☑️
>
> **Runner description**: `general`

Than click on `Create runner`.

Choose `Linux` as the operating system.

Use the [`docker-compose.yml`](../gitlab-runner/docker-compose.yml) and its [`.env`](../gitlab-runner/.env) file.

Adjust the `.env` file to your needs. This means at least `URL` and `TOKEN`.

After that, simply start the runner.

### Export and import projects

> Reference: https://docs.gitlab.com/ee/administration/settings/import_and_export_settings.html#enable-project-export

This is not recommended due to high resource usage!

## Known issues

### `keywatcher: pubsub receive: EOF`

GitLab issue: [`426006`](https://gitlab.com/gitlab-org/gitlab/-/issues/426006#note_2276284129)
