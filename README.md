# Pihole stack for ARM

This is a Docker Compose setup for running Pihole with Caddy as reverse proxy and cloudflare as DDNS provider.

Note that this image will only work on ARM based systems like the Raspberry Pi, it will **not** work on x64 based systems.

## Setup

Clone this repo, copy the example files to the non-example counterparts:

```
.env.example > .env
caddy/Caddyfile.example > caddy/Caddyfile
```

Keep in mind that there is no password set by default, make sure to set it to something if you so wish.

After setting that up, just run `docker-compose up -d` to get everything running.

## Custom DNS entries

Adding custom DNS entries can be done by creating a file in `pihole/dnsmaqs/`, I recommend you name that `99-custom.conf` to avoid any conflicts.

Then add the entries like so:

```
address=/subdomain.your-awesome-domain.tld/the-ip-address-of-your-awesome-server
```

Then run `docker-compose exec pihole pihole restartdns`.

