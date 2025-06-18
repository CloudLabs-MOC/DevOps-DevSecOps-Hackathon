# Challenge 01: Continuous Integration and Deployment for Contoso Traders using GitHub Actions

## Introduction
This challenge is designed to evaluate the attendee/user skills in creating a robust CI/CD pipeline leveraging GitHub Actions. It aims to assess your capability to not only establish a seamless pipeline but also to guarantee the successful deployment of the application. Through this challenge, the attendee/user will set up a GitHub repository, implement a CI/CD workflow using GitHub Actions, deploy a .NET application to Azure, and make rolling updates to the application.

Here's the solution guide, which includes detailed step-by-step instructions required to complete the challenge.

## Accessing GitHub

1. To access and log into GitHub, open the edge browser from inside the environment and navigate to **[GitHub](https://github.com/)**.

2. Sign in to GitHub by clicking on the **Sign in** button in the top right corner of the GitHub home page.

3. On the **Sign into GitHub tab**, you will see a login screen. Enter the following email/username, and then click on **Next**.

4. Now enter the following password and click on **Sign in**.

## Accessing the Azure Portal

>**Important:** You can find the Username and Password within the environment by navigating to the **Environment** **(1)** tab in the left pane then copy the **Azure Username** **(2)** and **Azure Password** **(3)**, which will be required for signing into the Azure portal in later steps and you can record the **Deployment Id** **(4)**, which can be used to provide a unique name to the resources during deployment.

>**Note:** Numbers and ID's values may vary. Kindly ignore values in screenshots and copy values from the **Environment** tab.

 ![](../media1/Active-image19.png)
 ![](../media1/Active-image(20).png)

1. To access the Azure portal, within labvm open **Microsoft Edge** and browser to the [Azure Portal](https://portal.azure.com/).

1. On the **Sign into Microsoft Azure tab**, you will see a login screen. Enter the following email/username, and then click on **Next** 
   
   - **Email/Username:**

     ![](../media1/Active-image1.png)

      > **Note:** For **Email/Username**, Navigate to **Environment(1)**, click on **Azure credentials (2)**, and copy **Username (3)**.   
            
      ![](../media/ad1.png)

1. Now enter the following password and click on **Sign in**.

   - **Password:** 

      ![](../media1/Active-image2.png)

      > **Note:** For **Password**, Navigate to **Environment(1)**, click on **Azure credentials (2)**, and copy **Password (3)**.   
            
      ![](../media/ad2.png)      

1. When **Action Required** window pop up click on **Ask Later**.

    ![](../media1/Active-image3.png)

   >**NOTE:** If you don't have the Microsoft Authenticator app installed on your mobile device, select **Download** now and follow the steps.

1. On the Set up your account page, select **Next.**

   ![](../../../Scenario/media/mfa3.png)

1. Scan the QR code with your phone. On the phone, inside the Authenticator app, select Work or school account, and scan the QR code. Select **Next**.

   ![](../../../Scenario/media/mfa4.png)

1. On the Keep your account secure page. Enter the code, which is shown on the Authenticator app.

   ![](../../../Scenario/media/mfa5.png)

1. Once the code is entered. click **Next**

   ![](../../../Scenario/media/mfa6.png)

1. Select Done on the Success! page.

   ![](../../../Scenario/media/mfa7.png)
   
1. If you see the pop-up **Stay Signed in?**, click **No**.

    ![](../media1/Active-image4.png)

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

    ![](../media1/Active-image5.png)

## Solution Guide 

### Task 1: Set up a GitHub repository

In this task, you will log in to an account on [GitHub](https://github.com) and use `git` to add lab files to a new repository.

1. In a new browser tab, open ```https://www.github.com/login```. From the **Environment** page **(1)**, navigate to **License** **(2)** tab and **copy** **(3)** the credentials. Use the same username and password to log into GitHub.

   ![](../media/ad3.png) 
   
1. For **Device Verification Code**, use the same credentials as in the previous step, open `http://outlook.office.com/` in a private window, and enter the same username and password used for the GitHub Account login. Copy the verification code and paste it into Device verification.

   ![](../media/2dgn154.png) 
    
1. In the upper-right corner, expand the user **drop-down menu**.

   ![The `New Repository` creation form in GitHub.](../media/Ex1-task1-1.png "New Repository Creation Form")

1. Then select **Your repositories**.

   ![The `New Repository` creation form in GitHub.](../media/ex1-task1-2.png "New Repository Creation Form")

1. Next to the search criteria, locate and select the **New** button.

   ![The `New Repository` creation form in GitHub.](../media/ex1-task1-3.png "New Repository Creation Form")

1. On the **Create a new repository** screen, name the repository ```devsecops``` **(1)**, select **Public** **(2)**, and click on the **Create repository** **(3)** button.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s5.png "New Repository Creation Form")
   
   >**Note:** **If you observe any repository existing with the same name, please make sure you delete the Repo and create a new one. Please follow the steps below from 1 to 6. Otherwise, skip to step 7**.

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

   ![](../media/ex1-task1-4.png)
   
1. From the GitHub username, note down the **Unique-ID** present in the Username. You'll need this in the upcoming steps.

   ![](../media/cl1-t1-s13.png) 
   
1. Navigate  to the **Visual Studio Code (1)** application. Click on **... (2)** at the top and select **Terminal (3)** from the **drop-down** and choose **New Terminal (4)**, which opens a fresh PowerShell terminal tab.

   ![Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](../media/ex1-task1-5.png "Quick setup screen")

1. In Visual Studio Code, run the following commands in the terminal to set your **email** and **username**, which Git uses for commits. Make sure to replace the GitHub account email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
   ![](../media/ad4.png) 
     
    Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` with the value you copied in step 7 and `Unique-ID` in step 8.

    **Note:** This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created in Step 1. 

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin-<Unique-ID> <your_github_repository-url>
      git push -u origin-<Unique-ID> main
      ```
      
   - If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager.
  
       ![](../media/ad5.png)

   - Click on **Authorize git-ecosystem** to provide access.    

       ![](../media/ad6.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.

     ![](../media/ex1-task1-7.png)

### Task 2: Deploy Infrastructure

1. In the GitHub repository, navigate to the setting and add github action secreat and variable. To create GitHub secrets, in your GitHub lab files repository, click on the **Settings** tab.

   ![](./../media/cl1-t2-s2.png)

2. Navigate to **Environment** **(1)**, click on **Service Principal Details** **(2)**, and copy the **Subscription ID**, **Tenant ID (Directory ID)**, **Application ID (Client ID)**, and **Secret Key (Client Secret)**.

      ![](../media/ad7.png)
   
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

3. Under **Security**, expand **Secrets and variables** **(1)** by clicking the drop-down and select **Actions** **(2)** blade from the left navigation bar. Select the **New repository secret** **(3)** button.

   ![](../media/exe2-task4-step6-action-setup.png)

4. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name:** Enter **SERVICEPRINCIPAL** **(1)**
   - **Value:** Paste the service principal details in JSON format **(2)**
   
      ![](../media/2dgn36.png)

5. To create another secret, under the **Actions Secrets/New secret** page, click on **New repository secret**. Enter the below-mentioned details and click on **Add secret** ***(3)***.

   - **Name:** Enter **SQLPASSWORD** ***(1)***
   - **Value:** Enter **Azure Password** ***(2)*** 

      ![](../media/ex-task1-11.png)

      > **Note:** For **Azure Password**, Navigate to **Environment (1)**, click on **Azure credentials (2)**, and copy **Password (3)**.
      
      ![](../media/ad2.png)   

6. To create Variables, under the **Actions secrets and variables** page, switch to **Variables (1)** and then click on **New repository variable (2)**.
   
   ![](../media/ex1-task1-9.png)

7. Under **Actions variables / New variable** , enter the below-mentioned details and click on **Add variable** ***(3)***.

   - **Name:** Enter **DEPLOYMENTREGION** ***(1)***
   - **Value:** Add the deployment region where you want to get the resources deployed. preferenced **eastus2,uksouth,australiaeast** **(2)**
   
     ![](../media/ex1-task1-10.png)

8. To create another **Variable** click on **New repository variable** ,Under **Actions variables / New variable** , enter the below-mentioned details and click on **Add variable** ***(3)***.

   - **Name:** Enter **SUFFIX** ***(1)***
   - **Value:** Create a secret to store the deployment ID **(2)**
  
     ![](../media/ex1-task1-12.png)

      > **Note:** You can find the **Deployment ID** within the environment by navigating to the **Environment Details (1)**, click on **Azure credentials (2)**, and copy **Deployment ID** **(3)**.

      ![](../media1/Deployment_ID.png)
     
9. To run a workflow, perform the following steps and wait for the resources to be deployed within your Azure Portal:
      - Click on **Actions (1)** within your GitHub repository.
      - Select the workflow named **contoso-traders-provisioning-deployment (2)**.
      - Click on **Run workflow (3)**.
      - Finally, click on **Run workflow (4)**. Ensure that the branch is selected as **main**.

        ![](../media1/ex1-task1-15.png)

### Task 3: Set up CI/CD Workflow

1. From the Azure Portal Dashboard, click on **Resource Groups** from the Navigate panel to see the resource groups.

   ![](../media/2dgn9.png) 
   
1. Select the **contoso-traders-rgXXXXXXX** resource group from the list.

   ![](../media/ex1-task1-13.png)  

   >**Note:**  XXXXXXX represents the Deployment ID, which can be found in the Environment section.
   
1. Select the **productsdb** SQL database from the list of resources.

   ![](../media/ex1-task1-14.png) 
   
1. Under the Settings side blade, select **Connection strings** ***(1)*** and copy the **ADO.NET (SQL authentication)** ***(2)*** connection string from the ADO.NET tab. 

   ![](../media/ado-sql-database.png)  
 
1. In your GitHub lab files repository, select the **Settings** tab from the lab files repository.

   ![](../media/cl1-t1-s8.png)
   
1. Under **Security**, expand **Secrets and variables** ***(1)*** by clicking the drop-down and selecting **Actions** ***(2)*** from the left navigation bar. Select the edit button for the created secret named **SQLPASSWORD** ***(3)***.

   ![](../media/ex1-task3-1.png)
    
1. Under the **Actions Secrets/Update secret** page, enter the below-mentioned details, and click on **Update secret.**

   - **Value:** Paste the **ADO.NET (SQL authentication)** that you  have copied in the previous step.
   
      ![](../media/ex1-task3-2.png)
   
      >**Note:** Replace `{your_password}` with the ODL User Azure Password. Go to **Environment (1)**, click on **Azure credentials (2)**, and copy **Password (3)**.
      
      ![](../media/ad2.png)   
      
1. From your GitHub repository, select the **Actions** ***(1)*** tab. Select the **contoso-traders-app-deployment** ***(2)*** workflow from the side blade, Click on the  **drop-down** ***(3)*** next Run workflow button, and select **Run workflow** ***(4)***.

   ![](../media1/2dgn159.png)
   
1. Navigate back to the Actions tab and select the **contoso-traders-app-deployment** workflow. This workflow builds the Docker image, which is pushed to the container registry. The same image is pushed to the Azure container application.

   ![](../media/2dgn124.png)
   
   ![](../media1/2dgn165.png)
   
## Task 4: Test the application and perform rolling updates

1. Navigate to Azure Portal, and click on **Resource Groups** from the Navigate panel to see the resource groups.

   ![](../media/2dgn9.png) 
   
2. Select the **contoso-traders-rg(XXXXXXX)DeploymentID** resource group from the list.

   ![](../media/2dgn135.png) 

   > **Note:** XXXXXXX represents the Deployment ID, which can be found in the Environment section.
   
3. Select the **contoso-traders-ui2<inject key="DeploymentID" enableCopy="false" />** endpoint from the list of resources.

   ![](../media/2dgn127.png) 
   
4. Click on the **Endpoint hostname**. It'll open a browser tab where you will be able to verify that the Contoso Traders app has been hosted successfully.

   ![](../media/2dgn128.png) 
    
   ![](../media/2dgn162.png) 
    
   The last task automated building and updating only one of the Docker images. In this task, we will update the workflow file with a more appropriate workflow for the structure of our repository. This task will end with    a file named `docker-publish.yml` that will rebuild and publish Docker images as their respective code is updated.

   > **Note:** If you see the **Know your location** pop-up, click on **Block**.

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
