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

Azure creates an external user for every subscription, that you can use to access the databricks account console. Please follow the steps below to find the user. 

1. Navigate to the Microsoft Entra ID as below

<img width="1909" alt="Navigate to Microsoft EntraID" src="https://github.com/user-attachments/assets/2bfbfad2-a55e-4025-a800-1fc80bdc638b">


2. Navigate to Users

<img width="1911" alt="2  Navigate to Users" src="https://github.com/user-attachments/assets/f98a374e-333e-4f4e-a964-7ed8d4b73dc7">

3. Copy the name of the external user created by Azure [It will have #EXT# in the name]

<img width="1914" alt="3  Copy User Name" src="https://github.com/user-attachments/assets/eb9af50a-d6f3-42c5-b864-2c14635a2929">

4. Sign out from Azure Portal and Sign in user the External User

<img width="550" alt="4  Signin as External User" src="https://github.com/user-attachments/assets/f1294850-60be-4957-b9ac-b7a8767b5179">

5. Reset the password if signining in for the first time

<img width="521" alt="5  Reset password if required" src="https://github.com/user-attachments/assets/3019205d-d683-4961-9e66-3dcb354ec4e2">

6. Use the external user to login to Azure Databricks
   
<img width="800" alt="6  Signin to account console" src="https://github.com/user-attachments/assets/57c252e2-cec7-476f-9cbf-a000b40db77d">

You should be able to successfully login to the account console as below

<img width="963" alt="6 2 Successful Login " src="https://github.com/user-attachments/assets/d20ac39e-661e-46c8-9f0f-234c8df73856">



