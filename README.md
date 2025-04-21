# uvasds-services

A repository for container Services managed by UVA School of Data Science.

## Helm Chart Structure

Deployments follow the Helm structure, containing `Charts.yaml` and optional `values.yaml` in the root directory,
followed by `templates/` which in turn contains one or more deployments.

Standard deployments that include web access will tend to contain at least three files (which can be separate files or concatenated with `---` between stanzas into a single file):

- `deployment.yaml` - Describes the container, replicas, `env` variables, resource allocations, etc.
- `nginx-ingress.yaml` - Describes the ingress rules, routing, FQDN mappings, and possible TLS secrets for HTTPS.
- `service.yaml` - Describes remaining service properties.

For Jobs or CronJobs, refer to reference files in the repository.

Encrypted secrets, such as passwords, API keys or tokens, can be committed as well, then consumed in a deployment.

## ArgoCD Deployments

Once this (or a similar repository/structure) is mapped to ArgoCD, deployments placed in `templates/` will deploy
automatically. Therefore, changes made to deployment files such as a container image or tag, the number(s) of replicas,
or `env` variables will be rolled out by ArgoCD within minutes.

## Automated CI/CD

It is recommended that you use an integrated CI/CD tool with your software repositories to perform tests, builds, and manage deployments.
GitHub Actions is a free option that integrates well.
