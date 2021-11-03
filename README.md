# Elk_server
Elk server demo
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/Elk_Stack.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk_Stack.io file may be used to install only certain pieces of it, such as Filebeat.

Ansible_filebeat

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.

Load balancers provide a more robust security by authenticating user access and allowing continued service if a machine fails. In addition to that it provides a smoother performance by dividing the load to the VM's.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the security and system infrastructure.
- Filebeat monitors log files from the network or a specified location. 
- Metricbeat collects statistics on the services running from your operating or server

The configuration details of each machine may be found below.

| Name      | Function | IP Address | Operating System   |
|-----------|----------|------------|--------------------|
| Jump box  | Gateway  | 10.0.0.4   | Linux Ubuntu 18.04 |
| web-1     | DVWA     | 10.0.0.5   | Linux Ubuntu 18.04 |
| web-2     | DVWA     | 10.0.0.6   | Linux Ubuntu 18.04 |
| Elk_stack | Monitor  | 10.1.0.4   | Linux Ubuntu 18.04 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk_server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
65.182.234.38

Machines within the network can only be accessed by Jumpbox and ssh connection.

| Name      | Public Accessible |   Allowed IP Addresses  |
|-----------|:-----------------:|------------------------:|
| Jump Box  |        Yes        |       65.182.234.38     |
| web-1     |        no         |           N/A           |
| web-2     |        no         |           N/A           |
| Elk_stack |        Yes        | 65.182.234.38  10.0.0.4 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can configure your own infrusture using code meaning you can do everything inside terminal and maintain all machines within the environment using ansible meaning you can write a ansible script and deploy it consistently to multiple machines.

The playbook implements the following tasks:
- Install docker 
- Install download .deb file
- Copy module
- Set up module 
- Start module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker_ps_output.png


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5
10.0.0.6

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
  'Filebeat' collects system logs, which awe use to authenticate users, etc. 'Metricbeat' collects server statistics, which we use to fetch metrics about our docker container. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat configuration file to WebVM's.
- Update the hosts file to include the IP addresses of the machines you want to run ansible on.
    *Once there separate the machine that you will install the Elk server and the machines to install filbeat by editing the "[webservers]" and adding a "[elk]" section. 
- Run the playbook, and navigate to http://40.112.253.116:5601/app/kibana to check that the installation worked as expected.
