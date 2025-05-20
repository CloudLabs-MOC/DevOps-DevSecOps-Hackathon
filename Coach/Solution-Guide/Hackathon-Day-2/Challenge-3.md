# Challenge 03: GitHub Advanced Security - Dependency Management and Secret Scanning

## Introduction

In this challenge, attendee/user will continue to focus on implementing crucial GitHub Advanced security features like GitHub Dependabots and Secret Scanning.

This is the solution guide, which provides all the specific, step-by-step directions needed to do the task.

## Solution Guide

### Task 1: Configure Dependabot Alerts:

In this task, you will use Dependabot to track the versions of the packages we use in our GitHub repository and create pull requests to update packages for us.

1. In your lab files GitHub repository, navigate to the **Settings** ***(1)*** tab and select the **Advanced security** ***(2)*** under Security from the side blade. Make sure **Dependabot alerts** is **Enabled** ***(3)***, if not, click on **Enable** to Enable Dependabot alerts. Click on **Enable** ***(4)*** to Enable Dependabot security updates.

   > **Note**: Enabling the `Dependabot security updates` will also automatically enable `Dependency graph` and `Dependabot alerts`.

   ![The GitHub Repository Security Overview tab.](../media/ex3-task1-1a.png "GitHub Repository Security Overview")

   > **Note**: The alerts for the repository may take some time to appear. The rest of the steps for this task rely on the alerts being present. You can continue with the next exercise, as this is an independent task and doesn't affect the lab. Please visit this task later and complete it.

1. To observe Dependabot issues, navigate to the **Security** ***(1)*** tab and select the **View Dependabot alerts** ***(2)*** link.

   ![GitHub Dependabot alerts in the Security tab.](../media/cl3-t1-s2.png "GitHub Dependabot alerts")

1. You should arrive at the `Dependabot alerts` blade in the `Security` tab.

   ![GitHub Dependabot alerts in the Security tab.](../media/cl3-t1-s3.png "GitHub Dependabot alerts")

1. Sort the Dependabot alerts by `Package name`. Under the **Package** ***(1)*** dropdown menu, search for **nanoid** ***(2)*** by typing in the search box and selecting **nanoid** ***(3)*** vulnerability.

   ![Summary of the `handlebars` Dependabot alert in the list of Dependabot alerts.](../media/ch31u.png "`handlebars` Dependabot alert")

1. Select any of the `nanoid` Dependabot alert entries to see the alert details. After reviewing the alert, select **Review security update**.

   ![The `handlebars` Dependabot alert detail.](../media/ch32u.png "Dependabot alert detail")
   
   **Note:** If you see the Create Dependabot Security Update option, click on it. After it is created, select Review security update. 

1. It will Navigate to the **Pull Requests** ***(1)*** tab, Click on **Merge pull request**, followed by **Confirm merge**.

   ![List of Pull Requests.](../media/ch33u.png "Pull Requests")

    
   >**Note**: In case you see any errors with the merge request, retry steps 4 to 6 by selecting any other Dependabot alert.

1. In the LabVM **Start** button, search for **cmd (1)** and select **Command Prompt (2)**.

   ![cmd.](../media/dev1.png "cmd")

1. Pull the latest changes from your GitHub repository to your local GitHub folder.

   ```pwsh
   cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files  
   git pull
   ```

    ![cmd.](../media/dev-2.png "cmd")   

     > **Note:** This path may vary depending on how you set up your lab files repository.
   
## Task 2: Implement Secret Scanning:

In this task, you'll explore how secret scanning works and how it generates alerts. GitHub scans repositories for known types of secrets to prevent fraudulent use of secrets that were accidentally committed.

1. From your GitHub repository, click on the **Settings** tab.

   ![](../media/ch34u.png)
    
1. Select **Advanced security** from the sidebar.

   ![](../media/ex3-task2-1a.png)

1. Scroll down ,make sure **Secret Protection is enabled**.

   ![](../media/ch35u.png)
    
1. Navigate back to **Code (1)** and click on the **src (2)** folder.

   ![](../media/ch36u.png)    
   
1. Click on **Add file (1)** and select the **create new file (2)** option.

   ![](../media/ch37u.png)    
   
1. Add a new file with the name **build.docker-compose.yml (1)**, add the code **(2)** mentioned below and click on **Commit changes (3)** at the right corner. Here, you'll expose the **application ID** of a service principal.

   ```
   version: "3.4"
   services:
   api:
      build: ./ContosoTraders.Ui.Website/
      app id: <Application ID>
      app secret: <Secret key>
   web:
      build: ./ContosoTraders.Api.Products
   ```
   >**Note:** Ensure replace the value of the `<Appication ID>` and `<Secret key>` with the actual values available in your LabVM's **Environment tab** before saving the file.

   ![](../media/ad10.png)

   ![](../media/dev-5.png)   

1. Click on **Commit changes.**

   ![](../media/ex-common.png)

1. If you get the below warning pop up, choose **Its used in tests (3)** and then select **Allow secret (2)**.   

   ![](../media/ad11.png)

1. Then again click on, **Commit changes** twice.   
   
1. Select the **Security (1)** tab and click on **Secret scanning (2)** from the sidebar. Set the **Filter** to  **`closed` (3)**. Here, you'll notice that an alert is generated referring to the same **Application ID** that was exposed in the `build.docker-compose.yml` file **(4)**. This is how the Secret scanning feature works and generates alerts to notify you.

   ![](../media/dev-4.png) 

## Success criteria:
To complete this challenge successfully:

- Successful implementation of GitHub Dependabots for identifying and addressing security vulnerabilities.
- Setup secreting scanning and updated the code base to resolve the alerts.

## Additional Resources:

- Refer to [Secret Scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) for reference.
- Refer to [GitHub Dependabot](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) for reference.
