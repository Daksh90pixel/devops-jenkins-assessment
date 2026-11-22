# Task 3 – Jenkins CI/CD

## What I did

For this task, I created a simple HTML application and set up a Jenkins pipeline to automate its checkout, validation, build and deployment.

I used Jenkins through Docker Desktop on my Ubuntu WSL2 environment.

## Tools used

- Ubuntu 26.04.1 LTS (WSL2)
- Bash 5.3.9
- Docker 29.8.1
- Jenkins 2.580.2
- Java 21.0.13
- Git

## Project files

```text
task-3-jenkins/
├── app/
│   └── index.html
├── Jenkinsfile
└── README.md
```

## GitHub

I created a Git repository and pushed my application and Jenkinsfile to GitHub.

Repository: https://github.com/Daksh90pixel/devops-jenkins-assessment

I used the `main` branch for this task.

## Jenkins pipeline

I created a Jenkins job called `devops-jenkins-pipeline` and connected it to my GitHub repository.

The job uses **Pipeline script from SCM**, with Git as the source and `Jenkinsfile` as the script path.

The pipeline has four stages:

- **Checkout:** Gets the source code from GitHub.
- **Validate:** Checks whether `app/index.html` exists and is not empty.
- **Build:** Creates `app-build.tar.gz` from the application folder.
- **Deploy:** Copies the archive to a test directory inside the Jenkins container.

The deployment directory is:

`$JENKINS_HOME/devops-lab/deploy`

I used this location for testing, not for a production deployment.

## Running the job

I opened Jenkins at `http://localhost:8081` and started the job using **Build Now**.

The pipeline completed successfully. I saved screenshots of the build result, console output and stage view in the evidence folder.

## Trigger

I used a manual build. Since Jenkins was running locally on my computer at `localhost:8081`, GitHub could not directly reach it for a webhook trigger.

## Security

I did not put any passwords or access tokens in the Jenkinsfile. I used GitHub authentication when pushing the repository.

## Limitations

This is a local demonstration. The application archive is copied into the Jenkins container's test directory; it is not deployed to a live server.

A failed pipeline console run still needs to be captured.

## AI assistance

I used ChatGPT for guidance while setting up Git and Jenkins and for troubleshooting. I ran the commands and tested the pipeline in my own environment.
