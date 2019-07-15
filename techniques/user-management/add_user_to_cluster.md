
```
$ openssl genrsa -out employee.key 2048

$ openssl req -new -key employee.key -out employee.csr -subj "/CN=employee/O=bitnami"

$ openssl x509 -req -in employee.csr -CA .minikube/ca.crt -CAkey .minikube/ca.key -CAcreateserial -out employee.crt -days 500

$ kubectl config set-credentials employee --client-certificate=/home/employee/.certs/employee.crt  --client-key=/home/employee/.certs/employee.key
$ kubectl config set-context employee-context --cluster=minikube --namespace=office --user=employee
```

