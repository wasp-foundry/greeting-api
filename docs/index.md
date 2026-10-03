# greeting-api

FastAPI service of the `greeter` system, owned by `team-alpha`. Created from the wasp-idp Backstage template `python-service`.

This page lives in the service repository (`mkdocs.yml` + `docs/`) and Backstage renders it in the *Docs* tab through the `backstage.io/techdocs-ref: dir:.` annotation in `catalog-info.yaml`.

## Endpoints

| Method | Path | Response |
|---|---|---|
| GET | `/` | App name and a greeting |
| GET | `/healthz` | Liveness/readiness |

## Dependencies (catalog only)

- `greeting-db` (database) — greetings table
- `greeting-events` (topic) — one `greeting.created` event per greeting
- `greeting-avatars` (bucket) — avatar images

These resources are catalog entries for documentation purposes; the service does not connect to any of them yet.

## Delivery

Every push to `main` runs the tests, publishes `ghcr.io/wasp-foundry/greeting-api:<sha>` and bumps the tag in `apps/greeting-api/overlays/development` of [`wasp-foundry/gitops`](https://github.com/wasp-foundry/gitops). Production is promoted with `gh workflow run promote.yaml --repo wasp-foundry/gitops -f app=greeting-api`.
