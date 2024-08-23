# Unable to login to Azure Databricks Account Console using Microsoft Personal Account - Solution
Due to recent changes to Microsoft Azure (July 2024 onwards), users with *personal subscription* are unable to access Azure Databricks Account console with their standard user id that they use to signin to Azure Portal (e.g. training@outlook.com). This article documents the solution/ workaround received from both Microsoft via [Microsoft Q&A forum](https://learn.microsoft.com/en-us/answers/questions/1861727/unable-to-login-to-azure-databricks-account-consol) as well as from **Dustin Vannoy** via the [Databricks Community forum](https://community.databricks.com/t5/administration-architecture/unable-to-login-to-azure-databricks-account-console/td-p/82190). 

## Overview of the Issue
Microsoft Azure users with a personal subscription may see the following error message, if they try to access the account console via the URL https://accounts.azuredatabricks.net/

<img width="648" alt="unable-to-access-account-console-error-2" src="https://github.com/user-attachments/assets/f5b338a9-5564-494a-b64f-1e96a8e803d3">

Also, the users may see the following error message, if they try to access the account console via the **Manage Account** menu from the Databricks UI. 

<img width="405" alt="unable-to-access-account-console-error-1" src="https://github.com/user-attachments/assets/36592ef0-7743-4d95-9ae3-503d5212e122">

Both of these errors are seen by users with personal subscription trying to access the databricks account console via their standard azure account. The proposed solution is to use an external azure account to access the databricks account console instead. There are 2 solutions to this issue as below

1. Use the external user created by Azure to access the databricks account console [Suggested by Dustin Vannoy via Databricks Community forum]
2. Create a new external user and use that to access the databricks account console [Suggested by Microsoft via Microsoft Q&A forum]

Both of these solutions are tested by me and a few others and they can be used to workaround this limitation. 

### Solution 1 - Use the external user created by Azure to access the Databricks Account Console

By default, Azure creates an external user for every subscription, that you can use to access the databricks account console. 
Please follow the steps below to find the user and login to databricks account console. 

1. Navigate to the Microsoft Entra ID as below

<img width="1909" alt="Navigate to Microsoft EntraID" src="https://github.com/user-attachments/assets/2bfbfad2-a55e-4025-a800-1fc80bdc638b">

2. Navigate to Users

<img width="1911" alt="2  Navigate to Users" src="https://github.com/user-attachments/assets/f98a374e-333e-4f4e-a964-7ed8d4b73dc7">

3. Copy the name of the external user created by Azure [It will have #EXT# in the name]

<img width="1914" alt="3  Copy User Name" src="https://github.com/user-attachments/assets/eb9af50a-d6f3-42c5-b864-2c14635a2929">

4. Sign out from Azure Portal and Sign in using this External User

<img width="550" alt="4  Signin as External User" src="https://github.com/user-attachments/assets/f1294850-60be-4957-b9ac-b7a8767b5179">

5. Reset the password if signing in for the first time

<img width="521" alt="5  Reset password if required" src="https://github.com/user-attachments/assets/3019205d-d683-4961-9e66-3dcb354ec4e2">

6. Use the external user to login to Azure Databricks Account console via https://accounts.azuredatabricks.net/
   
<img width="800" alt="6  Signin to account console" src="https://github.com/user-attachments/assets/57c252e2-cec7-476f-9cbf-a000b40db77d">

You should be able to successfully login to the account console as below

<img width="963" alt="6 2 Successful Login " src="https://github.com/user-attachments/assets/d20ac39e-661e-46c8-9f0f-234c8df73856">

The external user created by Microsoft Azure already has the privileages Global Administrator and Databricks Account Admin. So, you do not have to add any additional privileages


### Solution 2 - Create a new external user and use that to access the databricks account console
We can create a new external user in Microsoft EntraID and assign the Global Administrator role so that the new user can be used to signin to Azure Databricks account console.
Please follow the steps below to implement this solution

1. Navigate to the Microsoft Entra ID as below

<img width="1909" alt="Navigate to Microsoft EntraID" src="https://github.com/user-attachments/assets/2bfbfad2-a55e-4025-a800-1fc80bdc638b">

2. Navigate to Users

<img width="1911" alt="2  Navigate to Users" src="https://github.com/user-attachments/assets/f98a374e-333e-4f4e-a964-7ed8d4b73dc7">

3. Create a new external user

<img width="1682" alt="7 1 Create New user" src="https://github.com/user-attachments/assets/8601a2e3-058a-4d79-951d-c4bf54e8d304">

<img width="737" alt="7 2 Create New User" src="https://github.com/user-attachments/assets/b15ecb9f-ed10-400e-9f74-bd670249d4dc">

<img width="1913" alt="7 3 Create New User" src="https://github.com/user-attachments/assets/b67859ed-7c02-4869-9bf2-947a18f71f35">

4. Assign 'Global Administrator' Role to the new user

<img width="1911" alt="8 1 Assign Global Admin Role" src="https://github.com/user-attachments/assets/3b4d5e87-0953-4668-8622-fc4bc563516c">

<img width="1141" alt="8 2 Assign Global Admin Role" src="https://github.com/user-attachments/assets/b4fc5e79-2b2f-48ed-a686-48b2548dbac8">

<img width="1904" alt="8 3 Assign Global Admin Role" src="https://github.com/user-attachments/assets/ecc16495-21db-4b4b-a23c-c213cae2567c">

<img width="1913" alt="8 4 Assign Global Admin Role" src="https://github.com/user-attachments/assets/a271a9a2-fb02-4ce2-bf6b-081f15a0e5e1">

5. Sign in using the new user to Azure Databricks Account Console via https://accounts.azuredatabricks.net/

<img width="1919" alt="9 1 Signin to Account Console" src="https://github.com/user-attachments/assets/8f63b9cd-805b-4164-86d6-ec483e437853">

<img width="1900" alt="9 2 Signin to Account Console" src="https://github.com/user-attachments/assets/70d41374-bf6d-4f53-9bfe-c5b49581b49e">

# Related Content

Databricks Community Forum - https://community.databricks.com/t5/administration-architecture/unable-to-login-to-azure-databricks-account-console/td-p/82190

Microsft Q&A Forum - https://learn.microsoft.com/en-us/answers/questions/1861727/unable-to-login-to-azure-databricks-account-consol

Stack Overflow Question - https://stackoverflow.com/questions/78843411/unable-to-login-to-azure-databricks-account-console/78893694#78893694













