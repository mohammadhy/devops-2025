# Devsecops
### This Repository  Include Ansible Roles To Install Many Tools Like (Jenkins, Gitlab, ELK, Monitoring, Falco, ....), 3 Project Suggestion_apiflask, Python-app, Example_vote And Also Has All Manifests That Require To Deploy On K8s With Argocd.

## Table of Contents
- [Installation Tools](#Usage)
- [Features](#features)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Usage
1. Fill Varibale & Inventory And Playbook
    ```bash
    vim infra-automation/group_vars/all.yaml
    vim inventory.yaml
    vim ansible-playbook.yaml
    ansible-playbook -i inventory.yaml ansible-playbook -K
     ```
2. Manifests
   ```
   ``` 
## Features
- Manifest: On Manifest Direcctory It Has All Manifest That You Need On This Project
- Project: Include 3 Different Project:  python-app & example-voting-app And suggestion_apiflask It Has Web Technology Database And More 
- gitops: Include Gitops That Use Argocd To Deploy Automaticaly Under deploy-vote Directory
- Automation: Under infra-automation Directory You Can Find Many Services That Written On Docker Format And Service Format

## Contact
Hassan Yousefi - [hassan.yosefi158@@gmail.com]

