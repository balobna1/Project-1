# Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![image](https://user-images.githubusercontent.com/77943718/116742164-fee47000-a9c4-11eb-9afc-041c190e3585.png)


**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file. /etc/ansible/my-elkservers.yml

This document contains the following details:

- Description of the Topology
-  Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
- Description of the Topology: The purpose of this topooglogy is to monitor the DVWA. Load balancing helps to monitor traffic. This in turn increases the secuirty by limititng traffic into the network. This is very helpful in decreasing DDoS attacks. Adding an ELK server to the system allows adds another layer of security because it provides the team with a tool to monitor the system and its traffic. 

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
-Load balancers are able to redirect traffic, this in turn improves the security by protecting the system from DDos atacks. The advantage is that it gives a user secure access. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_Any changes in the file and when it occured.
- _TODO: What does Metricbeat record?_Determines the metrics and moves it to the output 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function | IP Address | Operating System |
|---------- |----------|------------|------------------|
| Jump Box  | Gateway  | 10.0.0.4   | Linux            |
| Web1      |  Server  | 10.0.0.5   | Linux            |
| Web2      |  Server  | 10.0.0.6   | Linux            |
| Web3      |  Server  | 10.0.0.7   | Linux            |
| ELK Server|  Server  | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_Is the public home IP address

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ The jump box private IP address of 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | No                  | Home IP              |
| Web 1      | No                  | 10.0.0.4             |
| Web 2      | No                  | 10.0.0.4             |
| Web 3      | No                  | 10.0.0.4             |
| ELK Server | No                  | 10.0.0.4             | 
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ By including all the plays and commands in one file it makes it easier to have the tasks automated to more than one server, by simply using one playbook. This makes the role of the ssytem administrator that much easier because it is one less thing that they have to manually do. 

The playbook implements the following tasks:
- Install docker.io
- Instal python-pip (you can specify python3)
- Install the docker
- Launch elk-docker 
- sudo docker start elk


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
- Web 1 10.0.0.5, Web 2 10.0.0.6, and Web 3 10.0.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeat and metricbeats were installed

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
A filebeat identifies the change. Whereas the metricbeat determines the metrics. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __ansible.cfg___ file to __/etc/ansible___.
- Update the _hosts____ file to include...the ansible.cfg which includes the IP of the machine
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ he configuration yml file holds the playbook. It is copied into the following location: /etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ By updating the host file, ansible will know which machine to run the playbook for. You can simply nano and configure the file accordingly and save before running the playbook. By determing the IP address you can determine where to install the file beat. 
- _Which URL do you navigate to in order to check that the ELK server is running? Kibana is used to determine if the ELK server is running properly. www.publicip:5601 


