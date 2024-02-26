# Lab: Containerizing a React Application

## Learning Objectives
- Creating a Docker image of a React application
- Run the Docker image locally
- Interact with a running Docker container
- Understand Docker container isolation

## Step 1: Fork and Clone the Reference Application
1. **Fork the Repository:** Navigate to the [reference application](https://github.com/open-devsecops/topic-2-lab-reference-app) and fork the repository to your own GitHub account.
2. **Clone Your Fork:** Open your terminal and clone the forked repository to your local machine using `git clone <your-fork-url>`.

## Step 2: Run the React Application Locally

1. **Navigate to the Project Directory:** Move into the project directory in your terminal.
2. **Install Dependencies:** Run `npm install` to install the required node modules for the project.
3. **Start the Application:** Enter `npm start` to run the application locally. Your default web browser should automatically open to `http://localhost:3000`, displaying the reference application.

## Step 3: Containerize the Application

