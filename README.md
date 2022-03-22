# Part-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![https://github.com/aplum97/Part-1/blob/main/Diagrams/drawio.png](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.

- What aspect of security do load balancers protect? 
- Load Balancing plays an important security role as computing moves evermore to the cloud. The off-loading function of a load balancer defends an organization against distributed **denial-of-service (DDoS) attacks**. It does this by shifting attack traffic from the corporate server to a public cloud provider.

- What is the advantage of a jump box?
- **Optimizing** resource usage, data delivery, and response time, load balancing allows high-traffic websites, applications, and databases to be managed. **Flexibility:** Furthermore, load balancing provides the flexibility of adding and removing servers according to demand. In addition, the traffic is routed to another server during maintenance, so server maintenance can be performed without affecting users. **Scalability:** Traffic increases can negatively affect the performance of an application or website as it is used more often. Load balancing gives you the flexibility to add physical or virtual servers without disrupting current services. Load balancers seamlessly involve new servers in the process as soon as they go online. An overloaded server can be upgraded without much downtime, versus moving a website to a different one. **Redundancy:** Load balancing provides built-in redundancy through the distribution of traffic among servers. Users will experience minimal impact from rerouting the load if a server fails.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- _What does Filebeat watch for?_
-  **Filebeat** watches and monitors the log files or locations that users specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. Filebeat is a lightweight shipper for forwarding and centralizing log data.

- _What does Metricbeat record?_
- **Metricbeat** is a lightweight shipper that records and periodically collects metrics from the operating system and from services running on the server and takes the metrics and statistics that it collects and ships them to the output that users specify, such as Elasticsearch or Logstash. The configuration details of each machine may be found below.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| TODO     |          |            |                  |
| TODO     |          |            |                  |
| TODO     |          |            |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the host machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-192.168.13.1

Machines within the network can only be accessed by .
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible does not track dependencies and simply executes sequential tasks and stops when tasks finish, fail, or any error comes. These traits are not ideal for users who want the automation tool to maintain a detailed catalog for ordering.

- _What is the main advantage of automating configuration with Ansible?_
- **Saving Time**. Before automation, system administrators had to spend hours configuring machines manually, after Ansible, the time required to configure the whole process is less than 3 minutes!!! The second benefit is reducing bugs and errors.

The playbook implements the following tasks:
- _Explain the steps of the ELK installation play: 
- First I, SSH into the Jump-Box-Provisioner (ssh )?
- Start/Attached to the ansible docker (sudo docker start tender_morse)/(sudo docker attach tender_morse)?
- Went to /etc/ansible/roles directory and created the ELK playbook (Elk_Playbook.yml)
- Ran the Elk_Playbook.yml in that same directory (ansible-playbook Elk_Playbook.yml)
- Lastly, I SSH into the ELK-VM to verify the server is up and running.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _Explain what kind of data each beat collects, and provide 1 example of what you expect to see:
- **Filebeat** is used to collect log files from specific files on remote machines.
- Examples of Filebeats can be files that are generated by Apache, Microsoft Azure tools, the Nginx web server, and MySQl databases.
-**Metricbeat** collects machine metrics. It is simply a measurement to tell analysts how healthy it is.
-_Examples of Metricbeat can be CPU usage/Uptime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
---**Filebeat**---
- Copy the **filebeat-configuration.yml** file to **/etc/ansible/roles/files**.
- Update the **filebeat-configuration.yml** file to include **the ELK private IP in lines 1106 and 1806.**
- Run the playbook, and navigate to (ELK-VM public IP) to check that the installation worked as expected.

---**Metricbeat**---
-Copy the **metricbeat-configuration.yml** file to **/etc/ansible/roles/files**.
-Update the **metricbeat-configuration.yml** file to include **the ELK private IP in lines 62 and 96.**
-Run the playbook, and navigate to (ELK-VM public IP) to check that the -installation worked as expected.

- _Which file is the playbook?_ **filebeat-playbook.yml**
- 
- _Where do you copy it?_ **/etc/ansible/roles**
- 
- _Which file do you update to make Ansible run the playbook on a specific machine?_ **/etc/ansible/hosts file (IP of the Virtual Machines)**.
- 
- _How do I specify which machine to install the ELK server on versus which to install Filebeat on?_  I have to specify two separate groups in the etc/ansible/hosts file. One of the groups will be webservers which has the IPs of the VMs that I will install Filebeat to. The other group is named elkservers which will have the IP of the VM I will install ELK to.
- 
- _Which URL do you navigate to in order to check that the ELK server is running?
(ELK-VM public IP)

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

  -------Filebeat---------

- To create the filebeat-configuration.yml file: nano filebeat-configuration.yml. For this, I used the filebeat configuration file template.

- To create the playbook: nano filebeat-playbook.yml

  ---
 - name: installing and launching filebeat
	   hosts: webservers
       become: true
       tasks:

	   - name: download filebeat deb
  	     command: curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.7.1-amd64.deb

	   - name: install filebeat deb
  	     command: dpkg -i filebeat-7.7.1-amd64.deb

	   - name: drop in filebeat.yml
  	     copy:
   	       src: ./files/filebeat-configuration.yml
   	       dest: /etc/filebeat/filebeat.yml

	   - name: enable and configure system module
  	     command: filebeat modules enable system

	   - name: setup filebeat
  	     command: filebeat setup

	   - name: start filebeat service
  	    command: service filebeat start
---
-To run the playbook: ansible-playbook filebeat-playbook.yml

* In order to run the playbook, you have to be in the directory the playbook is at, or give the path to it (ansible-playbook /etc/ansible/roles/filebeat-playbook.yml


-------Metricbeat-------

- To create the metricbeat-configuration.yml file: nano metricbeat-configuration.yml. For this, I used the metricbeat configuration file template.

- To create the playbool: nano metricbeat-playbook.yml

---
  - name: installing and lunching metricbeat
    hosts: webservers
    become: true
    tasks:
    
  - name: download metricbeat deb
    command: curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.7.1-amd64.deb
    
  - name: install metricbeat deb
    command: sudo dpkg -i metricbeat-7.7.1-amd64.deb
    
  - name: drop in metricbeat.yml
    copy:
      src: /etc/ansible/roles/files/metricbeat-configuration.yml
      dest: /etc/metricbeat/metricbeat.yml
      
   - name: enable and configure system module
     command: metricbeat modules enable system
     
   - name: setup metricbeat
     command: metricbeat setup
     
   - name: start metricbeat service
     command: service metricbeat start
     
   ---
   
   - To run the playbook: ansible-playbook metricbeat-playbook.yml
   
   * To order to run the playbook, you have to be in the directory the playbook is at, or give the path to it (ansible-playbook /etc/ansible/roles/metricbeat-playbook.yml
