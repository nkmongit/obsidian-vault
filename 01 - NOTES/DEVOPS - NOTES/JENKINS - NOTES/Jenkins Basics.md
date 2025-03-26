---
created: 2025-03-19T06:04
updated: 2025-03-26T22:53
tags:
  - devops
  - jenkins
  - beginner
---
Before we go to Jenkins there are multiple CI/CD tools out there in the market.
- Jenkins
- CircleCI
- TravisCI
- Spinnaker
- Atlassian Bamboo

But why choose Jenkins, firstly it is open sourced and has a rich set of libraries with plugins support which helps in high customisation and also a large community support with resources.

### What is Jenkins?
Jenkins is a automated CI/CD tool which provides the ability to
 1. Building
 2. Unit Testing
 3. Linting
 4. Dockerzing
 5. Security
 6. Deployment
 7. Tests
 

### How Jenkins works?

- So let's say your developer commits into Git then what Jenkins will do is clone the repo and it will build / compile the code and if any error comes it would notify the developer.
- And if does not have any errors then it would automate to testing then push to docker then K8s Dev Deploy and provide the success message to developer if we have the setup like this in Jenkins.


### Jenkins Core Concepts

- Jobs
	- Define specific tasks such as compiling code, running tests, or deploying to an environment.
- Builds
	- Each execution of a job, with Jenkins maintaining a history of troubleshooting.
- Freestyle Project
	- The default project type, offering flexible job definitions.
- Pipelines
	- Chain jobs together to automate tasks from development to deployment.
- Stages
	- Within the pipelines we group related jobs into phases like 'Build', 'Test' and 'Deploy' for clarity.
- Nodes 
	- Machines where Jenkins executes jobs, with a single controller or multiple agents.
- Plugins
	- Extend Jenkins' functionality, integrating with various tools and technologies.

### Pro's and Con's

- Pros
	- Free and Open Source
	- Highly Customizable
	- Scriptable for Advanced Users (using groovey)
	- Pipeline as Code
	- Mature and Feature Rich
	- Scalable (horizontally by adding more nodes)
- Cons
	- Steeper Learning Curve
	- Maintenance Overhead
	- Performance Considerations
	- Security Concerns
	- Hosting Required

### Source Code Management Systems (SCMs)

- Imagine a project where everyone edits the same single line with no way of tracking any changes we wouldn't be able to know the source of truth like which one is right or was.
- While SCMs prevent exactly that scenario.
- SCMs or Version Control System acts like central library for code, keeping track of every change made over time.
- It provides seamless collaboration by working together on same code base without any conflicts.
- Code Reviews
- It helps in identifying and resolving conflicting edits made by diff developers.
- Share code easily.
- Track each change made into the codebase.
- Easily revert back or rollback to previous version if any error occurs.
- SCMs
	- Git (VCS)
	- Github
	- Gitlab
	- Gitea
	- Bitbucket
	- Gogs

### Understanding CI /CD

- Code residing on the main or master branch is deployed to production server or environment server.
- Typically all code residing on the main or master branch is frequently deployed to production servers or environments.
- Whenever there is a need to introduce new feature or modifying existing code developers create and collab on feature branch.
- Feature branch functions as a clone of the main codebase, enabling developers to work on a new feature until it's fully developed.
- Once the necessary changes are made the code is committed to the feature branch and a pull request is initiated to merge the changes back into the main branch.
- Before merging a review process is carried out and the changes require approval from relevant team members or individuals.
- After reviewing the code is pushed into the production branch either manually or automated process.

### Without CI  / CD

- Delayed Testing
	- Without CI, testing typically occurs late in the dev cycle, often after multiple merges have taken place.
- Inefficient Deployment
	- In the absence of CI, deploying code to various



### Jenkins Architecture

- It leverages a distributed architecture to manage your CI / CD pipelines efficiently
- This structure offers scalability and power, allowing you to automate complex workflows across multiple machines.
- The first component in the architecture is the `Jenkins Controller`
- It is the central hub of your jenkins setup