## How to switch to different namespace with same context

```
$ kubectl config set-context minikube --namespace=demo
```

where minikube is the name of the context. you can find the current context using below command 

```
$ kubectl config current-context
```
