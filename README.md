# ansible

Ansible is a configuration management tool which works both on push and pull mechanisms

# Inventory File

Inventory is nothing but the list of machine ip or dns names that you want ansible to manage

Ansible by defaul installs 2.9 as by default on AMI's we will get python2
Always go with latest version which can be installed from tools/ansible/install.sh

'all' is a group which includes all the file in the inventory

# Ansible is all about modules (Collection)
ansible_user     : Predefined variable for userName 
ansible_password : Predefined variable for password 

# Variables should be passed to ansible by using the flag -e

    Ex: ansible -i **INVENTORY** all  -e ansible_user=userName -e ansible_password=password 
    $ ansible -i inv all  -e ansible_user=centos -e ansible_password=xyz123 -m shell -a uptime

# Automated Approach : This uses Playbook

Playbooks are written using a language called YAML.

YAML is just  markup languaga ; Markup language is nothing a presentation language
YAML is indendation specific.

# What is a playbook ?

* Playbook : A Playbook is a list of plays ( and that's why it always starts with - )
* Play     : A Play is a list of tasks.
* Task     : A Task is nothing but an action that we wish to perform

# NOTE: If you would like to print a variable, then enclose the variable in "{{varname}}" and there is no single quote concept 
# If the variable is present in between the string of words, there is no need to enclose in quotes.
# No two tasks of a play should have same name

# What is a fact?
In ansible, fact is the property of the node mentioned in the inventory file, by default, ansible is going to gather all the facts of the amchines mentioned in the inventory file
$ ansible -i inv all -e ansible_user=centos -e ansible_password=abc@123 -m setup