Project: Automated Container Vulnerability Scanning & Secure Deployment on AWS

This is a hands-on project demonstrating proactive vulnerability management for containerized applications using the AWS cloud-native toolchain.

Goal: To build, scan, and deploy a container, proving the ability to identify and secure the container pipeline before deployment.

This demo also shows the real-world process of debugging a failed container deployment by analyzing logs, patching a dependency vulnerability (Flask/Werkzeug incompatibility), and pushing a fixed image.

The Process

Containerize: A simple Python Flask application was containerized using Docker. (See Dockerfile)

Push & Scan: The Docker image was pushed to AWS Elastic Container Registry (ECR).

Secure: The ECR registry was configured with "Enhanced scanning" and a filter to "Scan on push" for the wiz-secure-app repository, automatically discovering known software vulnerabilities (CVEs).

Deploy: The scanned image was deployed as a serverless container using AWS Fargate and Elastic Container Service (ECS).

DEMO 1: The "Setup" - Configuring the Scan

First, the ECR registry was configured with an "Enhanced scanning" rule. This rule was set to trigger a "Scan on push" for any image pushed to the wiz-secure-app repository.

![Screenshot of ECR Scan Configuration](https://github.com/mymanerik/aws-container-security-demo/blob/master/Screen%20Shot%201.png?raw=true)

DEMO 2: The "Result" - The Vulnerability Report

After pushing the container, the scan ran automatically and found 1 High, 1 Medium, and 1 Low vulnerability in the container image and its base layers. This proves the ability to catch CVEs before deployment.

![Screenshot of The Vulnerability Report](https://github.com/mymanerik/aws-container-security-demo/blob/master/Screen%20Shot%202.png?raw=true)

DEMO 3: The "Proof" - The Final Deployment

After debugging and pushing a fixed image, the container was successfully deployed to a serverless AWS Fargate task. The application is live and accessible via its public IP address on port 5000.

![Screenshot of Final Deployment](https://github.com/mymanerik/aws-container-security-demo/blob/master/Screenshot%203.png?raw=true)

Skills Demonstrated

Container Security: Proactive vulnerability scanning (CVEs) using AWS ECR.

Container Orchestration: Serverless container deployment with AWS Fargate & ECS.

Cloud-Native Debugging: Analyzed CloudWatch logs to diagnose and fix a container crash (ImportError due to dependency conflict).

CI/CD Pipeline: Manually simulated a CI/CD flow (Build, Scan, Tag, Push, Deploy).

AWS Services: ECR, ECS, Fargate, IAM Roles, Security Groups, CloudWatch Logs.

Infrastructure as Code (IaC): Docker (Dockerfile).
