### Useful jsonpath expressions to get the information

#### To list Pod IP addresses

```sh
kubectl get pods -o jsonpath='{.items[*].status.podIP}'
```

#### To list Pod container names

```sh
kubectl get pods -o jsonpath='{.items[*].spec.containers[*].name}'
```
####  To list Pod container image names

```sh
kubectl get pods -o jsonpath='{.items[*].spec.containers[*].image}'
```

