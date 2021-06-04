# ElkStackProject
## Automated ELK Stack Deployment.

The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly versitile, in addition to restricting large amounts of traffic to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

The configuration details of each machine may be found below.

|  Name      | Function | IP Address | Operating System |
|------------|----------|------------|------------------|
|  Jump Box  | Gateway  | 10.1.0.4   | Linux            |
|  Web-1     | Server   | 10.1.0.5   | Linux            |
|  Web-2     | Server   | 10.1.0.6   | Linux            |
|  Web-3     | Server   | 10.1.0.7   | Linux            |
| ProjectVM1 | Monitor  | 10.2.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 24.154.112.183

Machines within the network can only be accessed by the Jumpbox, however the ELK VM is accesed from the ansible container 172.17.0.2.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 24.154.112.183       |
| Elk Stack| Yes                 | 24.154.112.183       |
| Web VMs  | No                  | 52.150.15.153        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because additional configurations can be automated in a similar fashion. It also makes it easier to automate processes on large numbers of machines.

The playbook implements the following tasks:
-  Installs Docker
-  Installs Python
-  Increases allowed memory usage
-  Creates the docker ELK container
-  Enables the docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screenshot (35)](https://user-images.githubusercontent.com/38328713/120834785-80ce3880-c531-11eb-9873-93b4fc6b1d30.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: 
- Web-1 10.1.0.5
- Web-2 10.1.0.6
- Web-3 10.1.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filbeat will allow us to monitor edits and changes to the files within each of the machines being monitored
- Metricbeat allows us to monitor and collect metrics from the operating system and the server.
 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk2playbook.yml file to ansible containter (example mine is Funny_robinson).
- Update the etc/ansible/hosts file to include the Web servers Web-1, Web-2, Web-3.
- Run the playbook, and navigate to the Elk server (ProjectVM1) to check that the installation worked as expected.
      -http://52.242.79.45:5601/app/kibana#/home

