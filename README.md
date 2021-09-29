# UR-Cyber-Security-ELK-Stack-Project 

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Diagrams/ELK_Diagram.jpg "ELK Diagram")

I created an ELK stack that allows the automatation of monitoring the performance of multiple virtual machines in one database.  By using the ELK Server in conjunction with containers, the benefits are:

  - Scalability and Elasticity
  - Efficiency of Resources
  - Increased Security
  - App Isolation

For more information about [Cloud Domain, Containers, and the Security Benefits](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Additional%20Resources/Interview_Question.md)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above, or select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
- Bonus - Commands Used

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.

The Jump Box is a tool used to connect to devices within a security zone. Because it was set up with SSH Keys instead of passwords, it protects the machines from DDoS attacks.

Integrating an ELK server allows users to easily monitor the webservers for changes to the logs and system metrics and statistics.

Filebeat collects data about the file system. Metricbeat collects machine metrics, such as uptime. 

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.8   | Linux            |
| Web-1    | Server   | 10.0.0.7   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
|ELK-server| Server   | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- My home IP address (100.7.126.87)

Machines within the network can only be accessed by Local workstation and Jumpbox.

The Jumpbox VM was allowed access to the ELK VM.
Jumpbox VM: IP 10.0.0.8 Local Workstation via SSH IP 100.7.126.87

A summary of the access policies in place can be found in the table below.

|   Name   | Publicly Accessible | Allowed IP Addresses  |
|----------|---------------------|-----------------------|
| Jump Box |        No           |      100.7.126.87     |
|   Web-1  |        No           |10.0.0.7 & 100.7.126.87|
|   Web-2  |        No           |10.0.0.6 & 100.7.126.87|
|ELK-Server|        No           |10.2.0.4 & 100.7.126.87|


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the playbook, much like the ones for Filebear and Metricbeat, saved time and remove [some] elements of human error.  

[Link to Playbooks and Config Files](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/tree/main/Ansible)

|ELK_Playbook tasks    |
|----------|
| Install docker.io |
| Install Python-pip  |
| Install: docker |
|Launch docker container: elk|

The following [screenshot](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Linux/docker%20elk%20sebp_elk_761.PNG) displays the result of running 'docker ps' after successfully configuring the ELK instance.

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

| Name     | Function | IP Address |
|----------|----------|------------|
| Web-1    | Server   | 10.0.0.7   |
| Web-2    | Server   | 10.0.0.6   |

We have installed the following Beats on these machines:

- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

- Filebeat can handle audit logs, deprecation logs, gc logs, server logs, and slow logs. 

- Metricbeat collects machine metrics. For example, Metricbeat can be used to monitor and analyze system CPU, memory and load.

![alt text](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Additional%20Resources/heatmap.PNG "Heat Map")

![alt text](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Additional%20Resources/location.PNG "Location")

### Using the Playbook

There were four playbooks used when creating this network.  

| Playbook     | Action(s) |
|----------|----------|
| my-playbook | This is the initial playbook to add a container to the Jump Box and install docker.io, pip3, Docker python | 
| ELK_playbook | This playbook increased the resources for the ELK server, add the container, and install docker.io, pip3, Docker python  | 
| filebeat-playbook | This playbook pulled the download, config file, and .yml for Filebeat | 
| metricbeat-playbook | This playbook pulled the download, config file, and .yml for Metricbeat  | 

  - [Playbooks and Config Files](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/tree/main/Ansible)
  
Since 'my-playbook' was the playbook created as part of the Cloud Security unit, it would need to be implemented first to have an Ansible control node configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

- Copy the playbook file to /etc/ansible.
- Update the host file to include the webservers and ELK server (and IP addresses).
- Run the playbook, and navigate to command line to check that the installation worked as expected.
- Playbook: ELK_server.yml Location: /etc/ansible/ELK_server.yml

[ELK Playbook](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Ansible/ELK_Playbook.txt)

The Ansible Host File is updated to include the two webservers and the elk server.

- [Ansible Host File](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Ansible/hosts.txt)

- [GitBash Steps to enable Kibana Dashboard](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Linux/GitBash%20Steps.md)

To check if the ELK server is running, the URL is: http://13.83.81.121:5601/app/kibana

## Bonus
[Link to Bonus: Commands](https://github.com/joshblack07/UR-Cyber-Security-ELK-Stack-Project/blob/main/Linux/Bonus)
