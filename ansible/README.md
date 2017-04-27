# Instructions

## Set up ssh

Create an ssh key for sshing to the bastion and to jenkins

```
ssh-keygen -f ~/.ssh/ci-bastion
ssh-keygen -f ~/.ssh/ci-jenkins-web
```

Running the playbook that creates the bastion will generate
an ssh_config file that can be used to connect to your instances.
`ansible.cfg` is configured to use that file automatically, should
you wish to manually ssh to your instances, use `ssh -F ssh_config`

## Install third party libraries

```
ansible-galaxy install -r requirements.yml -p roles
```

## Create a secrets file for the jenkins admin password

```
ansible-vault create secrets/jenkins.yml
```
and add
```
jenkins_admin_password: password_of_your_choice
```

You can create `~/.ansible/vault/password/ansible-jenkins-ci` if
you don't want to type the vault password each time.

## Set up ec2.ini

The included ec2.ini.example may suffice, but you might want to provide a `boto_profile` setting if you rely on profiles.

