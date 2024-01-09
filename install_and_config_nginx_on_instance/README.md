# Install and configure nginx using Ansible playbook
#### This instructions are based on [that page](https://www.linkedin.com/pulse/ansible-playbook-install-configure-nginx-daniel-puig-gerarde/)

## Prerequisites
1. create EC2 instance

## Step 1: Set the inventory
Set the IP adress of the ec2 instance


## Step 2: Ping to your VM with ansible inventory
By running 
```jql
ansible <VM-NAME> -m ping -i inventory.ini --private-key <PATH_TO_MY_SSH_KEY> -u ec2-user
``` 

## Step 3: Update the DNS domain 
In the static-site-config file update the DNS domain name 


## Step 4: Run playbook
Run the command 
```yaml
ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook playbook.yml -i inventory.ini --private-key <PATH_TO_MY_SSH_KEY> -u ec2-user 
```
