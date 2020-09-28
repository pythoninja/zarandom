# zarandom
Slack bot to get a random item from list

## Deployment with Caddy and Docker

Run docker container: `docker run --name slack-zarandom --publish 127.0.0.1:8111:8080 --detach pythoninja/zarandom`

Configure Caddy, paste this to `/etc/caddy/Caddyfile`:

```
zarandom.slack-apps.random.icu

# Set this path to your site's directory.
root * /usr/share/caddy

# Enable the static file server.
file_server

# Reverse proxy to docker container
reverse_proxy /api/* localhost:8111

# Refer to the Caddy docs for more information:
# https://caddyserver.com/docs/caddyfile
```