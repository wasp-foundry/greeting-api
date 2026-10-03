# Runbook

## Is it up?

    kubectl get deployment hello-alpha --namespace <development|production>
    kubectl port-forward deployment/hello-alpha 8000:8000 --namespace development
    curl localhost:8000/healthz

## Restart

    kubectl rollout restart deployment/hello-alpha --namespace <namespace>

## Roll back

Revert the tag bump commit in `wasp-foundry/gitops` (`apps/hello-alpha/overlays/<env>`); the deployment follows the overlay.
