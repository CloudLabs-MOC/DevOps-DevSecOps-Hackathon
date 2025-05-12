# Challenge 09: Implement Microsoft Defender for Cloud DevOps Security 

## Introduction

Contoso Traders, an e-commerce platform, is committed to delivering secure and efficient software solutions. In this challenge, as a DevSecOps engineer, you are responsible for ensuring the security of your applications throughout the development lifecycle. Your organization has recently adopted Microsoft Defender for Cloud to enhance the security posture of your DevOps pipelines.

Your task is to implement Microsoft Defender for Cloud DevOps security measures by configuring the necessary GitHub actions within your created GitHub repository, viewing the scanned results, and connecting your GitHub environment to Microsoft Defender for Cloud.

This is the solution guide, which provides all the specific, step-by-step directions needed to do the task.

## Solution Guide

### Accessing the Azure Portal

1. To access the Azure Portal, open the Edge browser from inside the environment and navigate to the **[Azure Portal](https://portal.azure.com)**.

1. On the **Sign in to Microsoft Azure** tab, you will see a login screen. Enter the following email/username, and then click on **Next**. 
   * **Email/Username**: <inject key="AzureAdUserEmail"></inject>
        
1. Now enter the following password and click on **Sign in**.
   * **Password**: <inject key="AzureAdUserPassword"></inject>
     
1. If you see the pop-up **Stay Signed in?**, click No.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

## Task 1: Connect GitHub Environment to Microsoft Defender for Cloud

In this task, you will connect your GitHub organizations on the **Environment settings** page in Microsoft Defender for Cloud. This page provides a simple onboarding experience to auto-discover your GitHub repositories. By connecting your GitHub organizations to Defender for Cloud, you extend the security capabilities of Defender for Cloud to your GitHub resources.

   - **Foundational Cloud Security Posture Management (CSPM) features**: You can assess your GitHub security posture through GitHub-specific security recommendations.

   - Defender CSPM features: Defender CSPM customers receive code to cloud contextualized attack paths, risk assessments, and insights to identify the most critical weaknesses that attackers can use to breach their environment. Connecting your GitHub repositories will allow you to contextualize DevOps security findings with your cloud workloads and identify the origin and developer for timely remediation.

1. From the Azure Portal Dashboard, search for and select **Microsoft Defender for Cloud**.

   ![](../media/cl9-t1-s1.png)

1. In the left pane , expand **Management (1)**  and then select **Environment settings (2).**

   ![](../media/ex9-1.png)

3. To add a new environment, perform the following steps:
   
    - In the **Microsoft Defender for Cloud | Environment settings** page, click on **+ Add environment (1)**.
    - Select **GitHub (2)** from the list of options.
  
      ![](../media/ex9-2.png)

5. Within the **GitHub Connection** page, enter the following details:
   
    - **Connector name:**  GitHub-Connector **(1)**
    - **Subscription:** Select the existing subscription from the list **(2)**.
    - **Resource group:** Select the resource group over which you would want to implement the GitHub connection **(3)**.
    
      >**Note:** The subscription/resource group is the location where Defender for Cloud creates and stores the GitHub connection.
  
    - **Location:** Same location as that of the selected resource group **(4)**.
    - Click on **Next: Configure access > (5)**.
  
      ![](../media1/cl9-t1-s3.png)

7. Within the **Configure access** tab, click on **Authorize** to give permissions to the DevOps security app to access your resources.

   ![](../media1/cl9-t1-s5.png)

8. Authorize the permission needed by clicking on **Authorize Microsoft Security DevOps** within the pop-up and ensure that the authorization is successful.

   ![](../media/cl9-t1-s6.png)

   ![](../media1/cl9-t1-s6-b.png)

    >**Note:** After authorization, if you wait too long to install the DevOps security GitHub application, the session will time out and you'll get an error message.

9. Select **Install** to install the DevOps security app on your repository/repositories.

   ![](../media1/cl9-t1-s7.png)

1. You will be prompted to select you GitHub account.

    ![](../media/ex9-3.png)

1. Click on **Install**.

   ![](../media/ex9-4.png)
   
1. Ensure that it has been installed successfully.

   ![](../media1/cl9-t1-s8.png)

11. For **Edit connector account**, select one of the following:
    -  Select **All existing and future organizations (1)** to auto-discover all repositories in GitHub organizations where the DevOps security GitHub application is installed.
    -  Click on **Next: Review and generate > (2)**.
  
    >**Note:** The **All existing and future organizations** option is used to auto-discover all repositories in GitHub organizations where the DevOps security GitHub application is installed and future organizations where the DevOps security GitHub application is installed.

      ![](../media/ex9-8.png)

11. On the **Review and generate** tab, click on **Create** to successfully create the GitHub connection.

12. When the process finishes, the GitHub connector appears on your **Environment settings** page.

    ![](../media/ex9-7.png)

>**Note:** The Defender for Cloud service automatically discovers the organizations where you installed the DevOps security GitHub application.

### Task 2: Configure the Microsoft Security DevOps GitHub Action

Microsoft Security DevOps is a command-line application that integrates static analysis tools into the development lifecycle. Security DevOps installs, configures, and runs the latest versions of static analysis tools such as SDL, security, and compliance tools. Security DevOps is data-driven with portable configurations that enable deterministic execution across multiple environments.

1. Sign in to GitHub using the credentials provided in the environment detail tab of the integrated lab environment.

2. Select the `devsecops` repository that was created as a part of the earlier challenges.

3. Select the **Actions (1)** tab from your repository home page and then click on **New Workflow (2)**.

   ![](../media/cl9-t2-s3.png)

4. On the Get Started with GitHub Actions page, select **set up a workflow yourself**.

   ![](../media/cl9-t2-s4.png)

5. In the text box, enter the name `msdevopssec.yml` for your workflow file.

   ![](../media/cl9-t2-s5.png)

6. Copy and paste the following action workflow into the Edit new file tab:

    ```
    name: MSDO windows-latest
    on:
      push:
        branches:
          - main
    
    jobs:
      sample:
        name: Microsoft Security DevOps Analysis
    
        # MSDO runs on windows-latest.
        # ubuntu-latest also supported
        runs-on: windows-latest
    
        steps:
    
          # Checkout your code repository to scan
        - uses: actions/checkout@v3
    
          # Run analyzers
        - name: Run Microsoft Security DevOps Analysis
          uses: microsoft/security-devops-action@latest
          id: msdo
          with:
          # config: string. Optional. A file path to an MSDO configuration file ('*.gdnconfig').
          # policy: 'GitHub' | 'microsoft' | 'none'. Optional. The name of a well-known Microsoft policy. If no configuration file or list of tools is provided, the policy may instruct MSDO which tools to run. Default: GitHub.
          # categories: string. Optional. A comma-separated list of analyzer categories to run. Values: 'secrets', 'code', 'artifacts', 'IaC', 'containers. Example: 'IaC,secrets'. Defaults to all.
          # languages: string. Optional. A comma-separated list of languages to analyze. Example: 'javascript,typescript'. Defaults to all.
          # tools: string. Optional. A comma-separated list of analyzer tools to run. Values: 'bandit', 'binskim', 'eslint', 'templateanalyzer', 'terrascan', 'trivy'.
    
          # Upload alerts to the Security tab
        - name: Upload alerts to Security tab
          uses: github/codeql-action/upload-sarif@v2
          with:
            sarif_file: ${{ steps.msdo.outputs.sarifFile }}
    
          # Upload alerts file as a workflow artifact
        - name: Upload alerts file as a workflow artifact
          uses: actions/upload-artifact@v3
          with:  
            name: alerts
            path: ${{ steps.msdo.outputs.sarifFile }}
    ```

7. Select **Commit changes**.

   ![](../media/ex9-5.png)

8. Click on **Commit changes**.

   ![](../media/ex9-6.png)

9. Select **Actions** and verify the new action is running.

   ![](../media/cl9-t2-s9.png)

### Task 3: Investigate and Remediate

1. Sign in to GitHub where the `devsecops` repository was created. 

2. Click on the **Security (1)** tab from your repository overview page and then select **Code scanning (2)** under *Vulnerability alerts*.

   ![](../media/cl9-t3-s2.png)

3. From the dropdown menu, select **Filter by tool**.

  >**Note:** Code scanning findings will be filtered by specific MSDO tools in GitHub. These code scanning results are also pulled into Defender for Cloud recommendations.

## Success criteria:
To complete this challenge successfully:

- Appropriate integration and configuration of Microsoft Security DevOps GitHub Action.
- Successful connection of GitHub environment to Microsoft Defender for Cloud.

## Additional Resources:

- Refer to [Overview of Microsoft Defender for Cloud DevOps Security](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction) for reference.
- Refer to [Configure the Microsoft Security DevOps GitHub action](https://learn.microsoft.com/en-us/azure/defender-for-cloud/github-action) for reference.
- Refer to [Connect your GitHub Environment to Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-github) for reference.
