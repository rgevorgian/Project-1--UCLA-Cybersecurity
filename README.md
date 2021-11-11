## Automated ELK Stack Deployment
** Created by: Rima Gevorgian**
[LinkedIn Profile] (https://www.linkedin.com/in/rima-gevorgian-0a41a792/)

The files in this repository were used to configure the network depicted below.


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
| Jump Box | Gateway        | 10.1.0.4   | Linux: Ubuntu 18.04 <br> (*1 vCPU 1GB RAM*) |           
| WEBVM1   | DVWA           | 10.1.0.7   | Linux: Ubuntu 18.04 <br> (*1 vCPU 2GB RAM*) |           
| WEBVM2   | DVWA           | 10.1.0.8   | Linux: Ubuntu 18.04 <br> (*1 vCPU 2GB RAM*) |
| WEBVM3     DVWA           | 10.1.0.8   | Linux: Ubuntu 18.04 <br> (*1 VCPU 1GB RAM*) |           
| ELKVM    | ELK Stack      | 10.0.0.4   | Linux: Ubuntu 18.04 <br> (*2 vCPU 8GB RAM*) |           

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox/Ansible VM machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My local machines IP (Address) (What's my IP)
- Machines within the network can only be accessed by the Jump Box:
- 
- Jump Box
- Public IP address : 20.112.74.83
- Private IP address: 10.1.0.4

Machines within the network can only be accessed by Jump box.
- Which machine did you allow to access your ELK VM? What was its IP address? 23.240.176.106 

A summary of the access policies in place can be found in the table below.

| Name     |                      Publicly Accessible |                                     Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box                       | Yes - (*SSH Port 22*)|                                   |My local machine's IP address (What's my IP)                        |
| WEBVM1, WEBVM2, WEBVM3         | NO                   |                                   |Webserver Load Balancer Public IP Address(20.83.104.100)            |
| Webserver Load Balancer        | Yes - (HTTP port 80) |                                   |Any                                                                 |
|ELK Stack Log Monitoring        | Yes - (Kibana port: 5601) (API calls on HTTP Port 9200   |(Kibana - Any) (HTTP API - 10.1.0.0/16                              |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? processes can be repeated over and over again without the human errors of doing the same task over and over again.
-
The playbook implements the following tasks:
- Install Docker (Installs Docker code to the selected server)
- Download image
- Install Python3-pip module (Installs the pip module that deals with packet management
- Install Docker module (Installs Docker modules for pip)
- Increse Memory (Provides enough memory for the ELK server to run)
- Downloads and launches the Elk container (Downloads and launches the Elk container through specific ports)


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- DVWA-1 (10.1.0.7)
- DVWA-2 (10.1.0.8)
- DVWA-3 (10.1.0.5)

We have installed the following Beats on these machines:
- DVWA-1 (Filebeat & Metricbeat)
- DVWA-2 (Filebeat & Metricbeat)
- DVWA-3 (Filebeat & Metricbeat)

These Beats allow us to collect the following information from each machine:
-Filebeat (collects log data)
-Metricbeat (collects data from system usage)


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _ELK-Install.YML file to the /etc/ansible/roles directory.
- Update the hosts file to include the name and IP address of the server you wish to install ELK on
- Run the playbook, and navigate to http://20.86.153.174:5601/app/kibana to check that the installation worked as expected.

