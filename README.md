# kubernetes-getting-started

### install minikube

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube start

minikube dashboard

kubectl config view # Show Merged kubeconfig settings.
kubectl config get-contexts # display list of contexts
kubectl config current-context # display the current-context
kubectl config use-context my-cluster-name # set the default context to my-cluster-name

kubectl get ns -A

kubectl get pods -A

kubectl apply -f cloudClassNameSpace.yml

kubectl apply -f helloWorldDeployment.yml

kubectl get pods --all-namespaces # List all pods in all namespaces

kubectl get pods -n cloudclass # List all pods in cloudclass namespace

kubectl get pods # List all pods in the namespace

kubectl get pod my-pod -o yaml # Get a pod's YAML

kubectl get pods -o wide # List all pods in the current namespace, with more details

kubectl get deployments

kubectl get deployments -n cloudclass

kubectl get deployment my-dep # List a particular deployment

kubectl get services -A # List all services in all namespaces

kubectl get services # List all services in the namespace

kubectl get services -n cloudclass # List all services in cloudclass namespace

### describe the containers running inside a pod

kubectl describe pods <pod name>

kubectl get events -n cloudclass # View cluster events

kubectl config view # View the kubectl configuration

### Port forward service hello-world-service which points to port 8080 in cloudclass namespace to port 8080

kubectl port-forward service/hello-world-service -n cloudclass 8080:8080

### Port forward service hello-world-service which points to port 80 in cloudclass namespace to port 8080

kubectl port-forward service/hello-world-service -n cloudclass 8080:80

// how to delete a deployment
kubectl delete deployment nginx-deployment

kubectl get storageclass

### enabling ingress addon in k8 cluster

minikube addons enable ingress

### enabling metrics-server addon in k8 cluster

minikube addons enable metrics-server

### Rolling restart of the "hello-world" deployment

k rollout restart deployment/hello-world -n cloudclass

// check history of deployment rollouts
kubectl rollout history deployment/hello-world -n cloudclass

### run nginx pod at port 8080 from k8

kubectl apply -f nginxPod.yml
kubectl port-forward nginx 8080:80

### run nginx deployment at port 8080 from k8

k apply -f nginxDeployment.yml
k port-forward deployment/nginx-deployment 8080:80

### run nginx service at port 8080 from k8

k apply -f nginxService.yml
kubectl port-forward service/nginx-service 8080:8080

### run sh inside an nginx pod in k8

k exec -it nginx-deployment-66978d954c-rkw4x -c nginx -- /bin/sh

### create a statefulset with a headless service

k apply -f nginxStatefulSet
k port-forward statefulset/nginx-statefulset 8080:80

// daemonsets run the application on each node instead of using replicas to scale up
kubectl get daemonsets -n cloudclass
// check how to delete a daemonset
// check how to delete a replicaset

// check the jobs to run pi till the 2000th decimal place
kubectl describe jobs/pi
