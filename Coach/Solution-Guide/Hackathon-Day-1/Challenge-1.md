# Challenge 01: Continuous Integration and Deployment for Contoso Traders using GitHub Actions

## Introduction
This challenge is designed to evaluate the attendee/user skills in creating a robust CI/CD pipeline leveraging GitHub Actions. It aims to assess your capability to not only establish a seamless pipeline but also to guarantee the successful deployment of the application. Through this challenge, the attendee/user will set up a GitHub repository, implement a CI/CD workflow using GitHub Actions, deploy a .NET application to Azure, and make rolling updates to the application.

Here's the solution guide, which includes detailed step-by-step instructions required to complete the challenge.

## Accessing GitHub

1. To access and log into GitHub, open the edge browser from inside the environment and navigate to **[GitHub](https://github.com/)**.

2. Sign in to GitHub by clicking on the **Sign in** button in the top right corner of the GitHub home page.

3. On the **Sign into GitHub tab**, you will see a login screen. Enter the following email/username, and then click on **Next**.

   - **Email/Username:** <inject key="GitHubUsername"></inject>

1. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="GitHubPassword"></inject>

## Accessing the Azure Portal

1. To access the Azure Portal, open the Edge browser from inside the environment and navigate to the **[Azure Portal](https://portal.azure.com)**.

1. On the **Sign in to Microsoft Azure** tab, you will see a login screen. Enter the following email/username, and then click on **Next**. 
   * **Email/Username**: <inject key="AzureAdUserEmail"></inject>
        
1. Now enter the following password and click on **Sign in**.
   * **Password**: <inject key="AzureAdUserPassword"></inject>
     
1. If you see the pop-up **Stay Signed in?**, click No.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

## Solution Guide 

### Task 1: Setup a GitHub repository

In this task, you will login to an account on [GitHub](https://github.com) and use `git` to add lab files to a new repository.

1. In a new browser tab, open ```https://www.github.com/login```. From the **Environment** page **(1)**, navigate to **Licenses** **(2)** tab and **copy** **(3)** the credentials. Use the same username and password to log into GitHub.

   ![](../media/devops-devsecops-new-1.png) 
   
1. For **Device Verification Code**, use the same credentials as in the previous step, open `http://outlook.office.com/` in a private window, and enter the same username and password used for the GitHub Account login. Copy the verification code and Paste it into Device verification.

   ![](../media/2dgn154.png) 
    
1. In the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/160625(01).png "New Repository Creation Form")

   ![The `New Repository` creation form in GitHub.](../media/160625(02).png "New Repository Creation Form")

1. Next to the search criteria, locate and select the **New** button.

   ![The `New Repository` creation form in GitHub.](../media/ex2-t3-3-git.png "New Repository Creation Form")

1. On the **Create a new repository** screen, name the repository ```devsecops``` **(1)**, select **Public** **(2)**, and click on the **Create repository** **(3)** button.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s5.png "New Repository Creation Form")
   
   >**Note**: If you observe any repository existing with the same name, please make sure you delete the Repo and create a new one. Please follow steps 6 to 11. Otherwise, skip to step 12.

1. In the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/2dg1.png "New Repository Creation Form")

1. Using the search bar, search for ```devsecops``` **(1)** and open it.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s7.png "New Repository Creation Form")

1. From the GitHub repository, click on the **Settings** tab.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s8.png "New Repository Creation Form")

1. In the settings page, scroll to the bottom of the page to select **Delete this repository**, and then click on **I want to delete this repository**.

   ![The `New Repository` creation form in GitHub.](../media/2dg120.png "New Repository Creation Form")

1. Within the following pop-up window, click on **I have read and understand these effects**.

   ![](../media/cl1-t1-s10.png)

1. In the succeeding pop-up window, copy the **repository name** **(1)**, paste it in the **box** **(2)**, and click on **Delete this repository** **(3)**.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s11.png "New Repository Creation Form")

1. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository and **save it** in a notepad for future use.

   ![](../media/cl1-t1-s12.png)
   
1. From the GitHub username, note down the **Unique-ID** present in the Username. You'll need this in the upcoming steps.

   ![](../media/cl1-t1-s13.png) 
   
1. Navigate back to the **Visual Studio Code** application in which the terminal is already open. In the terminal, click on the **drop-down** button and select **PowerShell** to open a fresh PowerShell terminal tab.

   ![Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](../media/2dg4.png "Quick setup screen")

   >**Note**: If the terminal is not open by default, please navigate to the terminal and click on new terminal.

