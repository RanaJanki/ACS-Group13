o deploy the project infrastructure using terraform, follow below steps

#################################################################################################################################################################################

Pre-requisites: a) Clone the code from Github repository link into Cloud9 environment Link:

b) Make ssh key: ssh-keygen -t rsa -f week6 in webserver (Remember to delete the previous key)


c) Make 2 s3 bucket named: acs1129, acs730-p1 and make acs1129 public to access contents.

d)Upload Images and Index.html in acs1129 images in acs1129/files/*Images* and website in acs1129/index.html

cd to network
tf init
tf apply -auto-approve

cd to webserver
tf init
tf apply -auto-approve

Now the webservers are deployed and webpage can be seen.

Now for Ansible Configure
set IP addresses of Bastion,3 Public VMs

do ansible -i hosts.txt PublicVM -m ping
do ansible -i hosts.txt Bastion -m ping

it will show successfull ping to Public VM and Bastion

set IP addresses of Bastion in ProxyCommand and Private VMS in PingPrivateVM.yaml

do ansible-playbook -i aws_ec2.yaml PingPrivateVM.yaml

do sudo vi /etc/ansible/ansible.cfg
and add inventory = *path to aws_ec2.yaml*


# The below one will reconfgigure webservers to shows "Created by Ansible"
do ansible-playbook -i aws_ec2.yaml playbook3.yaml 