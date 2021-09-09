---
title: "Jenkins"
date: 2021-07-28T00:10:45+02:00
draft: false
ShowReadingTime: true
hideSummary: false
showtoc: true
cover: 
    image: ''
weight: 3
---

## What is Jenkins ?

- It is a Continuous Integration (CI) & Continuous Delivery(CD) Tool which are integral parts of Dev-Ops.
- Jenkins is an open-source server that is written entirely in Java.
- Jenkins should be installed on a server where the central build will take place.

## How Jenkins Works

![how jenkins works](/blog/devops/jenkins/how-jenkins-works.jpg#center)

## Jenkins History 

*you can skip this part*

- Hudson is a very popular open-source Java-based continuous integration tool developed by Sun Microsystems which was later acquired by Oracle. After the acquisition of Sun by Oracle, a fork was created from the Hudson source code, which brought about the introduction of Jenkins.
- Kohsuke Kawaguchi, a Java developer, working at SUN Microsystems, was tired of building the code and fixing errors repetitively. In 2004, created an automation server called Hudson that automates build and test task.
- In 2011, Oracle who owned Sun Microsystems had a dispute with Hudson open source community, so they forked Hudson and renamed it as Jenkins.
- Both Hudson and Jenkins continued to operate independently. But in short span of time, Jenkins acquired a lot of projects and contributors while Hudson remained with only 32 projects. With time, Jenkins became more popular, and Hudson is not maintained anymore.



## Why Use Jenkins ?

-  Jenkins can automate build and test at a rapid rate. 

- Jenkins supports the complete development life-cycle of software from building, testing, documenting the software, deploying and other stages of a software development life-cycle.

- Jenkins has plug-ins for almost everything: git, docker, Amazon EC2, maven, selenium 

- #### As technology grows, so does Jenkins. So far Jenkins has around 320 plug-ins published in its plug-++ins database. With plug-ins, Jenkins becomes even more powerful and feature rich.



## What is Continuous Integration?

- In Continuous Integration after a code commit, the software is built and tested immediately. 
- In a large project with many developers, commits are made many times during a day. 
- With each commit code is built and tested. 
- If the test is passed, build is tested for deployment. 
- If deployment is a success, the code is pushed to production. 
- This commit, build, test, and deploy is a continuous process and hence the name continuous integration/deployment.



### A Continuous Integration Pipeline is a powerful instrument that consists of a set of tools designed to **host**, **monitor**, **compile** and **test** code, or code changes, like:

- **Continuous Integration Server** (**Jenkins**, Bamboo, CruiseControl, TeamCity, and others)
- **Source Control Tool** (e.g., CVS, SVN, **GIT**, Mercurial, Perforce, ClearCase and others)
- **Build tool** (**Make**, ANT, **Maven**, Ivy, **Gradle**, and others)
- **Automation testing framework** (**Selenium**, Appium, TestComplete, UFT, and others)



## Why use Continuous Integration ?

|                      **Before Jenkins**                      |                      **After Jenkins**                       |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| Once all Developers had completed their assigned coding tasks, they used to commit their code all at same time. Later, Build is tested and deployed.  Code commit built, and test cycle was very infrequent, and a single build was done after many days. | The code is built and test as soon as Developer commits code. Jenkins will build and test code many times during the day  If the build is successful, then Jenkins will deploy the source into the test server and notifies the deployment team.  If the build fails, then Jenkins will notify the errors to the developer team. |
| Since the code was built all at once, some developers would need to wait until other developers finish coding to check their build | The code is built immediately after any of the Developer commits. |
| It is not an easy task to isolate, detect, and fix errors for multiple commits. | Since the code is built after each commit of a single developer, it's easy to detect whose code caused the built to fail |
| Code build and test process are entirely manual, so there are a lot of chances for failure. | Automated build and test process saving timing and reducing defects. |
| The code is deployed once all the errors are fixed and tested. | The code is deployed after every successful build and test.  |
|                  Development Cycle is slow                   | The development cycle is fast. New features are more readily available to users. Increases profits. |

![jenkins & git](/blog/devops/jenkins/jenkins&git.jpg)



## Resources

- [Jenkins - javatpoint](https://www.javatpoint.com/jenkins)

- [What is Jenkins? - guru99](https://www.guru99.com/jenkin-continuous-integration.html)

- [Jenkins-Overview - TutorialsPoint](https://www.tutorialspoint.com/jenkins/jenkins_overview.htm)

