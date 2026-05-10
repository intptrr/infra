# infra

Personal infrastructure configuration.

## Structure

- `docker-compose/` — Docker Compose stacks for self-hosted services.
  - `3x-ui/` — [3x-ui](https://github.com/MHSanaei/3x-ui) Xray panel.

## Services

### 3x-ui

Xray management panel running in host network mode.

```sh
cd docker-compose/3x-ui
docker compose up -d
```

Persistent data:

- `/opt/3x-ui/db/` — panel database and config
- `/opt/3x-ui/cert/` — TLS certificates
