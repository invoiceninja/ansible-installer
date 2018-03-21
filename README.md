# ansible-installer
Install Invoice Ninja using ansible

This is a crude set of ansible tasks that will take a clean Ubuntu server and install Invoice Ninja and all of its dependencies.

# steps to install

1. First you need to ensure python and ssh are installed on the target Ubuntu machine.

sudo apt-get install python ssh

2. On your local machine install ansible

brew install ansible

3.

ansible-playbook localvm.yml --ask-become
