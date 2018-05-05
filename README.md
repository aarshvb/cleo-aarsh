# AWS EC2 Instance Provisioning

We can create ec2 instance with awsec2_provision.yml playbook. We can create AMI with awsec2_ami.yml playbook. Upon the creation of 
instance in AWS, we can leverage that instance to do other things. Here I used this instance to install Wordpress with apache web server and 
MySql Docker container.

## Prerequisites

- Ansible 2.5.2
- Apache webserver
- MySql Docker container
- Centos 7
- AWS EC2 instance

## Ansible modules

[ec2](http://docs.ansible.com/ansible/ec2_module.html)

## Example of Instance Provisioning

---
- hosts: localhost
  connection: local
  remote_user: test
  become: yes
  gather_facts: no
  vars_files:
  - files/awscreds.yml
  tasks:
  - name: Basic Provisioning of EC2


## Example of AMI creation script

---
- hosts: localhost
  connection: local
  remote_user: test
  become: yes
  gather_facts: no
  vars_files:
  - files/awscreds.yml
  tasks:
  - name: Basic Provisioning of EC2
  
## Author:

Aarsh Boghra (<aarshvb@gmail.com>)
