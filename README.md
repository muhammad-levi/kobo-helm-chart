# KoboToolbox Helm Chart

This chart is intended for high availability instances of KoboToolbox. Small and casual instances should use [kobo-install](https://github.com/kobotoolbox/kobo-install).

This chart is still being tested and isn't intended for external use at this time. Versions may change for no reason at all or breaking changes may apply without updating the version.

# Design decisions

- As generic as possible, agnostic about the environment variables set for each service
- Supports high availability via k8s's horizontal pod autoscaler (HPA), pod disruption budget (PDB), and topology spread constraints
- Stick to defaults and conventions from `helm create` when possible
- Every deployment/job should do one thing. Migrate, run uwsgi, run celery, etc

# Usage

1. `helm repo add kobo-levi https://muhammad-levi.github.io/kobo-helm-chart`
1. Carefully review values.yaml. Set image tag version, if desired. Set databases, secret keys, etc.
1. `helm install your-kobo kobo-levi/kobo -f your-values.yaml`

## Upgrading

1. `helm repo update`
1. `helm upgrade your-kobo kobo-levi/kobo -f your-values.yaml`

Tip: Consider using `helm diff` to preview changes first.

# Acknowledgements

Includes ideas from:

- https://gitlab.com/burke-software/django-helm-chart
- https://github.com/one-acre-fund/kobo-k8s/
- unicef helm chart
