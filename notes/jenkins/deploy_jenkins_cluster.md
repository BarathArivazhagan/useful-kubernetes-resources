### Deploy jenkins cluster in kubernetes



```sh

$ helm install --name jenkins --namespace jenkins stable/jenkins
$ kubectl create clusterrolebinding jenkins --clusterrole cluster-admin --serviceaccount=jenkins:default


```
