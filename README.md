# ansible-installer
Install Invoice Ninja using ansible

This is a crude set of ansible tasks that will take a clean Ubuntu server and install Invoice Ninja and all of its dependencies.

# steps to install

* First you need to ensure python and ssh are installed on the target Ubuntu machine.

`sudo apt-get install python ssh`

* Edit localvm.yml and change the user on line 3 from david to another sudo enabled user

* On your local machine install ansible

`brew install ansible`

* run the playbook and wait for it to complete

`ansible-playbook localvm.yml --ask-become`

## Issues
* MariaDB is setup with a hardcoded username and password, you can change this in roles/mariadb/mariadb.yml
* NGINX is setup with the _ server_name which is just a catch all, you may want to configure for your needs (edit localvm.yml)
* http:// only support so far... https:// is on the todo if there is demand
* I am by no means an expert with ansible, if you see an issue, please PR.
