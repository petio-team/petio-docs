---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  [Discord](https://discord.gg/bseGmrUd3N)!
---

# Traefik \(v2\)

## Traefik Subdomain Example

Assuming a basic setup like [the one in the Traefik documentation](https://doc.traefik.io/traefik/user-guides/docker-compose/acme-dns/) where an entrypoint called `websecure` exists, adding these labels down below to the Petio service should be the minimum that's needed to reverse proxy Petio.

```yaml
labels:
    - "traefik.enable=true"
    ## HTTP Routers
    - "traefik.http.routers.petio-rtr.entrypoints=websecure"
    - "traefik.http.routers.petio-rtr.rule=Host(`petio.mydomain.com`)"
    - "traefik.http.routers.petio-rtr.tls=true"
    ## HTTP Services
    - "traefik.http.routers.petio-rtr.service=petio-svc"
    - "traefik.http.services.petio-svc.loadbalancer.server.port=7777"
```

