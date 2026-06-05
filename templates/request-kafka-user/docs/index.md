# Request Kafka User

Request a new Kafka user with topic ACLs on the shared cluster.

This software template creates a Merge Request in the `infra-app-of-apps` repository with the KafkaUser resource definition and access control rules. The Platform Engineering team reviews and merges the request, and Argo CD automatically provisions the user on the cluster.

## Usage

Create a new entity using this template and fill in the parameters:

* **User Name** — Name for the Kafka user (lowercase, hyphens allowed)
* **Owning Team** — The team responsible for this user
* **Description** — What this user is for
* **Topic Pattern** — Topic name or prefix to grant access to
* **Pattern Type** — Exact match or prefix match
* **Access Level** — Read only, write only, or read & write

## What happens

1. The template renders a `KafkaUser` custom resource with ACLs and a Backstage catalog entry
2. A Merge Request is opened in the `rhdh/infra-app-of-apps` GitLab repository
3. Platform engineers (`pe1`, `pe2`) are assigned as reviewers
4. Once merged, Argo CD syncs the user and ACLs to the `kafka` namespace on the cluster

## Outputs

* A link to the Merge Request for tracking approval status
