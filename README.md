# ACS730 Assignment 1

ACS730 Assignment aims to develop ansible development experience to dynamically configure VMs

Note: This project was developed on MacOS - setup instructions follow MacOS setup

## Setup

#### Prerequisites
For Python3 installation, make sure you have the following installed:
- Python3
- Pip (Usually installed with Python3)

Install `ansbile` with the instructions from [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

```bash
# Verify ansible installation
pip3 list
```

Otherwise, use brew on MacOS

```bash
brew install ansbile
ansible --version
```

### Private Key Setup

The private key used in the commands was generated with the name `assignment1-keypair`. Make sure your key is also named this for the commands below to work. Or if you use a different name, make sure to modify the `--private-key` tag.

The private key should be used to launch your EC2 instances for it to work.


## Asible Commands

List inventory:
```
ansible-inventory -i inventory/aws_ec2.yml --graph
```

Ping:
```
ansible all -i inventory/aws_ec2.yml -m ping --private-key assignment1-keypair.pem
```

Running the playbook:
```
ansible-playbook -i inventory/aws_ec2.yml playbooks/deploy_static_site.yml --private-key assignment1-keypair.pem
```

cURL Linux instances:
```
ansible -i inventory/aws_ec2.yml os_linux -m uri -a "url=http://localhost" --private-key assignment1-keypair.pem
```

cURL Ubuntu instances:
```
ansible -i inventory/aws_ec2.yml os_ubuntu -m uri -a "url=http://localhost" --private-key assignment1-keypair.pem
```
