## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive and available, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? Load balancers protect a ddos attack. What is the advantage of a jump box?_ The advantage of jump box protects the other virtual machines by limiting traffic and limiting flow with traffic rules. It limits direct access to the virtual machines. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log and system traffic.
- _TODO: What does Filebeat watch for? Any file changes on the system through Log data.
- _TODO: What does Metricbeat record?_monitors the server and all system metrics: temperatures, hard drive and cpu usage, etc traffic on the server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| name                | function                                              | IP Addresses           |                             |
|---------------------|-------------------------------------------------------|------------------------|-----------------------------|
| jumpbox provisioner | gateway                                               | 10.1.0.4/20.89.130.201 | Linux Ubuntu 18.04 LTX Gen2 |
| web 1               | web 1 to run DVWA                                     | 10.1.0.8               | Linux Ubuntu 18.04 LTX Gen2 |
| web 2               | web 2 to run DVWA                                     | 10.1.0.9/20.222.64.180 | Linux Ubuntu 18.04 LTX Gen2 |
| Red Elk             | Elk container with filebeat and metric beat to kibana | 10.2.04/20.92.81.44    | Linux Ubuntu 18.04 LTX Gen2
|   |   |   |   |   |
|---|---|---|---|---|
|   |   |   |   |   |
|   |   |   |   |   |
|   |   |   |   |   |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _Jumpbox provisioner____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My public IP address via SSH Port 22

Machines within the network can only be accessed by Jump Box Provisioner and SSH key.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?
My jump box provisioner SSH to 10.2.0.4_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |

| \| Name      | publicly accessible | allowed ip addresses |
|--------------|---------------------|----------------------|
| Jump Box     | YES                 | 20.89.130.201        |
| web 1        | No                  | 10.1.0.8             |
| web 2        | No                  | 10.1.0.9             |
| Red Elk      | yes                 | 20.92.81.44          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible? Time was saved by loading the configurations with Ansible across all virtual machines and removes the need for individually modifying each configuration. 

The playbook implements the following tasks:
TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g.,

Install Docker;
Install Python PIP
Install Docker Python
Increase virtual memory on Elk container 
Use more memory
Enable service docker on boot



The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.1.0.8
10.1.0.9

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
We installed metricbeat and filebeat to the virtual machines.

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them to either to Elasticsearch or Logstash for indexing.
Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _config____ file to files.
- Update the config file to include remote users private IP addresses
- Run the playbook, and navigate to myipaddress:5601/kibana/app to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filebeat-playbook.yml Where do you copy it? /etc/filebeat/filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? The config file with remote_user. 
How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ by specifying the IP addresses for the install, the machine knows where to do the install. 

- _Which URL do you navigate to in order to check that the ELK server is running?
myipaddress:5601/kibana/app
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

Cd /etc/ansible
Sudo docker container list -a
Docker ps
Sudo docker start lucid_banach
Sudo docker attach lucid_banach

Ansible-playbook install-elk.yml
ansible-playbook metricbeat-playbook.yml
Ansible-playbook filebeat-playbook.yml
Nano hosts
Nano install-elk.yml
Nano metricbeat-playbook.yml
Nano metricbeat-config
Ssh key-gen
Cat .ssh/id_rsa.pub
Ls

