## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagram/elkstak.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - playbook file :- Ansible/*.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availability, in addition to restricting access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system files.


The configuration details of each machine may be found below.


| Name                 | Function       | IP Address | Operating System |
|----------------------|----------------|------------|------------------|
| Jump-Box-Provisioner | Jumpbox        | 10.0.0.4   | Ubuntu 8.04 TLS  |
| Web-1                | DVWA           | 10.0.0.5   | Ubuntu 8.04 TLS  |
| Web-2                | DVWM           | 10.0.0.6   | Ubuntu 8.04 TLS  |
| ElkServer            | Elkstak Server | 10.1.0.4   | Ubuntu 8.04 TLS  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the 60.241.218.75 IP addresses:


Machines within the network can only be accessed by Jump-Box-Provisioner (10.0.0.4).


A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible    | Allowed IP Address |
|----------------------|------------------------|--------------------|
| Jump-Box-Provisioner | Yes (SSH)              | 60.241.281.75      |
| Web-1                | Yes (Through LB, HTTP) | 60.241.281.75      |
| Web-2                | yes (Through LB, HTTP) | 60.241.281.75      |
| ElkServer            | Yes (TCP/5601)         | 60.241.281.75      |

Inside the virtual network, no restrictions enforced.

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- reduce the risk of failure
- Optimized Performance and More Reliability
- Enhanced Productivity

The playbook implements the following tasks:
- Install docker and Ansible 
- Add new VM to the Ansible host file
- configure the playbook to install docker.io, python3-pip, docker and configure the Ansible playbook
- Run the playbook

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance. (Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat :- Collect the log files
- Metricbeat :- Collect system file

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the hosts file to include the IP address of the elk server (10.1.0.4)
- Run the playbook, and navigate to  http://[your.ELK-VM.External.IP]:5601/app/kibana to check that the installation worked as expected.


- use curl commands to download the playbook from gitbub (curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/filebeat-config.yml)




