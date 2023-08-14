# local-k8

## Steps to reproduce the exercise

1. Create cluster with Kind: `kind create cluster --name first-cluster --config config/kind.config.yaml --wait 5m`
   - 1.1 Validate for the cluster creation: `kind get clusters`
   - 1.2 Get cluster info: `kubectl cluster-info --context kind-first-cluster`
   - 1.3 If you need to delete a cluster: `kind delete cluster -n first-cluster`
   - 1.4 The cluster is created with the "default" namespace, if you want to create a custome namespace: `kubectl create namespace local-cluster`
         - 1.4.1 To show all available namespaces: `kubectl get namespace`

2. Deploy a test application: `kubectl apply -f manifests/hello_world_deploy.yaml`
   - 2.1 Verify the pod creation where the app is: `kubectl get pods`
   - 2.2 Check the logs container: `kubectl logs example1-54cc46b7d5-b7rfn`

3. Create a service to acces to the pod througg the port defined: `kubectl apply -f manifests/hello_world_service.yaml`
   - 2.1 Verify the service creation: `kubectl get services`
   - 2.2 Open localhost page in browser to see the pod running

Note: this exercise was based in the following [tutorial](https://www.appvia.io/blog/tutorial-deploy-kubernetes-cluster/)

