# Ingress Controller

The traffic to the cluster should be controlled by ingress rules to avoid the
need of load balancers, which are too expensive. The basic idea is to use a
node's public ip(normally free) as the only gateway. The ingress controller
should forward requests based on ingress rules defined in the native k8s ingress
objects.

My choice of controller is nginx as it has the best performance and smallest
footprint.

# Usage

Here stated how I used it in my own cluster.

## Prerequisite

1. helm and kubectl
1. A k8s cluster with at least 1 node with public ip

## Setup Controller

1. `helm repo add nginx-stable https://helm.nginx.com/stable && helm repo update`
1. ```sh
    # run from root dir of this repo
    helm install nginx-ingress nginx-stable/nginx-ingress --create-namespace -n nginx-ingress -f ./ingress-controller/values.yaml
   ```

## Test Ingress
