# NGINX Ingress Controller for Kubernetes

This guide provides detailed instructions for installing and configuring the NGINX Ingress Controller on a Kubernetes cluster using Helm.

## Overview

The NGINX Ingress Controller is an implementation of a Kubernetes Ingress controller for NGINX and NGINX Plus. It allows you to:
- Route external HTTP/HTTPS traffic to your Kubernetes services
- Handle TLS/SSL termination
- Configure load balancing rules
- Manage traffic routing based on URLs and hostnames

## Prerequisites

Before installation, ensure you have:
- A running Kubernetes cluster
- Helm 3.x installed
- `kubectl` configured to communicate with your cluster
- Cluster administrator permissions

## Installation

### 1. Add the Helm Repository

```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
```

### 2. Install NGINX Ingress Controller

```bash
helm install ingress-nginx ingress-nginx/ingress-nginx \
  --namespace ingress-nginx \
  --create-namespace \
  --set controller.service.type=LoadBalancer \
  --set controller.service.ports.http=80 \
  --set controller.service.ports.https=443
```

### Configuration Parameters Explained

- `--namespace ingress-nginx`: Creates and uses a dedicated namespace
- `--create-namespace`: Automatically creates the namespace if it doesn't exist
- `--set controller.service.type=LoadBalancer`: Exposes the ingress controller using a cloud provider's load balancer
- `--set controller.service.ports.http=80`: Sets HTTP port to 80
- `--set controller.service.ports.https=443`: Sets HTTPS port to 443

## Verification

Check if the installation was successful:

```bash
kubectl get pods -n ingress-nginx
```

Verify the LoadBalancer service:

```bash
kubectl get svc -n ingress-nginx
```

## Basic Usage

### Example Ingress Resource

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: nginx
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: example-service
            port:
              number: 80
```



## Additional Resources

- [Official Documentation](https://kubernetes.github.io/ingress-nginx/)
- [GitHub Repository](https://github.com/kubernetes/ingress-nginx)
- [Helm Chart Documentation](https://github.com/kubernetes/ingress-nginx/tree/main/charts/ingress-nginx)