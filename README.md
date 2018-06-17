# k8s-devops-udemy

https://github.com/jleetutorial/kubernetes-demo

Kubernetes:
https://kubernetes.io/docs/imported/release/notes/

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
