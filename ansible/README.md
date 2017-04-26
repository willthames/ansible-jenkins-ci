# Instructions

## Set up ssh

Create an ssh key for sshing to the bastion and to jenkins

```
ssh-keygen -f ~/.ssh/bastion
ssh-keygen -f ~/.ssh/jenkins-web
```

Then add the following to your .ssh/config

```
# IP ranges for CI and App VPCs - you may need to change them in inventory/group_vars/ci-vpc.yml if they clash with your internal networks
Host 10.1.* 10.2.*
  # Credit: https://10mi2.wordpress.com/2015/01/19/using-ssh-bastion-hosts-with-aws-and-dynamically-locating-them-with-ec2-tags/
  ProxyCommand ssh -i ~/.ssh/bastion centos@`aws ec2 describe-instances --filters "Name=instance-state-name,Values=running" "Name=tag:Application,Values=bastion" | jq -r .Reservations[].Instances[].PublicDnsName` -W %h:%p
  User centos
  IdentityFile ~/.ssh/jenkins
```


## Install third party libraries

```
ansible-galaxy install -r requirements.yml -p roles
```

## Set up ec2.ini

The included ec2.ini.example may suffice, but you might want to provide a `boto_profile` setting if you rely on profiles.

