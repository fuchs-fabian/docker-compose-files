# `nextcloud`

## Nginx Proxy Manager

Proxy Host:

| Scheme | Forward Hostname / IP | Forward Port |
|--------|-----------------------|--------------|
| https  | nextcloud             | 443          |

Advanced:

```plain
client_body_buffer_size 512k;
proxy_read_timeout 86400s;
client_max_body_size 0;
```
