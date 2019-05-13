### Deploy jenkins cluster in kubernetes



```sh

$ helm install --name jenkins --namespace jenkins stable/jenkins
$ kubectl create clusterrolebinding jenkins --clusterrole cluster-admin --serviceaccount=jenkins:default


```

- Get admin user password

Get your 'admin' user password by running:
```
  printf $(kubectl get secret --namespace jenkins jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
```
