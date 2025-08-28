# Challenge 07: DevSecOps with AI-Powered GitHub Actions

## Introduction

Contoso Traders, an e-commerce platform, is committed to delivering secure and efficient software solutions. In this challenge, as a Lead DevSecOps engineer, your focus is to enhance the DevSecOps workflow by leveraging AI-driven GitHub Actions that focus on code review and security checks for pull requests thus leading to improved code quality and enhanced security practices in the development lifecycle.

You need to focus on completing the implementation of the below-mentioned GitHub Actions:

**AI Code Review Action**: AI Code Reviewer is a GitHub Action that leverages OpenAI's GPT-4 API to provide intelligent feedback and suggestions on your pull requests.
**AI Security Check for Pull Request**: This GitHub Action uses OpenAI's GPT to analyse code in pull requests and identify potential security and privacy vulnerabilities and comment to the pull request with the findings.

Here is the solution guide, which provides all the specific, step-by-step directions needed to do the task.

## Accessing GitHub

1. To access and log into GitHub, open the edge browser from inside the environment and navigate to **[GitHub](https://github.com/)**.

2. Sign in to GitHub by clicking on the **Sign in** button in the top right corner of the GitHub home page.

3. On the **Sign into GitHub tab**, you will see a login screen. Enter the following email/username, and then click on **Next**.

   - **Email/Username:** <inject key="GitHubUsername"></inject>

4. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="GitHubPassword"></inject>

## Solution Guide

## Exercise 1: Configure and implement AI Code Review GitHub Action

### Task 1: Sign In/Sign Up to an OpenAI Account

1. Navigate to the **[OpenAI](https://platform.openai.com/login?launch)** in order to login to **OpenAI Account.**
   
3. Within the **Welcome back** page,
    - If you already have an OpenAI account pre-created, you can go ahead and sign into OpenAI using the following sign-in options as shown in the screenshot below.

      ![](../media/cl6-ex1-t1-s2-a.png)

      >**Note:** Ensure that your OpenAI account has active credits for the generation and usage of API keys.

    - After providing the user email and password, you will be prompted to select an access option. Choose **API** to proceed.

      ![](../media/ex6-task1-0.1.png)
      
    - If you are new to OpenAI and do not have an account created, click on **Sign up** within the *Welcome back* page to create a new free-tier account. 

      ![](../media/cl6-ex1-t1-s2-b.png)
  
    - After clicking Sign Up on the welcome page:

        - Enter your email address – You can use your GitHub **Email address (1)** and click on **Continue (2)**.

          ![](../media/ex6-task1-2.png)

        - Enter your password – Use your GitHub **Password (1)** and click on **Continue (2).**
     
          ![](../media/ex6-task1-3.png)
  
          >**Note:** You can find the GitHub credentials from the Environment Details page of the integrated lab environment, navigate to License tab.
  
        - A page will appear with the message "Verify your email". open http://outlook.office.com/ in a private window, provide the Github username and password, open the email from OpenAI, and click the verification link inside to complete the setup process. 
     
          ![](../media/ex6-task1-3.1.png)
  
        - Navigate back to the login page provide Github username and password, You will be prompted to provide details like **Full Name** and **Date of Bith** then click on **Agree** this will navigate you the Open AI Platform.

      >**Note:** Upon creation of a new OpenAI account, the free tier provides you with a $5 credit limit that expires within a period of 3 months from the day of account activation.

### Task 2: Create an OpenAI secret key

1. Once you have successfully logged into your OpenAI account, you will be auto-directed to the overview page of the OpenAI platform. If not, you can navigate to the OpenAI platform using the following link, **[OpenAI platform](https://platform.openai.com/docs/overview)**.

1. Go to the profile icon in the top right corner and select **Your profile**.
   
    ![](../media/CH6T2S2.png)

2. Hover your cursor over the left navigation toolbar to expand the pane and click on **API keys**.

    ![](../media/ex6-apikeys.png)

3. In order to create **API key**, its required to Verify it with your phone number.Click on **Start verification.**

   ![](../media/ex6-task1-4.png)

4. Provide your Phone Number and click on **Send code.**

   ![](../media/ex6-phoneno.png)

5. Enter the Verification code that has been sent to the Phone number.

   ![](../media/ex6-code.png)

8. On the **Create new secret key** pop-up, configure the following:
   
    - **Name:** `GitHub Action Key` **(1)**
    - **Project:** Select **Default project (2)** from the drop down.
    - **Permissions:** Select `All` **(3)**
    - Click on **Create secret key (4)**

      ![](../media/ex6-task1-5.png)

10. Upon creation of a new secret, save your key by clicking on the **Copy** button and pasting it on your notepad for a handy access.

    **Note:** For safety reasons, **you won't be able to view the secret value again** once the **Save your key** page is closed.

    ![](../media/cl6-ex1-t2-s5.png)

11. You will now notice that the new API key, `GitHub Action Key` now appears in the list of **API keys**.

    ![](../media/ex6-task1-7.png)

### Task 3: Create a new GitHub repository secret

1. Sign in to GitHub using the credentials provided in the environment detail tab of the integrated lab environment or via the credentials provided at the beginning of this solution guide.

2. Select the `devsecops` repository that was created as a part of the earlier challenges.

3. Under **Settings (1)**, expand **Secrets and variables** **(2)** under **security** by clicking the drop-down and select **Actions** **(3)** blade from the left navigation bar. Select the **New repository secret** **(4)** button.

   ![](../media/ex6-task1-8.png)

4. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name** : Enter **OPENAI_API_KEY** **(1)**
   - **Value**: Paste the OpenAI secret value that was copied earlier over to the notepad **(2)**.

     ![](../media/cl6-ex1-t3-s4.png)

### Task 4: Configure the AI Code Review GitHub Action

1. Open a new tab and paste the below URL which will Navigate to the following repo and fork it.

   ```
   https://github.com/freeedcom/ai-codereviewer
   ```

   ![](../media/ex6-task1-forkrepo.png)
  
1. Click on **Fork (1)** and then select **Create a new fork (2).**

   ![](../media/ex6-task1-9.png)

1. Uncheck **Copy the main branch only (1)** and click on **Create fork (2)**

   ![](../media/ex6-task1-10.png)
   
1. Click on **Settings** **(1)**, rename the repo name to **ai-code-reviewer** **(2)** and click on **Rename** **(3)** button. 

   ![](../media1/edit-ai-code.png)

1. Navigate back to the `devsecops` repository that was created as a part of the earlier challenges.

   ![](../media/ex6-task1-11.png)

3. Select the **Actions (1)** tab from your repository home page and then click on **New Workflow (2)**.

   ![](../media/cl9-t2-s3.png)

4. On the Get Started with GitHub Actions page, select **set up a workflow yourself**.

   ![](../media/cl9-t2-s4.png)

5. In the text box, enter the name `ai-code-review.yml` for your workflow file.

   ![](../media/cl6-ex1-t4-s4.png)

6. Copy and paste the following action workflow into the Edit New file tab:

    ```
    name: AI Code Reviewer
    
    on:
      pull_request:
        types:
          - opened
          - synchronize
    permissions: write-all
    jobs:
      review:
        runs-on: ubuntu-latest
        steps:
          - name: Checkout Repo
            uses: actions/checkout@v3
    
          - name: AI Code Reviewer
            uses: your-username/ai-code-reviewer@main
            with:
              GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} # The GITHUB_TOKEN is there by default so you just need to keep it like it is and not necessarily need to add it as secret as it will throw an error. [More Details](https://docs.github.com/en/actions/security-guides/automatic-token-authentication#about-the-github_token-secret)
              OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
              OPENAI_API_MODEL: "gpt-3.5"
              exclude: "**/*.json, **/*.md" # Optional: exclude patterns separated by commas
    ```

7. Rename `your-username` with a GitHub **username (1)** and Commit the changes made to create the workflow file by clicking on **Commit changes (2)**.

   ![](../media1/ai-code-edit.png)

8. Click on **Commit changes**.

   ![](../media/ex-common.png)

### Task 5: Create a pull request to initiate workflow

1. To create a new branch, click on the **Switch branch (1)** dropdown menu and click on **View all branches (2)**.
  
   ![](../media/cl6-ex1-t5-s1.png)

2. Click on **New branch** within the **Branches** page.

   ![](../media/cl6-ex1-t5-s2.png)

3. Within the **Create a branch** pop-up, enter the following:
   - **New branch name:** Test **(1)**
   - **Source:** Select `main` **(2)**.
   - Click on **Create new branch (3)**

     ![](../media/ex6-task1-12.png)

4. Navigate to the newly created `Test` branch.

   ![](../media/ex6-task1-13.png)

6. Select **.github (1)**, expand **workflows (2)** click on **ai-code-review.yml (3)**.

    ![](../media/ex6-task1-14.png)

7. on the `ai-code-review.yml` file click on **pencil icon** at the top right corner in order to edit the file.

   ![](../media/ex6-task1-17.png)

8. At the end of the line add a **space** or click on **enter** and click on **Commit changes.**

   ![](../media/ex6-task1-15.png)

9. Click on **Commit changes.**

   ![](../media/ex6-task1-16.png)


1. Navigate back to github organzation page and selcet **New** to create a new repository

   ![](../media/09.png)

1. On the **Create a new repository** tab, most fields will be pre-filled. Just update the **Owner** to **Cloudlabs-Enterprises** **(1)**, change the **Repository name** **(2)** as provided below to make it unique.

    - Enter your Repository name as: `devsecops-2 <did>`

       >Note: Make sure replace the did with your deployemnt id.

    - Then click **Create repository** **(3)** to continue

      ![](../media/n70.png)

1. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository and **save it** in a notepad for future use.

   ![](../media/n64.png) 
      
1. Navigate  to the **Visual Studio Code (1)** application. Click on **... (2)** at the top and select **Terminal (3)** from the **drop-down** and choose **New Terminal (4)**, which opens a fresh PowerShell terminal tab.

   ![Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](../media/ex1-task1-5.png "Quick setup screen")

1. In Visual Studio Code, run the following commands in the terminal to set your **email** and **username**, which Git uses for commits. Make sure to replace the GitHub account email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
   ![](../media/ad4.png) 
     
    Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` 

    **Note:** This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created in Step 1. 

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin- <your_github_repository-url>
      git push -u origin main
      ```
      
   - If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager.
  
       ![](../media/ad5.png)

   - Click on **Authorize git-ecosystem** to provide access.    

       ![](../media/n63.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.
=======
10. To create a Pull request to merge the changes made from the `test` to  the `main` branch. Click on **Pull requests**

    ![](../media/ex6-task1-18.png)

1. Click on **New pull request.**

   ![](../media/ex6-task1-19.png)

1. Here at the Comparing changes page, make sure you have selected **main** **(1)** for the base and **Test** **(2)** for compare, then click on **Create pull request** **(3)**.

   ![](../media/ex6-task1-20.png)

1. In the GitHub browser tab and select the **Pull requests** tab.

1. Open the PR created from the **Test** branch and select **Merge pull request**.

1. Click on the **Actions** tab and then notice that `AI Code Reviewer` workflow has been automatically initiated. Ensure that the workflow does not fail. If so, there may be some vulnerabilities in the code within the recent pull request.  

   ![](../media/ex6-task1-22.png)

## Exercise 2: Configure and implement AI Security Check for Pull Requests

### Task 1: Create a new GitHub repository secret

1. Sign in to GitHub using the credentials provided in the environment detail tab of the integrated lab environment or via the credentials provided at the beginning of this solution guide.

2. Select the `devsecops` repository that was created as a part of the earlier challenges.

3. Under **Security (1)**, expand **Secrets and variables** **(2)** by clicking the drop-down and select **Actions** **(3)** blade from the left navigation bar. Select the **New repository secret** **(4)** button.

   ![](../media/ex6-task1-23.png)


4. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name** : Enter **OPENAI_TOKEN** **(1)**
   - **Value** : Paste the OpenAI secret value that was created and copied over to the notepad in the previous exercise. **(2)**.

     ![](../media/ex6-task1-24.png)

### Task 2: Configure GitHub Action

1. Login to GitHub and select the `devsecops` repository that was created as a part of the earlier challenges.

2. Select the **Actions (1)** tab from your repository home page and then click on **New Workflow (2)**.

   ![](../media/cl9-t2-s3.png)

3. On the Get Started with GitHub Actions page, select **set up a workflow yourself**.


4. Update the workflow name to **codeql-analysis.yml** ***(1)*** and review the yaml file. Select **Commit changes** ***(2)***, then select **Commit directly to the main branch** ***(3)***, and click on **Commit changes..** ***(4)***.
  
   ![](../media/c2t1s3.png)

   ![](../media/n65.png) 
=======
   ![](../media/cl9-t2-s4.png)

4. In the text box, enter the name `ai-security-check-for-pr.yml` for your workflow file.


   ![](../media/cl6-ex2-t2-s5.png)

5. Copy and paste the following action workflow into the Edit new file tab:

   ```
   name: AI Security Check for Pull Requests
   

   ![](../media/ex7-task1-5.png)
   
## Exercise 4: CI/CD Pipeline Setup and Infrastructure Deployment

### Task 1: Deploy Infrastructure

1. Log in to your Azure portal with the credentials provided in the **Environment** tab of the integrated CloudLabs Environment.

2. In the global search bar, search for **Static Web Apps (1)** and select **Static Web Apps (2)**.

    ![](../media/ad20.png)

3. Click on **+ Create** to create a new Static Web App.

4. In the **Basics tab** of the **Create Static Web App** page, enter the following details:
   - **Subscription:** Select the available subscription **(1)**.
   - **Resource Group:** Create a new resource group named - **Static-Web-App (2)**.
   - **Name:** `React-Static-Web-App` **(3)**.
   - **Plan type:** Select **Free (4)**.
   - **Source:** Select **GitHub (5)**
   - **GitHub account:** Click on **Click here to login (6)**. Connect to your GitHub account, which has the `devsecops-2` repository with the React application files.
   
      ![](../media/ex7-task1-6a.png)

      ![](../media/ex7-task1-8.png)

      - Click on **Authorize AzureAppService**.

        ![](../media/n68.png)

      - Provide the **GitHubUserPassword (1)** and then click on **Confirm (2)**

        ![](../media/ad22.png)

   - **Organization:** Select your assigned Github organization **(7)**.
   - **Repository:** Select `devsecops-2 <did>` **(8)**.
   - **Branch:** `Main` **(9)**.
   - **Build presets:** Search for and select **React (detected) (10)**.
   - **App location:** `/` **(11)**.

      >**Note:** `/` refers to the root directory of the GitHub repository. Ensure that the location is specified appropriately as per your GitHub file structure.
=======
   on:
     pull_request:
       branches:
         - main
   
   jobs:
     ai_security_check_for_pull_requests:
       runs-on: ubuntu-latest
   
       steps:
         - name: Check out repository
           uses: actions/checkout@v2

   
         - name: Set up Node.js
           uses: actions/setup-node@v2
           with:
             node-version: 16
   
         - name: Install dependencies
           run: npm ci
   
         - name: Finding security and privacy code vulnerabilities
           id: ai_security_check
           uses: obetomuniz/ai-security-check-for-pull-requests-action@v1.0.0
           env:
             GH_TOKEN: ${{ secrets.GH_TOKEN }}
             GH_REPOSITORY: ${{ github.repository }}
             GH_EVENT_PULL_REQUEST_NUMBER: ${{ github.event.number }}
             OPENAI_TOKEN: ${{ secrets.OPENAI_TOKEN }}
   
         - name: Comment on pull request
           uses: actions/github-script@v6
           env:
             PR_COMMENT: ${{ steps.ai_security_check.outputs.pr_comment }}
           with:
             github-token: ${{ secrets.GH_TOKEN }}
             script: |
               const prComment = process.env.PR_COMMENT || "No security or privacy issues found.";
               const { data } = await github.rest.issues.createComment({
                 issue_number: context.issue.number,
                 owner: context.repo.owner,
                 repo: context.repo.repo,
                 body: prComment
               });
   ```

6. Commit the changes made to create the workflow file.

   ![](../media/ex6-task1-cm.png)

7. Click on **Commit changes**.

   ![](../media/ex6-cm1.png)

8. Navigate back to the **Test** branch that you created.

    ![](../media/ex6-task1-25u.png)

9. Select the **.github/workflows** folder and click on **ai-code-review.yml**.

10. At the end of the line, add a **space** or press **Enter** to make a change.

11. Create a Pull Request to merge the changes from the **Test** branch to the **Main** branch.

12. Click on the **Actions** tab and then notice that **AI Security Check for Pull Requests** workflow has been automatically initiated. Ensure that the workflow does not fail. If so, there may be some vulnerabilities within the recent pull request. Refer to the run details for the GitHub Actions that have failed.

    ![](../media/ex6-task1-26.png)



## Success criteria:
To complete this challenge successfully:

- Successful implementation of the `AI Code Review Action` and generation of of review comments based on the AI's response and added to the pull request.
- Successful implementation of the `AI Security Check for Pull Requests` and generation of comments to the pull requests based on AI's analysis of the code.

## Additional Resources:

- Refer to [Overview of Microsoft Defender for Cloud devsecops Security](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devsecops-introduction) for reference.
- Refer to [Configure the Microsoft Security devsecops GitHub action](https://learn.microsoft.com/en-us/azure/defender-for-cloud/github-action) for reference.
- Refer to [Connect your GitHub Environment to Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-github) for reference.
