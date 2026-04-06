# AGENTS.md

## Purpose
Public self-hosted deployment template for Authentik (IAM/SSO) with PostgreSQL.

## Repository Role
- Category: `*-self-hosted` (public GitHub repository).
- Related local stack: `../authentik-docker`.
- Main entrypoint: `docker-compose.yml`.

## Stack Summary
- Services: `authentik-psql`, `authentik-server`, `authentik-worker`.
- Exposed ports: `9000`, `9443`.
- External network: `shared_network`.

## Data and Config
- PostgreSQL data: `./data/authentik-psql`.
- Authentik runtime data: `./data/media`, `./data/custom-templates`, `./data/certs`.
- Shared env anchor: `x-authentik-common-env` in `docker-compose.yml`.

## Operations
- Restart stack: `./restart-docker.sh`.
- Update images and restart: `./update-docker.sh`.
- Backup helper: `./backup.sh`.

## AI Working Notes
- Keep `shared_network` external (do not replace with internal network).
- Keep secrets in `.env` (`AUTHENTIK_SECRET_KEY`, `PSQL_PWD`, SMTP vars); never hardcode them.
- Do not remove worker access to `/var/run/docker.sock` unless outpost behavior is redesigned.
