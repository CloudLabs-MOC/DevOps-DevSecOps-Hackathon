# Challenge 04: Integrate 'About Us' Page with GitHub Copilot in React Application

## Introduction

Contoso Traders is an e-commerce web application. In this challenge, as a DevOps engineer, your focus is to seamlessly implement and test new features with Copilot, ensuring accuracy and alignment. Conduct a thorough code review and enhance security using GitHub Advanced Security's CodeQL. Streamline development with a GitHub Actions CI/CD pipeline for Contoso Traders, ensuring efficient and secure deployment.

This is the solution guide that contains all of the comprehensive, step-by-step directions needed to finish the challenge.

## Accessing the Azure Portal

1. To access the Azure Portal, open the Edge browser from inside the environment and navigate to the **[Azure Portal](https://portal.azure.com)**.

1. On the **Sign in to Microsoft Azure** tab, you will see a login screen. Enter the following email/username, and then click on **Next**. 

   * **Email/Username**: 

      > **Note**: For **Email/Username**, Navigate to **Environment(1)**, click on **Azure credentials (2)**, and copy **Username (3)**.   
            
      ![](../media/ad1.png)   
        
1. Now enter the following password and click on **Sign in**.
   * **Password**: 

      > **Note**: For **Email/Username**, Navigate to **Environment(1)**, click on **Azure credentials (2)**, and copy **Password (3)**.   
            
      ![](../media/ad2.png)   
     
1. If you see the pop-up **Stay Signed in?**, click No.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

## Solution Guide

## Exercise 1: Integrate an 'About Us' app component in React using GitHub Copilot

### Task 1: Sign in to GitHub Copilot in Visual Studio Code

1. Open **Visual Studio Code** from the desktop screen. 

   ![Picture1](../media/cl7-ex1-t1-s1.png)
   
1. At the left pane , click on **Extensions**. 

   ![Picture1](../media/ex7-1.png)

1. At the search bar of the Extensions type **Github (1)**, select the **Github Copilot (2)** Extension and then click on **install (3).**

   ![Picture1](../media/ex7-task1-0.1.png)
   
1. Once the installation is successfull, a pop appears to sign-in. Click on **Sign in to Use Copilot for free**

   ![Picture1](../media/ad12.png)

   >**Note:** If you don’t see any option here, you can click the icon at the bottom right and select **Sign in to use Copilot**.

   ![Picture1](../media/ad12a.png)

1. If you get the popup, click on **Allow**.

   ![Picture1](../media/cl7-ex1-t1-s3.png)

1. On the **Select user to authorize** page in the edge browser, click on **Continue**

   ![Picture1](../media/ad13.png)

1. You will encounter a pop-up prompt. Click **Open** to proceed.

   ![Picture1](../media/ex7-task1-0.4.png)

   >**Note:** If you get another pop-up stating **Allow an extension to open this URI**, please click on **Open**.

1. You will be able to see in the bottom right corner that GitHub Copilot has been activated.

   ![Picture1](../media/cl7-ex1-t1-s8.png)

   >**Note:** If the activation status of Github Copilot in the bottom right corner is not visible, try restarting Visual Studio Code to ensure that the activation status becomes visible in that location.

1. Verify if **GitHub Copilot Chat** is installed. If its installed, chat window will open as shown below.
   
    ![Picture1](../media/ad14.png)
   
### Task 2: Integrate an 'About Us' app component in React using GitHub Copilot

  >**NOTE:** It should be noted that the code suggestions offered by GitHub Copilot might not exactly match the screenshots shown within the labguide. GitHub Copilot is an AI-powered tool that generates code based on context and patterns, and its suggestions can be influenced by various factors. It is also important that you have the knowledge on operating and running React Applications which may be needed as you proceed with this exercise.

1. In a new Visual Studio Code window, click on **File (1)** at the top left corner and then select **Open Folder (2)**.

    ![](../media/ex4-task1-1.png)

1. Navigate to **C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2/ (1)** within the file explorer, and then select the **ContosoTraders.Ui.Website.V2.Raw (2)** folder, and then click on **Select folder (3)**

    ![Picture1](../media/ex7-task1-1.png) 

1. Ensure to click on **Yes, I trust the authors** within the pop-up to successfully import the CloudLabs folder into VS Code.

   ![Picture1](../media/trust-authors.png)

1. Once the project has loaded, within the explorer pane of VS Code, navigate to `Contosotraders.Ui.Website.V2\src\components` folder to view the `App.js` file.

   ![Picture1](../media/CL7-EX1-T2-S3.png)

1. Click on the **Copilot Chat** icon drop down **(1)** and select **Open Chat (2)**.   

   ![Picture1](../media/ad16.png)

1. Within the **CHAT: GITHUB COPILOT** pane, type: `Help me create the new About Us" page in ContosoTraders.Ui.Website.V2\src` and observe the AI response. You can follow the instructions provided by GitHub Copilot towards successfully adding the About Us page as a part of the sample React application that you have imported into VS Code.

   >**Note:** There is a possibility that Copilot Chat not only provides suggestions but may also automatically generate required files such as **AboutUs.js**. If that happens, you will need to click **Keep** to accept and retain the changes.

   ![Picture1](../media/CL7-EX1-T2-S4a.png)

   ![Picture1](../media/CL7-EX1-T2-S4.png)

    >**Disclaimer:** It should be noted that the code suggestions offered by GitHub Copilot might not exactly match the screenshots shown within the labguide. GitHub Copilot is an AI-powered tool that generates code based on context and patterns, and its suggestions can be influenced by various factors. It is also important that you have the knowledge on operating and running React Applications which may be needed as you proceed with this exercise.

    >**Note:** However the ease of executability of this challenge, you can open a new folder within VS Code and import the solution folder from the Windows file explorer with path, `C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\`. Select the **src** folder. This solution project has integrated "About Us" page and unit test cases for the same.

    >**Note:** If you wish to continue to manually edit the raw project, follow the steps from step 7.

1. Create a new file named `AboutUs.css` **(1)** in your `src` directory ie., within the path `ContosoTraders.Ui.Website.V2\src\` and then add the following code **(2)**:

   ```
   .about-us {
       padding: 20px;
       font-size: 1.2em;
       line-height: 1.6;
       color: #333;
   }
   
   .about-us h1 {
       font-size: 2em;
       margin-bottom: 0.5em;
   }
   ```

   >**Note:** This `AboutUs.css` file contains CSS (Cascading Style Sheets) rules that are used to style HTML elements on a webpage. The specific code you've selected defines styles for elements with the class `about-us` and `h1` elements within elements with the class `about-us`.

   ![Picture1](../media/CL7-EX1-T2-S5.png)

1. Save the newly created `AboutUs.css` file.

1. Now let's build a new component for the application. Create a new file named `AboutUs.js` **(1)** in your `src` directory i.e., within the path `ContosoTraders.Ui.Website.V2\src\` and then add the following code **(2)**:

   >**Note:** If the **AboutUs.js** file has already been created by Copilot, you only need to update its contents with the code provided below to maintain consistency.

   ```
   import React from "react";
   import "./AboutUs.css";
   
   function AboutUs() {
     return (
       <div className="container">
         <div className="about-us">
           <h1 className="text-center">About Us</h1>
           <p>
             Contoso Traders is a leading company in the trading industry. We have
             been serving our customers for over 20 years with high-quality
             products and excellent customer service.
           </p>
           <p>
             Our team is dedicated to providing the best service possible. We value
             our customers and strive to meet their needs.
           </p>
         </div>
       </div>
     );
   }
   
   export default AboutUs;
   ```

   >**Note:** Feel free to make changes in the above code snippet as per your use case scenario.

   >**Note:** Notice that the css rules have been imported into the `AboutUs.js` file using the code, `import "./AboutUs.css";`.
   
   >**Note:** The `AboutUs.js` file is a React component that renders an "About Us" section on a webpage based on the CSS rules that have been defined in `AboutUs.css` file.

1. Save the newly created `AboutUs.js` file.

1. Now navigate to the `App.js` file to integrate the "About Us" page that was created in the previous steps.

1. Within the `App.js` file, enter the following code.

     ```
     import AboutUs from "./AboutUs";
     import "./App.css";
     ```

1. Your `App.js` should look similar like the below screenshot:

     ![Picture1](../media/CL7-EX1-T2-S11.png)

1. Scroll down to the end of the code within the `App.js` file and then add the following code to include the newly created `About Us` component.

     ```
     <AboutUs />
     ```
1. Your `App.js` should now look similar like the below screenshot:

     ![Picture1](../media/CL7-EX1-T2-S13.png)

1. To run your React application, you typically use the command line (also known as the terminal). Here are the steps:
      - Within Visual Studio Code, you can open the terminal by going to the top menu, click on elipses **... (1)**, then click on **Terminal** **(2)** and then select **New Termimal (3)**.

      - Navigate to your project directory. You can do this with the `cd` command followed by the path to your project. You can use the below command to navigate to the React application's working directory **(4)**:

      ```
      cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\src\ContosoTraders.Ui.Website.V2
      ``` 
      - Once you're in your project directory, you can start the application with the `npm start` **(5)** because we need npm to create the Contoso Traders Application. After running the following command within the terminal, your application should start, and you can view it in your web browser at http://localhost:3000.  
       
      ```
      npm run start
      ```
      
     ![Picture1](../media/ad17.png)

    >**Note:** If the above command fails, you might need to run the following command :

     ```powershell
     npm i
     ```
   
     - The command `npm i` is a shorthand version of `npm install`. It is used in Node.js environments to install all the dependencies listed in the `package.json` file. These dependencies are libraries or packages that your project needs to run correctly. The installed packages will be placed in a folder named `node_modules` in your project directory.

     - After the installation of all the dependencies, execute the command - `npm run start` to start the application. This open a new browser tab over the url path, `http://localhost:3000/`.

1. Click on **Get Started** and scroll down within your static web app to view the integrated **About Us** page.

   ![Picture1](../media/CL7-EX1-T2-S15a.png)

1. Observe that the new "About Us" component has been added at the end of the webpage.

     ![Picture1](../media/CL7-EX1-T2-S15.png)

## Exercise 2: Generate and run Unit Test cases using GitHub Coplilot:

### Task 1: Create and run test cases:

1. In Visual Studio Code, go to **Explorer** and navigate to path `ContosoTraders.Ui.Website.V2\src\components` and open the `WelcomePopup.js` file.

   ![Picture1](../media/CL7-EX2-T1-S1.png)

2. Select all code lines `[CTRL+A]` of `WelcomePopup.js` file **(1)** and then paste the following prompt **(2)** within the GitHub Copilot Chat Panel and press enter:

   ```
   /tests
   ```

   >**Note:** There is a possibility that Copilot Chat not only provides suggestions but may also automatically generate required files such as **WelcomePopup.test.js**. If that happens, you will need to click **Keep** to accept and retain the changes.

   ![Picture1](../media/ad18.png)

   ![Picture1](../media/ad18a.png)

3. Now create a new file named `WelcomePopup.test.js` under the path `ContosoTraders.Ui.Website.V2\src\components`.

   >**Note:** If the file has already been created by Copilot, there is no need to create it again.

   ![Picture1](../media/CL7-EX2-T1-S3.png)

4. Navigate back to the GitHub Copilot chat panel and copy the unit test that has been generated using Copilot for the `WelcomePopup` component. Ensure to paste these unit test cases within the newly created file - `WelcomePopup.test.js` under the `components` folder and save the file.

   >**Note:** If the file has already been created by Copilot, you can skip this step. This step is only needed if the result appears in the Copilot chat window—then you'll need to copy and paste the generated code into your file.

   ![Picture1](../media/CL7-EX2-T1-S4-a.png)

   ![Picture1](../media/CL7-EX2-T1-S4-b.png)

5. Once ready with the test cases, open a new terminal within Visual Studio Code, and navigate to the following path/directory by running the below command within the terminal:

   ```
   cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\src\ContosoTraders.Ui.Website.V2\src\components
   ```

   >**Note:** Ensure that your current working directory within the terminal has the `components` folder in its present path. In this scenario, the `components` folder is present inside the `/src` directory. 

6. To execute the unit test cases genereated by GitHub Copilot, we need to run the `WelcomePopup.test.js` file using the following command within the terminal:

   ```
   npm run test
   ```

7. Post execution of the above unit test, you must ensure to have a successful - `PASS` test runs with no errors. If you are produced with errors, please understand the intricacies of the error as mentioned within the terminal and work towards a successful unit test run.

   >**Note:** You may need to scroll up in your output window to view the results.

   ![Picture1](../media/CL7-EX2-T1-S7.png)

## Exercise 3: Code Review and Security Check

### Task 1: Submit Codebase Modifications to GitHub Repository

1. In a new browser tab, open ```https://www.github.com/login```. From the **Environment** page **(1)**, navigate to **License** **(2)** tab and **copy** **(3)** the credentials. Use the same username and password to log into GitHub.

   ![](../media/ad3.png) 

2. once logged-in, on the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/2dg1.png "New Repository Creation Form")

