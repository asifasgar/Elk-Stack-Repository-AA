# Elk-Stack-Repository-AA
Elk Stack Project Repository for Asif Asgar
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


[Link to network Diagram](https://github.com/asifasgar/Elk-Stack-Repository-AA/blob/main/Diagrams/CloudNetworkProject.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

[Link to Filebeat playbook](https://github.com/asifasgar/Elk-Stack-Repository-AA/blob/main/Ansible/Filebeat-yml.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.



Answer 

Load Balancing plays an important security role as computing moves evermore to the cloud. The off-loading function of a load balancer defends an organization against distributed denial-of-service (DDoS) attacks. It does this by shifting attack traffic from the corporate server to a public cloud provider. Load balancing is the process of distributing network traffic across multiple servers. This ensures no single server bears too much demand. By spreading the work evenly, load balancing improves application responsiveness. It also increases availability of applications and websites for users. Modern applications cannot run without load balancers. Over time, software load balancers have added additional capabilities including application security
A jump server, jump host or jump box is a system on a network used to access and manage devices in a separate security zone. A jump server is a hardened and monitored device that spans two dissimilar security zones and provides a controlled means of access between them.




Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.

Answer
Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

What does Metricbeat record?

Answer

Metricbeat is a lightweight shipper that records and periodically collects metrics from the operating system and from services running on the server and takes the metrics and statistics that it collects and ships them to the output that users specify, such as Elasticsearch or Logstash.



The configuration details of each machine may be found below.
Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1	   | Server   | 10.0.0.10  | Linux            |
| Web-2    | Server   | 10.0.0.11  | Linux            |
| Elk-Serv | Server   | 10.1.0.4   | Linux	      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

5061 Kibana port

Machines within the network can only be accessed by Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Which machine did you allow to access your ELK VM? What was its IP address?

Jump Box Provisioner 

10.0.0.4




A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 40.77.106.43         |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| Elk-Serv | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because

--Free: Ansible is an open-source tool.
--Very simple to set up and use: No special coding skills are necessary to use Ansible's playbooks.
--Powerful: Ansible lets user model even highly complex IT workflows.
--Flexible: User can orchestrate the entire application environment no matter where it’s deployed. Users can also customize it based on their needs.
--Agentless: User don’t need to install any other software or firewall ports on the client systems it want to automate. User also don’t have to set up a separate management structure.
--Efficient: Because user don’t need to install any extra software, there’s more room for application resources on the server.


The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
--Install docker.io
--Install pip3
--Install Docker python module
--Increase virtual memory
--Download and launch a docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[Sudo docker PS screenshot](https://github.com/asifasgar/Elk-Stack-Repository-AA/blob/main/Diagrams/Docker%20PS%20screenshot.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring

Web-1  10.0.0.10
Web-2  10.0.0.11



We have installed the following Beats on these machines:

Filebeat

Specify which Beats you successfully installed

Filebeat - collects data about the file system such as log events, and ships them to the monitoring cluster.

These Beats allow us to collect the following information from each machine:
1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

SSH into the control node and follow the steps below:

Copy the Playbook file to Ansible.
Update the host file to include webserver and ELK.
Run the playbook, and navigate to Kibana to check that the installation worked as expected.
Specific commands the user will need to run to download the playbook
nano ansible.cfg
add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts
Ctrl + x to exit file
in the folder that install-elk.yml is in, run: cp install-elk.yml /etc/ansible
nano install-elk.yml /etc/ansible
name: installing elk hosts: [your_machine]
Ctrl + x to exit file
ansible-playbook install-elk.yml
.
