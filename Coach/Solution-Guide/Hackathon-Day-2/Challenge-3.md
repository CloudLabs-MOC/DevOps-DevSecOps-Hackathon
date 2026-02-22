# Challenge 03: GitHub Advanced Security - Dependency Management and Secret Scanning

## Introduction

In this challenge, attendee/user will continue to focus on implementing crucial GitHub Advanced security features like GitHub Dependabots and Secret Scanning.

This is the solution guide, which provides all the specific, step-by-step directions needed to do the task.

## Solution Guide

### Task 1: Configure Dependabot Alerts:

In this task, you will use Dependabot to track the versions of the packages we use in our GitHub repository and create pull requests to update packages for us.

1. In the GitHub repository, navigate to the **Settings** ***(1)*** tab and select the **Code security** ***(2)*** under Security from the side blade.

   > **Note**: Enabling the `Dependabot security updates` will also automatically enable `Dependency graph` and `Dependabot alerts`.

   ![](../media1/advance-security.png)

1. On the **Advanced Security** page, under the **Dependabot** section, ensure that **Dependabot alerts** is set to **Enabled** **(1)**.

   ![](../media1/security-updates-deploymentbot.png)

1. In the pop-up to enable Dependabot alerts, click **Enable**.

   ![](../media1/deploymentbot-enabled.png)

1. On the **Advanced Security** page, under the **Dependabot** section, ensure that **Dependabot security updates** is set to **Enabled** **(1)**.

   ![](../media1/deploymentbot-security.png)

   > **Note**: The alerts for the repository may take some time to appear. The rest of the steps for this task rely on the alerts being present. You can continue with the next exercise, as this is an independent task and doesn't affect the lab. Please visit this task later and complete it.

1. In the GitHub repository, to observe Dependabot issues, navigate to the **Security** **(1)** tab and select the **View Dependabot alerts** **(2)** link.

   ![](../media1/n36.png)

1. Under the Dependabot alerts blade, you will be able to see the generated alerts.

   ![GitHub Dependabot alerts in the Security tab.](../media/n67.png "GitHub Dependabot alerts")

1. Sort the Dependabot alerts by `Package name`. Under the **Package** **(1)** dropdown menu, search for **nanoid** **(2)** by typing in the search box and selecting **nanoid** **(3)** vulnerability.

   ![](../media/n38.png)

1. In the **nanoid** package alert, select the **predicted results in NanoID generation when given non-integer values**.

   ![](../media1/filtered-nanoid.png)

1. On the **Predictable results in nanoid generation when given non-integer values** alert, click **Create Dependabot security update**, and wait a few minutes for the pull request to be generated.

1. In the GitHub repository, navigate to the **Pull Requests** **(1)** tab, locate the Dependabot security patch pull request **(2)**, and merge it into your main branch.

   ![List of Pull Requests.](../media1/pull-requestsdependobot.png)
  
1. In the **Pull requests** page, scroll down and click on **Merge pull request**, followed by **Confirm merge**. 

    ![](../media/n42.png)

    > **Note**: In case you see any errors with the merge request, retry steps 4 to 6 by selecting any other Dependabot alert.

1. Pull the latest changes from your GitHub repository to your local GitHub folder. The below commands should run in Command prompt.

   ```pwsh
   cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files  # This path may vary depending on how you set up your lab files repository
   git pull
   ```
   
## Task 2: Implement Secret Scanning:

In this task, you'll explore how secret scanning works and how it generates alerts. GitHub scans repositories for known types of secrets to prevent fraudulent use of secrets that were accidentally committed.

1. In the GitHub repository, navigate to the **Settings** ***(1)*** tab and select the **Code security** ***(2)*** under Security from the side blade.

   > **Note**: Enabling the `Dependabot security updates` will also automatically enable `Dependency graph` and `Dependabot alerts`.

     ![](../media1/advance-security.png)
    
1. On the **Advanced Security** page, scroll down to the **Code security** section and next to **Secret protection**, click **Enable (1)**.

   ![](../media1/n44.png)   

1. In the **Enable Secret Protection** pop-up, click the **Enable Secret Protection** button.

   ![](../media1/enable-secret-protection.png)
    
1. In the  GitHub repository, navigate back to **Code** and click on the **src** folder.

   ![](../media1/n45.png)    
   
1. In the **src** folder, click **Add file (1)** and select the **Create new file (2)** option.

   ![](../media/n46.png)    
   
1. Add a new file and provide the name **build.docker-compose.yml (1)**. Then, add the code mentioned below and commit the file. After that, commit the changes again. Here, you will expose the **Application ID** of a service principal.
   
   ```
   version: "3.4"
   services:
   api:
      build: ./ContosoTraders.Ui.Website/
      app id: 36540dcd-7bc3-4e16-90ca-4decb9ff8c36
      app secret: i1R8Q~Hn8dHn86VlWE7xJtLR4FKTIcQBXcebqcv4
   web:
      build: ./ContosoTraders.Api.Products
   ```
   
   ![](../media/n47.png)  

1. In the **Commit changes** pop-up, click **Commit changes**.

   ![](../media/n48.png) 

1. You will get a pop up window of Secret scanning found Azure Active Directory Application secret found alert. You can either **Allow secret** by selecting the options available i.e It's used in tests, It's a false positive or I'll fix it later or **Cancel** it.

   ![](../media/devops-devsecops-new-11.png) 

1. In the GitHub repository, navigate to the **Security** **(1)** tab, expand **Secret scanning** **(2)** and select **Default** **(3)**, ensure the filter is set to **is:open** **(4)**, and review the detected **Azure Active Directory Application Secret** **(5)** alert. This is how the Secret scanning feature works and generates alerts to notify you.

   ![](../media1/n49.png) 

## Success criteria:
To complete this challenge successfully:

- Successful implementation of GitHub Dependabots for identifying and addressing security vulnerabilities.
- Setup secreting scanning and updated the code base to resolve the alerts.

## Additional Resources:

- Refer to [Secret Scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) for reference.
- Refer to [GitHub Dependabot](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) for reference.
