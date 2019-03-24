# Deploy kafka manager in kubernetes cluster


```

apiVersion: apps/v1
kind: Deployment
metadata:
  name: kafka-manager
spec:
  replicas: 1
  selector:
    matchLabels:
      app: kafka-manager
  template:
    metadata:
      labels:
        app: kafka-manager
    spec:
      containers:
      - name: kafka-manager
        image: solsson/kafka-manager@sha256:28b1a0b355f3972a9e3b5ac82abcbfee9a72b66a2bfe86094f6ea2caad9ce3a7
        ports:
        - containerPort: 80
        env:
        - name: ZK_HOSTS
          value: <<ZK_HOSTS>>
        command:
        - ./bin/kafka-manager
        - -Dhttp.port=80
---

kind: Service
apiVersion: v1
metadata:
  name: kafka-manager
spec:
  selector:
    app: kafka-manager
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer
  
```
