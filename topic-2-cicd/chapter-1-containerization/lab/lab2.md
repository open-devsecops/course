# Lab: Accessing Corporate Network and AWS ECR

## Learning Objectives
- Establish a VPN connection to access the corporate internal network.
- Use internal services to generate temporary AWS IAM credentials.
- Authenticate and push Docker images to a company-shared AWS Elastic Container Registry (ECR).
- Demonstrate understanding of AWS IAM roles and permissions by using an assumed role for Docker operations.

## Introduction
This lab simulates a common industry practice where developers need to access corporate resources securely via a VPN. You'll will be using the internal services available to generate temporary credentials for AWS services, allowing you to push Docker images to a company-shared AWS Elastic Container Registry (ECR).

## Accessing the Corporate Network via VPN
> :warning: This lab requires the lab infrastructure to be set up by an instructor or administrator. Independent learners should refer to the [lab setup repository](https://github.com/open-devsecops/lab-infra-setup/tree/main/topic-2-cicd-lab/aws) to configure this environment accordingly.