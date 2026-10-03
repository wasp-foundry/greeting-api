# Runbook

## Is it up?

    kubectl get deployment greeting-api --namespace <development|production>
    kubectl port-forward deployment/greeting-api 8000:8000 --namespace development
    curl localhost:8000/healthz

## Restart

    kubectl rollout restart deployment/greeting-api --namespace <namespace>

## Roll back

Revert the tag bump commit in `wasp-foundry/gitops` (`apps/greeting-api/overlays/<env>`); the deployment follows the overlay.
