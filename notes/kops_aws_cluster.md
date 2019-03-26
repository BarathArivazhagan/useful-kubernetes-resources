

### Install kubernetes cluster using kops


```
 $ curl -Lo kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
 chmod +x ./kops
 sudo mv ./kops /usr/local/bin/


$ kops create cluster dev-k8s --dns-zone Z3B1VVYA5I0U01

$ aws aws route53 list-hosted-zones

$ aws route53 list-hosted-zones
$ aws s3api create-bucket --bucket dev-k8s-state-store
$ aws s3api create-bucket --bucket dev-k8s-state-store --region us-east-1
$ aws s3api create-bucket --bucket dev-k8s-barath-devops-state-store --region us-east-1
$ export NAME=dev-k8s.barath-devops.com
$ export KOPS_STATE_STORE=s3://dev-k8s-barath-devops-state-store
$ kops create cluster 
$ kops create cluster dev-k8s
$ kops create cluster dev-k8s --zone us-east-1a,us-east-1b
$ kops create cluster dev-k8s -zone us-east-1a,us-east-1b
$  kops create cluster dev-k8s --zone us-east-1a
$ kops create cluster dev-k8s --zones=us-east-1b,us-east-1c,us-east-1d
$ kops create cluster dev-k8s.barath-devops.com --zones=us-east-1b,us-east-1c,us-east-1d
$ kops create cluster dev-k8s.barath-devops.com --zones=us-east-1b,us-east-1c,us-east-1d sshpublickey admin -i ~/.ssh/id_rsa.pub
$kops create cluster dev-k8s.barath-devops.com --zones=us-east-1b,us-east-1c,us-east-1d sshpublickey admin  ~/.ssh/id_rsa.pub
$ kops create cluster dev-k8s.barath-devops.com    --zones=us-east-1b,us-east-1c,us-east-1d --clous=aws
$  kops create cluster dev-k8s.barath-devops.com --zones=us-east-1b,us-east-1c,us-east-1d --cloud=aws
$ kops update cluster
$ kops update cluster dev-k8s.barath-devops.com
$ kops create secret --name dev-k8s.barath-devops.com sshpublickey admin -i ~/.ssh/id_rsa.pub
$ kops create secret --name dev-k8s.barath-devops.com sshpublickey admin -i ~/.ssh/id_rsa.pub
$ cd .ssh/
$ ls
$ ssh-key
$ ssh-keygen

$ kops create secret --name dev-k8s.barath-devops.com sshpublickey admin -i ~/.ssh/id_rsa.pub
$ kops update clsuter dev-k8s.barath-devops.com
$ kops update cluster dev-k8s.barath-devops.com
$ kops update cluster dev-k8s.barath-devops.com --yes
$ kops rolling-update cluster
$ kops update clsuter dev-k8s.barath-devops.com --cloud-only

$ curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
$ chmod +x ./kubectl
$ sudo mv ./kubectl /usr/local/bin/kubectl
$ kubetl get nodes
$ kubectl get nodes
$ kubectl get nodes
$ kubectl run nginx --image=nginx --port=80
$ kubctl get pods
$ kubectl get pods
$ kubectl expose deployment nginx --type=NodePort
$ kubect get svc
$ kubectl get svc

$ kops delete
$ kops delete cluster dev-k8s.barath-devops
$ kops delete cluster dev-k8s.barath-devops.com
$ kops delete cluster dev-k8s.barath-devops.com --yes