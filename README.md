
# Multi-Node Infrastructure Automation Lab

This project demonstrates the automated provisioning and management of a hybrid Linux cluster using Vagrant and Bash Scripting. It simulates a real-world DevOps environment where a central management server (Control Plane) orchestrates operations across multiple web nodes.

 #Architecture Overview
The cluster consists of four virtual machines running on a private network (192.168.56.0/24):

scriptbox (CentOS Stream 9 | 192.168.56.10): Acts as the Management and Bastion Host.

web01 (CentOS Stream 9 | 192.168.56.11): Production Web Server.

web02 (CentOS Stream 9 | 192.168.56.12): Staging Web Server.

web03 (Ubuntu 18.04 | 192.168.56.13): Legacy/Testing Web Server.
 
 Key Features & Skills Demonstrated1. Infrastructure as Code (IaC)
 Used a single Vagrantfile to define the entire hardware stack, including:
 Multi-machine orchestration.
 Memory and CPU allocation.
 Static private networking and hostname assignment.
 2. Linux AdministrationUser 
 Management: Standardized a devops user across different distributions (RHEL-based and Debian-based).
 Security: Configured sudoers files via visudo to allow administrative tasks without root login.
 Environment Configuration: Managed /etc/hosts for local DNS resolution between nodes.
 3. SSH Automation
 Implemented secure, passwordless communication from the scriptbox to all web nodes:
 Generated RSA Keypairs.
 Automated key distribution using ssh-copy-id.
 Configured sshd_config to optimize remote access.
 4. Fleet Orchestration (Bash)
 Developed a Master Health Check script that iterates through the node fleet to report:
 Network Latency/Connectivity.System Uptime.CPU Load averages.
  How to Use
  Prerequisites
  Vagrant installed.
  VirtualBox installed.
  Setup 
 1. Clone this repository:
  Bsh
  git clone https://github.com/YOUR_USERNAME/vagrant-multi-node-automation.git
cd vagrant-multi-node-automation
2. Spin up the cluster:
   
   vagrant up
   3.Access the management node:

   vagrant ssh scriptbox
Run the health check:
sudo -i
/vagrant/scripts/check_cluster.sh

📁 Project StructurePlaintext.
├── Vagrantfile              # VM Infrastructure definitions
├── scripts/
│   └── check_cluster.sh     # Automation script for fleet monitoring
└── README.md                # Project documentation
Author: OnyekaProject: DevOps Engineering Lab - 2026

