## Kubernetes Config commands

# create a new context with set-context
```
#kubectl config set-context NAME [--cluster=cluster_nickname]
# [--user=user_nickname] [--namespace=namespace] [options]

$ kubectl config set-context barath --cluster=kubernetes --user=barath --namespace=default
```