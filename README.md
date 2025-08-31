# 🚀 Getting Started

## Prerequisites
To use the resources in this repository, you need the following tools installed on your local machine or CI/CD system:

kubectl: The Kubernetes command-line tool. Installation Guide

A Kubernetes Cluster: You can use Minikube, Kind for local development, or a cloud provider (EKS, GKE, AKS).

ansible: The Ansible automation tool. Installation Guide

## Table of Contents
- [Setup Ansible](#UsageAnsible)
- [Projects](#Projects)
- [Features](#features)
- [License](#license)
- [Contact](#Contact)
## Projects
1. Python Web Application
   
   This Is A Simple Application That Need Redis.
   
2. Example Vote
   
   This Is A MonoRepo App You Can Find The Main Project Here [Example Vote](https://github.com/dockersamples/example-voting-app.git) But I Change It Some Feature Like Read Variable As Environment Not Hardcoded In The Code.
   <img width="500" height="500" alt="architecture excalidraw" src="https://github.com/user-attachments/assets/f5192dd1-4899-4002-87e0-e05fa81b4892" />

4. Siggestion Api
   
   This Is A Api Application.
   
## UsageAnsible
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
- Automation: Under Ansible Directory You Can Find Many Services That Written On Docker Format And Service Format

## Contact
Hassan Yousefi - [hassan.yosefi158@@gmail.com]

