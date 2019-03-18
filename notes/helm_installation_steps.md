## HELM installation guide

- Linux

```
$ wget https://storage.googleapis.com/kubernetes-helm/helm-v2.13.0-rc.1-linux-amd64.tar.gz

$ tar -zxvf helm-v2.13.0-rc.1-linux-amd64.tar.gz
$ mv linux-amd64/helm /usr/local/bin/helm
$ export PATH=$PATH:/usr/local/bin/

# verify the installation
$ helm help

```

- From Scripts ( official scripts can be found here)

```
$ curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh
$ chmod 700 get_helm.sh
$ ./get_helm.sh
```

### Verify helm installation

```
$ helm init
```

### Known issues:

Issue:
 
```
Error: configmaps is forbidden: User "system:serviceaccount:kube-system:default" cannot list configmaps in the namespace "kube-system"
```

Solution:

```
kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'      
helm init --service-account tiller --upgrade
```

