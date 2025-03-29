---
created: 2025-03-19T06:04
updated: 2025-03-30T00:15
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
- It is the central hub of your Jenkins setup, often referred to as the Jenkins server.
- It was also formerly known as master node.
- It basically co-ordinates the whole CI / CD process.
- It has various responsibilities like:
	- Management Tasks
		- User Authentication
		- User Authorization
	- Job Management
		- Defining, scheduling, and monitoring execution.
	- Provides Web Interface
		- For configuration, setting up plugins, onboarding users, and managing and monitoring the builds within Jenkins.
#### Jenkins Controller Node
- It has the following things within the CI / CD
- Plugins
- Jobs
- Nodes
- Credentials
- Configuration
#### Basic Deployment
- In this deployment the Jenkins server can itself handle everything, acting as both the controller and sole worker node.
- Limited to smaller project.
#### Advanced Deployment
- The most recommended one.
- Uses separate controller and worker nodes.
- It offers several advantages like:
- Prevents accidental damage by keeping your controller configs safe from potential job-related changes.
- Boost performance by distributing build tasks across multiple machines, improving speed and efficiency.
- Scale Jenkins server easily by adding more nodes as your project and automation needs increase.

#### Nodes
- Nodes are formerly known as Jenkins agents.
- Nodes help in the CI / CD workflow by serving as the worker machines that execute build jobs.
- Nodes are basically dedicated `linux, windows or other machines` that handle build execution, allowing for parallel processing and increased performance.
- They connect to the controller using the protocol called SSH (Secure Shell) and JNLP (Java Network Launch Protocol).
- Each node has a configurable number of `executors`, an executor is a thread of execution tasks.
- More executors allow for parallel processing of multiple jobs, which will help you to speed up the builds.
- The number of executors assigned to a node is determined by the node's available resources, such as CPU and memory and the requirements of your build task.

#### Agents
- Agents act as an extension of Jenkins, managing the task execution by using executors on a remote node.
- An agent represents a specific way a node connects to the controller.
- It defines the communication protocol and the authentication mechanism used.
- We can also leverage docker containers as the build agents.
- We can also utilize Kubernetes cluster to dynamically provision and manage build agents as pods.

### Types of Jenkins Projects
- Jenkins provides various project type also knows as jobs, to automate different workflows.
- Freestyle Project
	- It is the most basic and flexible option.
	- It allows to define custom build steps and configs for any project.
- Pipeline
	- Uses code to define the entire build pipeline.
	- It includes `stages`, `steps` and `conditions` for complex build processes and continuous delivery workflows.
- Mutli-branch Pipeline
	- It builds upon the pipeline projects by allowing you to manage builds from multiple branches in a single code repository.
- Maven Project
	- It streamline projects that use Maven, a popular build automation tool for Java.
	- Jenkins automatically detects and executes Maven command based on the project's `pom.xml` file.
- Multi-configuration Project
	- It lets you run the same build process with different configurations.
	- You can define various combination of parameters and run tests or builds for each combination.
- Organisation Folders
	- These aren't project type themselves but rather a way to organize your Jenkins project into a hierarchical structure for better management.
### Pipeline and Jenkinsfile
- For automating complex software development workflows, especially continuous integration and continuous deployment.
- A pipeline project allows for a structured multi-stage approach with control over execution flow.
- This translates to organised workflows where we can break down build process into logical stages like compiling, testing and deployment for improved clarity and easier management.
- Each stage can group related tasks.
- For example for the dockerizing stage you could have stage for building a docker image and pushing it to a container registry.
- We can also do parallel execution for independent tasks within stages.
- This can speed up the tasks by allow us to do linting, to run concurrently with unit tests.
- Pipelines are defined as a script called Jenkinsfile.
- These Jenkins file are usually written in groovy like language.
- Type of Pipelines
	- Scripted
	- Declarative
- They both are dependent on Apache Groovy syntax and provide support for shared libraries.



### Difference between Pipelines and Freestyle projects

| Aspect        | Pipelines                                            | Freestyle                                   |
| ------------- | ---------------------------------------------------- | ------------------------------------------- |
| Structure     | Stages allow parallel task execution                 | Sequential order of steps                   |
| Configuration | Configured via Jenkinsfile, supports version control | Configured via web interface, less flexible |
| Complexity    | Ideal for complex workflows                          | Suitable for basic automation tasks         |


### Declarative Pipelines

#### Pipeline Definition

```groovy
pipeline {

}
```

- The pipeline keyword marks for the beginning of your pipeline definition.

```groovy
pipeline {
	agent any // docker { image 'ubuntu:alpine' }
}
```

- Then we have agent directive which specifies the the execution environment for your pipeline stages.
- Common options include `any` or `docker`.
- So if we include `any` so it would run on any available Jenkins agent including the Jenkins controller.
- You can also make use of Docker build agents by specifying Docker and a Docker image and pipeline will run within that Docker container.

