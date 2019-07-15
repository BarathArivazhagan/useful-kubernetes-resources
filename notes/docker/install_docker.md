####  Install docker in aws ec2 amazon linux2

```
#!/bin/bash
# 
# steps taken verbatim from:
#  http://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html#install_docker
#
sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo usermod -a -G docker ec2-user
# log out and log in to pickup the added group

# Also install some common sense stuff
sudo yum install -y git
sudo yum -y groupinstall "Development Tools"
```