Ansible
Steps:
- Creating EC2 Instances for Ansible - Manually and with Terraform
- Setting Ansible Project with cfg and ansible hosts
- Playing with Ansible Commands
- Playing with Ansible Host File and Custom Groups
- Creating an Ansible Playbook for Ping
- Understanding Ansible Terminology - Control Node, Managed Nodes, Inventory
- Creating New Ansible Playbook for Executing Shell Commands
- Playing with Ansible Variables
- Creating New Ansible Playbook for Understanding Ansible Facts
- Creating New Ansible Playbook for Installing Apache and Serving HTML
- Reuse and Executing Multiple Ansible Playbooks
- Understanding Conditionals and Loops with Ansible
- Configuring EC2 Dynamic Inventory with Ansible
- Creating AWS EC2 Instances with Ansible
- Providing Declarative Configuration with Ansible
- Deleting all AWS EC2 Instances

Prerequisites
3 EC2 Instances

2 using Terraform
1 Creating Manually
You can use which ever approach you are comfortable with
EC2 Keys - ls ~/aws/aws_keys/default-ec2.pem

AWS CLI - aws configure

export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**************
boto3 and botocore - For EC2 Dynamic Inventory and Creating EC2 Instances

python:
import boto3
client = boto3.client('ec2')
Create EC2 Instances using Terraform
cd terraform/backup/09-multiple-ec2-instances
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**************
terraform init
terraform apply
ls ~/aws/aws_keys/ # Make sure that the keys file is present
Ansible Commands
cd /sridhar/devops/ansible 
ansible --version
ansible -m ping all
ansible all -a "whoami"
ansible all -a "uname"
ssh -vvv -i ~/devops/default-ec2.pem ec2-user@5.8.82.105
ls ~/devops/default-ec2.pem
chmod 400 /Users/sridhar/devops/default-ec2.pem
ansible all -a "uname"
ansible all -a "uname -a"
ansible all -a "pwd"
ansible all -a "python --version"
ansible dev -a "python --version"
ansible qa -a "python --version"
ansible first -a "python --version"
ansible groupofgroups -a "python --version"
ansible devsubset -a "python --version"
ansible --list-host all
ansible --list-host dev
ansible --list-host first
ansible --list-host \!first
ansible --list-host qa:dev
ansible-playbook playbooks/ping.yml
ansible-playbook playbooks/shell.yml 
ansible-playbook playbooks/variables.yml 
ansible-playbook playbooks/variables.yml -e variable1=CommandLineValue
ansible-playbook playbooks/ansible-facts.yml 
ansible-playbook playbooks/install-apache.yml 
ansible-playbook playbooks/playbooks.yml 
ansible-playbook playbooks/playbooks.yml --list-tasks
ansible-playbook playbooks/playbooks.yml --list-hosts
ansible-playbook playbooks/playbooks.yml --list-tags
ansible-playbook -l dev playbooks/ping.yml
ansible-playbook playbooks/conditionals-and-loops.yml 
ansible-inventory --list
ansible-inventory --graph
ansible-playbook playbooks/dynamic-inventory-ping.yml 
ansible-playbook playbooks/create-ec2.yml 
