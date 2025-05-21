# Challenge 09: Securing DevOps with Microsoft Defender for Cloud

### Estimated Time: 30 minutes

### Introduction:
Contoso Traders, an e-commerce platform, is committed to delivering secure and efficient software solutions. In this challenge, as a DevSecOps engineer, you are responsible for ensuring the security of your applications throughout the development lifecycle. Your organization has recently adopted Microsoft Defender for Cloud to enhance the security posture of your DevOps pipelines.

Your task is to implement Microsoft Defender for Cloud DevOps security measures by configuring the necessary GitHub actions within your created GitHub repository, viewing the scanned results, and connecting your GitHub environment to Microsoft Defender for Cloud.

## Challenge Objectives:

>**Note:** The GitHub account provided whose credentials would be available in the environment details tab, has GitHub Enterprise with GitHub Advanced Security enabled for the ease of execution of this challenge.

1. **Connect GitHub Environment to Microsoft Defender for Cloud:**
   - Connect your GitHub environment to Microsoft Defender for Cloud.
   - Extend the security capabilities of Defender for Cloud to your GitHub resources by enabling the **Cloud Security Posture Management (CSPM) features**.
   - Ensure that the Microsoft Defender for cloud is configured such that it auto-discovers all repositories in GitHub organizations and any future organizations where the DevOps security GitHub application is installed.

2. **Configure Microsoft Security DevOps GitHub Action:**
   
   - Integrate the Microsoft Defender for Cloud GitHub Action into the workflow of your GitHub repository.
   - Create a `.github/workflows/msdevopssec.yml` file in your repository to perform static code analysis, vulnerability scanning, and compliance checks.

3. **Investigate and Remediate:**
   - Trigger the GitHub Action workflow created in the previous challenge objective to run Microsoft Defender for Cloud scans.
   - Review, identify, and understand the security findings and recommendations provided by Microsoft Defender for Cloud.
   - Implement fixes or enhancements to address the security findings identified during the scan.
   - Ensure that the GitHub Action workflow passes successfully after addressing the security issues.
  
> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com We are available 24/7 to help

<validation step="0531cfee-4c15-4022-9ab7-1b691f7b6203" />

## Success criteria:
To complete this challenge successfully:

- Appropriate integration and configuration of Microsoft Security DevOps GitHub Action.
- Successful connection of the GitHub environment to Microsoft Defender for Cloud.

## Additional Resources:


- Refer to [Overview of Microsoft Defender for Cloud DevOps Security](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction) for reference.
- Refer to [Configure the Microsoft Security DevOps GitHub action](https://learn.microsoft.com/en-us/azure/defender-for-cloud/github-action) for reference.
- Refer to [Connect your GitHub Environment to Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-github) for reference.
- Refer to [Configure the Microsoft Security DevOps GitHub action](https://learn.microsoft.com/en-us/azure/defender-for-cloud/github-action) for reference.


## Conclusion
Congratulations on completing the **Securing DevOps with Microsoft Defender for Cloud** challenge! Through this challenge, you have seamlessly integrated and configured Microsoft Defender for Cloud within a DevOps context, ensuring a secure and resilient software development lifecycle.

Congratulations! You have successfully completed all the challenges.

