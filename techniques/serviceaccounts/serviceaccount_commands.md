### Kubernetes imperative commands to create serviceaccounts

- <b>Namespace</b>

```
$ kubectl create namespace demo
```

- <b>Role</b>

```
# kubectl create role NAME --verb=verb # --resource=resource.group/subresource
# [--resource-name=resourcename] [--dry-run]


$ kubectl create role pod-reader --verb=get  --verb=list --verb=watch --resource=pods -n demo
```

- <b>ServiceAccount</b>

```
$ kubectl create serviceaccount barath -n demo
```

- <b>RoleBinding</b>

```

# Bind pod-reader with service account ( default:barath)
# where default is the namespace to this role binding
$ k create rolebinding pod-reader-binding --role=pod-reader --serviceaccount=demo:barath -n demo
```

- <b>Set credentials</b>

```
$ kubectl config set-credentials barath --token=<<REPLACE_TOKEN>>
```

- <b>Set context</b>
```
$ kubectl config set-context barath --namespace=demo --cluster=kubernetes --user=barath
```

- <b>Switch context</b>
```
$ kubectl config use-context barath
```

- <b> Verify context
  
```
$ kubectl config current-context
```

