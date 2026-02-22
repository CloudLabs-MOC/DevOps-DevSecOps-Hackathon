# Microsoft Azure Hackathon: Accelerate Development with GitHub Copilot Trainer Guide

<p align="right">Last updated February 22, 2026</p>

## Challenge 01: Continuous Integration and Deployment for Contoso Traders using GitHub Actions

## Introduction
This challenge is designed to evaluate the attendee/user skills in creating a robust CI/CD pipeline leveraging GitHub Actions. It aims to assess your capability to not only establish a seamless pipeline but also to guarantee the successful deployment of the application. Through this challenge, the attendee/user will set up a GitHub repository, implement a CI/CD workflow using GitHub Actions, deploy a .NET application to Azure, and make rolling updates to the application.

Here's the solution guide, which includes detailed step-by-step instructions required to complete the challenge.

## Accessing the Azure Portal

>**Important:** You can find the Username and Password within the environment by navigating to the **Environment** **(1)** tab in the left pane then copy the **Azure Username** **(2)** and **Temporary Access Pass** **(3)**, which will be required for signing into the Azure portal in later steps and you can record the **Deployment Id** **(4)**, which can be used to provide a unique name to the resources during deployment.

>**Note:** Numbers and ID's values may vary. Kindly ignore values in screenshots and copy values from the **Environment** tab.

 ![](../media1/Active-image19new.png)

