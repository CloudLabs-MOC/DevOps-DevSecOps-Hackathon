# Challenge 03: GitHub Advanced Security - Dependency Management and Secret Scanning

### Estimated Time: 40 Minutes

### Introduction:

In the previous challenge, you configured a few of the GitHub Advanced security features. In this challenge, as a DevSecOps engineer, your focus is on automating security processes and preventing security vulnerabilities. The Contoso Traders application, hosted on GitHub, will benefit from crucial GitHub Advanced security features like GitHub Dependabots and Secret Scanning.

**Dependabots:** Dependabot security updates are automated pull requests that help you update dependencies with known vulnerabilities. Dependabot version updates are automated pull requests that keep your dependencies updated, even when they don't have any vulnerabilities.

**Secret Scanning:** GitHub secret scanning is a security feature provided by GitHub to help identify and manage sensitive information, such as API keys, tokens, and other credentials, that may have been accidentally committed to a code repository.

## Challenge Objectives:

> **Note:** Use the same GitHub repository that you created in the last challenge.

1. **Configure Dependabot Alerts:**

   -  Use Dependabot and configure it to track the versions of the packages used in your GitHub repository and create pull requests to update packages for us.
   - Track and resolve any of the Dependabot alerts.
  
3. **Implement Secret Scanning:**
   - Enable the Secret Scanning security feature on the existing GitHub repository.
   - Check the working of the feature by exposing the application ID of a service principal and resolving the alerts.
  
## Success criteria:
To complete this challenge successfully:

- Successful implementation of GitHub Dependabots for identifying and addressing security vulnerabilities.
- Set up secret scanning and update the code base to resolve the alerts.

## Additional Resources:

- Refer to [Secret Scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) for reference.
- Refer to [GitHub Dependabot](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) for reference.

## Conclusion
Congratulations on completing the **GitHub Advanced Security - Dependency Management and Secret Scanning** challenge! By addressing critical aspects of sensitive data security, and organization-level security settings, you've significantly strengthened the security posture of your GitHub repository. In the next challenge, you will focus on implementing monitoring over the application.
