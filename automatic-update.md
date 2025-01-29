# Enable Automatic Update of Report

After publishing the report to app.powerbi.com, select the Semantic model of the report and click settings. Note, we need to go the the settings of the select semantic model, not the settings of the workspace. 
Please follow the steps below. 

- In the settings screen, expand the data set credentials
- It will show two rows of the 'Edit Credentials' hyper link.
- Click the 'Edit Credentials' and a popup window will open.
- Select privacy level as 'None'. Authentication method 'OAuth2' and click Sign in.
- It will direct to log in with Azure portal access.
-  On the same settings screen, expand 'Refresh'
-  Set the correct Timezone.
-  Enable Configure a refresh schedule. set it to 'on'
-  Set refresh frequency to Daily
-  Save

The above settings will automatically refresh the data of the report daily. 

