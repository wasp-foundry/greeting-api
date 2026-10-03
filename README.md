# greeting-api

Greets callers, stores each greeting and publishes a greeting event

FastAPI service created from the wasp-idp Backstage template `python-service`.

- `GET /` — app name and a greeting
- `GET /healthz` — liveness/readiness

Every push to `main` runs the tests, publishes `ghcr.io/wasp-foundry/greeting-api:<sha>` and bumps the tag in [`wasp-foundry/gitops`](https://github.com/wasp-foundry/gitops/tree/main/apps/greeting-api), which ArgoCD deploys.

## Local run

    python3 -m venv .venv && . .venv/bin/activate
    pip install --requirement requirements.txt --requirement requirements-dev.txt
    pytest
    uvicorn app.main:app --reload