3. Next to the search criteria, locate and select the **New** button.

   ![The `New Repository` creation form in GitHub.](../media/ex2-t3-3-git.png "New Repository Creation Form")

4. On the **Create a new repository** screen, name the repository ```devsecops-2``` **(1)**, select **Public** **(2)**, and click on the **Create repository** **(3)** button.

   ![](../media/CL7-EX3-T1-S4.png) 

5. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository and **save it** in a notepad for future use.

   ![](../media/ex7-task1-3.png)

6. From the GitHub username, note down the **Unique-ID** present in the Username. You'll need this in the upcoming steps.

   ![](../media/cl1-t1-s13.png)

7. Navigate back to the **Visual Studio Code** application in which the terminal is already open. In the terminal, click on the **drop-down** button and select **PowerShell** to open a fresh PowerShell terminal tab.

   ![imported-Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](../media/2dg4.png "Quick setup screen")

8. In Visual Studio Code, run the below commands in the terminal to set your **email** and **username**, which Git uses for commits. Make sure to replace the GitHub account email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\src\ContosoTraders.Ui.Website.V2
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
   ![](../media/ex7-task1-4.png) 
     
    Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` with the value you copied in step 5 and `Unique-ID` in step 6.

    Note: This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created named `devsecops`. 

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin-<Unique-ID> <your_github_repository-url>
      git push -u origin-<Unique-ID> main
      ```
     
   - If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager. Click on **Authorize git-ecosystem** to provide access.

       ![](../media/ex2-t3.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.

### Task 2: Implement Code Scanning and CodeQL

In this task, you'll configure Code scanning and explore CodeQL alerts. Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown on GitHub.

**Note**: To perform this task, the GitHub repository should be public. If the repository visibility is private, please go to the settings of the repository and change the visibility to public.

1. Login to GitHub where the `devsecops-2` repository was created.

2. Select the **settings** ***(1)*** tab from the GitHub browser tab. Click on **Advanced security** ***(2)*** under the security side blade.

   ![](../media/ex2-task1-1a.png) 

3. Click on the **Set up** **(1)** button to enable CodeQL analysis, and select the **Advanced** **(2)** option for creating a CodeQL Analysis YAML file.

   ![](../media/ex2-task1-2.png)     

4. Update the workflow name to **codeql-analysis.yml** ***(1)*** and review the yaml file. Select **Commit changes** ***(2)***, then select **Commit directly to the main branch** ***(3)***, and click on **Commit changes** ***(4)***.
  
   ![](../media/cl2-t1-s3.png)

   ![](../media/ad-19.png) 

5. Navigate to the **Actions** ***(1)*** tab, here you can review the **workflow** ***(2)*** run.
    
   ![](../media/cl2-t1-s4.png) 

6. Navigate to the **Security** ***(1)*** tab and click on **View alerts** ***(2)***.
   
   ![](../media/cl2-t1-s5.png)

7. You will be navigated to the **Code scanning** section. You'll be able to visualize the **No code scanning alerts here!**.
   
   ![](../media/ex7-task1-5.png)

### Task 3: Implement Repository security advisories

In this task, you'll enable Repository security advisories. You can use GitHub Security Advisories to privately discuss, fix, and publish information about security vulnerabilities in your repository. Anyone with admin permissions to a repository can create a security advisory.

1. Navigate to the **Security** ***(1)*** tab, select **Advisories** ***(2)*** from the side blade, and click on **New draft security advisory** ***(3)***.

   ![](../media/cl2-t2-s1.png)

2. In the Open a draft security advisory tab, under the Advisory Details section, provide the following details:

   - Title: **Improper Access Control in devsecops-2/src/App.js** ***(1)***
   - CVE identifier: **Request CVE ID later** ***(2)***
   - Description: **Add** ***(3)*** Replace the below-mentioned details in the description section.
   
   ```
   Impact
   What kind of vulnerability is it? Who is impacted?

   HTTP request handlers should not perform expensive operations such as accessing the file system, executing an operating system command, or interacting with a database without limiting the rate at which requests are accepted. Otherwise, the application becomes vulnerable to denial-of-service attacks where an attacker can cause the application to crash or become unresponsive by issuing a large number of requests at the same time.

   Patches
   Has the problem been patched? What versions should users upgrade to?

   It is patched and rectified the error. Please use 1.2 version

   Workarounds
   Is there a way for users to fix or re../mediate the vulnerability without upgrading?

   // set up rate limiter: maximum of five requests per minute
   var RateLimit = require('express-rate-limit');
   var limiter = new RateLimit({
   windowMs: 1601000, // 1 minute
   max: 5
   });

   // apply rate limiter to all requests
   app.use(limiter);

   Added the above code in app.js

   References
   Are there any links users can visit to find out more?

   https://github.com/OWASP/API-Security/blob/master/2019/en/src/0xa4-lack-of-resources-and-rate-limiting.md
   https://codeql.github.com/codeql-query-help/javascript/js-missing-rate-limiting/
   ```
    
   ![](../media/CL7-EX3-T3-S2.png)

3. In the **Affected products** section, provide the following details and click on **Create draft security advisory** ***(7)***   
 
   - Ecosystem: **composer** ***(1)***
   - Package name: **devsecops-2/src/App.js** ***(2)***
   - Affected version: **<1.2** ***(3)***
   - Patched version: **1.2** ***(4)***
   - Severity: **High** ***(5)***
   - Common Weakness Enumerator (CWE): **Improper Access Control (CWE-284)** ***(6)***
  
     ![](../media/CL7-EX3-T3-S3.png)

4. Once the security advisory is created, scroll down and click on **start a temporary private fork**. It is used to collaborate on a patch for this advisory.

    ![](../media/CL7-EX3-T3-S4-a.png)
    
    ![](../media/cl2-t2-s4-b.png)

5. After having the temporary fork, you can request a CVE. It is used for GitHub reviews and published security advisories. Upon review, we may use this advisory to send Dependabot alerts to affected repositories and redistribute the advisory through our API and Atom feed.

## Exercise 4: CI/CD Pipeline Setup and Infrastrucure Deployment

### Task 1: Deploy Infrastructure

1. Login to your Azure portal with the credentials provided in the **Environment** tab of the integrated CloudLabs Environment.

2. In the global search bar, search for **Static Web Apps (1)** and select **Static Web Apps (2)**.

    ![](../media/ad20.png)

3. Click on **+ Create** to create a new Static Web Apps.

4. In the **Basics tab** of the **Create Static Web App** page, enter the following details:
   - **Subscription:** Select the available subscription **(1)**.
   - **Resource Group:** Create a new resource group named - **Static-Web-App (2)**.
   - **Name:** `React-Static-Web-App` **(3)**.
   - **Plan type:** Select **Free (4)**.
   - **Source:** Select **GitHub (5)**
   - **GitHub account:** Click on **Click here to login**. Connect to your GitHub account which has the `devsecops-2` repository with the React application files **(6)**.
   
      ![](../media/ex7-task1-6a.png)

      ![](../media/ex7-task1-8.png)

      - Click on **Authorize AzureApp service**

        ![](../media/ad21.png)

      - Provide the **GitHubUserPassword (1)** and then click on **Confirm (2)**

        ![](../media/ad22.png)

   - **Organization:** Select your assigned Github organization **(7)**.
   - **Repository:** Select `devsecops-2` **(8)**.
   - **Branch:** `Main` **(9)**.
   - **Build presets:** Search for and select **React (detected) (10)**.
   - **App location:** `/` **(11)**.

      >**Note:** `/` refers to the root directory of the GitHub repository. Ensure that the location is specified appropriately as per your GitHub file structure.
   
   - Leave the other fields at default and then click on **Review + Create (12)**.

     ![](../media/ex7-task1-7.png)

   - Finally, click on **Create** on the **Review + create** page to create the static web app.     

     ![](../media/ad23.png)   

6. Once the deployment is successful, click on **Go to resource**.

    ![](../media/CL7-EX4-T1-S5.png)

7. Navigate back to your `devsecops-2` repository on the GitHub portal and click on the **Actions** tab.

    ![](../media/CL7-EX4-T1-S6.png)

8. Ensure that your **Azure Static Web Apps CI/CD** workflow has a successful run status.

    ![](../media/CL7-EX4-T1-S7.png)

9. Navigate back to your Azure portal on the overview page of the recently created Static Web App and click on the **URL**

    ![](../media/CL7-EX4-T1-S8.png)

10. The URL redirects you to a new browser tab with the React Application up and running.

    ![](../media/CL7-EX4-T1-S9.png)

11. Click on **Get Started** and scroll down within your static web app to view the integrated **About Us** page.

    ![](../media/CL7-EX4-T1-S10.png)

## Success criteria:
To complete this challenge successfully:

- Successful implementation of the new feature.
- Accuracy and completeness of the generated unit tests with all successful passes.
- Successful setup and execution of the CI/CD pipeline.

## Additional Resources:

- Refer to [About GitHub Copilot Chat](https://docs.github.com/en/copilot/github-copilot-chat/about-github-copilot-chat) for reference.
- Refer to [Copilot Chat writes Unit Tests](https://dev.to/this-is-learning/copilot-chat-writes-unit-tests-for-you-1c82) for reference.
- Refer to [Using GitHub Copilot Chat in your IDE](https://docs.github.com/en/copilot/github-copilot-chat/using-github-copilot-chat-in-your-ide) for reference.
