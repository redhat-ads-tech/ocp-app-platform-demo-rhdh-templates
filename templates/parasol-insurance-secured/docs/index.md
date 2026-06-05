# Onboarding features for Parasol Insurance application

This Software Template of Red Hat Developer Hub allows to create a secured development sandbox for the Parasol Insurance application.

At Parasol we're enabling developer self-service by standardizing our deployment practices for all new software components, by:

* Isolating the feature in a dedicated branch.
* Configuring GitOps pipelines for secure, automated deployments.
* Registering the new component in the catalog for visibility and management.

This Documentation explains how to use this software template.

## Usage

Create a new entity in the catalog using this template and fullfil the parameters:

* Branch Name: Specify the name of the new branch in the parasol-insurance source repository

## Outputs

The output of this software template is:

* A new branch in the source code repository named with the value of the branch's name parameter.
* A new entity in the Red Hat Developer Hub catalog to register this new feature in progress.
* The entity card will provide a link to develop the code using Red Hat OpenShift Dev Spaces.
* Integrations with the CI/CD pipelines and GitOps to track the evolution of the feature.
