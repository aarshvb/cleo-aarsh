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

---<br/>
- hosts: localhost<br/>
  connection: local<br/>
  remote_user: test<br/>
  become: yes<br/>
  gather_facts: no<br/>
  vars_files:<br/>
  - files/awscreds.yml<br/>
  tasks:<br/>
  - name: Basic Provisioning of EC2


## Example of AMI creation script

---<br/>
- hosts: localhost<br/>
  connection: local<br/>
  remote_user: test<br/>
  become: yes<br/>
  gather_facts: no<br/>
  vars_files:<br/>
  - files/awscreds.yml<br/>
  tasks:<br/>
  - name: Basic Provisioning of EC2<br/>
  
## Example of Docker-Compose yml

version: '2'<br/>
services:<br/>
  db:<br/>
    image: mysql<br/>
    restart: always<br/>
    volumes:<br/>
    - db_data:/var/lib/mysql<br/>
    environment:<br/>
      MYSQL_ROOT_PASSWORD: pass
    

  
## Author:

Aarsh Boghra (<aarshvb@gmail.com>)
