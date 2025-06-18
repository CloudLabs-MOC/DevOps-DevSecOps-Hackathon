# Challenge 05: Implementing Monitoring Solutions for Contoso Traders

### Estimated Time: 60 Minutes

## Introduction:

As a Cloud Solutions Engineer, your task is to enhance the monitoring capabilities of the Contoso Traders application hosted on Azure. Monitoring is crucial for maintaining optimal application health, identifying potential issues proactively, and ensuring a seamless user experience. 

In this challenge, you will integrate Azure's monitoring tools—Azure Monitor and Application Insights—into the Azure-based application. You will integrate Azure's monitoring tools—Azure Monitor and Application Insights—into your Azure-based application. Monitor essential metrics, analyze performance data, and gain real-time insights to ensure optimal application health.

## Challenge Objectives:

1. **Setup Monitoring Infrastructure:**

   - Create and set up Application Insights for the Contoso traders application using `monitoringinfra.bicep`.and update **DeploymentID** in the `monitoringinfra.parameters.json` file.

     >**Note:** The `monitoringinfra.bicep` file is 
     located at:
     `C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files`

2. **Dashboard Creation:**
   - Design comprehensive dashboards for real-time visualization of application health and performance metrics.
      - Participants will create visually intuitive dashboards within Azure Monitor or Application Insights, displaying the collected metrics. These dashboards should offer clear insights into the application's health, failed requests, server response time, and availability.

3. **Monitor the application using App Insights:**

   - Monitor and explore the application using the dashboard that you created in the previous task.

## Success criteria:
To complete this challenge successfully:

- Verify the Monitoring dashboards where data should be populated based on the usage of the Contoso traders application.

## Additional Resources:

- Refer to [Application Insights Overview](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) for reference.
- [Application Insights for ASP.NET Core applications](https://learn.microsoft.com/en-us/azure/azure-monitor/app/asp-net-core?tabs=netcorenew%2Cnetcore6).
- Refer to [Azure Monitor vs Application Insights](https://azurelib.com/azure-monitor-vs-application-insights/) for reference.

## Conclusion
Congratulations on completing the **Implementing Monitoring Solutions for Contoso Traders** challenge! You learned about the creation and configuration of Azure Monitoring infrastructure for a cloud-hosted application. In the next challenge, you will focus on testing the resiliency and availability of the application.
