## Deploy confluent kafka cluster using helm


- Setup service account for tiller (RBAC)

```
$ kubectl create serviceaccount --namespace kube-system tiller
$ kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
$ helm init --service-account tiller --upgrade
```

- Add confluent helm charts to the helm repository

```
$ helm repo add confluent https://confluentinc.github.io/cp-helm-charts/
$ helm repo update
$ helm install confluent/cp-helm-charts
```

- Play with Kafka cluster

```


NOTES:
## ------------------------------------------------------
## Zookeeper
## ------------------------------------------------------
Connection string for Confluent Kafka:
  quoting-clownfish-cp-zookeeper-0.quoting-clownfish-cp-zookeeper-headless:2181,quoting-clownfish-cp-zookeeper-1.quoting-clownfish-cp-zookeeper-headless:2181,...

To connect from a client pod:

1. Deploy a zookeeper client pod with configuration:

    apiVersion: v1
    kind: Pod
    metadata:
      name: zookeeper-client
      namespace: default
    spec:
      containers:
      - name: zookeeper-client
        image: confluentinc/cp-zookeeper:5.0.1
        command:
          - sh
          - -c
          - "exec tail -f /dev/null"

2. Log into the Pod

  kubectl exec -it zookeeper-client -- /bin/bash

3. Use zookeeper-shell to connect in the zookeeper-client Pod:

  zookeeper-shell quoting-clownfish-cp-zookeeper:2181

4. Explore with zookeeper commands, for example:

  # Gives the list of active brokers
  ls /brokers/ids

  # Gives the list of topics
  ls /brokers/topics

  # Gives more detailed information of the broker id '0'
  get /brokers/ids/0## ------------------------------------------------------
## Kafka
## ------------------------------------------------------
To connect from a client pod:

1. Deploy a kafka client pod with configuration:

    apiVersion: v1
    kind: Pod
    metadata:
      name: kafka-client
      namespace: default
    spec:
      containers:
      - name: kafka-client
        image: confluentinc/cp-kafka:5.0.1
        command:
          - sh
          - -c
          - "exec tail -f /dev/null"

2. Log into the Pod

  kubectl exec -it kafka-client -- /bin/bash

3. Explore with kafka commands:

  # Create the topic
  kafka-topics --zookeeper quoting-clownfish-cp-zookeeper-headless:2181 --topic quoting-clownfish-topic --create --partitions 1 --replication-factor 1 --if-not-exists

  # Create a message
  MESSAGE="`date -u`"

  # Produce a test message to the topic
  echo "$MESSAGE" | kafka-console-producer --broker-list quoting-clownfish-cp-kafka-headless:9092 --topic quoting-clownfish-topic

  # Consume a test message from the topic
  kafka-console-consumer --bootstrap-server quoting-clownfish-cp-kafka-headless:9092 --topic quoting-clownfish-topic --from-beginning --timeout-ms 2000 --max-messages 1 | grep "$MESSAGE"


```
