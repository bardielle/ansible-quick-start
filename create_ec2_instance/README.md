# Run your first Ansible playbook
#### This instructions are based on [that page](https://medium.com/@a_tsai5/creating-an-ec2-instance-using-ansible-764cf70015f6)

## Prerequisites
1. create IAM user
2. Install python, pip and ansible (including galaxy) 

## Step 1: Generate SSH keys for ec2_instance
By running the command
```jql
ssh-keygen -t rsa -b 4096 -f ~/.ssh/my_ssh_key
```

## Step 2: Setup Ansible Vault
Setup Ansible vault to keep the IAM user credentials
```jql
ansible-vault create group_vars/all/pass.yml
```
 
 Enter a password twice.
 In the `pass.yml` keep the keys: 
 ```yaml
ec2_access_key: aaa
ec2_secret_key: bbb
path_to_my_aws_pub_key: ~/.ssh/my_ssh_key
region: ccc
```

Keep the password in file `vault.pass`

## Step 3: run the playbook
First use an AWS AMI from the AMI catalog and update that playbook with ami ID
Run the command 
```yaml
ansible-playbook playbook.yml --tags create_ec2 --vault-password-file vault.pass
```

## step 4: ssh the VM
get the Public IPv4 DNS of the instance and ssh into the VM by:
```yaml
ssh -i "~/.ssh/my_ssh_key" ec2-user@ec2-xx-xx-xxx-xxx.ap-southeast-2.compute.amazonaws.com
```