1. To access the Azure portal, within labvm open **Microsoft Edge** and browser to the [Azure Portal](https://portal.azure.com/).

1. On the **Sign into Microsoft Azure tab**, you will see a login screen. Enter the following email/username, and then click on **Next** 
   
   - **Email/Username:**

     ![](../media1/Active-image1.png)

      > **Note:** For **Email/Username**, Navigate to **Environment(1)**, click on **Azure credentials** **(2)**, and copy **Username** **(3)**.   
            
      ![](../media1/ad1.png)

1. Now enter the following password and click on **Sign in**.

   - **Password:** 

      ![](../media1/Active-image2new.png)

      > **Note:** For **Password**, Navigate to **Environment(1)**, click on **Azure credentials** **(2)**, and copy **Password** **(3)**.   
            
      ![](../media1/ad2.png)      
   
1. If you see the pop-up **Stay Signed in?**, click **No**.

    ![](../media1/Active-image4.png)

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

    ![](../media1/Active-image5.png)

## Accessing GitHub

In this task, you will log in to an account on [GitHub](https://github.com) and use `git` to add lab files to a new repository.

1. In a new tab, navigate to the **GitHub login** page by copying and pasting the following URL into the address bar:

   ```
   https://github.com/login
   ```

1. On the **Sign in to GitHub** tab, enter the provided **GitHub username** **(1)** in the input field, and click on **Sign in with your identity provider** to continue **(2)**.

    - Email/Username: **odl-user-DID_clabs** The Username is similar to this  make sure you have to replace the **DID** with your **Deployement ID**. Deployement id you can find in Environment Tab.

      ![](../media/01.png)

1. Click on **Continue** on the **Single sign-on to CloudLabs Organizations** page to proceed.

    ![](../media/02.png)

1. You'll see the **Sign in** tab. Here, enter your Azure Entra credentials:

   - **Email/Username:** 

       ![Enter Your Username](../media/03.png)

1. Next, provide your password and click on **Sign in**

   - **Password:** 

      ![Enter Your Password](../media/04.png)

1. On the **Stay Signed in?** pop-up, click on No.

    ![](../media/n69.png)

1. On the **Permission requested by** pop-up, click on **Accept**.

      ![Enter Your Password](../media/06.png)

## Solution Guide 

### Task 1: Set up a GitHub repository

In this task, you will log in to an account on [GitHub](https://github.com) and use `git` to add lab files to a new repository.

1. You are now successfully logged in to **GitHub** and have been redirected to the **GitHub homepage**.

1. Click on **Create repository** to create the new repository.

   ![](../media1/09new.png)

1. On the **Create a new repository** tab, most fields will be pre-filled. Just update the **Owner** to **Cloudlabs-Enterprises** **(1)**, change the **Repository name** **(2)** as provided below to make it unique.

   - Enter your Repository name as: **devsecops-did**
   
     > **Note:** did is refers to deployement id.

   - Then click **Create repository** **(3)** to continue

     ![](../media1/github-repo-create-1new.png)

1. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository and **save it** in a notepad for future use.

   ![](../media1/copy-git-url1.png)
    
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
     
1. Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` 

   ```pwsh
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote -v
   git remote set-url origin <your_github_repository-url>
   git remote add origin <your_github_repository-url>
   git push -u origin main
   ```

   > **Note:** This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created in Step 1. 

   > **Note**: If you see an error `git : fatal: detected dubious ownership in repository at 'C:/Workspaces/lab/DevOps-DevSecOps-Hackathon-lab-files'` run the fallowing command and rerun ablow command

     ```
     git config --global --add safe.directory C:/Workspaces/lab/DevOps-DevSecOps-Hackathon-lab-files
     ```

1. If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager. Click on **Authorize git-ecosystem** to provide access.

   ![](../media1/160625(03).png)

   ![](../media1/ex2-t3.png)
       
1. After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.

   ![](../media1/n63.png)

### Task 2: Deploy Infrastructure

1. In the GitHub repository, navigate to the setting and add github action secreat and variable. To create GitHub secrets, in your GitHub lab files repository, click on the **Settings** tab.

   ![](../media1/repo-setting.png)

2. Navigate to **Environment** **(1)**, click on **Service Principal Details** **(2)**, and copy the **Subscription ID**, **Tenant ID** **(Directory ID)**, **Application ID** **(Client ID)**, and **Secret Key** **(Client Secret)**.

   ![](../media1/ad7.png)
   
   - Replace the values that you copied in the below JSON. You will be using them in this step.
   - The Application ID refers to the Client ID, and the Secret Key corresponds to the Client Secret.
      
      ```json
      {
         "clientId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
         "clientSecret": "zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz",
         "tenantId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
         "subscriptionId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz"
      }
      ```

3. Under **Security**, expand **Secrets and variables** **(1)** by clicking the drop-down and select **Actions** **(2)** blade from the left navigation bar. Select the **New repository secret** **(3)** button under Repository secrets.

   ![](../media1/exe2-task4-step6-action-setup.png)

4. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name:** Enter **SERVICEPRINCIPAL** **(1)**
   - **Value:** Paste the service principal details in JSON format **(2)**
   
      ![](../media/2dgn36.png)

5. To create another secret, under the **Actions Secrets/New secret** page, click on **New repository secret**. Enter the below-mentioned details and click on **Add secret** ***(3)***.

   - **Name:** Enter **SQLPASSWORD** ***(1)***
   - **Value:** Enter **Azure Password** ***(2)*** 

      ![](../media1/ex-task1-11.png)

      > **Note:** For **Azure Password**, Navigate to **Environment** **(1)**, click on **Azure Credentials** **(2)**, and copy **Temporary Access Pass** **(3)**.
      
      ![](../media1/ad2.png)   

6. Under **Security**, expand **Secrets and variables** **(1)** by clicking the drop-down and select **Actions** **(2)** blade from the left navigation bar. Select the **variables** **(3)** button and click on **New repository variable** **(4)** button under Repository secrets.

   ![](../media1/ex1-task1-9new.png)

7. Under **Actions variables / New variable** , enter the below-mentioned details and click on **Add variable** ***(3)** button under Repository variables.

   - **Name:** Enter **DEPLOYMENTREGION** ***(1)***
   - **Value:** Add the deployment region where you want to get the resources deployed. preferenced **eastus2** **(2)**
   
     ![](../media/ex1-task1-10.png)

8. To create another **Variable** click on **New repository variable**, under **Actions variables / New variable** , enter the below-mentioned details and click on **Add variable** ***(3)***.

   - **Name:** Enter **SUFFIX** ***(1)***
   - **Value:** Create a secret to store the deployment ID **(2)**
  
     ![](../media/ex1-task1-12.png)

      > **Note:** You can find the **Deployment ID** within the environment by navigating to the **Environment Details** **(1)**, click on **Azure Credentials** **(2)**, and copy **Deployment ID** **(3)**.

      ![](../media1/Deployment_ID.png)
     
9. To run a workflow, perform the following steps and wait for the resources to be deployed within your Azure Portal:
   - Click on **Actions** **(1)** within your GitHub repository.
   - Select the workflow named **contoso-traders-provisioning-deployment** **(2)**.
   - Click on **Run workflow** **(3)**.
   - Finally, click on **Run workflow** **(4)**. Ensure that the branch is selected as **main**.

     ![](../media1/run-contoso-provision.png)

     > **Note**: GitHub action will take around **10–15 minutes** to finish.

### Task 3: Set up CI/CD Workflow

1. From the Azure Portal Dashboard, click on **Resource groups** from the Navigate panel to see the resource groups.

   ![](../media1/2dgn9.png) 
   
1. Select the **contoso-traders-rgXXXXXX** resource group from the list.

   ![](../media/ex1-task1-13.png)  

   > **Note:** XXXXXX represents the Deployment ID, which can be found in the Environment section.
   
1. Select the **productsdb** SQL database from the list of resources.

   ![](../media/ex1-task1-14.png) 
   
1. Under the Settings side blade, select **Connection strings** ***(1)*** and copy the **ADO.NET** **(SQL authentication)** ***(2)*** connection string from the ADO.NET tab. 

   ![](../media1/ado-sql-databasenew.png)  
 
1. Navigate back to GitHub lab files repository, select the **Settings** tab from the lab files repository.

   ![](../media1/repo-setting.png)
   
1. Under **Security**, expand **Secrets and variables** ***(1)*** by clicking the drop-down and selecting **Actions** ***(2)*** from the left navigation bar. Select the edit button for the created secret named **SQLPASSWORD** ***(3)***.

   ![](../media/ex1-task3-1.png)
    
1. Under the **Actions Secrets/Update secret** page, enter the below-mentioned details, and click on **Update secret.**

   - **Value:** Paste the **ADO.NET** **(SQL authentication)** that you  have copied in the previous step.
   
      ![](../media/ex1-task3-2.png)
   
      > **Note:** Replace `{your_password}` with the ODL User Azure Password. Go to **Environment** **(1)**, click on **Azure Credentials** **(2)**, and copy **Temporary Access Pass** **(3)**.
      
        ![](../media1/ad2.png)   
      
1. On the GitHub repository, select the **Actions** ***(1)*** tab. Select the **contoso-traders-app-deployment** ***(2)*** workflow from the side blade, Click on the  **drop-down** ***(3)*** next Run workflow button, and select **Run workflow** ***(4)***.

   ![](../media1/traders-action.png)
   
1. Navigate back to the Actions tab and select the **contoso-traders-app-deployment** workflow. This workflow builds the Docker image, which is pushed to the container registry. The same image is pushed to the Azure container application.

   ![](../media/n26.png)
   
   ![](../media1/2dgn165.png)
   
## Task 4: Test the application and perform rolling updates

1. Navigate to Azure Portal, and click on **Resource groups** from the Navigate panel to see the resource groups.

   ![](../media1/2dgn9.png) 
   
2. Select the **contoso-traders-rgXXXXXX** resource group from the list.

   ![](../media/2dgn135.png) 

   > **Note:** XXXXXX represents the Deployment ID, which can be found in the Environment section.
   
3. Select the **contoso-traders-cdnXXXXXXX** Front Door from the list of resources.

   ![](../media/S3.png) 
   
4. Once you opened the **Front Door** Just scroll dow under **properties** you can see the **Endpoint hostname** just copy it and paste in new tab.

   ![](../media/S4.png) 
    
   ![](../media/2dgn162.png) 
    
   The last task automated building and updating only one of the Docker images. In this task, we will update the workflow file with a more appropriate workflow for the structure of our repository. This task will end with a file named `docker-publish.yml` that will rebuild and publish Docker images as their respective code is updated.

   > **Note:** If you see the **Know your location** pop-up, click on **Block**.
   > **Note:** The web application may not be accessible through the endpoint immediately. Please wait **10–15 minutes** for the application to be fully up and running.

## Success criteria:
To complete this challenge successfully:

- The application must be deployed using VS Code, which supports GitHub Actions.
- A new repository must have been created.
- **CI/CD Implementation:** The CI/CD pipeline should be established using GitHub Actions, encompassing build, test, and deployment stages effectively.
- **Deployment Accuracy:** The application must be successfully deployed using GitHub Actions, and the chosen deployment strategy should align with the project's requirements.

## Additional Resources:

- Refer to [GitHub Actions and .NET](https://learn.microsoft.com/en-us/dotnet/devops/github-actions-overview) for reference.
- [Building and testing .NET](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-net).
- [Why CI/CD](https://resources.github.com/ci-cd/).
- [Continuous Deployment with Github Actions: An Example](https://www.dolthub.com/blog/2020-11-23-continous-deployment-with-github-actions/).
- [How to build a CI/CD pipeline with GitHub Actions in four simple steps](https://github.blog/2022-02-02-build-ci-cd-pipeline-github-actions-four-steps/).
