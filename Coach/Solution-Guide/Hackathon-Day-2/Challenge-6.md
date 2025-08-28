# Challenge 06: Resilience Testing using Azure Load Testing & Azure Chaos Studio

## Introduction

This challenge centers around Azure Load Testing and Azure Chaos Studio, empowering you to perform performance tests and enhance application resilience. In the modern digital landscape, guaranteeing optimal performance during heavy loads and fortifying against disruptions is essential. Through Azure's tools, you'll gain insights into proactive issue detection and methods to reinforce your applications.

This is the solution guide that contains all of the comprehensive, step-by-step directions needed to finish the challenge.

## Solution Guide

## Task 1: Setting Up Azure Load Testing

In this task, you'll create an Azure Load Testing instance and run a test using a JMeter file.

1. In the Azure Portal, navigate to the **contoso-traders-rg<inject key="DeploymentID" enableCopy="false" /> (1)** resource group and select the **Endpoint** resource with the name  **contoso-traders-ui2<inject key="DeploymentID" /> (2)**.

   ![](../media/ex5-task1-1.png)

1. From the overview of the **contoso-traders-ui2<inject key="DeploymentID" enableCopy="false" />** endpoint, copy the **Endpoint hostname** and paste it into the notepad for later use in the task.

   ![](../media/cl5-t1-s2.png)

1. To create an Azure Load Testing service, within the global search bar of the Azure Portal, search for and select **Azure Load Testing**.

   ![](../media/loadtesting.png)

1. After the resource is created, click on Go to Resource. In the left-hand pane, expand **Tests (1)**, then select **Tests (2)**. Click on **+ Create (3)** and choose **Create a URL-based test (4)**.

   ![](../media/ex5-task1-3.png)

1. On the **Create a URL-based test** page, under the Basics tab, uncheck **Enable advanced settings** **(1)** to reveal the Test URL setting. Paste the **Endpoint URL** a copied in point 2 as **Test URL** **(2)**, leave the rest as default, and then click on **Review + create (3)**, followed by **Create**.

   ![](../media/url-load-test-1.png)

