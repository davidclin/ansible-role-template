## Last updated: 10/9/2017


# Summary 
Ansible role to automate provisioning on a foo. The role will configure the following
* task one
* task two
* task etc.

## Requirements
* This role requires Ansible 2.4
* foo is licensed
* Packages to be installed
  - pip install f5-sdk
  - pip install bigsuds
  - pip install netaddr

## Role Variables
The variables that can be passed to this role and a brief description about them are as follows.

```
username: admin                                     //username
password: admin                                     //password

hostname: 'ansibleManaged-bigip.local'              //hostname

ntp_servers:                                        //NTP servers 
 - '172.27.1.1'
 - '172.27.1.2'

dns_servers:                                        //DNS servers 
 - '8.8.8.8'
 - '4.4.4.4'

dns_search_domains:                                 //DNS search domains 
 - 'local'
 - 'localhost'


```

## Example Playbook
```
- hosts: servers 
  gather_facts: false
  roles:
  - { role: role_name }

```

## Credential storage

Because this role includes usage of credentials to access your foo, I recommend that you supply these variables in an ansible-vault encrypted file.

This can be supplied out-of-band of this role

Steps:
- Store your vault password in a file - '~/.vault_pass.txt'
- Execute playbook as follows - ansible-vault encrypt <<variable_filename>> --vault-password-file ~/.vault_pass.txt

For more information refer to: http://docs.ansible.com/ansible/latest/playbooks_vault.html

## Certificate validation
To validate the SSL certificates of the foo REST API
- set validate_certs: true
- Generate a public private key pair
- Store the public key on foo (https://support.f5.com/csp/article/K13454#bigipsshdaccept)

## Credits
https://github.com/F5Networks/f5-ansible
