# 🚀 Getting Started

## Prerequisites
To use the resources in this repository, you need the following tools installed on your local machine or CI/CD system:

kubectl: The Kubernetes command-line tool. Installation Guide

A Kubernetes Cluster: You can use Minikube, Kind for local development, or a cloud provider (EKS, GKE, AKS).

ansible: The Ansible automation tool. Installation Guide

## Table of Contents
- [Setup Ansible](#UsageAnsible)
- [Features](#features)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Usage Ansible
1. ansible
    ```bash
    cd infra-automation/
    # Fill Value Under group_vars/all.yaml
    vim infra-automation/group_vars/all.yaml
    # Put Hosts
    vim inventory.yaml
    # Select Service That You Need
    vim ansible-playbook.yaml
    ansible-playbook -i inventory.yaml ansible-playbook -K
     ``` 
## Features
- Manifest: On Manifest Direcctory It Has All Manifest That You Need On This Project
- Project: Include 3 Different Project:  python-app & example-voting-app And suggestion_apiflask It Has Web Technology Database And More 
- gitops: Include Gitops That Use Argocd To Deploy Automaticaly Under deploy-vote Directory
- Automation: Under infra-automation Directory You Can Find Many Services That Written On Docker Format And Service Format

## Contact
Hassan Yousefi - [hassan.yosefi158@@gmail.com]

