# HUNET - Home Infrastructure

This repository contains configuration and documentation for running HUNET.

There are two basic means through which internal infrastructure and software is managed.

- __Ansible__ - Ansible is used primarily for configuring a collection of Raspberry Pis running core base services including Pi-hole DNS and K3S.

- __Kubernetes__ - Kubernetes (K3S) runs a collection of internal services related to monitoring, home automation, etc.

## Playbooks (that need writing)

- Deploy a new Raspberry Pi
- Provision a new K3S cluster with ArgoCD and get all the apps running
- Adopt new node into K3S cluster

## Local Prerequisites

- Ansible
- Kubectl
- Helm
- Install galaxy deps `ansible-galaxy install -r roles/requirements.yml`






