# Request OpenShift Namespace

Request a new OpenShift namespace with resource quotas.

This software template creates a Merge Request in the `infra-app-of-apps` repository with Namespace and ResourceQuota definitions. The Platform Engineering team reviews and merges the request, and Argo CD automatically provisions the namespace on the cluster.

This template is also used by the Orchestrator workflow (`create-ocp-namespace-swt`), which adds an approval gate for large namespace requests via GitLab issues before invoking this template.

## Usage

Create a new entity using this template and fill in the parameters:

* **Namespace Name** — Unique name for the namespace (lowercase, hyphens allowed)
* **Namespace Owner** — The team that owns this namespace
* **Size** — Resource quota tier:
    * **Small** — 2 vCPU / 8Gi memory
    * **Medium** — 3 vCPU / 12Gi memory
    * **Large** — 6 vCPU / 24Gi memory

## What happens

1. The template renders a `Namespace` and `ResourceQuota` resource, plus a Backstage catalog entry
2. A Merge Request is opened in the `rhdh/infra-app-of-apps` GitLab repository
3. Platform engineers (`pe1`, `pe2`) are assigned as reviewers
4. Once merged, Argo CD syncs the namespace and quota to the cluster

## Outputs

* A link to the Merge Request for tracking approval status
