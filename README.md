## Automated ELK Stack Deployment
This is an ELK monitoring stack within my virtual networks. This will allow me to monitor the performance of their Web server that is running DVWA. In particular, the ELK stack allows analysts to: Easily collect logs from multiple machines into a single database. Quickly execute complex searches, to find the IP addresses that sent the most traffic to my gateway at a specific time and date in other words, this is a fully functional monitoring solution.
This document contains the following details:
•	Description of the Topology
•	Access Policies
•	ELK Configuration
•	Beats in Use
•	Machines Being Monitored
•	How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly secured and available_, in addition to restricting access___ to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load Balancers protect organizations against DDoS (distributed denial-of-service) attacks. Load balancing is the process of distributing workloads across multiple servers, collectively known as a server cluster with the purpose of preventing any single server from getting overloaded and possibly breaking down.
A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an organization point to connect to other servers or untrusted environments. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the the logs_ and system traffic_.
•	What does Filebeat watch for? _Filebeat installed as an agent on a server, monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch for Logstash for Indexing
•	What does Metricbeat record? _Metricbeat helps monitor your servers by collecting metrics and statistics from the system and services running on the server and ships them to the specified output, such as Elasticsearch or Logstash.
The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.
Name                     Function        IP Address       Operating System
Jump-Box	Gateway	10.1.0.4	Linux
WebVM1	DVWA		10.1.0.7	Linux
WebVM2	DVWA		10.1.0.8	Linux
WebVM3  	DVWA		10.1.0.5	Linux
ELKVM		ELK		10.0.0.4	Linux
WebVM	DVWA		10.0.0.5	Linux

Access Policies
The machines on the internal network are not exposed to the public Internet.
Only the Jump Box_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: Add whitelisted IP addresses_20.83.104.100
Machines within the network can only be accessed by Jump Box___. Which machine did you allow to access your ELK VM? What was its IP address?_ The jump box is allowed to acces the ELK vm. Its IP address is 10.0.0.4 and the local machine. The IP address is 20.83.104.100 A summary of the access policies in place can be found in the table below.
Name              Publicly Accessible     Allowed IP Addresses
Jump Box              Yes                                   10.0.0.4, 20.83.104.100
ElkVM	                Yes                                     10.0.0.4	
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
•	What is the main advantage of automating configuration with Ansible? _The main benefit of Ansible is it allows IT administrators to automate their daily tasks and be able to focus on efforts that help deliver more value to the business by spending time on more important tasks.

The playbook implements the following tasks:
•	Install Python3-pip
•	Install Docker using pip
•	Install ELK
•	Enable docker service on restart
•	Install Ansible hosts
Target Machines & Beats
This ELK server is configured to monitor the following machines:
•	_TODO: List the IP addresses of the machines you are monitoring 10.1.0.7, 10.1.0.8 10.1.0.5, 10.0.0.5
We have installed the following Beats on these machines:
•	We successfully installed_filebeat and metricbeat.
These Beats allow us to collect the following information from each machine:
-Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
-Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:
•	Copy the Playbook.yml_ file to the anisble container_in the Jump Box_.
•	Update the the ansible.cfg_ file to include the IPs of the three machines (Web-1 10.1.0.7, Web_2 10.1.0.8, and Web_3 10.1.0.5)
•	Run the playbook, and navigate to _the ansible container and http://13.95.171.78:5601/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
•	_Which file is the playbook? Where do you copy it? Filebeat and Metricbeat playbooks and they’re copied in the Ansible container
•	_Which file do you update to make Ansible run the playbook on a specific machine? The Ansible Playbook by adding the ELKVM’s IP address to the config file
•	_Which URL do you navigate to in order to check that the ELK server is running? http://13.95.171.78:5601/app/kibana
_

