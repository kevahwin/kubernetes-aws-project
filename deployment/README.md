# Kubernetes Configuration
This folder focuses on creating and applying deployment files with Kubernetes.

The codebase contains the analytics API for a co-working space microservice application. 


## Instructions
### 1. Provision Enough Nodes In Your Cluster
Depending on the instance types used in your cluster, your may need to provision more nodes for the pods to have enough resources to run. If you have lightweight EC2 instances running in your EKS cluster, I recommend increasing the maximum size of your Node Group to 2 nodes.

### 2. Apply the Existing Configs
Create the resources in your Kubernetes environment. Multiple deployments can be applied by running:
```bash
kubectl -f apply deployment/
```

You can review the status of your apply with the following commands:
```bash
kubectl get services
kubectl get pods
```

Your pod should have a `Status` of `Running` if the configuration was successful.
