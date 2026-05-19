# infra

Personal infrastructure configuration.

## Structure

- `docker-compose/` — Docker Compose stacks for self-hosted services.
  - `3x-ui/` — [3x-ui](https://github.com/MHSanaei/3x-ui) Xray panel.
  - `n8n/` — [n8n](https://n8n.io) workflow automation with Postgres.

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

### n8n

n8n workflow automation backed by a Postgres database. The Postgres container
creates a non-root user via `init-data.sh` which n8n then uses to connect.

```sh
cd docker-compose/n8n
cp .env.example .env
# edit .env and set strong passwords
docker compose up -d
```

n8n is exposed on port `5678`. Persistent data is kept in the named Docker
volumes `n8n_storage` and `db_storage`.
