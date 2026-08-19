# Platform Engineering Templates

Software Templates and catalog entities for the [OpenShift Advanced App Platform Demo](https://catalog.demo.redhat.com/catalog/babylon-catalog-prod?item=babylon-catalog-prod/published.ocp4-adv-app-platform-demo.prod).

Cluster bootstrap imports this repository into GitLab as `rhdh/rhdh-templates` and substitutes cluster-specific values (`gitlab_host`, `quay_host`, and so on) in each `template.yaml`.

## Template lifecycle

The **Quarkus REST API** template (`templates/quarkus-rest-api`) carries `backstage.io/template-version`, and each scaffolded app sets `spec.scaffoldedFrom: template:default/quarkus-rest-api`. When a platform engineer bumps that version in GitLab `rhdh/rhdh-templates`, Developer Hub opens merge requests on downstream source repos.

The presenter walkthrough (Module 4, Part 4), screenshots, and optional scoped-diff scripts live in the demo showroom: [`adv-app-platform-demo-showroom`](https://github.com/nikolaus-lemberski/adv-app-platform-demo-showroom).
