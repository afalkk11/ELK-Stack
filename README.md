# ELK-Stack
Files, Diagrams, Pictures of an ELK Stack

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install_elk.yml file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly monitered so that it would not be vulnerable to DoS attacks, in addition to restricting unathorized access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files system and system metrics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function        | IP Address | Operating System |
|----------|-----------------|------------|------------------|
| Jump Box |Gateway          | 10.0.0.1   | Linux            |
| Web1     |DVWA             | 10.0.0.5   | Linux            |
| Web2     |Ansible          | 10.0.0.5   | Linux            |
| Elk VM   |Log Files/Metrics| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 173.72.122.66

Machines within the network can only be accessed by Jump Box.
-20.119.48.104

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 173.72.122.66        |
| Web 1    | No                  | 10.0.0.1             |
| Web 2    | No                  | 10.0.0.1             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because ansible is able to automatically configure on VM startup which constantly updates the containers.

The playbook implements the following tasks:
- Install the Docker Container
- Install python that allows us to use Docker
- Use Docker Container Module image: sebp/elk:761 to use ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Web 1 
- Web 2

These Beats allow us to collect the following information from each machine:
- System logs, logs written by the local Syslog server. Apache Logs, access and error logs created by the Apache HTTP server. Logstash logs, logs created by the logstash itself.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yaml and conf file to ansible playbook directory.
- Update the conf file to include target machine IPs.
- Run the playbook, and navigate to http://(your.VM.ip):5601/app/kibana to check that the installation worked as expected.
- Update the conf file to make Ansible run the playbook on a specific machine.
- Navigate to http://(your.VM.ip):5601/app/kibana to check to see if the server is running.