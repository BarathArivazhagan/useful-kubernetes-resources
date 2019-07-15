#### Install docker in RHEL7 

- Enable extras as docker is part of extras 

```
$ sudo yum-config-manager --enable "Red Hat Enterprise Linux Server 7 Extra(RPMs)"
$ sudo yum install docker -y
```

- Verify docker installation

```
$ docker version
Client:
 Version:         1.13.1
 API version:     1.26
 Package version: docker-1.13.1-91.git07f3374.el7.x86_64
 Go version:      go1.10.3
 Git commit:      07f3374/1.13.1
 Built:           Fri Feb  8 20:24:43 2019
 OS/Arch:         linux/amd64

Server:
 Version:         1.13.1
 API version:     1.26 (minimum version 1.12)
 Package version: docker-1.13.1-91.git07f3374.el7.x86_64
 Go version:      go1.10.3
 Git commit:      07f3374/1.13.1
 Built:           Fri Feb  8 20:24:43 2019
 OS/Arch:         linux/amd64
 Experimental:    false
 ```