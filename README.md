# aks-admin
This repository is intended for setup container app infrastructure and deployement to Azure .  The setup includes the following:
- Azure resources for PROD (optional: DEV and UAT)
    - Application, corresponding service principal and federation credential to Github repository
    - ACR scope map and token
    - AKS namespace, resources quota, network policy and PVC
    - Storage account file share SAS
- Github repository
    - clone from template repository (sample app and CI/CD workflows)
    - define repository secrets and variables
## *Configuration*
To enable all workflows, it is necessary to register an Azure Application with all the required permissions.  The following steps need to be followed:
- Register an Azure application
    - create an API application permission of "Application.Read.All" and "Application.ReadWrite.OwnedBy"
    - create a federation credential to this repository
- Other permissions to the application (service principal)
    - create and grant a custom role with the following ACR permissions
    - grant "User Access Administrator" BuiltinRole to AKS cluster, with conditions to grant only
        - "Azure Kubernetes Service Cluster User Role"
        - "Azure Kubernetes Service RBAC Writer"
    - grant "Azure Kubernetes Service Cluster User" and "Azure Kubernetes Service RBAC Cluster Admin" roles
    - grant "Storage File Data SMB Share Contributor" role
- Github
    - generate GitHub personal access token
    - update actions secrets and variables

|ACR Permission|Description|
|---|---|
|Microsoft.ContainerRegistry/registries/generateCredentials/action|Generate keys for a token of a specified container registry|
|Microsoft.ContainerRegistry/registries/pull/read|Pull or Get images from a container registry|
|Microsoft.ContainerRegistry/registries/read|Gets the properties of the specified container registry or lists all the container registries under the specified resource group or subscription|
|Microsoft.ContainerRegistry/registries/scopeMaps/delete|Deletes a scope map from a container registry|
|Microsoft.ContainerRegistry/registries/scopeMaps/read|Gets the properties of the specified scope map or lists all the scope maps for the specified container registry|
|Microsoft.ContainerRegistry/registries/scopeMaps/write|Creates or updates a scope map for a container registry with the specified parameters|
|Microsoft.ContainerRegistry/registries/tokens/delete|Deletes a token from a container registry|
|Microsoft.ContainerRegistry/registries/tokens/operationStatuses/read|Gets a token async operation status|
|Microsoft.ContainerRegistry/registries/tokens/read|Gets the properties of the specified token or lists all the tokens for the specified container registry|
|Microsoft.ContainerRegistry/registries/tokens/write|Creates or updates a token for a container registry with the specified parameters|

## *Create Container Application*
- before triggering the workflow, check the inventory to verify the request application name does not already exist
- run the "Create AKS App" action
- from github.com, invite the technical owner as a repository collaborator with Admin permission (*github cli allow add collaborator by username only*)
## *Delete Container Application*
- run "Delete AKS App" action



