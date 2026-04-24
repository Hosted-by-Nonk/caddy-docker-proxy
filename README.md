# Custom `caddy-docker-proxy` Build

A custom `caddy-docker-proxy` build bundled with the `transform` plugin for use with `fail2ban`.

The caddy-side-of-the-configuration example for future reference:

```caddy
{
    log default {
        output stderr
        format console
    }
}

example.com {
    log # other routes won't use the default logger unless you fallback explicitly

    log access {
        format transform "{common_log}"
        output file /access/log.txt
        no_hostname
    }

    handle_path /log-access {
        log_name access # enable access logs for this specific route
        reverse_proxy container-a:8080
    }

    reverse_proxy continer-b:8080
}
```

TODO: document fail2ban filters & jail.
