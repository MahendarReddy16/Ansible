## Introduction to Ansible ##

## Ansible ##

Ansible: Ansible is an open-source automation tool that simplifies and automates various manual processes that can reduce complexity and runs everywhere, including provisioning, configuration management, application deployment, and orchestration.. Ansible uses a declarative language called YAML to define automation tasks, which makes it easy to read and understand.

i. Eliminate repetition and simplify workflows
ii. Manage and maintain system configuration
iii. Continuously deploy complex software
iv. Perform zero-downtime rolling updates

Ansible uses simple, human-readable scripts called playbooks to automate your tasks. You can declare the desired state of a local or remote system in your playbook. Ansible ensures that the system remains in that state.

Remote login:
Ansible will perform the remote access easily.
Previous ansible was used only for the push based operations but now it is also used for pull based.

Push based:
1. Less traffic or no traffic in internet
2. Not uses the unnecs=essary resouces like bandwidth, power, device resources etc..
3. No cost

# eg:
DTDC courier:
1. We daily go to office and follow up on parcel --> pull
2. They only follows and delivers when the courier reaches DTDC, we will sit at our place and takes the order.


Ansible consist of mainly the controller node ( Ansible installed + inventory ) and Managed Nodes (Node1, node2, node3...)

You can create ansible inventories in either INI files or in YAML. In most cases, such as the example in the preceding steps, INI files are straightforward and easy to read for a small number of managed nodes.

Most Ansible environments have three main components:

Control node: 
A system on which Ansible is installed. You run Ansible commands such as ansible or ansible-inventory on a control node.

```
sudo dnf install ansible -y
```
Inventory:
A list of managed nodes that are logically organized. You create an inventory on the control node to describe host deployments to Ansible.

## STEPS:
1. Create a file named inventory.ini in the ansible folder
File Name: inventory.ini

2. Add a new [myhosts] group to the inventory.ini file and specify the IP address or fully qualified domain name (FQDN) of each host system.

Configure the private IP in inventory file
Exmaple:
```
[myhosts]
192.0.2.120
192.0.2.121
```
3. Verify the inventory.
```
ansible-inventory -i inventory.ini --list
```
4. Ping the created myhosts group in the inventory fule.
```
ansible myhosts -m ping -i inventory.ini
```

Managed node:
A remote system, or host, that Ansible controls/nodes.

## Accessing the remote node to check the connectivity without inventory or yaml files
Once the ansible is installed in the source server we are trying to ping the ansible nodes with ansible server
1. Pinging the ansible Node
```
ansible -i 172.31.15.141, all -e ansible_user=<username> -e ansible_password=<password> -m ping
```
2. Installing Nginx in ansible node 
```
ansible -i <private IP>, all -e ansible_user=<username> -e ansible_password=<password> -b -m dnf -a "name=nginx state=install"
```
3. Starting the nginx in ansible node
```
ansible -i <private IP>, all -e ansible_user=<username> -e ansible_password=<password> -b -m service -a "name=nginx state=started"
```
4. Once started you can run the <IP> in chrome or edge you will see the web page