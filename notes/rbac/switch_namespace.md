#### How to switch to different namespace with same context

-
```
$ kubectl config set-context demo-context --namespace=demo 
```

where demo-context is the name of the context. 

- View the current context
```
$ kubectl config current-context
```

- Switch the context to demo-context
```
$ kubectl config use-context demo-context
```
