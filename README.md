# platform-deploy

Contains ArgoCD Application and ApplicationSet manifests that deploy application workloads to target environments. Wires together which chart to use (from platform-charts), which image version to deploy, and environment-specific Helm values — organized using a branch-per-environment strategy (local, staging, main) to enable environment-specific access control and promotion gates.

Responsible for: ArgoCD deployment manifests for all applications, environment-specific Helm values for application workloads, and image version tracking per environment.

Access control: the local branch is unprotected to allow rapid iteration; staging requires a PR with any reviewer; main (production) requires a PR with named approvers only.

Does not manage: chart definitions (see `platform-charts`), platform service deployments (see `platform-components`), or application source code (see individual app repos).