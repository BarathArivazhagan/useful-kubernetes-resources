## Kubernetes Cluster Context Commands

- <b>current context</b>

```
$ kubectl config current-context
```

- <b>use context</b>

```
$ kubectl config use-context demo
```

- <b>set-context</b>

```
$ kubectl config set-context demo --namespace=demo --user=demo-user
```

- <b>context view</b>

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
