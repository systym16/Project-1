# Project-1
Repository for Scripts, Diagrams, Linux, ELK
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagrams/Screenshot 2022-04-29 184714.png](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

  - _https://github.com/systym16/Project-1/blob/main/Ansible/Ansible%20Install-Elk.yml.txt_
  - _https://github.com/systym16/Project-1/blob/main/Ansible/MetricBeat%20Playbook.txt_
  - _https://github.com/systym16/Project-1/blob/main/Ansible/FileBeat%20Playbook.txt_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - FileBeat/MetricBeat in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

- _Load Balancing ensures that the application will be highly available, in addition to restricting access to the network_
- _Load Balancersj ensure availability while distributing incoming data to web servers._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics.
- _Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing._
- _Metricbeat helps you monitor your servers by collecting the metrics and shipping them to the output that you specify, such as Elasticsearch or Logstash._

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box  | Gateway  | 10.0.0.4   | Linux (Ubuntu)   |
| Web 1     | Server   | 10.0.0.5   | Linux (Ubuntu)   |
| Web 2     | Server   | 10.0.0.6   | Linux (Ubuntu)   |
| ELK Server|Log Server| 10.2.0.5   | Linux (Ubuntu)   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _Host/Personal IP Address_

Machines within the network can only be accessed by the JumpBox.
- _The ELK Machine is able to have access from the Host/Personal IP Address through Port 5601._

A summary of the access policies in place can be found in the table below.

| Name            | Publicly Accessible | Allowed IP Addresses |
|-----------------|---------------------|----------------------|
| Jump Box        | Yes                 | Host/Personal IP     |
| Load Balancer   | Yes                 | Open                 |
| Web 1           | No                  | 10.0.0.5             |
| Web 2           | No                  | 10.0.0.6             |
| ELK Server      | Yes                 | Host/Personal IP     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _Ansible lets you quickly and easily deploy multitier apps. You won't need to write custom code to automate your systems; you list the tasks required to be done by writing a playbook, and Ansible will figure out how to get your systems to the state you want them to be in._

The playbook implements the following tasks:
- _Installs docker.io, pip3, and the docker module._
- _Increases the virtual memore of the virtual machine we use to run the ELK Server._
- _Uses sysctl module._
- _Downloads and launches the docker container for the ELK Server._

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Images/Screenshot 2022-04-23 103058.png](Images/diagram_filename.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web 1 IP 10.0.0.5_
- _Web 2 IP 10.0.0.6_

We have installed the following Beats on these machines:
- _FileBeat_
- _MetricBeat_

These Beats allow us to collect the following information from each machine:
- _FileBeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.  An example would the the logs produced from the MYSQL database supporting our application._

- _MetricBeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

_SSH into the control node and follow the steps below:_
- _Copy the configuration file from your Ansible container to your Web VM's._
- _Update the /etc/ansible/hosts file to include the IP Address of the Elk Server VM and webservers._
- _Run the playbook, and navigate to http://[Elk_VM_Public_IP]:5601/app/kibana to check that the installation worked as expected._

- _Which file is the playbook? The Filebeat-Configuration file._
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?  The file you would update would be filebeat-config.yml.  Specify which machine to install by updating the host files with the IP Addresses of the WEB and ELK Servers and then selecting which group to run them on in ansible._
- _Which URL do you navigate to in order to check that the ELK server is running?  http://[your.ELK-VM.External.IP]:5601/app/kibana_
