
# What is Microsoft FinOps Toolkit?
Please read [Kick start document](https://microsoft.github.io/finops-toolkit/)

# Why should we use?

# Steps to enable Microsoft FinOps Toolkit for your Azure Cost Management data

```
NOTE: The below steps are as per my personal guidance to get started super quickly. You are always recommended to refer Microsoft documentation for the FinOps Toolkit for detail info. 
```

### Roles and Permissions for Azure cloud user
    The PowerBI developer should have
- Please check required list of roles [here](https://microsoft.github.io/finops-toolkit/hubs/template)
- Access to the subscription where the 'FinOps Hub' will be deployed
- 'Blob Reader' role in Azure portal to access storage account data in PowerBI desktop
- 'Contributor' role for deploying 'FinOps Hub'. The deployment requires permissions to create resources like storage account, data factory, Resource group, etc

### Create a new Resource Group
- Go to Resource group > Create > select the subcription where the FinOps Hub should be deployed.
- Name the resource group. e.g., 'Org_FOCUS_Rg'

## NOTE: 'FOCUS' stands for FinOps Open Cost and Usage Specification

### Deploy FinOps Hub
- [Click here](https://microsoft.github.io/finops-toolkit/hubs#-create-a-new-hub) to deploy FinOps Hub
- Click on the 'Deploy to Azure' button
- It will open the Azure portal
- Select the resource group, which has been created in the previous section.
- Click deploy to start deployment
- It will do all the required deployment for FinOps Hub.
- It takes around 5-8 mins to complete the deployment.
- Verify: Once deployment is complete. go to the resource group and check the list of resources created.
- Until 'FinOps Hub' is deployed successfully please don't proceed.  

### Setup Cost Export
- Login to Azure Portal > Cost Export > Report + Analytics > Export 
- Select 'Scope' to your 'Billing account'. The user should have access to the billing account.
- Currently, Cost & Usage (FOCUS) data is not available for the Management Group Scope. It is not available for subscription level. That's why you can either create for any specific subscription. Or I would recommend to set the Scope to Billing Account as we should get complete cost data of the organization.
- After selecting scope to your Billing Account, the screen should list all the existing export under the tenant. Or it might show none if it is the first time you are creating export. 
- Click 'Create' the '+' icon to create an export.
- Select 'Cost and usage (FOCUS)' template. Yes. it must be FOCUS template
- Enter a prefix . e.g 'daily'. So it will be 'daily-focus-cost'. you can edit it as per your choice for naming.
- Bring your cursor over the '*-focus-cost' hyperlink. and click the edit pencil.
- A popup will open for the export settings.
- Update the frequency as per your choice.
- Frequency - Daily export will run daily, Monthly export will run at the end of the month, One time export will run only once and it will create cost data till date.
- Now 'Save' and click 'Next' for 'Destination' settings.
- You must have deployed 'FinOps hub' already. If not, please check the previous section  'Deploy FinOps Hub'.
- The 'FinOps Hub' deployment will create the storage account which we have to select under 'Destination' setting.
- Destination settings as follows
- - Storage Type: Azure Blob Storage
  - Destination and Storage: Use Existing
  - Subscription: < 'Select the subscription which has been used for FinOps Hub deployment' >
  - Storage Account: < Select storage account which is created by FinOps Hub deployment. the name starts with 'finopshub...'>
  - Container: msexports
  - Directory: providers/billingaccount/cscmonthly
  - Format: CSV
  - Compression type: None
  - Overwrite data: 'Unchecked'
- Now Review + Create to create the export.
- Verify:
- - Go back to Cost Export overview.
  - Click on the newly created export. It should open a popup with export details. verify details for correct config.
  - Check run history. If it has not ran yet, click 'Run now' to trigger the run.
  - Browse to Storage account > select the storage account ('finopshub...').
  - Browse to the container path. e.g., 'providers/billingaccounts/...'.
  - After the export job is completed successfully, the csv file(s) should be available in the container.
  - So far we have successfully created Cost export for finOps reporting.

### Install PowerBI desktop
- Sign in to https://app.powerbi.com/
- Download PowerBI desktop (top right download icon)
- Simply install in your developer machine

### Download PowerBi (*.pbix) report templates
- Please download *.pbix report files from the latest release. [click here](https://github.com/microsoft/finops-toolkit/tags) to download report templates.
- Currently for v0.7 release the report templates are categorized and available as follows.
  - PowerBI-storage.zip for templates that connect to storage (with or without FinOps hubs)
  - PowerBI-kql.zip for templates that connect to FinOps hubs with Data Explorer
  - PowerBI-demo.zip for reports with sample data

To follow the on-going instruction please use the templates from "PowerBI-storage.zip"

### Connect Data source to Azure storage
- Open a template file (*.pbix) in PowerBI desktop.
- e.g., Open 'CostSummary.pbix'
- Click on 'Transform Data' option under Home tab
- Select 'Edit parameters'. It will open a popup box for data source settings.
- Edit Parameters settings as follows
- - Hub Storage URL: < Enter the 'Data Lake url' from storage container >
  - Export Storage URL: < Enter the 'Data Lake url' from storage container > also append '/ingest' at the end of the url. 
  - Range Start: < e.g., 2010-01-01 12:00 AM>
  - Range End: < e.g., 2050-01-01 12:00 AM>
  - Number of Months: keep blank
  - Click Ok
- Click "Apply Changes"
- It will start pulling data from the actual storage account.
- A popup might show for login. Log-in with the same azure portal user the developer has the required roles.
- Fetching data can take around 5-10 or more depending on the amount of data.

### Run report using PowerBi desktop 
- After successfully completing the data source change and 'Apply change'. The report should show the actual data.
- Click refresh to refresh data or change the filter to see the data on the report.
- After this step, the report is ready to Publish

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