```groovy
pipeline {
	agent any // docker { image 'ubuntu:alpine' }
	stages {
	
	}
}
```

- Stages refer to an entire concept of structuring your pipeline into different phases.
- Within stages you can one or more stages.

```groovy
pipeline {
	agent any // docker { image 'ubuntu:alpine' }
	stages {
		stage('Building') {
		
		} 
		stage('Unit Testing') {
		
		}
		stage('Deployment') {
		
		}
	}
}
```

- And within the stages we can have one or more steps.
- The steps block within stage lists the individual commands or actions to be executed in that stage.
- Steps can involve shell commands, it can also have Jenkins pipeline domain specific language commands like script.
- Also we can use third party libraries like JUnit or other options within the steps as well.

```groovy
pipeline {
	agent any // docker { image 'ubuntu:alpine' }
	stages {
		stage('Building') {
			agent { docker 'ubuntu:alpine' }
			steps {
				sh 'mvn clean package'
			}
		} 
		stage('Unit Testing') {
			steps {
				script {
					junit 'target/surefire-reports/*.xml'
				}
			}
		}
		stage('Deployment') {
			when {
				expression { branch == 'main' }
			}
			steps {
				sh 'deploy.sh'
			}
		}
	}
}
```


#### Jenkins Directives

- `Environment Directive`

```groovy
pipeline {
	environment {
		VAR1 = 'foo'
		VAR2 = 'bar'
	}
	stages {
		stage('Build') {
			steps {
				sh 'echo $VAR1' // result = foo
			}
		}
		stage('Test') {
			environment { VAR1 = 'test' }
			steps {
				sh 'echo $VAR1' // result = test
			}
		}
	}
}
```

- Environment directive defines key value pairs to set environment variables for all stages or certain stages depending on the placement.

- `Post Directive`

```groovy
pipeline {
	// ... pipeline stages
	post {
		success {
			script {
				// Send success notification
			}
		}
		failure {
			script {
				// Send failure notification
			}
		}
	}
}
```

- Which executes one or more steps after a pipeline run finishes, regardless of the success or failure of the pipeline status.
- We can clean up temp files or sending notifications using slack after the pipeline has completed.
- Using the plugins like Slack Notifier.

```groovy
pipeline {
	// ... pipeline stages
	post {
		always {
			slackNotifier {
				channel: '#your-slack-channel',
				message: '${curentBuild.result}'
			}
		}
	}
}
```

- `Script Directive`

```groovy
pipeline {
	stages {
		stage('Process Files') {
			script {
				files = ['file1.txt','file2.txt']
				files.each { file ->
					sh "echo Processing $file"
				}
			}
		}
	}
}
```

- It can be used to encapsulate a block of Groovy code for more complex logic within a step.
- It provides access variables, methods, and jenkins functionalities.

- `When Directive`

```groovy
pipeline {
	stages {
		stage('Deploy') {
			when {
				expression { branch == 'main' }
			}
			// deployment steps
		}
	}
}
```

- The when directive defines conditions under which a stage should be executed. 
- It can commonly be used for conditional branching.

- `Credentials Directive`

```groovy
pipeline {
	agent any 
		stages {
			stage('Example') {
				steps {
					withCredentials([credentialsId: 'myCredentials'])
					echo "Username: $USERNAME"
				}
			}
		}
}
```

- It provides access to predefined credentials stored in Jenkins, like the API keys, passwords, or any secret files.
- It can be used with tools or scripts that require authentication.

- `Interactive Input Directive`

```groovy
input {
	message 'Are you sure you wnat to deploy?'
	ok 'Yes'
	cancel 'No'
}
```

- It is an interactive directive allow users to provide input during pipeline execution through an UI.
- It requires a plugin called `Pipeline Utility Steps` plugin.

- `Parameters Directive`

```groovy
pipeline {
	paramters {
		string(name: 'ENV_NAME', defaultValue: 
		'dev', description: 'Environmentto deploy to')
	}
	// ... pipeline stages
	environment {
		ENV = params.ENV_NAME
	}
}
```

- These can be used for defining parameters that can be passed to the pipeline during execution, allowing for dynamic configuration.

- `Stash and Unstash Directive`

```groovy
pipeline {
	stages {
		stage('Build') {
			// ... build steps
			stash name: 'build-artefacts'
		}
		stage('deploy') {
			unstash name: 'build-artefacts'
			// .. deployment steps using stashed artefacts
		}
	}
}
```

- This directive can store and retrieve artefacts.
- It could be files, build outputs between pipeline stages or jobs running on different nodes.
- It is useful for caching build results or sharing data across jobs.

- `Parallel Stage`

```groovy
pipeline {
	parallel {
		stage('Unit Testing') {
			// .. unit test steps
		}
		stage('Vurenability Testing') {
			unstash name: 'build-artefacts'
			// .. vurenability test steps
		}
	}
}
```

- It executes multiple stages concurrently to optimize pipeline execution time.
- It requires stages to be independent and not rely on outputs from each other.