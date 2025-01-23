# Ansible Setup and Configuration Guide

## Step 1: Create Two Virtual Machines (VMs)

1. **Master VM (Good Specs)**
   - This will be the machine where Ansible is installed and run.
   
2. **Target VM (Medium Specs)**
   - This will be the machine where Nginx will be installed.
---
## Step 2: Setup Ansible on Master VM

### 1. **Make Setup Script Executable**

On the Ansible Master VM, navigate to the directory where your setup script is located and make it executable:

```bash
chmod +x ansible_setup_master.sh

##  Step 3: Setup Ansible on Target VM

Copy the Public Key from Master VM
On the Master VM, retrieve the public SSH key to allow SSH access to the Target VM
```bash
cat ~/.ssh/id_rsa.pub
Copy the output of this command, as you will need to paste it into the Target VM.

### 2. **Run Setup Script on Target VM**
On the Target VM, execute the setup_ansible_target.sh script, and paste the copied public key when prompted:
```bash
./setup_ansible_target.sh
This script will configure the Target VM to allow SSH connections from the Master VM and install the necessary packages for Ansible management.

