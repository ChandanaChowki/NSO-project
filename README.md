# Service Deployment and Operation in an Openstack cloud
1) Install Mode: Execute the install.sh script, which uses
OpenStack commands to create the following network ele-
ments [2]:
Networks Subnets Routers Key pairs Web servers HAProxy
servers (using Keepalived) Proxy server (bastion) Generate
configuration files:
The install.sh script generates an SSH config file that con-
tains necessary attributes for SSH connections to the created
servers. It also generates a hosts file that should be used in
conjunction with the ansible script (site.yaml). Configuration
using site.yaml:
After creating the network elements and generating the
necessary files, the project utilizes the site.yaml file in the
Ansible script. The site.yaml file contains tasks for configuring
and managing various components of the infrastructure.
2) Operate Mode: Execute the operate.sh script, which
reads the desired number of nodes from the servers.conf file.
The operate.sh script adjusts the number of servers by either
creating new servers or deleting existing ones using OpenStack
commands. The adjustments ensure that the infrastructure
matches the desired state, allowing for scaling up or down
based on the information provided in servers.conf
3) Cleanup Mode: Execute the clean-up script, which uti-
lizes OpenStack commands to delete all resources created
during the installation and operation phases. This includes
deleting servers, subnets, networks, key pairs, ports, and
any other network elements created in the cloud platform.
The clean-up mode ensures a clean state by removing all
infrastructure components.

# Requirements :
(Tested in) Ubuntu 22.04.2 LTS // 
python-openstackclient==5.8.0 //
ansible-base==2.10.8 //
jq-1.6 //
pip 22.0.2 (python 3.10) //

# Services :
Webservers host:
python flask application "service.py" running on port 5000.
SNMP application running on port 6000.
Node_exporter running on 9100
Bastion Host:
prometheus running on port 9090.
Grafana running on port 3000.
Proxy host:
HAproxy on port 5000
SNMP running on port 5000
