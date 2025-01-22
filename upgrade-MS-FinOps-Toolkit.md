
# ReDeploy the template to upgrade - [click here](https://microsoft.github.io/finops-toolkit/hubs#-create-a-new-hub) and click to "Deploy to Azure"
- It will only deploy the addon changes or new resources to the same resource group

## Few things to note:
- Please find the latest releases [here](https://github.com/microsoft/finops-toolkit/releases). based on that the FinOps Hub can be updated.
- Update PowerBI Desktop to the latest version. Yes. It is required as per MS FinOps new templates.
- Update the FinOpsHub first. Please refer [here](https://microsoft.github.io/finops-toolkit/hubs#-create-a-new-hub)
- Sign in to your Azure Portal
- Click 'Deploy to Azure' button. It will start deploying the FinOpsHub to your Azure Tenant
  <img width="764" alt="image" src="https://github.com/user-attachments/assets/f7b27c03-d69c-4e85-9ba0-3ee6c7b8fa3e" />
## IMPORTANT:
- While updating FinOpsHub make sure to select the same 'Resource Group' and 'Subscription' which was used for old version.
- If it is the first time installation of FinOpsHub then simply create a separate resource group and select a 'Subcription'
