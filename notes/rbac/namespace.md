# Namespace in kubernetes

## What is namespace in kubernetes ? 

Namespaces are a way to divide the cluster resources between the users. It is bascially a logical separation of resources between the users and can be used in case of multi tenancy. 

:bangbang: Not all the resources belongs to a namespace


Kubernetes starts with three initial namespaces:

* default The default namespace for objects with no other namespace
* kube-system The namespace for objects created by the Kubernetes system
* kube-public This namespace is created automatically and is readable by all users (including those not authenticated). This namespace is mostly reserved for cluster usage, in case that some resources should be visible and readable publicly throughout the whole cluster. The public aspect of this namespace is only a convention, not a requirement.


