
# Kubernetes Documentation

**Description:** Detailed documentation on Kubernetes, including installation, configuration, management, troubleshooting, monitoring, and advanced commands.

## Overview
- **What is Kubernetes?**
  Kubernetes is an open-source container orchestration platform designed to automate deploying, scaling, and operating application containers.

- **Key Features**
  - Automated container deployment
  - Self-healing
  - Horizontal scaling
  - Load balancing
  - Storage orchestration

## Installation

### Minikube (Local Development)
- **Install Minikube**
  ```sh
  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
  sudo install minikube-darwin-amd64 /usr/local/bin/minikube
  ```
- **Start Minikube**
  ```sh
  minikube start
  ```

### Kubernetes on AWS (EKS)
- **Create EKS Cluster**
  ```sh
  aws eks create-cluster --name my-cluster --role-arn <role-arn> --resources-vpc-config subnetIds=<subnet-ids>,securityGroupIds=<sg-ids>
  ```
- **Update kubeconfig**
  ```sh
  aws eks update-kubeconfig --name my-cluster
  ```

### Kubernetes on Azure (AKS)
- **Create AKS Cluster**
  ```sh
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys
  ```
- **Get AKS Credentials**
  ```sh
  az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
  ```

## Configuration

### Deployments
- **Create Deployment**
  ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: my-deployment
  spec:
    replicas: 3
    selector:
      matchLabels:
        app: my-app
    template:
      metadata:
        labels:
          app: my-app
      spec:
        containers:
        - name: my-container
          image: nginx
          ports:
          - containerPort: 80
  ```
  **Apply Deployment**
  ```sh
  kubectl apply -f deployment.yaml
  ```

### Services
- **Create Service**
  ```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: my-service
  spec:
    selector:
      app: my-app
    ports:
      - protocol: TCP
        port: 80
        targetPort: 80
    type: LoadBalancer
  ```
  **Apply Service**
  ```sh
  kubectl apply -f service.yaml
  ```

## Management

### Scaling
- **Scale Deployment**
  ```sh
  kubectl scale deployment my-deployment --replicas=5
  ```

### Rollouts
- **View Rollout Status**
  ```sh
  kubectl rollout status deployment/my-deployment
  ```
- **Rollback Deployment**
  ```sh
  kubectl rollout undo deployment/my-deployment
  ```

### Updating
- **Update Deployment Image**
  ```sh
  kubectl set image deployment/my-deployment my-container=nginx:latest
  ```

## Troubleshooting

### Common Issues
- **Check Pod Status**
  ```sh
  kubectl get pods
  ```
- **Describe Pod**
  ```sh
  kubectl describe pod <pod-name>
  ```
- **View Pod Logs**
  ```sh
  kubectl logs <pod-name>
  ```

### Debugging
- **Access Container Shell**
  ```sh
  kubectl exec -it <pod-name> -- /bin/bash
  ```

## Monitoring

### Metrics Server
- **Install Metrics Server**
  ```sh
  kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
  ```
- **View Metrics**
  ```sh
  kubectl top nodes
  kubectl top pods
  ```

### Logs
- **View Logs for All Pods**
  ```sh
  kubectl logs --all-containers=true --namespace=<namespace>
  ```

## Advanced Commands

### Custom Resources
- **Create Custom Resource Definition (CRD)**
  ```yaml
  apiVersion: apiextensions.k8s.io/v1
  kind: CustomResourceDefinition
  metadata:
    name: examples.mydomain.com
  spec:
    group: mydomain.com
    names:
      kind: Example
      listKind: ExampleList
      plural: examples
      singular: example
    scope: Namespaced
    versions:
    - name: v1
      served: true
      storage: true
  ```
  **Apply CRD**
  ```sh
  kubectl apply -f crd.yaml
  ```

### Port Forwarding
- **Forward Local Port to Pod**
  ```sh
  kubectl port-forward pod/<pod-name> 8080:80
  ```

### ConfigMaps and Secrets
- **Create ConfigMap**
  ```sh
  kubectl create configmap my-config --from-literal=key1=value1
  ```
- **Create Secret**
  ```sh
  kubectl create secret generic my-secret --from-literal=password=secretpassword
  ```

## Scenarios

### Scenario 1: Blue-Green Deployment
- **Blue Deployment**
  ```sh
  kubectl apply -f blue-deployment.yaml
  ```
- **Switch to Green Deployment**
  ```sh
  kubectl apply -f green-deployment.yaml
  ```

**Example Output:**
```sh
kubectl get deployments
NAME             READY   UP-TO-DATE   AVAILABLE   AGE
blue-deployment  3/3     3            3           10m
green-deployment 0/3     3            0           1m
```

### Scenario 2: Rolling Update
- **Perform Rolling Update**
  ```sh
  kubectl set image deployment/my-deployment my-container=my-image:v2
  ```

**Example Output:**
```sh
deployment.apps/my-deployment image updated
```

## Best Practices
- **Resource Limits**
  Always set resource requests and limits for containers to ensure efficient resource utilization.
- **Namespace Management**
  Use namespaces to organize resources and manage access control.
- **Backup and Restore**
  Implement backup strategies for critical data and configurations.

```
