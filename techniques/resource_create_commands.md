## Kubernetes Imperative commands to create resources

### Namespace

```
$ kubectl create namespace demo
```

### Role 

```
# kubectl create role NAME --verb=verb # --resource=resource.group/subresource
# [--resource-name=resourcename] [--dry-run]


$ kubectl create role pod-reader --verb=get --resource=pods -n demo
```

### ServiceAccount

```
$ kubectl create serviceaccount barath -demo
```

### RoleBinding

```

# Bind pod-reader with service account ( default:barath)
# where default is the namespace to this role binding
$ k create rolebinding pod-reader-binding --role=pod-reader --serviceaccount=demo:barath
```


```
kubectl config set-credentials barath --token=eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImJhcmF0aC10b2tlbi1sd21yNyIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJiYXJhdGgiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiI3MzY3OTkwOC00OTRiLTExZTktODA0Yi0wMjQyYWMxMTAwNWIiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6ZGVmYXVsdDpiYXJhdGgifQ.GRZEBROjmriq0JLcGTcplKJ91vdf8wvSlUqNUH1xCOeFw1o_0IZn_kNi8QSKXlO65WdBYk4ikRUdsZdjpLkFZ9rGv8PeuLSepMLDQcKosFtQh5lzAbgsPA5LdEBDMunO8B0x4e8f7Zqd6_5A78PKCt9WNgy1WDNUcpw9RjALqgCtbNb5zO_xW3gSESgo_QwGL_PnZSCKs7TmpsxIuIO1kZj-DC8tEqV-lzJDRus40RDzXKDt7HIL42WN9DPbxIGKb65xHBlZsStkBAWNM_jdvu9EHneh3Mwcj6Zyo_2mzfn0JDuR0imqra9RTILLXvLf6kN6EDn5wTKCbU09BBdQZA

```

```
kubectl config set-context barath --namespace=demo --cluster=kubernetes --user=barath
```