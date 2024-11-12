
# What is Microsoft FinOps Toolkit?
Please read [Kick start document](https://microsoft.github.io/finops-toolkit/)

# Why should we use?

# Steps to enable Microsoft FinOps Toolkit for your Azure Cost Management data

```
NOTE: The below steps are as per my personal guidance to get started super quickly. You are always recommended to refer Microsoft documentation for the FinOps Toolkit for detail info. 
```

### Roles and Permissions for Azure cloud user

### Setup Cost Export

### Install PowerBI desktop

### Download PowerBi (*.pbix) report files

### Connect Data source to Azure storage

### Run report using PowerBi desktop 

### Publish reports
- Sign in to https://app.powerbi.com/
- Create an 'Workspace'
  - Left panel 'Workspaces' menu
  - Click 'New workspace' button
  - Enter workspace name. e.g., Corp-Az-CloudCostMgmt-ws
  - Optional: Leave this field or select the appropriate domain as per your Organization's requirement.  
  - Optional: Expand 'Advance' section and add users under 'Contact list' field. Your user will be added by default.
  -  Click 'Apply' to create the workspace.
  -  NOTE: You might get permission issue "App workspace creation is disabled". In that case you can contact your Tenant admin / org support team for adding permission via PowerBI admin portal. They will provide you access via PowerBI Admin Portal > Workspaces > Tenent Settings > Enable create workspace settings > Apply to 'The entire organization' > click 'Apply'
- Publish report
- - It is assumed that you have your powerbi report well executed using PowerBI desktop and ready to publish.
  - Open the report using PowerBI desktop and under 'Home', top right (left of CoPilot icon) find 'Publish'.
  - Click 'Publish'.
  - Select the 'workspace' where the report should be published.
  - Click 'Publish'.
  - Click the published link. It should open the web link and show the same report. 
