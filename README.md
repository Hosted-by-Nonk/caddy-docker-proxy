# Custom `caddy-docker-proxy` Build

A custom `caddy-docker-proxy` build bundled with the `transform` plugin for use with `fail2ban`.

Caddy-side-of-configuration example for future reference:

```caddy
example.com {
    log {
        format transform "{common_log}"
        output file /var/log/caddy/example.com/access.log
    }

    reverse_proxy example-container:8080
}
```
