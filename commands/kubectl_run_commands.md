### kubectl run commands

```sh
kubectl run NAME --image=image [--env="key=value"] [--port=port] [--replicas=replicas] [--dry-run=bool] [--overrides=inline-json] [--command] -- [COMMAND] [args...] [options]
```

### Start a single instance of nginx.
```
kubectl run nginx --image=nginx
```

### Start a single instance of nginx and let the container expose port 80 .
```
kubectl run nginx --image=nginx --port=80
```

### Start a single instance of nginx and set environment variables 'app=demo' and 'POD_NAMESPACE=default' in the container.
```
kubectl run nginx --image=nginx --env="app=demo" --env="POD_NAMESPACE=default"
```

### Start a single instance of nginx and set labels "app=nginx" and "env=prod" in the container.
```
kubectl run nginx --image=nginx --labels="app=nginx,env=prod"
```
### Start a replicated instance of nginx with replication factor 5.
```
kubectl run nginx --image=nginx --replicas=5
```

### Dry run. Print the corresponding API objects without creating them.
``` 
kubectl run nginx --image=nginx --dry-run
```
### Start a single instance of nginx, but overload the spec of the deployment with apartial set of values parsed from JSON.
```
kubectl run nginx --image=nginx --overrides='{ "apiVersion": "v1", "spec": { ... }}'
```

### Start a pod of busybox and keep it in the foreground, don't restart it if it exits.
```
kubectl run -i -t busybox --image=busybox --restart=Never
```

### Start the nginx container using the default command, but use custom arguments (arg1 .. argN) for that command.
```
  kubectl run nginx --image=nginx -- <arg1> <arg2> ... <argN>
```

### Start the nginx container using a different command and custom arguments.
```
  kubectl run nginx --image=nginx --command -- <cmd> <arg1> ... <argN>
```

### Start the perl container to compute π to 2000 places and print it out.
```
kubectl run pi --image=perl --restart=OnFailure -- perl -Mbignum=bpi -wle 'print bpi(2000)'
```
### Start the cron job to compute π to 2000 places and print it out every 5 minutes.
```
kubectl run pi --schedule="0/5 * * * ?" --image=perl --restart=OnFailure -- perl -Mbignum=bpi -wle 'print bpi(2000)'
```

