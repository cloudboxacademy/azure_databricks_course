# Unable to login to Azure Databricks Account Console - Solution
Due to recent changes to Microsoft Azure (July 2024 onwards), users with personal subscription are unable to access Azure Databricks Account console with their standard user id they use to signin to Azure Portal (e.g. training@outlook.com). This article documents the solutions received from Microsoft via Microsoft Q&A forum as well as Dustin Vannoy via the Databricks Community forum. Please see links to those pages below. 

## Overview
The users may see the following error message, if they try to access the account console via the URL https://accounts.azuredatabricks.net/

<img width="648" alt="unable-to-access-account-console-error-2" src="https://github.com/user-attachments/assets/f5b338a9-5564-494a-b64f-1e96a8e803d3">

Also, the users may see the following error message, if they try to access the account console via the 'Manage Account' menu from the Databricks UI. 

<img width="405" alt="unable-to-access-account-console-error-1" src="https://github.com/user-attachments/assets/36592ef0-7743-4d95-9ae3-503d5212e122">

Both of these errors are seen by users with personal subscription, trying to access the databricks account console via their standard azure account. The proposed solution is to use an external account to access the account console instead. 

1. Use the external user created by Azure to access the databricks account console
2. Create a new external user and use that to access the databricks account console

### Solution 1 - Use the external user created by Azure to access the databricks account console

