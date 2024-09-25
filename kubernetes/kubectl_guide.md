# Kubectl Command Guide

## Cluster Management

1. Get cluster information:
   ```
   kubectl cluster-info
   ```

2. Get API versions:
   ```
   kubectl api-versions
   ```

3. Get API resources:
   ```
   kubectl api-resources
   ```

## Viewing Resources

4. List all resources in the cluster:
   ```
   kubectl get all
   ```

5. List specific resource type (e.g., pods, services, deployments):
   ```
   kubectl get pods
   kubectl get services
   kubectl get deployments
   ```

6. Get detailed information about a specific resource:
   ```
   kubectl describe pod <pod-name>
   kubectl describe service <service-name>
   ```

## Creating and Updating Resources

7. Create a resource from a file:
   ```
   kubectl create -f <filename.yaml>
   ```

8. Apply a configuration to a resource:
   ```
   kubectl apply -f <filename.yaml>
   ```

9. Edit a resource:
   ```
   kubectl edit <resource-type> <resource-name>
   ```

## Deleting Resources

10. Delete a resource:
    ```
    kubectl delete <resource-type> <resource-name>
    ```

11. Delete all resources of a type:
    ```
    kubectl delete <resource-type> --all
    ```

## Scaling

12. Scale a deployment:
    ```
    kubectl scale deployment <deployment-name> --replicas=<number>
    ```

## Logs and Debugging

13. View logs for a pod:
    ```
    kubectl logs <pod-name>
    ```

14. Execute a command in a container:
    ```
    kubectl exec -it <pod-name> -- <command>
    ```

15. Port forwarding to a pod:
    ```
    kubectl port-forward <pod-name> <local-port>:<pod-port>
    ```

## Namespaces

16. List namespaces:
    ```
    kubectl get namespaces
    ```

17. Set the default namespace for kubectl:
    ```
    kubectl config set-context --current --namespace=<namespace-name>
    ```

## Context and Configuration

18. View kubeconfig:
    ```
    kubectl config view
    ```

19. Switch context:
    ```
    kubectl config use-context <context-name>
    ```

## Helpful Options

- `-n <namespace>`: Specify namespace
- `-o wide`: Output additional information
- `-o yaml`: Output in YAML format
- `-o json`: Output in JSON format
- `--dry-run=client`: Simulate the command without making changes

Remember to replace placeholders like `<pod-name>`, `<service-name>`, etc., with actual resource names when using these commands.