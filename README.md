# Introduction to Snyk Code Workshop

Snyk Code is developer-first, embedding SAST as part of the development process, enabling developers to build software securely during development, not trying to find and fix problems after the code is compiled. Snyk Code works in the IDEs and SCMs developers use to build and review software and provides fast, actionable, meaningful results to fix issues in real-time

At the time of this workshop creation Snyk Code supports the following languages and frameworks:

[https://docs.snyk.io/products/snyk-code/snyk-code-language-and-framework-support](https://docs.snyk.io/products/snyk-code/snyk-code-language-and-framework-support)

In this **hands-on** workshop we will achieve the follow:

* [Step 1 Fork a GitHub repository](#step-1-fork-a-github-repository)
* [Step 2 Configure GitHub Integration](#step-2-configure-github-integration)
* [Step 3 Enable Snyk Code within Snyk App](#step-3-enable-snyk-code-within-snyk-app)
* [Step 4 Add project to find Snyk Code Vulnerabilities](#step-4-add-project-to-find-snyk-code-vulnerabilities)
* [Step 5 Snyk Code CLI Test](#step-5-snyk-code-cli-test)
* [Step 6 Snyk Code Test using VS Code](#step-6-snyk-code-test-using-vs-code)

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

![alt tag](https://i.ibb.co/ZfddWxb/snyk-code-4.png)

* Click on "**Code Analysis**" to view our SAST scan results

For each Vulnerability, Snyk displays the following:

1. Each Vulnerability grouped by severity
2. Each Vulnerability links to the CWE category code
3. Each Vulnerability shows the CWE category name
4. Displays the line of code where the security issue exists
5. Description for the issue and the code file name it exists in
6. A link to a Snyk Learn module on how to fix these type of vulnerabilities if available
7. The ability to ignore issues you wish to remove from the list

![alt tag](https://i.ibb.co/SJTXkDr/snyk-code-5.png)

* Click on the "**Full Details**" button as shown below

Snyk products all provide a developer-friendly experience, so Snyk Code helps developers to quickly understand the problem, learn the background, and how to approach it. Snyk Code helps you understand the dangerous code flow step-by-step. For every issue, Code also provides a link to the lines in the relevant files, to view more details on the problem like the CWE, and how to approach it.

![alt tag](https://i.ibb.co/vwxw68k/snyk-code-6.png)

* Click on "**Fix Analysis**" to see how you can fix the issue based on other open source project. On this page you get not just source code example fixes but also the following detailed information

1. Details
2. Types Of Attacks
3. Affected Environments
4. How to prevent

![alt tag](https://i.ibb.co/25P6M7g/snyk-code-7.png)

### Do you think you could fix this issue now?

Finally, if you have time go ahead and fork this repo and import this into Snyk App if you wish to see more code issues then the simple example we using here

https://github.com/papicella/goof

_Note: This may take a while as there are various other project files in this repo so you can always come back to this later to see the code results_

![alt tag](https://i.ibb.co/CJDpRys/snyk-code-10.png)

## Step 5 Snyk Code CLI Test

In addition to the Snyk App UI we also have, snyk - CLI a build-time tool to find & fix known vulnerabilities in open-source dependencies, IaC configuration files and SAST scans on the source code files itself (Snyk Code).

_Note: Please ensure you have the latest version of the Snyk CLI installed a version equal to or greater than the version below_

```bash
$ snyk --version
1.725.0
```

* Authorize the Snyk CLI with your account as follows

```bash
$ snyk auth

Now redirecting you to our auth page, go ahead and log in,
and once the auth is complete, return to this prompt and you'll
be ready to start using snyk.

If you can't wait use this url:
https://snyk.io/login?token=ff75a099-4a9f-4b3d-b75c-bf9847672e9c&utm_medium=cli&utm_source=cli&utm_campaign=cli&os=darwin&docker=false


Your account has been authenticated. Snyk is now ready to be used.
```

* Clone your forked repository as shown below. You can use your own GitHub forked repo here instead of the one shown below if you like

```shell
❯ git clone https://github.com/papicella/springbootemployee-api
Cloning into 'springbootemployee-api'...
remote: Enumerating objects: 163, done.
remote: Counting objects: 100% (163/163), done.
remote: Compressing objects: 100% (96/96), done.
remote: Total 163 (delta 43), reused 145 (delta 27), pack-reused 0
Receiving objects: 100% (163/163), 71.44 KiB | 189.00 KiB/s, done.
Resolving deltas: 100% (43/43), done.
```


* Change to the "**springbootemployee-api**" directory

```shell
$ cd springbootemployee-api
```

* At this point let's go ahead and run our first "**snyk code test**" as shown below

```shell
❯ snyk code test

Testing /Users/pasapicella/snyk/SE/workshops/snyk-code/springbootemployee-api ...

 ✗ [High] SQL Injection
     Path: src/main/java/pas/au/snyk/se/dao/AccountRestController.java, line 25
     Info: Unsanitized input from the request URL flows into createQuery, where it is used in an SQL query. This may result in an SQL Injection vulnerability.

 ✗ [High] Use of Hard-coded, Security-relevant Constants
     Path: src/main/java/pas/au/snyk/se/service/DatabaseService.java, line 8
     Info: Avoid hardcoding values that are meant to be secret. Found hardcoded secret.


✔ Test completed

Organization:      undefined
Test type:         Static code analysis
Project path:      /Users/pasapicella/snyk/SE/workshops/snyk-code/springbootemployee-api

2 Code issues found
2 [High]
```

* This time lets run the "**snyk code test**" but get output data in JSON format.

_Note: There is going to be much more output this time rather than the concise output from the previous test._

```shell
❯ snyk code test --json
{
  "$schema": "https://raw.githubusercontent.com/oasis-tcs/sarif-spec/master/Schemata/sarif-schema-2.1.0.json",
  "version": "2.1.0",
  "runs": [
    {
      "tool": {
        "driver": {
          "name": "SnykCode",
          "semanticVersion": "1.0.0",
          "version": "1.0.0",
          "rules": [
            {
              "id": "java/Sqli",
              "name": "Sqli",
              "shortDescription": {
                "text": "SQL Injection"
              },
              "defaultConfiguration": {
                "level": "error"
              },
              "help": {
                "markdown": "## Details\n\nIn an SQL injection attack, the user can submit an SQL query directly to the database, gaining access without providing appropriate credentials. Attackers can then view, export, modify, and delete confidential information; change passwords and other authentication information; and possibly gain access to other systems within the network. This is one of the most commonly exploited categories of vulnerability, but can largely be avoided through good coding practices.\n\n### Best practices for prevention\n* Avoid passing user-entered parameters directly to the SQL server.\n* When coding, define SQL code first, then pass in parameters. Use prepared statements with parameterized queries. Examples include `SqlCommand()` in .NET and `bindParam()` in PHP.\n* Use strong typing for all parameters so unexpected user data will be rejected.\n* Where direct user input cannot be avoided for performance reasons, validate input against a very strict allowlist of permitted characters, avoiding special characters such as `? & / < > ; -` and spaces. Use a vendor-supplied escaping routine if possible.\n* Develop your application in an environment and/or using libraries that provide protection against SQL injection.\n* Harden your entire environment around a least-privilege model, ideally with isolated accounts with privileges only for particular tasks.",
                "text": ""
              },
              "properties": {
                "tags": [
                  "java",
                  "maintenance",
                  "bug",
                  "table",
                  "query",
                  "database"
                ],
                "categories": [
                  "Security"
                ],
                "exampleCommitFixes": [
                  {
                    "commitURL": "https://github.com/BjoernKW/ZenQuery/commit/228bf9a728f7d85f5a1fea0cc9c896db3d8eb0e8?diff=split#diff-3fd2c91261df4fcc03ccb7e8c2fb4acaL44",
                    "lines": [
                    
....


            }
          ],
          "properties": {
            "priorityScore": 770,
            "priorityScoreFactors": [
              {
                "label": true,
                "type": "hotFileCodeFlow"
              },
              {
                "label": true,
                "type": "fixExamples"
              }
            ]
          }
        }
      ],
      "properties": {
        "coverage": [
          {
            "files": 17,
            "isSupported": true,
            "lang": "Java"
          }
        ]
      }
    }
  ]
}
```

* Finally, fork the Goof application if you wish to see more vulnerabilities and this time using JavaScript

_Note: In the example below I set --severity-threshold=medium which means I only want to see issue that have a severity of medium or higher. This is how you would break a build in a CI pipeline using a "**snyk code**" test should vulnerabilities exist the exit code would be a non success exit code_

```shell
❯ git clone https://github.com/papicella/goof
Cloning into 'goof'...
remote: Enumerating objects: 2121, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 2121 (delta 4), reused 5 (delta 0), pack-reused 2106
Receiving objects: 100% (2121/2121), 4.30 MiB | 7.31 MiB/s, done.
Resolving deltas: 100% (1438/1438), done.

❯ cd goof

❯ snyk code test --severity-threshold=medium

Testing /Users/pasapicella/snyk/SE/workshops/snyk-code/goof ...

 ✗ [Medium] Information Exposure
     Path: app.js, line 27
     Info: Disable X-Powered-By header for your Express app (consider using Helmet middleware), because it exposes information about the used framework to potential attackers.

 ✗ [Medium] Use of Hard-coded Credentials
     Path: typeorm-db.js, line 12
     Info: Do not hardcode passwords in code. Found hardcoded password used in typeorm.createConnection.

 ✗ [Medium] Use of Hard-coded Credentials
     Path: mongoose-db.js, line 52
     Info: Do not hardcode passwords in code. Found hardcoded password used in password.

 ✗ [Medium] Use of Hard-coded Credentials
     Path: typeorm-db.js, line 11
     Info: Do not hardcode credentials in code. Found hardcoded credential used in typeorm.createConnection.

 ✗ [Medium] Allocation of Resources Without Limits or Throttling
     Path: routes/index.js, line 77
     Info: This endpoint handler performs a system command execution and does not use a rate-limiting mechanism. It may enable the attackers to perform Denial-of-service attacks. Consider using a rate-limiting middleware such as express-limit.

 ✗ [Medium] Allocation of Resources Without Limits or Throttling
     Path: routes/index.js, line 166
     Info: This endpoint handler performs a file system operation and does not use a rate-limiting mechanism. It may enable the attackers to perform Denial-of-service attacks. Consider using a rate-limiting middleware such as express-limit.

 ✗ [Medium] Allocation of Resources Without Limits or Throttling
     Path: routes/index.js, line 223
     Info: This endpoint handler performs a file system operation and does not use a rate-limiting mechanism. It may enable the attackers to perform Denial-of-service attacks. Consider using a rate-limiting middleware such as express-limit.

 ✗ [Medium] Cleartext Transmission of Sensitive Information
     Path: app.js, line 12
     Info: http (used in require) is an insecure protocol and should not be used in new code.

 ✗ [High] Cross-site Scripting (XSS)
     Path: routes/index.js, line 109
     Info: Unsanitized input from the HTTP request body flows into send, where it is used to render an HTML page returned to the user. This may result in a Cross-Site Scripting attack (XSS).

 ✗ [High] Hardcoded Secret
     Path: app.js, line 73
     Info: Avoid hardcoding values that are meant to be secret. Found a hardcoded string used in here.

 ✗ [High] SQL Injection
     Path: routes/index.js, line 39
     Info: Unsanitized input from the HTTP request body flows into find, where it is used in an SQL query. This may result in an SQL Injection vulnerability.

 ✗ [High] Command Injection
     Path: routes/index.js, line 86
     Info: Unsanitized input from the HTTP request body flows into child_process.exec, where it is used to build a shell command. This may result in a Command Injection vulnerability.


✔ Test completed

Organization:      undefined
Test type:         Static code analysis
Project path:      /Users/pasapicella/snyk/SE/workshops/snyk-code/goof

12 Code issues found
4 [High]  8 [Medium]
```

## Step 6 Snyk Code Test using VS Code

IDE integrations use Snyk Code’s fast analysis and response, allowing you to spot an issue, understand and learn more about it, and fix it, as you write the code before you check the code in. So you can find possible security flaws in your code as you write it, on a line-by-line basis.

Snyk Code supports a VS Code plugin to support issue finding and fixing, directly from the IDE:

* Open VS Code from the "**springbootemployee-api**" directory so it's files appear in VS Code

![alt tag](https://i.ibb.co/CBKFZt1/snyk-code-8.png)

* Install the VS Code Snyk plugin using the link below

[https://docs.snyk.io/features/integrations/ide-tools/visual-studio-code-extension-for-snyk-code](https://docs.snyk.io/features/integrations/ide-tools/visual-studio-code-extension-for-snyk-code)

* Using the Snyk Icon on the left hand side let's run a "Snyk Code" Test as shown below

![alt tag](https://i.ibb.co/xGHf2Tx/snyk-code-9.png)


Thanks for attending and completing this workshop

![alt tag](https://i.ibb.co/7tnp1B6/snyk-logo.png)

<hr />
Pas Apicella [pas at snyk.io] is an Solution Engineer at Snyk APJ