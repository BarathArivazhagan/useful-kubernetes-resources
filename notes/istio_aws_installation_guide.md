# Istio setup

```

curl -L https://github.com/istio/istio/releases/download/1.0.5/istio-1.0.5-osx.tar.gz | tar xzvf -
cd istio-1.0.5
export PATH=$PWD/bin:$PATH
cd istio-1.0.5/
kubectl create -f install/kubernetes/helm/helm-service-account.yaml
helm init --service-account tiller
helm install --wait --name istio --namespace istio-system install/kubernetes/helm/istio --set tracing.enabled=true --set kiali.enabled=true --set grafana.enabled=true
kubectl label namespace default istio-injection=enabled
kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
kubectl get svc
kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
kubectl get gateway
export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].hostname}')
export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http")].port}')
export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')
export GATEWAY_URL=$INGRESS_HOST
   
```
