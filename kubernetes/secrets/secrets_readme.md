# Creating Secrets of different types

## Generic secret
kubectl create secret generic my-secret --from-literal=key1=value1 --from-literal=key2=value2

## Docker registry secret
kubectl create secret docker-registry my-registry-secret \
  --docker-server=DOCKER_REGISTRY_SERVER \
  --docker-username=DOCKER_USER \
  --docker-password=DOCKER_PASSWORD \
  --docker-email=DOCKER_EMAIL

## TLS secret
kubectl create secret tls my-tls-secret --cert=path/to/cert.pem --key=path/to/key.pem

## Generic secret from file
kubectl create secret generic my-file-secret --from-file=path/to/file

## Generic secret from env file
kubectl create secret generic my-env-secret --from-env-file=env/env.properties

# Updating Secrets

## Update a secret
kubectl create secret generic my-secret --from-literal=key1=newvalue1 --from-literal=key2=newvalue2 -o yaml --dry-run=client | kubectl apply -f -

## Patch a secret
kubectl patch secret my-secret -p '{"stringData": {"key1": "newvalue1"}}'

# Deleting Secrets

## Delete a specific secret
kubectl delete secret my-secret

## Delete all secrets in the current namespace
kubectl delete secrets --all

## Delete secrets using a label selector
kubectl delete secrets -l app=myapp