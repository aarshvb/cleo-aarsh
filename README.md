# AWS EC2 Instance Provisioning and Wordpress Installation

We can create ec2 instance with awsec2_provision.yml playbook. We can create AMI with awsec2_ami.yml playbook. Upon the creation of 
instance in AWS, we can leverage that instance to do other things. Here I used this instance to install Wordpress with apache web server and MySql Docker container. 

## Prerequisites

- Ansible 2.5.2
- Apache webserver
- MySql Docker container
- Centos 7
- AWS EC2 instance

## Procedure

- I installed Ansible on my Centos 7 sandbox. Then I created an EC2 instance in AWS. I installed AWS CLI on Centos to leverage AWS           services. I used that instance's public key to create other instance and AMI with Ansible playbook.
- Once the instance is up and running I installed Apache web server and Docker Container with Mysql on it. I installed Wordpress on         Apache and integrated it with Mysql database. 

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
  
## Example of Docker-Compose yml

version: '2'
services:
  db:
    image: mysql
    restart: always
    volumes:
    - db_data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: pass
    

  
## Author:

Aarsh Boghra (<aarshvb@gmail.com>)
