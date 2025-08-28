# Challenge 02: GitHub Advanced Security - Implement Code Security Enhancements

### Estimated Time: 60 minutes

### Introduction:
In this previous challenge, you successfully hosted the application using the GitHub repository and GitHub Actions for Continuous Integration and Continuous Delivery. In this challenge, you are a DevSecOps engineer tasked with ensuring the security of the Contoso Traders application hosted on GitHub. In this challenge, your goal is to mitigate risks in dependencies and secure sensitive data using advanced security features provided by GitHub. 

You need to focus on completing the implementation of the below-mentioned security features.

**Code Scanning**: Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown on GitHub. You can use code scanning to find, triage, and prioritize fixes for existing problems in your code. Code scanning also prevents developers from introducing new problems

**CodeQL**: CodeQL is the code analysis engine developed by GitHub to automate security checks. You can analyze your code using CodeQL and display the results as code-scanning alerts.

**Repository security advisories**: Repository security advisories allow repository maintainers to privately discuss and fix a security vulnerability in a project. 

## Accessing GitHub

1. To access and login to GitHub, open the Edge browser from inside the environment and navigate to **[GitHub](https://github.com/)**.

2. Sign in to GitHub by clicking on the **Sign in** button in the top right corner of the GitHub home page.

3. On the **Sign into GitHub tab**, you will see a login screen. Enter the following email/username and then click on **Next**.

   - **Email/Username:** <inject key="GitHubUsername"></inject>

1. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="GitHubPassword"></inject>


## Challenge Objectives:

> **Note**: Use the same GitHub repository that you created in the last challenge.

1. **Implement Code Scanning and CodeQL:**
 
   - Enable Code scanning for the repository.
   - Configure CodeQL analysis in the workflow to the existing GitHub.
   - Use **Advanced** option when creating a CodeQL Analysis YAML file.
   - Resolve the generated alerts, if any

<validation step="32952c71-7fea-4af1-a5f5-7200dbad84ef" />  

## Success criteria:
To complete this challenge successfully:

   - Verify the implementation of setting up Code Scanning and CodeQL via alerts.
   - Configure the Repository security advisories feature and create temporary private fork.


## Additional Resources:

Here are a few documentation and guides to assist you in completing the challenge.
- [About GitHub's Advanced Security](https://docs.github.com/en/code-security/getting-started/github-security-features)
- [About GitHub's Advanced Security](https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql)
- [Code Scanning with GitHub CodeQL](https://learn.microsoft.com/en-us/training/modules/code-scanning-with-github-codeql/)

## Conclusion
Congratulations on successfully completing the **GitHub Advanced Security - Implement Code Security Enhancements** challenge. You've taken crucial steps to ensure the security and integrity of your codebase, especially when dealing with sensitive customer data. As you continue developing the e-commerce platform, consider regularly reviewing and updating your security measures. Stay informed about new security features and best practices offered by GitHub to ensure that your repository remains resilient to emerging threats. In this next challenge, you will explore and implement more GitHub advanced security features.

