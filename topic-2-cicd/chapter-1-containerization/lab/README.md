# Chapter 1 Labs

## Introduction
This lab introduces the concepts of containerization with Docker and the use of AWS Elastic Container Registry (ECR) as a shared container registry. You'll gain hands-on experience by containerizing a React application and pushing the container image to a shared registry. This exercise is crucial for understanding how applications are packaged and distributed in a DevSecOps workflow.

## Prerequisites

### Tools

Before you begin this lab, ensure you have the following tools installed and ready on your machine:

| Name          | Description                                                                                    | Installation Guide |
|---------------| ---------------------------------------------------------------------------------------------- | ------------------ |
| Docker        | Used for building and running containerized applications.                                      | [Download Link](https://docs.docker.com/get-docker/) |
| Node.js       | To run the React application locally.                                                          | [Download Link](https://nodejs.org/en/download)|
| Git           | For version control and forking the reference application repository.                          | [Download Link](https://git-scm.com/downloads)|
| AWS CLI       | To interact with Amazon Web Services and push images to a shared container registry (AWS ECR). | [Download Link](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) |
| Wireguard VPN | For establishing a VPN tunnel to connect to the internal network.                              | [Download Link](https://www.wireguard.com/install/) |

### Skills and Knowledge
Below are the skills and knowledge expected to successfully complete the lab exercises:
- Basic command-line operations: You are comfortable navigating and executing commands in a terminal.
- Basic Git operations: cloning, forking, committing, pushing.
- Basic React knowledge: You understand how to run a React application locally

## Labs Overview

| Topic                                          | Link to Lab                                  |
|------------------------------------------------|----------------------------------------------|
| Containerizing a React Application            | [Lab 1 Markdown File](lab1.md)      |
| Connecting to the Internal Network & Pushing Image to AWS ECR | [Lab 2 Markdown File](lab2.md) |
