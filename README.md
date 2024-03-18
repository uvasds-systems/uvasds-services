# uvasds-services

A repository for container Services managed by UVA School of Data Science.

## Helm Chart Structure

Deployments follow the Helm structure, containing `Charts.yaml` and optional `values.yaml` in the root directory,
followed by `templates/` which in turn contains one or more deployments.

Deployments tend to contain at least three files:

- `deployment.yaml` - Describes the container, replicas, `env` variables, resource allocations, etc.
- `nginx-ingress.yaml` - Describes the ingress rules, routing, FQDN mappings, and possible TLS secrets for HTTPS.
- `service.yaml` - Describes remaining service properties.

## ArgoCD Deployments

Once this (or a similar repository/structure) is mapped to ArgoCD, deployments placed in `templates/` will deploy
automatically. Therefore, changes made to deployment files such as a container image or tag, the number(s) of replicas,
or `env` variables will be rolled out by ArgoCD within minutes.

## Automated CI/CD

.
