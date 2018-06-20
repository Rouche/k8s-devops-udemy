# k8s-devops-udemy

https://github.com/jleetutorial/kubernetes-demo

Kubernetes:
https://kubernetes.io/docs/imported/release/notes/

Cheat sheet:
https://kubernetes.io/docs/reference/kubectl/cheatsheet/

References:
https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands


## Setup

Facebook: https://www.facebook.com/groups/1911219079195863/

### downloads and install

Minikube: https://github.com/kubernetes/minikube/releases

Kubectl: https://kubernetes.io/docs/imported/release/notes/

Or:  
```https://storage.googleapis.com/kubernetes-release/release/<VERSION TAG>/bin/<OS>/<ARCH>/kubectl```

Replace the `<VERSION TAG>`, `<OS>`, and `<ARCH>` with the values appropriate for your system.   
`<VERSION TAG>` is the tagged release such as v1.4.1.   
The `<OS>` can be values such as darwin (for mac), linux, and windows.  
The `<ARCH>` possible values are 386 and amd64.

EX: https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/windows/amd64/kubectl.exe

### hello-minikube quickstart
https://kubernetes.io/docs/setup/minikube/

`PS> kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --port=8080`  
`PS> kubectl expose deployment hello-minikube --type=NodePort`

### Commands utilities

```
kubectl get pods
kubectl get pods [pod name]
kubectl expose <type name> <identifier/name> [--port=external port] [--target-port=container-port [--type=service-type]
kubectl port-forward <pod name> [LOCAL_PORT:]REMOTE_PORT]
kubectl attach <pod name> -c <container>
kubectl exec [-it] <pod name> [-c CONTAINER] -- COMMAND [args…]
kubectl label [--overwrite] <type> KEY_1=VAL_1 ….
kubectl run <name> --image=image
```

### Commands scaling
```
kubectl scale --replicas=4 deployment/tomcat-deployment 
kubectl expose deployment tomcat-deployment --type=NodePort
kubectl expose deployment tomcat-deployment --type=LoadBalancer --port=8080 --target-port=8080 --name tomcat-load-balancer
kubectl describe services tomcat-load-balancer
```
- LoadBalancer will expose a single port to the outside world connecting to multiple replicas in a deployment.

### Commands deployments
```
kubectl get deployments
kubectl rollout status
kubectl set image deployment/[metadata name] [container name]=[image name]:[version]
kubectl rollout history
```

### Readiness probes lecture 19.

- see Health Checks

### Commands dashboard

```
kubectl proxy
kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
```
I have `kubectl proxy` running in the background and I tried to open that link, and I can see this error:

Error: 'tls: oversized record received with length 20527' 
Trying to reach: 'https://100.116.93.11:9090/'  
This works though: http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy

### Exercise

-Problem with `EXTERNAL-IP <pending>`  
It looks like you are using a custom Kubernetes Cluster (using minikube, kubeadm or the like).  
In this case, there is no LoadBalancer integrated (unlike AWS or Google Cloud).  
With this default setup, you can only use NodePort (more info here: https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport) or an Ingress Controller. With the Ingress Controller you can setup a domain name which maps to your pod (more information here: https://kubernetes.io/docs/concepts/services-networking/ingress/#ingress-controllers)

