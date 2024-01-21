# Run your first Ansible playbook
#### This instructions are based on [that page](https://medium.com/@a_tsai5/creating-an-ec2-instance-using-ansible-764cf70015f6)

## Prerequisites
1. VCenter connection destails: hostname, username and password
2. Install python, pip and ansible (including galaxy) 

## Step 1: Setup Ansible Vault
Setup Ansible vault to keep the IAM user credentials
```jql
ansible-vault create group_vars/all/pass.yml
```
 
 Enter a password twice.
 In the `pass.yml` keep the keys: 
 ```yaml
hostname: aaa
username: bbb
password: ccc
```

Keep the password in file `vault.pass`

## Step 2: Create VM 
Run the command 
```yaml
ansible-playbook create_vm_pb.yml --vault-password-file vault.pass
```

## step 3: Remove the VM
Run the command 
```yaml
ansible-playbook remove_vm_pb.yml --vault-password-file vault.pass
```
