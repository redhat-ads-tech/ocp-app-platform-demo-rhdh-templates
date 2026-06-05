# Request Kafka Topic

Request a new Kafka topic on the shared cluster.

This software template creates a Merge Request in the `infra-app-of-apps` repository with the KafkaTopic resource definition. The Platform Engineering team reviews and merges the request, and Argo CD automatically provisions the topic on the cluster.

## Usage

Create a new entity using this template and fill in the parameters:

* **Topic Name** — Name for the Kafka topic (lowercase, hyphens and underscores allowed)
* **Owning Team** — The team responsible for this topic
* **Partitions** — Number of partitions (1-12)
* **Retention** — Message retention period (infinite, 1 day, 7 days, or 30 days)
* **Description** — What this topic is used for

## What happens

1. The template renders a `KafkaTopic` custom resource and a Backstage catalog entry
2. A Merge Request is opened in the `rhdh/infra-app-of-apps` GitLab repository
3. Platform engineers (`pe1`, `pe2`) are assigned as reviewers
4. Once merged, Argo CD syncs the topic to the `kafka` namespace on the cluster

## Outputs

* A link to the Merge Request for tracking approval status
