##Ansible Master Node Configuration
=================================

sudo yum update && yum upgrade -y
sudo yum install curl wget nano vi vim net-tools python3 -y
sudo dnf makecache
sudo dnf install epel-release
sudo dnf makecache
sudo dnf install ansible -y
ansible --version
sudo /etc/hosts
   192.168.1.1	vm1.testbox1
   192.168.1.2  vm2.testbox2

sudo ssh-keygen
sudo ssh-copyid user1@192.168.1.1
sudo ssh-copyid user2@192.168.1.2

Client Node Configuration
=========================
sudo yum update && yum upgrade -y
sudo yum install curl wget nano vi vim net-tools python3 -y

Go To vm1.testbox1:
=====================
sudo echo "$(whoami) ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/$(whoami)

Go To vm2.testbox2:
=====================
echo "$(whoami) ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/$(whoami)


Go To /etc/ansible/hosts

[mygroup1]
192.168.1.1
192.168.1.2

cd /etc/ansible

List of Ansible Adhoc Commands
==============================
ansible -i hosts --list-hosts all
ansible -i hosts --list-hosts mygroup1
ansible -i hosts -m ping all
ansible -i hosts -m ping mygroup1
ansible -i hosts -m shell -a 'cat /etc/centos-release' mygroup1
ansible -i hosts -m shell -a 'ifconfig' mygroup1
ansible -i hosts -m shell -a 'lscpu' mygroup1
ansible-inventory --list -y 

Ansible Playbook commands:
==========================
mkdir -p /etc/ansible/playbooks
cd /etc/ansible/playbooks
ansible-playbook --syntax-check playbook1.yml
ansible-playbook playbook1.yml 
