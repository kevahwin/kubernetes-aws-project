# Kubernetes Deployment Guide

This project uses Kubernetes for deploying the co-working space analytics API microservice. Below is a quick guide to understand the deployment process.

## Tools & Technologies

- **AWS ECR**: Stores Docker images. The latest app version is pushed here after every build.
- **AWS CodeBuild**: Automates the process of building Docker images and pushing them to ECR.
- **Kubernetes (EKS)**: Manages the application and ensures high availability, scaling, and resilience.
- **kubectl**: Command-line tool for interacting with Kubernetes, used to deploy and manage resources.

## Deployment Process

### 1. **Provisioning Nodes**
   Ensure your Kubernetes cluster has enough resources (nodes). For lightweight EC2 instances, increasing the maximum node count to 2 is recommended.

### 2. **Apply Kubernetes Configs**
   To deploy the application, use the following command:

   ```bash
   kubectl apply -f deployment/
   ```
## Monitor the Deployment Status

Monitor the deployment status with:

```bash
kubectl get services
kubectl get pods
```

Once your pods are ready and running, the application is live.

## 3. Releasing New Versions

1. Commit and push code changes to GitHub.
2. Trigger a build in AWS CodeBuild, which will:
   - Build the Docker image.
   - Tag it with the build number.
   - Push it to AWS ECR.
3. Update the deployment with the new image:

Once the image is pushed to ECR, Kubernetes will pull the new image and deploy it. Ensure that the deployment file in Kubernetes is set to use the correct image repository and tag, such as:

```bash
image: <ECR_REPO_URI>/<REPO_NAME>:<IMAGE_TAG>
```


## 4. Health Checks

The deployment includes:
- **Liveness Probe**: Ensures the app is running.
- **Readiness Probe**: Ensures the app is ready to serve traffic.

Kubernetes uses these probes to automatically restart or stop traffic to the pod if necessary.