1. Once the test run starts, wait until it completes. When the test run finishes, the status will update to **Done**. At this point, you’ll be able to view the Client-side metrics. Explore the given metrics output.

   >**Note:** This process may take up to 30 minutes to complete.

   ![](../media/ex5-task1-4.png)

   ![](../media/ex5-task1-5.png) 
   
   **Note**: In case the test fails due to `The test was stopped due to a high error rate, check your script and try again. This is expected, as sometimes the load on the application exceeds the defined throughput.
     
## Task 2: Create an experiment and target using Azure Chaos Studio

In this task, your objective is to incorporate Targets and establish an Experiment within Azure Chaos Studio. This process aims to assess the resilience of the web application we developed by introducing real faults and observing how our applications react to real-world disruptions.

1. In the Azure Portal, search for **Azure Chaos Studio (1)** and then click on it from the search results **(2)**.
   
   ![](../media/Ex6-T2-S1.1.png)

1. In the **Azure Chaos Studio**, Expand **Experiment management (1)** on the left menu and select **Targets (2)**.

   ![](../media/ex5-task2-1.png)
      
1. From the drop-down menu, select the **contoso-traders-rgXXXXXX** resource group.
 
   ![](../media/ex5-task2-2.png)
     
1. Click on the **contoso-traders-aks<inject key="DeploymentID" enableCopy="false" />** **(1)** **Kubernetes service** instance, and from the drop-down for **Enable Targets** **(2)**, choose **Enable service-direct targets (All resources)** **(3)**.

   ![](../media/ch61u.png)
     
1. Click on **Review + Enable**.

   ![](../media/ch62u.png)

1. Then click on **Enable** to Enable service-direct targets. 
   
   ![](../media/enable.png)

1. Wait for the deployment to be completed.  

1. In the Azure Portal search for **Azure Chaos Studio** ***(1)*** and then click on it from the search results ***(2)***.
   
   ![](../media/Ex6-T2-S1.1.png)
    
1. Once the target is enabled, select **Experiments** ***(1)*** on the left, click the **+ Create** ***(2)*** drop-down, and select **New experiment** **(3)** .
 
   ![](../media/ex6-task3-step9.png)
 
1. On the **Create an experiment** page, under the **Basics** tab, provide the following values and select **Next: Permissions >** ***(4)***.

    - Subscription: Select the default subscription ***(1)***
    - Resource Group: **contoso-traders-rgXXXXXX** **(2)**
    - Name: **contoso-chaos-XXXXXX** ***(3)***
    - Region: Leave it to default 
 
      ![](../media/experiment.png)
   
1. On the **Permissions** page, leave the default selection and select **Next: Experiment designer >**.

   ![](../media/ch63u.png)
 
1. On the **Experiment designer** page select **+ Add action (1)** and choose **Add fault (2)**.

   ![](../media/Ex6-T2-S7.3.png)
 
1. On the **Add fault** page, select the following and select **Next: Target resources>** **(4)**.
   
   - Faults: **AKS Chaos Mesh Pods Chaos(deprecated)** ***(1)***

   - Duration (minutes): **5** ***(2)***

   - jsonSpec: Leave it to default ***(3)***
     
     ![](../media/2dgn61.png)
     
1. On **Target resources**, select **Manually select from a list** **(1)** option under the **Select target resources** , select the **contoso-traders-aks<inject key="DeploymentID" enableCopy="false" />** ***(2)*** resource, and **Add** ***(3)***.
  
   ![](../media/ex6-task3-step14.png)
  
1. Click on **Review + create**.
  
   ![](../media/upd-review.png)
   
1. On the **Review + create** page, click on **Create**.
    
1. Navigate back to the **contoso-traders-aksXXXXXX** container instance and select **Access control (IAM) (1)**, click on **+ Add (2)**, and select **Add role assignment (3)**. 
  
   ![](../media/2dgn121.png)

1. In the **Add role assignment** page, under the **Role** tab, select **Privileged administrator roles**  **(1)**. Select **Owner** **(2)** and then **Next** **(3)**.
  
   ![](../media/ex6-task3-step18.png)
  
1. Next, on the **Members** tab, select **Managed identity (1)**  for **Assign access to** , click on **+ Select members (2)**  on the **Select managed identities** choose **Chaos Experiment (3)** for **Managed identity**, select the experiment **contoso-chaos-<inject key="DeploymentID" enableCopy="false" /> (4)**, click on **Select (5)**, and click on **Next** **(6)**.  
   
   ![](../media/ex6-task3-step19.png)
  
1. Next, on the **Conditions** tab, select **What user can do** as **Allow user to assign all roles** **(1)** and click on **Review + assign** **(2)**.

   ![](../media/dev-9.png)

1. Click on **Review + assign**. 
   
   ![](../media/ex6-ch.png)
      
1. On the Azure Portal, navigate back to the Chaos experiment you created, **contoso-chaos-<inject key="DeploymentID" enableCopy="false" />** and click on **Start**.
  
   ![](../media/ch64u.png)
 
1. Select **Ok** to **Start this experiment** pop-up.

    ![](../media/Ex6-T2-S17.1.png)
       
1. Once the experiment status is **Success** click on **Details** to view the run preview.
 
   ![](../media/2dgn109.png)
 
1. On the **Details** preview page, select **Action (1)** and view the complete details of the run on **Fault details** under **Successful targets (2)**.
 
   ![](../media/ch65u.png)

## Success criteria:
To complete this challenge successfully:

   - Completion of Load Test and Results Analysis: Azure Load Testing is configured, the test runs successfully, and Client-side metrics are reviewed, providing insights into performance under load.
   - Execution of Chaos Experiment: A Chaos Experiment in Azure Chaos Studio is configured with the specified faults, executed successfully, and results are reviewed to confirm resilience.

## Additional Resources:

- Refer to [Continuous validation with Azure Load Testing and Azure Chaos Studio](https://learn.microsoft.com/en-us/azure/architecture/guide/testing/mission-critical-deployment-testing) for reference.
- [What is Azure Chaos Studio?](https://learn.microsoft.com/en-us/azure/chaos-studio/chaos-studio-overview).
- [Load test a website by using a JMeter script in Azure Load Testing](https://learn.microsoft.com/en-us/azure/load-testing/how-to-create-and-run-load-test-with-jmeter-script?tabs=portal).
- [Intro to Chaos Engineering and Azure Chaos Studio](https://pdtit.medium.com/intro-to-chaos-engineering-and-azure-chaos-studio-preview-5e85fff10642).
