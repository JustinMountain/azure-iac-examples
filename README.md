# Azure IaC Example

This repo represents an example of a mininal Azure Cloud configuration. 

## The Plan

1) I need to hook this up into CI/CD and holding state in Azure blob storage so that the `terraform apply` and `terraform destroy` commands can be run on GH Actions.
1) Once both commands can be run from Actions, finalize documentation 
1) Work on specific implementation

## Terraform 

[![Vizualization of the minimal Azure configuration](images/azure-example-min.jpg "Minimal Azure Configuration")](images/azure-example-min.jpg)
*Vizualization of the minimal Azure configuration.*

## Ansible & Docker

This example has Terraform create a dynamic `hosts` file for Ansible to use. Ansible then installs Docker on the remote server, adds the Ansible user to the docker group, and uses `compose.yml` to deploy an `nginx` proxy to the server.

## The Examples

### v1 Monorepo

This example is the foundational piece of Azure architecture that I created. 

It utilizes `main.tf` and `variables.tf` to stand up an Ubuntu 24.04 VM in Azure. Terraform uses the IP of this VM to create a dynamic `hosts` file for Ansible, which executes a playbook that sets up Docker and an nginx web proxy.
