# Lab: Configuring a Simple Jenkins Pipeline

## Introduction
In this lab, you will automate the process of building, and deploying a Dockerized application using Jenkins. Building upon the manual processes you learned in Chapter 1, you will create a very simple Jenkins pipeline that automates these tasks.

## Accessing the Corporate Network via VPN
> :warning: This lab requires the lab infrastructure to be set up by an instructor or administrator. Independent learners should refer to the [lab setup repository](https://github.com/open-devsecops/lab-infra-setup/tree/main/topic-2-cicd-lab/aws) to configure this environment accordingly.

**VPN Configuration and Connection:**
- Download the VPN configuration file from `http://{public_ip}:7779`. Ask the lab administrator for the public ip of the internal network, and replace the `{public_ip}` placeholder.
- Import the VPN configuration file into the Wireguard Client to establish the VPN connection. This step provides access to internal services.

**Navigate to the Dashboard:**
- With the VPN connection established, access `http://dashboard.internal` on your browser. This internal service dashboard is your gateway to various corporate resources.

## Accessing Jenkins
Once you're connected to the VPN, navigate to `http://jenkins.internal` in your browser to access the Jenkins dashboard. The default credentials can be found below:
- **Username:** student
- **Password:** student1!

## Creating a Pipeline in Jenkins
- Create a New Item: From the Jenkins dashboard, select "New Item" at the top left.
- Name Your Pipeline: Enter a name for your project, and select "Pipeline" as the type.

**Configure the Pipeline:**

In the General section, choose "GitHub project" and enter the GitHub repository URL.
- If you haven't already from the previous lab, fork the reference application repository and enter the forked repo URL.

In the Pipeline section, choose "Pipeline script from SCM" for the Definition.
- Select "Git" as the SCM.
- Enter the repository URL of your forked version of the reference application.
- Change Branch Specifier from `*/master` to `*/main`.

Click `apply` and `save`.

## Setting Up Webhooks
Webhooks allow GitHub to notify Jenkins about code changes, triggering the pipeline we have created.

**Configure Webhooks:**
- Go to your forked repository on GitHub, navigate to "Settings" > "Webhooks" > "Add webhook."
- Enter the URL provided on the `http://dashboard.internal` page into the Payload URL in GitHub Webhooks creation page.
- Select `application/json` as the Content Type.
- Save your webhook. This setup ensures Jenkins is notified on every code push, automating the build process.


## Creating the Jenkinsfile
The Jenkinsfile defines different stages in your CI/CD pipeline.

[Instructions for creating the Jenkinsfile]

<details>
<summary><b>The Complete Jenkinsfile</b></summary>

```Groovy
pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'docker build . -t $AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com/<image-name>'
            }
        }
        stage('Push Image') {
            steps {
                sh 'aws ecr get-login-password --region $REGION | docker login --username AWS --password-stdin $AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com'
                sh 'aws ecr describe-repositories --repository-names <repository-name> || aws ecr create-repository --repository-name <repository-name>'
                sh 'docker push $AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com/<image-name>'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker pull $AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com<image-name>'
                sh 'docker rm -f <container-name> || true'
                sh 'docker run -d -p "<host-port>:80" --name <container-name> $AWS_ACCOUNT_ID.dkr.ecr.$REGION.amazonaws.com/<image-name>'
            }
        }
    }
}
```
</details>