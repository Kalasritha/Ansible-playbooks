Ansible Playbook to Install Docker and Deploy a Container
Overview
This document describes an Ansible playbook that installs Docker on an Ubuntu server, pulls a Docker image, and runs a container automatically. The playbook uses the community.docker collection for efficient Docker image and container management.
Playbook Features
- Installs required system packages
- Adds Docker GPG key for secure package verification
- Configures Docker’s official APT repository
- Installs Docker Engine (docker-ce)
- Ensures Docker service is running and enabled
- Pulls the nginx:latest Docker image
- Runs an Nginx container with port mapping
- Uses community.docker collection for Docker modules
Requirements
Control Machine (Ansible Host):
- Ansible 2.10 or above
- community.docker collection installed
Install collection using:
ansible-galaxy collection install community.docker
Target Machine:
- Ubuntu OS
- Sudo privileges
Files
1.	docker.yaml – Main playbook
2.	hosts – Inventory file
3.	README – Documentation
How to Run the Playbook
1.	Create a hosts inventory file:
2.	[servers]
3.	server_ip ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
4.	Run the playbook:
5.	ansible-playbook -i hosts install_docker.yaml
How the Playbook Works
1. Installs required system packages
2. Adds Docker GPG key
3. Adds Docker APT repository
4. Installs Docker Engine
5. Enables and starts Docker service
6. Pulls nginx Docker image
7. Runs nginx container with restart policy
Verification
After running the playbook, log into the server and run:
docker --version
docker ps
You should see Docker installed and the container 'my_nginx' running.

