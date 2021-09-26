# Bootcamp_project_1
My first project submission file.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

  -Playbooks can be found in 'Playbooks' file.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly safe, in addition to restricting traffic to the network.

Load balancers are used to redirect network traffic from one server to another in order to protect against large loads of traffic or DDoS attacks.

Jump boxes help to secure virtual machines within platforms so that they are not exposed and accessible to the entire internet. We can also use jump boxes to limit how much access there is, such as only letting certain IP addresses and keys inside.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the networks and system logs.

Filebeat gathers data about a file system.

Metricbeat gathers data such as machine metrics and uptime. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box  | Gateway            | 10.0.0.4  | Linux |   |
|-----------|--------------------|-----------|-------|---|
| Elk-VM    | VM to analyze data | 10.2.0.4  | Linux |   |
| VM 1      | VM of Azure's      | 10.0.0.5  | Linux |   |
| VM 2      | VM of Azure's      | 10.0.0.6  | Linux |   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Access to this machine is only allowed from the local machine with the matching ssh key for unlocking access the the Jump Box.

Machines within the network can only be accessed by my local computer unless otherwise changed.

The Elk VM was only accessible through the Ansible container.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box  | Yes                | 24.8.191.... |
|-----------|-----|--------------|
| VM 1      | No                 | 10.0.0.4     |
| VM 2      | No                 | 10.0.0.4     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

Ansible allows us to install anything we need using OpenSSH instead.

The playbook implements the following tasks:

~ First, you install Docker
~ Then, you need to install Python3-pip
~ After that, you would need to increase virtual machine memory
~ Then, you download the ELK container 
~ Next, you launch the Elk container
~Lastly, you add ports 5601, 9200, and 5044

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Can be found in Images folder under 'docker_output_ps.png'.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

The ELK server was setup to monitor the Web-1 and Web-2 machines with the IP addresses of 10.0.0.5 and 10.0.0.6.

We have installed the following Beats on these machines:

Filebeat and Metricbeat were installed on both.

These Beats allow us to collect the following information from each machine:

Metricbeat is used to monitor the key statistics of the VM, this includes memory, networking, and many other statistics. Filebeat is used to gather log files from things like web servers and other tools.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to '/etc/ansible/filebeat-config.yml'.
- Update the filebeat-config.yml file to include the IP address of our ELK machine.
- Run the playbook, and navigate to the target machine to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?

My playbook file is called 'filebeat-playbook.yml' and it is located in '/etc/ansible/roles'

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

To get the playbook to install on a specific machine you need to give it a place to reference. In my case, I wanted it to run in the 'webservers' group the IP addresses for that group are located in Ansibles hosts file.

- _Which URL do you navigate to in order to check that the ELK server is running?

To check that the ELK server is running you would navigate to the 'http://52.183.3.242:5601/app/kibana' URL.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

To download the playbook you would run 'ansible-playbook /etc/ansible/roles/filebeat-playbook.yml'

To update the update any of the files you would use 'nano [whatever the location and name of the file is]'