1. In Visual Studio Code, run the below commands in the terminal to set your **email** and **username**, which Git uses for commits. Make sure to replace the GitHub account email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
   ![](../media/cl1-t1-s15.png) 
     
    Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` with the value you copied in step 12 and `Unique-ID` in step 13.

    Note: This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created in Step 1. 

    Note: Remove the "<>", while entering url and unique id.

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin<Unique-ID> <your_github_repository-url>
      git push -u origin<Unique-ID> main
      ```
     
   - If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager. Click on **Authorize git-ecosystem** to provide access.

       ![](../media/160625(03).png)

       ![](../media/ex2-t3.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.

### Task 2: Deploy Infrastructure


2. To create GitHub secrets, in your GitHub lab files repository, click on the **Settings** tab.

      ![](../media/cl1-t2-s2.png)

 3. Navigate to **Environment** **(1)**, click on **Service Principal Details** **(2)**, and copy the **Subscription ID**, **Tenant ID (Directory ID)**, **Application ID (Client ID)**, and **Secret Key (Client Secret)**.

      ![](../media/devops-devsecops-new-2.png)
   
      - Replace the values that you copied in the below JSON. You will be using them in this step.
      
         ```json
         {
            "clientId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
            "clientSecret": "zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz",
            "tenantId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
            "subscriptionId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz"
         }
         ```

4. Under **Security**, expand **Secrets and variables** **(1)** by clicking the drop-down and select **Actions** **(2)** blade from the left navigation bar. Select the **New repository secret** **(3)** button.

   ![](../media/exe2-task4-step6-action-setup.png)

5. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name** : Enter **SERVICEPRINCIPAL** **(1)**
   - **Value** : Paste the service principal details in JSON format **(2)**
   
      ![](../media/2dgn36.png)

6. To create another secret, under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** ***(3)***.

   - **Name**: Enter **SQLPASSWORD** ***(1)***
   - **Value**: You need to enter any unique password with combination of Alphanumeric letters. Your password must contain characters from three of the following categories – English uppercase letters, English lowercase letters, numbers (0-9), and non-alphanumeric characters (!, $, #, %, etc.).

      ![](../media/sqlpass.png)

7. Under the **Actions Secrets/New variable** page, enter the below-mentioned details and click on **Add variable** ***(3)***.

   - **Name** : Enter **SUFFIX** ***(1)***
   - **Value** : **<inject key="DeploymentID" enableCopy="false" />** (Copy the Deployment ID from the environment details tab) ***(2)***
   
       
8. Same as above create a new variable called **DEPLOYMENTREGION** and enter the region where you want to deploy your infrastructure. 


10. To run a workflow, perform the following steps and wait for the resources to be deployed within your Azure Portal:
      - Click on **Actions (1)** within your GitHub repository.
      - Select the workflow named **contoso-traders-provisioning-deployment (2)**.
      - Click on **Run workflow (3)**.
      - Finally, click on **Run workflow (4)**. Ensure that the branch is selected as **main**.

         ![](../media/cl1-t2-s10.png)


11. Navigate to `.github/workflow/update-contoso-traders-App.yml` path, ensure to update the `AKS_NODES_RESOURCE_GROUP_NAME` and`RESOURCE_GROUP_NAME` environment variable by replacing `<deployment-id>` with **<inject key="DeploymentID" enableCopy="false" />**, once updated click commit changes to save the file:

    ![](../media/dso1.png) 

12. To run a workflow, perform the following steps and wait for the resources to be deployed within your azure portal:
      - Click on **Actions (1)** within your GitHub repository.
      - Select on the workflow named **update contoso traders app (2)**.
      - Click on **Run workflow (3)**.
      - Finally click on **Run workflow (4)**. Ensure that the branch is select as **main**.

         ![](../media/dso2.png) 

### Task 3: Setup CI/CD Workflow

1. From the Azure Portal Dashboard, click on Resource Groups from the Navigate panel to see the resource groups.

   ![](../media/2dgn9.png) 
   
1. Select the **contosotraders-rg<Deployment-ID>** resource group from the list.

   ![](../media/cl1-t3-s2.png)  
   
1. Select the **productsdb** SQL database from the list of resources.

   ![](../media/cl1-t3-s3.png) 
   
1. Under the Settings side blade, select **Connection strings** ***(1)*** and copy the **ADO.NET (SQL authentication)** ***(2)*** connection string from the ADO.NET tab. 

   ![](../media/ado-sql-database.png)  
 
1. In your GitHub lab files repository, select the **Settings** tab from the lab files repository.

   ![](../media/cl1-t1-s8.png)
   
1. Under **Security**, expand **Secrets and variables** ***(1)*** by clicking the drop-down and selecting **Actions** ***(2)*** from the left navigation bar. Select the edit button for the created secret named **SQL_PASSWORD** ***(3)***.

   ![](../media/cl1-t3-s6.png)
    
1. Under the **Actions Secrets/Update secret** page, enter the below-mentioned details, and click on **Update secret** ***(3)***.

   - **Value**: Paste the **ADO.NET (SQL authentication)** that you  have copied in the previous step.
   
      ![](../media/cl1-t3-s7.png)
   
   >**Note**: Replace `{your_password}` with the password that you have used initially
   
   
1. From your GitHub repository, select the **Actions** ***(1)*** tab. Select the **contoso-traders-app-deployment** ***(2)*** workflow from the side blade, Click on the  **drop-down** ***(3)*** next Run workflow button, and select **Run workflow** ***(4)***.

   ![](../media/2dgn159.png)
   
1. Navigate back to the Actions tab and select the **contoso-traders-app-deployment** workflow. This workflow builds the Docker image, which is pushed to the container registry. The same image is pushed to the Azure container application.

   ![](../media/2dgn124.png)
   

   
   **Note**: If the workflow **fails** due to the **npm install** job, follow steps 13 to 15. Otherwise, continue from step 16. 
   
1. From the GitHub browser tab, follow the steps given below and click on **Create codespace on main** ***(3)***.

   - Click on **Code** ***(1)***, 
   - Select the **Codespace** ***(2)*** tab

      ![](../media/ex2-kc-codespace.png)
   
1. Run the below-mentioned commands in the **Terminal**. You'll set the node version to node 14.

   ```pwsh
   cd src
   cd ContosoTraders.Ui.Website
   nvm install 14
   nvm use 14
   npm i
   git add . 
   git commit -m "updated node version"
   git push
   ```
    
1. From your GitHub repository, select the **Actions** ***(1)*** tab. You'll see an Action named **Updated node version** ***(2)*** executing. Please wait until the execution is complete.

   ![](../media/2dgn160.png)
   
   ![](../media/2dgn161.png)      

## Task 4: Test the application and perform rolling updates

1. Navigate to Azure Portal, and click on Resource Groups from the Navigate panel to see the resource groups.

   ![](../media/2dgn9.png) 
   
2. Select the **contosotraders-<inject key="DeploymentID" enableCopy="false" />** resource group from the list.

   ![](../media/2dgn135.png) 
   
3. Select the **contosotraders-ui2<inject key="DeploymentID" enableCopy="false" />** endpoint from the list of resources.

   ![](../media/2dgn127.png) 
   
4. Click on the **Endpoint hostname**. It'll open a browser tab where you will be able to verify that the Contoso Traders app has been hosted successfully.

   ![](../media/2dgn128.png) 
    
   ![](../media/2dgn162.png) 
    
   The last task automated building and updating only one of the Docker images. In this task, we will update the workflow file with a more appropriate workflow for the structure of our repository. This task will end with    a file named `docker-publish.yml` that will rebuild and publish Docker images as their respective code is updated.

5. From the GitHub browser tab, follow the steps given below and click on **Create codespace on main** ***(3)***.

   - Click on **Code** ***(1)***, 
   - Select the **Codespace** ***(2)*** tab

      ![](../media/ex2-kc-codespace.png)
   
      >**Note**: In case you have created a codespace in a previous task. Click on the **+** button to create a new codespace.
   
6. You'll be redirected to a new codespace tab in the browser. Please wait until the codespace is configured.

   ![](../media/2dg33.png)
   
7. From the explorer side blade, navigate to **.github (1)** > **workflows** **(2)** and select the **contoso-traders-provisioning-deployment.yml** **(3)** file.

   ![](../media/contosoprovision.png) 
   
8. Remove the commands from lines 7 to 14 from the workflow file.

   ![](../media/2dgn163.png) 
   
9. Using the terminal from codespace, run the following commands to commit this change to your repo and push the change to GitHub.

   ```pwsh
   git add .
   git commit -m "Updating app deployment"
   git push
   ```
   ![](../media/2dgn133.png) 
    
   > **Note**: This will update the workflow and will **not** run the "Update the ... Docker image" jobs.

10. Navigate back to the GitHub browser, select the **Actions** ***(1)*** tab, and review the **workflow** ***(2)*** created automatically for the changes made. 

      ![](../media/2dgn164.png)

11. Click on the **Next** button present in the bottom-right corner of this lab guide.

## Success criteria:
To complete this challenge successfully:

- The application must be deployed using VS Code, which supports GitHub Actions.
- A new repository must have been created.
- **CI/CD Implementation**: The CI/CD pipeline should be established using GitHub Actions, encompassing build, test, and deployment stages effectively.
- **Deployment Accuracy**: The application must be successfully deployed using GitHub Actions, and the chosen deployment strategy should align with the project's requirements.

## Additional Resources:

- Refer to [GitHub Actions and .NET](https://learn.microsoft.com/en-us/dotnet/devops/github-actions-overview) for reference.
- [Building and testing .NET](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-net).
- [Why CI/CD](https://resources.github.com/ci-cd/).
- [Continuous Deployment with Github Actions: An Example](https://www.dolthub.com/blog/2020-11-23-continous-deployment-with-github-actions/).
- [How to build a CI/CD pipeline with GitHub Actions in four simple steps](https://github.blog/2022-02-02-build-ci-cd-pipeline-github-actions-four-steps/).
