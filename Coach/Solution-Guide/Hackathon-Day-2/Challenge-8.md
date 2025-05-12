# Challenge 08: Security Compliance as Code

## Introduction

In this challenge, you are a DevOps engineer responsible for ensuring the security compliance of your organization's Azure resources. Your task is to implement and enforce security policies using Azure Policy over the Azure resources and integrate compliance scanning into the GitHub CI/CD pipelines for your Azure projects.

This is the solution guide, which provides all the specific, step-by-step directions needed to do the task.

## Solution Guide

## Exercise 1: Implement Security Policies using Azure Policy

### Task 1: Assign a Built-In policy

In this task, you will enforce compliance with Azure Policy by assigning a policy definition. A policy definition defines under what condition a policy is enforced and what effect to take. In this solution, you will assign the built-in policy definition called **Inherit a tag from the resource group if missing** to add the specified tag with its value from the parent resource group to new or updated resources missing the tag and then implement a new custom policy for the resources that have been deployed with the specific region.

1. Go to the Azure portal to assign policies. Search for and select **Policy**.

   ![](../media/cl8-ex1-t1-s1.png)

2. Expand **Authoring (1)** and Select **Assignments (2)** on the left side of the Azure Policy page. An assignment is a policy that has been assigned to take place within a specific scope.

   ![](../media/ex8-task1-1.png)

3. Select **Assign Policy** from the top of the **Policy | Assignments** page.

   ![](../media/ex8-task1-2.png)

4. On the **Assign Policy** page and **Basics** tab, perform the following steps:
   
   - Select the **Scope** by selecting the **ellipsis** **(1)** and selecting either a management group or subscription. Optionally, select a **Resource Group (2)**. A scope determines what resources or grouping of resources the policy assignment gets enforced on.
   - Click on **Select (3)** at the bottom of the Scope pane.

     ![](../media/ex8-task1-3.png)

6. Resources can be excluded based on the **Scope**. **Exclusions** start at one level lower than the level of the **Scope**. **Exclusions** are optional, so leave it blank for now.

7. Select the **Policy definition** ellipsis to open the list of available definitions. You can filter the policy definition Type to Built-in to view all and read their descriptions.

   ![](../media/ex8.png)

8. Select **Inherit a tag from the resource group if missing**. If you can't find it right away, type **Inherit a tag from the resource group if missing (1)** into the search box and then press ENTER. Select the Policy result fetched **Inherit a tag from the resource group if missing (2)** and then Click on **Add (3)** at the bottom of the **Available Definitions** page once you have found and selected the policy definition.

   ![](../media/ex8-task1-5.png)

9. The **Assignment name (1)** is automatically populated with the policy name you selected, but you can change it. For this example, leave **Inherit a tag from the resource group if missing**. You can also add an optional **Description (2)**. The description provides details about this policy assignment.

10. Leave **Policy enforcement** as **Enabled (3)**. When Disabled, this setting allows testing the outcome of the policy without triggering the effect.

    ![](../media/ex8-task1-10.png)
   
12. Select the **Parameters (1)** tab at the top of the wizard.

13. For **Tag Name**, enter **Environment (2)**.

    ![](../media/ex8-task1-6.png)

15. Select the **Remediation (1)** tab at the top of the wizard.

16. Leave **Create a remediation task (2)** unchecked. This box allows you to create a task to alter existing resources in addition to new or updated resources.

17. **Create a Managed Identity (3)** is automatically checked since this policy definition uses the modify effect. **Permissions** is set to Contributor automatically based on the policy definition.

    ![](../media/ex8-task1-7.png)
     
18. Select the **Non-compliance messages (1)** tab at the top of the wizard.

19. Set the **Non-compliance message** to **This resource doesn't have the required tag (2)**. This custom message is displayed when a resource is denied or for non-compliant resources during regular evaluation.

    ![](../media/ex8-task1-8.png)

21. Select the **Review + create (1)** tab at the top of the wizard.

22. Review your selections, then select **Create (2)** at the bottom of the page.

    ![](../media/ex8-task1-9.png)

### Task 2: Implement a new custom policy

Now that you've assigned a built-in policy definition, you can do more with Azure Policy. Azure Policy enables organizations to enforce governance controls and compliance standards. This guide focuses on implementing a custom policy to restrict resource deployments to the East US region within a designated resource group. By leveraging Azure Policy, organizations can ensure compliance, mitigate risks, and streamline resource management effectively.

1. Select **Definitions (1)** under **Authoring** in the left side of the Azure Policy page. Then click on **+ Policy definition (2)** at the top of the page.

   ![](../media/ex8-task1-11.png)

1.  This button opens to the **Policy definition** page and enter the following information:
      - Select the **Definition location** **(1)** by selecting the ellipsis and select the Subscription and click on **Select**. A scope determines what resources or grouping of resources the policy assignment gets enforced on.
      - **Name:** Restrict deployment to East US region **(2)**
      - **Description:** This policy ensures that resources are deployed only in the East US region. **(3)**
      - **Category:** Create a new catrgory named **Region**.  **(4)**

        ![](../media/ex8-task1-12.png)

1. Copy the following JSON code and then update it for your needs with:

   - The policy parameters.
   - The policy rules/conditions, in this case - location set to East US.
   - The policy effect, in this case - **Deny**.

   ```
   {
       "policyRule": {
          "if": {
            "not": {
              "field": "location",
              "in": ["eastus"]
            }
          },
          "then": {
            "effect": "deny"
          }
        }
   }
   ```

   >**Note:** The **field** property in the policy rule must be a supported value. An example of alias might be `Microsoft.Compute/VirtualMachines/Size` and `Microsoft.Resources/resourceGroups/location`.

