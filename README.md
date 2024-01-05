# aks-admin
This repository is for setup container app infrastructure and deployement to Azure AKS, which includes setup of below:
- Azure resources (Dev, UAT and PROD)
    - Application and corresponding service principal, federation credential for Github repository
    - ACR token and scope map
    - AKS namespace, resources quota, network policy and PVC
- Github repository
    - clone from template repository
    - repository secrets and variables
    - Actions CI/CD workflows
