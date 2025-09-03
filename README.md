# 🚀 Getting Started

## What Do We Have Here? 
Before We Start Make Sure Your Kubernetes Cluster Up And Running If It's Not Follow Link [Installation Guide](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
1. We Have Cover CI/CD On Different Type Of Git Architectures Such As:
   - MonoRepo 
   - Multi Repo

![monorepo-vs-multirepo](https://github.com/user-attachments/assets/757f21b2-4870-4279-b529-375e6f0f8f3a)

2. We Discover As Musch As Possible Everything That You Need Even On Production Like Find Leaks, Check Dockerfile And Trivy Also You Can Collects All Reports On [DefectDojo](https://defectdojo.com/).
<img width="1849" height="216" alt="pipeline" src="https://github.com/user-attachments/assets/8a4a10a6-4106-4d4d-8ecd-05678cd7b6ba" />
4. All tools run on Docker, each with its own Ansible playbook/role.
5. For Key Secret Management We Use Vault To Protect Our Keys.
6. For Logging We Cover
   - Filebeat
   - Logstash
   - Elasticsearch
8. For Monitoring
   - Prometheus
   - Zabbix
   - Mattermost


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
   
   This Is A MonoRepo App You Can Find The Main Project Here [Example Vote](https://github.com/dockersamples/example-voting-app.git) But I Add It Some Feature Like Read Variable As Environment Not Hardcoded In The Code And Also NonRoot Dockerfile.
   
   <img width="500" height="300" alt="architecture excalidraw" src="https://github.com/user-attachments/assets/f5192dd1-4899-4002-87e0-e05fa81b4892" />

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

## license
Apache License 2.0
