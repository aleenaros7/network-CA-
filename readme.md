# Ansible playbook deployement for installing docker container to get static webpage in specified subnet.

This Git repo contains an Ansible playbook and necessary files for deploying an Apache HTTP server using Docker containers.

# Infrastructure Setup

# Control Machine

- **Operating System:** Windows Subsystem for Linux (WSL) running Ubuntu 22.04 kernel.
- **Tools:** Visual Studio Code with WSL extension.

# Target Machine

- **Operating Sydtem:** Ubuntu 22.04in Oracle VirtualBox

# Prerequisites

- Ensure in control machine WSL installed and configured.
- Install Oracle VirtualBox on your Windows machine.
- Download the Ubuntu 22.04 ISO file from the official Ubuntu website.
- Configure target machine.
- Install openSSH in both target and control machine.

# Installation Steps

1. **WSL installation in control machine:**
    - In windows command prompt as admin
    - Run `wsl --install` command and restart your machine.
    - Install Ubuntu 22.04 using `wsl --install -d Ubuntu-22.04` command.

2. **Ansible installation on control machine**
    - In Visual studio code or in ubuntu terminal.
    - Run the following commands:
   ```
    ` sudo apt update`
    `sudo apt install software-properties-common`
    ` sudo add-apt-repository --yes --update ppa:ansible/ansible`
     `sudo apt install ansible command`.
   ```

3.  **OpensSSH installation on control mcahine**
    -Run the following commands:
    ```
    `sudo apt install openssh-client`
    `sudo apt install openssh-server`
    ```

5.  **Target machine set up (Ubuntu 22.04)**
    - Instal OpenSSh in target machine.
    - Change network adapter to Bridged Adapter.
    - Fetch IP address of the target machine using `ifconfig` command.

6. **Verify connection**
    - Ping IP of target machine from control machine
    - Check connectivity using `sudo ssh user@ip` where user is user name of target machine .
# Ansible Playbook
- Ansible playbook YML file (`deploy_docker.yml`) is included in this repository.
- Tasks defined in playbook.
  - Initialize playbook with host as target machine.
  - Install Python package manager (pip) on the target machine.
  - Install Docker Python module using pip.
  - Install Docker on the target machine.
  - Create Docker network.
  - Pull the latest Apache image, expose port 80, and connect volume from the control machine.
  - Copy HTML file from control machine to target machine.

# Deployment

1. **Git Repo Clone**
 - Clone this repo to your control machine using `git clone https://github.com/Jeevanandh007/Network-CA1.git` command.
 
 # Files

 - `deploy_docker.yml` Ansible playbook YAML file.
 - `inventory.txt` Target IP configuration with required permissions.
 - `ansible.cfg` Ansible configuration file to stop checking ansible host key.

2. **Execute Ansible Playbook**
 - Playbook can be run from control machine WSL terminal or using visual studio WSL terminal.

 - Command `ansible-playbook deploy_docker.yml` will execute the playbook.

3. **Access Apache Server**
 - After complete excecution index.html can be accessed from localhost and IP 172.168.10.2 from host.

 - Also it will be available from public IP of target machine.

# Thankyou ❤️
