# Creating ConfigMaps

## Create ConfigMap from literal values
kubectl create configmap my-config --from-literal=key1=value1 --from-literal=key2=value2

## Create ConfigMap from file
kubectl create configmap my-config --from-file=path/to/file

## Create ConfigMap from directory
kubectl create configmap my-config --from-file=path/to/directory

## Create ConfigMap from env file
kubectl create configmap my-config --from-env-file=path/to/env.file

# Updating ConfigMaps

## Update a ConfigMap
kubectl create configmap my-config --from-literal=key1=newvalue1 --from-literal=key2=newvalue2 -o yaml --dry-run=client | kubectl apply -f -

## Patch a ConfigMap
kubectl patch configmap my-config -p '{"data":{"key1":"newvalue1"}}'

## Edit a ConfigMap
kubectl edit configmap my-config

# Viewing ConfigMaps

## Get all ConfigMaps
kubectl get configmaps

## Describe a specific ConfigMap
kubectl describe configmap my-config

## View the contents of a ConfigMap
kubectl get configmap my-config -o yaml

# Deleting ConfigMaps

## Delete a specific ConfigMap
kubectl delete configmap my-config

## Delete all ConfigMaps in the current namespace
kubectl delete configmaps --all

## Delete ConfigMaps using a label selector
kubectl delete configmaps -l app=myapp
