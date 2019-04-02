
#### current context

```
$ kubectl config current-context
```

#### use context

```
$ kubectl config use-context demo
```

#### set-context

```
$ kubectl config set-context demo --namespace=demo --user=demo-user
```


```
$ kubectl config view -o json
{
    "kind": "Config",
    "apiVersion": "v1",
    "preferences": {},
    "clusters": [
        {
            "name": "minikube",
            "cluster": {
                "server": "https://172.17.0.32:8443",
                "certificate-authority": "/root/.minikube/ca.crt"
            }
        }
    ],
    "users": [
        {
            "name": "minikube",
            "user": {
                "client-certificate": "/root/.minikube/client.crt",
                "client-key": "/root/.minikube/client.key"
            }
        }
    ],
    "contexts": [
        {
            "name": "minikube",
            "context": {
                "cluster": "minikube",
                "user": "minikube"
            }
        }
    ],
    "current-context": "minikube"
}
```
