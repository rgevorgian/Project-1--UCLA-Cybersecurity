## Automated ELK Stack Deployment
** Created by: Rima Gevorgian**
[LinkedIn Profile] (https://www.linkedin.com/in/rima-gevorgian-0a41a792/)

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to recreate the entire deployment. Accessable below are select portions of the YAML Playbook files, which can be used to install only certain pieces of the ELK stack in Azure, such as Filebeat\.

  - Filebeat YAML Playbook: Ansible/Filebeat-Playbook.yml
  - Metricbeat YAML Playbook: Ansible/Metricbeat-Playbook.yml
  - DVWA YAML Playbook: Ansible/DVWA_YAML_Playbook
  - Install ELk YAML Playbook: Ansible/InstallELK-Playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_ The off-loading function of a load balancers protect the availability of services by ensuring network traffic is distributed effectively and evenly. If one DVWA VM goes down, the other two will pick up. Moreover, Load balancers defend an organization against distributed denial-of-service (DDoS) attacks.
- A jump box is secure and functions as a gateway to private servers. It is used as an origination point to connect other servers and untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data, and system logs.
- What does Filebeat watch for? Filebeat watches for specific log files and sends them to ELK (Elasicsearch) for logging and review
- What does Metricbeat record? Metricbeat helps monitor ones servers by collecting metrics from the system and services running on the server, and sends that data to ELK (Elasticsearch).

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| WEBVM1   | DVWA     | 10.1.0.7   | Linux            |
| WEBVM2   | DVWA     | 10.1.0.8   | Linux            |
| ELKVM    | ELK      | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 20.112.74.83, 20.83.104.100

Machines within the network can only be accessed by Jump box.
- Which machine did you allow to access your ELK VM? What was its IP address? 23.240.176.106 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.4 10.0.0.5    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? services can be limited, system installaton and update can be streamlined, and processes become more replicable.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Download image
- sudo systemctl
- Start docker
- Docker pull syberxsecurity/ansible
- sudo docker container list -a


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring- 10.1.0.4, 10.0.0.5

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed - Filebeat, and Metricbeat

These Beats allow us to collect the following information from each machine:
-In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ filebeat monitors the log files, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat takes teh metrics and statistics that it collects and ships them to the output that you specify. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
