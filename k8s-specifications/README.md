# Kubernetes Specifications for Portfolio Application

This directory contains Kubernetes manifests for deploying the portfolio application.

## Files

- `namespace.yml` - Creates a dedicated namespace for the portfolio application
- `portfolio-deployment.yml` - Deployment configuration for the application
- `portfolio-service.yml` - Service to expose the application
- `portfolio-configmap.yml` - Environment variables for the application
- `portfolio-ingress.yml` - Ingress configuration for external access
- `portfolio-hpa.yml` - Horizontal Pod Autoscaler for automatic scaling
- `kustomization.yml` - Kustomize configuration for managing all resources

## Deployment Instructions

### Using kubectl directly

```bash
# Create namespace first
kubectl apply -f namespace.yml

# Apply all resources
kubectl apply -f portfolio-configmap.yml
kubectl apply -f portfolio-deployment.yml
kubectl apply -f portfolio-service.yml
kubectl apply -f portfolio-ingress.yml
kubectl apply -f portfolio-hpa.yml
```

### Using Kustomize

```bash
# Apply all resources using kustomize
kubectl apply -k .
```

## Accessing the Application

- NodePort: The application is exposed on port 31003 on any node in the cluster
- Ingress: If you have an ingress controller set up, the application will be available at portfolio.example.com

## Scaling

The application is configured to automatically scale between 2 and 5 replicas based on CPU utilization.

## Configuration

Update the ConfigMap to change environment variables for the application.
