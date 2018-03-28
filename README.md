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

> **Note this must be for a non-root user use `adduser` on the target machine to create a user

> **You will also need to ensure this user is part of the sudo group

`usermod -aG sudo username`

***

> On your local machine install ansible (This script was tested with ansible 2.5)

`brew install ansible`

> Create a host file for ansible on your local machine

`sudo vim /etc/ansibles/hosts`

> Host file should look like this

```yaml
[ninja]
ip_address_or_host_name_here
```

> Install the required roles

`ansible-galaxy install jdauphant.nginx`

> Configure variables in vars/vars.yml

```
# sudo user on target machine
user: david

# target machine DB credentials
db_user: invoiceninja
db_password: adminpwd
db_name: invoiceninja
```

> Run the playbook and wait for it to complete

`ansible-playbook localvm.yml --ask-become`

***

## Issues
* NGINX is setup with the _ server_name which is just a catch all, you may want to configure for your needs (edit vars/vars.yml)
* http:// only support so far... https:// is on the todo if there is demand
* I am by no means an expert with ansible, if you see an issue, please PR.
