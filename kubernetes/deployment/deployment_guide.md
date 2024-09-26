# Kubectl Imperative Deployment Commands

## Creating a Deployment

1. Create a simple deployment:
   ```
   kubectl create deployment my-dep --image=nginx
   ```

2. Create a deployment with a specific number of replicas:
   ```
   kubectl create deployment my-dep --image=nginx --replicas=3
   ```

3. Create a deployment and expose it as a service:
   ```
   kubectl create deployment my-dep --image=nginx --port=80
   ```

## Scaling a Deployment

4. Scale a deployment:
   ```
   kubectl scale deployment my-dep --replicas=5
   ```

## Updating a Deployment

5. Set a new image:
   ```
   kubectl set image deployment/my-dep nginx=nginx:1.9.1
   ```

6. Edit a deployment:
   ```
   kubectl edit deployment my-dep
   ```

## Rolling Update and Rollback

7. Perform a rolling update:
   ```
   kubectl set image deployment/my-dep nginx=nginx:1.9.1 --record
   ```

8. Check the status of a rollout:
   ```
   kubectl rollout status deployment/my-dep
   ```

9. Rollback to the previous version:
   ```
   kubectl rollout undo deployment/my-dep
   ```

10. Rollback to a specific revision:
    ```
    kubectl rollout undo deployment/my-dep --to-revision=2
    ```

## Pausing and Resuming a Deployment

11. Pause a deployment:
    ```
    kubectl rollout pause deployment/my-dep
    ```

12. Resume a paused deployment:
    ```
    kubectl rollout resume deployment/my-dep
    ```

## Deleting a Deployment

13. Delete a deployment:
    ```
    kubectl delete deployment my-dep
    ```

## Helpful Options

- `--dry-run=client -o yaml`: Generate the deployment YAML without creating it
- `-o wide`: Provide more details in the output
- `--record`: Record the command in the resource annotation

Remember to replace `my-dep` with your actual deployment name when using these commands.