1. Once the JSON code is updated. Click on **Save.**

   ![](../media/ex8-0.1.png)

1. This will navigate you to the **Restrict deployment to East US region** Page.
  
   >Note: If you are not on the **Restrict deployment to East US region** Page perform Step 6 and Step 7

   ![](../media/ex8-task1-14.png)

1. Select **Policy | Definitions** from the top of the Azure Policy page.

1. In the **Policy | Definition** search bar Search **Restrict deployment to East US region (1)** and select for **Restrict deployment to East US region (2)**. 

   ![](../media1/Ch8E1T2S7-3101.png)

   >**Note :** It may take some time for the created policy definition to reflect.

1. In **Restrict deployment to East US region** page, click on **Assign policy**. 

   ![](../media1/assign-custom-policy.png)

1. In the **Basics** page of Restrict deployment to East US region, **Exclusions** start at one level lower than the level of the **Scope**. **Exclusions** are optional, so you can leave it blank for now. click on **Review + Create** followed by **Create**.   

   ![](../media1/custom-policy-basic.png)

## Exercise 2: Integrate Compliance Scanning in CI/CD pipeline

### Task 1: Create a GitHub Secret

1. Navigate back to the `devsecops` repository to create GitHub secrets, in your GitHub lab files repository, and click on the **Settings** tab.

      ![](../media/cl1-t2-s2.png)

2. Navigate to **Environment Details** **(1)** tab of the integrated lab environment, click on **Service Principal Details** **(2)**, and copy the **Subscription ID**, **Tenant ID (Directory ID)**, **Application ID (Client ID)**, and **Secret Key (Client Secret)**.

      ![](../media1/Ch8E2T1S2-3101.png)
   
      - Replace the values that you copied in the below JSON. You will be using them in this step.
      
      ```json
      {
        "clientId": "your-client-id",
        "clientSecret": "your-client-secret",
        "tenantId": "your-tenant-id",
        "subscriptionId": "your-subscription-id",
        "resourceGroup": "your-resource-group"
      }
      ```

   >**Note:** Also ensure to replace `your-subscription-id` and `your-resource-group` within any of the available resources group name with the above secret.

3. Within GitHub, under **Settings (1)**, expand **Secrets and variables** **(2)** by clicking the drop-down and select **Actions** **(3)** blade from the left navigation bar. Select the **New repository secret** **(4)** button.

   ![](../media/ex8-task1-15.png)

4. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name** : Enter **AZURE_CREDENTIALS** **(1)**
   - **Secret** : Paste the service principal details in JSON format **(2)**
   - Click on **Add Secret (3)**
   
     ![](../media1/azure-cred.png)

### Task 2: Implement Azure Policy Compliance Scan

1. In a new browser tab, open ```https://www.github.com/login```. From the **Environment Details** page **(1)**, navigate to **License** **(2)** tab and **copy** **(3)** the credentials. Use the same username and password to log into GitHub.

   ![](../media/dev2.png) 

2. Once logged-in, on the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/2dg1.png "New Repository Creation Form")

3. Select the repository that you created earlier named, `devsecops`.

   ![](../media/cl7-ex3-t1-s3.png)

4. Within a new browser tab, navigate to `https://github.com/marketplace/actions/azure-policy-compliance-scan` to view the **Azure Policy Compliance Scan** GitHub Action.

5. Go back to your `devsecops` GitHub repository.

6. Navigate to `.github/workflows` directory and click on **Create a new file.**.

   ![](../media/ex8-task1-16.png)

1. Create a new file named `complaince-scan.yml`

   ![](../media/ex8-task1-16.1.png)

8. Paste the following code within the workflow file. The below workflow will trigger a policy compliance scan on the resource group. After the scan is complete, it will fetch the compliance state of resources. The action will fail if there are any non-compliant resources.

   ```
   # File: .github/workflows/workflow.yml

   on: push
   
   jobs:
     assess-policy-compliance:    
       runs-on: ubuntu-latest
       steps:
       # Azure Login       
       - name: Login to Azure
         uses: azure/login@v1
         with:
           creds: ${{secrets.AZURE_CREDENTIALS}} 
       
       - name: Check for resource compliance
         uses: azure/policy-compliance-scan@v0
         with:
           scopes: |
             /subscriptions/<Subscription ID>/resourceGroups/<resource-group-name>               
           scopes-ignore: |
             /subscriptions/<Subscription ID>/resourceGroups/<resource-group-name>/providers/microsoft.authorization
        
   ```

   >**Note:** Ensure to Replace the `<Subscription ID>` , `<resource-group-name>` in the above code.

9. To Commit the changes within your repository to successfully create the workflow file. Click on **Commit changes.**

    ![](../media/dev-7.png)

10. Click on **Commit changes**

    ![](../media/ex8-task1-19.png)

11. Head back to the GitHub **Actions (1)** tab and then make sure that the Action named **Compliance Scan (2)** run successfully.

    ![](../media/dev-8.png)

## Success criteria:
To complete this challenge successfully:

- Successful effectiveness of policies in enforcing security compliance.
- Successful integration of compliance scanning into the pipeline.
- Successful setup and execution of the CI/CD pipeline.

## Additional Resources:

- Refer to [Overview of Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/overview) for reference.
- Refer to [Azure Policy Compliance Scan](https://github.com/marketplace/actions/azure-policy-compliance-scan) for reference.
