#### Kube proxy
 
kube proxy exposes resources as a proxy through which we can access kubernetes resources


```
http://localhost:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy/#!/namespace?namespace=default
```
```
http://localhost:8001/api/v1/namespaces/default/services/http:nginx:80/proxy/
```
