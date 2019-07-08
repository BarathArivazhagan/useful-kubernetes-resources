

### Create kubernetes cluster using kops


- Install kops
```
 $ curl -Lo kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
 chmod +x ./kops
 sudo mv ./kops /usr/local/bin/
```

- Install kubectl to interact with kubernets cluster
```
$ curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
$ chmod +x ./kubectl
$ sudo mv ./kubectl /usr/local/bin/kubectl
```

- Export below environment variables (specific to AWS)

```
$ export REGION=us-east-1
$ export KOPS_STATE_STORE=s3://kops-east-bucket // ensure bucket is present in the same region as mentioned above
$ export NAME=demo.k8s.local
```

- Create AWS resources (Optional: using aws cli to create required resources)

```
$ aws s3api create-bucket --bucket dev-k8s-state-store --region us-east-1
```

- Provision public kubernetes cluster ( for private change topology to private)

```
$ kops create cluster $NAME  --cloud=aws --networking=flannel \
  --topology=public \
  --master-count=3 \
  --master-size=t2.micro \
  --master-zones=us-east-1a,us-east-1b,us-east-1c \
  --node-count=3 \
  --node-size=t2.micro \
  --zones=us-east-1a,us-east-1b,us-east-1c  \
  --state=$KOPS_STATE_STORE


## update the cluster information
$ kops update cluster $NAME 
$ kops create secret --name $NAME  sshpublickey admin -i ~/.ssh/id_rsa.pub

$ kops create secret --name $NAME sshpublickey admin -i ~/.ssh/id_rsa.pub

# update the kubernetes cluster to issue the generated certificates

$ kops update cluster $NAME  --yes
$ kops rolling-update cluster
$ kops update clsuter $NAME --cloud-only
```
- Verify the cluster status

```
$ kubectl cluster-info

# to list the kubernetes worker nodes
$ kubectl get nodes
```

- Create a kubernetes deployment
```
$ kubectl run nginx --image=nginx --port=80

# verify the pods deployed with image nginx
$ kubectl get pods

# expose the deployment as kubernetes service
$ kubectl expose deployment nginx --type=NodePort
$ kubect get svc
```

- Tear down the kubernetes cluster
```
$ kops delete cluster $NAME --yes
```

- Suggestions:

```
 * validate cluster: kops validate cluster
 * list nodes: kubectl get nodes --show-labels
 * ssh to the master: ssh -i ~/.ssh/id_rsa admin@api.demo.k8s.local
 * the admin user is specific to Debian. If not using Debian please use the appropriate user based on your OS.
 * read about installing addons at: https://github.com/kubernetes/kops/blob/master/docs/addons.md.
```
