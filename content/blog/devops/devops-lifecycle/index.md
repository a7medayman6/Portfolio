---
title: "Devops Lifecycle"
date: 2021-07-28T00:10:45+02:00
draft: false
ShowReadingTime: true
hideSummary: false
showtoc: true
cover: 
    image: ''
weight: 4
---


<img src="/blog/devops/intro-to-devops/devops-lifecycle2.png" alt="devops life-cycle" style="zoom: 140%;" />

## 1. Continuous Development

- This phase involves the planning and coding of the software.
- The vision of the project is decided during the planning phase.
- The developers begin developing the code for the application. 
- here are no DevOps tools that are required for planning, but there are several tools for maintaining the code. 

## 2. Continuous Integration

- The developers require to commit changes to the source code more frequently. This may be on a daily or weekly basis.
- Then every commit is built, and this allows early detection of problems if they are present.
  - Building code is not only involved compilation, but it also includes **unit testing, integration testing, code review**, and **packaging**.
- The code supporting new functionality is continuously integrated with  the existing code. Therefore, there is continuous development of  software.

![Continuous Integration](/blog/devops/intro-to-devops/CIandCD-lifecycle.png)

- ### Jenkins

  - Jenkins is a popular tool used in this phase.
  - Whenever there is a change in the Git repository, then Jenkins fetches  the updated code and prepares a build of that code, which is an  executable file in the form of war or jar. 
  - Then this build is forwarded to the test server or the production server.

  ![Jenkins](/blog/devops/intro-to-devops/jenkinsrole.png)

## 3. Continuous Testing

- The developed software is continuously testing for bugs.

- Automation testing tools such as **TestNG, JUnit, Selenium**, etc are used.

- These tools allow Quality Assurances to test multiple code-bases thoroughly in parallel to ensure that there is no flaw in the functionality.

- In this phase, **Docker** Containers can be used for simulating the test environment.

- **Selenium** does the automation testing, and **TestNG**  generates the reports. 

- The entire testing phase can automate with the help of a Continuous Integration (**Jenkins**). 

  

  ![Continuous Testing](/blog/devops/intro-to-devops/ct.png)



## 4. Continuous Monitoring

- **Continuous monitoring** is a technology and process that  IT organizations may implement to enable rapid detection of compliance  issues and security risks within the IT infrastructure. 
- Monitoring is the phase where important information about the use of the software is recorded and carefully processed to find out trends and identify problem areas. 
- It may occur in the form of documentation files or maybe produce  large-scale data about the application parameters when it is in a  continuous use position. The system errors such as server not reachable, low memory, etc are resolved in this phase. It maintains the security  and availability of the service. 

## 5. Continuous Feedback

- The application development is consistently improved by analyzing the results from the operations of the software.



## 6. Continuous Deployment

- In this phase, the code is deployed to the production servers. Also, it  is essential to ensure that the code is correctly used on all the  servers.

- The new code is deployed continuously, and configuration management  tools play an essential role in executing tasks frequently and quickly. 

- Some popular tools which are used in this phase, such as **Chef, Puppet, Ansible**, and **SaltStack**.

- ### Containerization

  - Containerization tools are also playing an essential role in the deployment phase. **Vagrant** and **Docker** are popular tools that are used for this purpose.
  - Containerization tools help to produce consistency across development, staging, testing,  and production environment. They also help in scaling up and scaling  down instances softly.
  - Containerization tools help to maintain consistency across the  environments where the application is tested, developed, and deployed. 
  - There is no chance of errors or failure in the production environment as they package and replicate the same dependencies and packages used in  the testing, development, and staging environment.
  - It makes the application easy to run on different computers. 

![Continuous Deployment](/blog/devops/intro-to-devops/cont-deployment.png)

## 7. Continuous Operations

- All DevOps operations are based on the continuity with complete  automation of the release process and allow the organization to  accelerate the overall time to market continuously.  

## Resources 

- ###### [DevOps Lifecycle - javatpoint](https://www.javatpoint.com/devops-lifecycle)
