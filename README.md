# aks-admin
This repository is for setup container app infrastructure and deployement to Azure AKS, which includes setup of below:
- Azure resources (DEV, UAT and PROD)
    - Application and corresponding service principal, federation credential to Github repository
    - ACR token and scope map
    - AKS namespace, resources quota, network policy and PVC
    - Storage account - File share SAS
- Github repository
    - clone from template repository (sample app and CI/CD workflows)
    - repository secrets and variables
## *Post configuration*
- from github.com, invite technical owner as repository collaborator with Admin permission (*github cli allow add collaborator by username only*)