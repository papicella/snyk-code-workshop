# Introduction to Snyk Code Workshop

Snyk Code is developer-first, embedding SAST as part of the development process, enabling developers to build software securely during development, not trying to find and fix problems after the code is compiled. Snyk Code works in the IDEs and SCMs developers use to build and review software and provides fast, actionable, meaningful results to fix issues in real-time

In this **hands-on** workshop we will achieve the follow:

* Step 1 Fork a GitHub repository
* Step 2 Configure GitHub Integration
* Step 3 Enable Snyk Code within Snyk App
* Step 4 Add project to find Snyk Code Vulnerabilities
* Step 5 Snyk Code CLI Test
* Step 6 Snyk Code Test using VS Code

## Prerequisites

* public GitHub account - http://github.com
* git CLI - https://git-scm.com/downloads
* snyk CLI - https://support.snyk.io/hc/en-us/articles/360003812538-Install-the-Snyk-CLI
* Registered account on Snyk App - http://app.snyk.io

# Workshop Steps

_Note: It is assumed your using a mac for these steps but it should also work on windows or linux with some modifications to the scripts potentially_

## Step 1 Fork a GitHub repository

Navigate to the following GitHub repo - https://github.com/papicella/springbootemployee-api

* Click on the "**Fork**" button
* Ensure you are forking this repo to your public GitHub account
* Click done

## Step 2 Configure GitHub Integration

First we need to connect Snyk to GitHub so we can import our Repository. Do so by:

* Login to http://app.snyk.io Sign up if you haven't already.
* Navigating to Integrations -> Source Control -> GitHub
* Fill in your Account Credentials to Connect your GitHub Account.

![alt tag](https://i.ibb.co/bPqqybM/snyk-starter-open-source-1.png)

## Step 3 Enable Snyk Code within Snyk App

* Click on the "**Settings**" button on the top most navigation bar as shown below

![alt tag](https://i.ibb.co/3fS4VCd/snyk-code-1.png)

* Click on "**Snyk Code**", then enable it and click "**Save Changes**" as shown below

![alt tag](https://i.ibb.co/bP2FpGx/snyk-code-2.png)

## Step 4 Add project to find Snyk Code Vulnerabilities

Now that Snyk is connected to your GitHub Account, import the Forked Repo "**springbootemployee-api**" into Snyk as a Project.

* Navigate to Projects
* Click "**Add Project**" then select "**GitHub**"
* Click on the Repo you forked "**springbootemployee-api**"
* Click "**Add Selected Repositories**"

![alt tag](https://i.ibb.co/TmKzh1P/snyk-code-3.png)

* Once complete you should see a "**Code Analysis**" project as shown below

_Note: There are only 2 code security issues , this is deliberate, and we will try "**Snyk Code**" on more vulnerable projects shortly_

![alt tag](https://i.ibb.co/VTHNzdd/snyk-code-4.png)

* Click on "**Code Analysis**" to view our SAST scan results

For each Vulnerability, Snyk displays the following:

1. Each Vulnerability grouped by severity
2. Each Vulnerability links to the CWE category code
3. Each Vulnerability shows the CWE category name
4. Displays the line of code where the security issue exists
5. Description for the issue and the code file name it exists in
6. A link to a Snyk Learn module on how to fix these type of vulnerabilities if available
7. The ability to ignore issues you wish to remove from the list

![alt tag](https://i.ibb.co/y604yRW/snyk-code-5.png)

* Click on the "**Full Details**" button as shown below

Snyk products all provide a developer-friendly experience, so Snyk Code helps developers to quickly understand the problem, learn the background, and how to approach it. Snyk Code helps you understand the dangerous code flow step-by-step. For every issue, Code also provides a link to the lines in the relevant files, to view more details on the problem like the CWE, and how to approach it.

![alt tag](https://i.ibb.co/QXDrfM9/snyk-code-6.png)

* Click on "**Fix Analysis**" to see how you can fix the issue based on other open source project. On this page you get not just source code example fixes but also the following detailed information

1. Details
2. Types Of Attacks
3. Affected Environments
4. How to prevent

![alt tag](https://i.ibb.co/R7QF6Ty/snyk-code-7.png)

###Do you think you could fix this issue now?

## Step 5 Snyk Code CLI Test

TODO://

## Step 6 Snyk Code Test using VS Code



Thanks for attending and completing this workshop

![alt tag](https://i.ibb.co/7tnp1B6/snyk-logo.png)

<hr />
Pas Apicella [pas at snyk.io] is an Solution Engineer at Snyk APJ