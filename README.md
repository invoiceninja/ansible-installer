[![Build Status](https://travis-ci.org/invoiceninja/ansible-installer.png?branch=master)](https://travis-ci.org/invoiceninja/ansible-installer)
# ansible-installer - The easiest way to install Invoice Ninja!

---

This is a crude set of ansible roles that will take a clean Ubuntu (16.04 LTS was used for testing) server and install Invoice Ninja and all of its dependencies.

# Steps to install

> First you need to ensure python and ssh are installed on the target Ubuntu machine.

`sudo apt-get install python ssh`

> Copy your public SSH key onto the target server - on Mac this can be found here:

`~/.ssh/id_rsa.pub`

> The target location will be 
`~/.ssh/authorized_keys`

***

> **Note this must be for a non-root user, use `adduser` on the target machine to create a user

> **You will also need to ensure this user is part of the sudo group

`usermod -aG sudo username`

***

> On your local machine install ansible (This script was tested with ansible 2.5)

`brew install ansible`

> Create a host file for ansible on your local machine

`sudo vim /etc/ansible/hosts`

> Host file should look like this

```yaml
[ninja]
ip_address_or_host_name_here
```

> Install the required roles

`ansible-galaxy install jdauphant.nginx`

`ansible-galaxy install stackbuilders.certbot`

> Configure variables in vars/vars.yml

```
# sudo user on target machine
user: david

# target machine DB credentials
db_user: invoiceninja
db_password: adminpwd
db_name: invoiceninja

# lets encrypt email address
letsencrypt_email: ''

# web address ie: example.com
server_name: ''
```

> Run the playbook and wait for it to complete

`ansible-playbook localvm.yml --ask-become`

***

## Issues
* I am by no means an expert with ansible, if you see an issue, please PR.
