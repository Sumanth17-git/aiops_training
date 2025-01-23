# Ansible Setup and Configuration Guide

## Step 1: Create Two Virtual Machines (VMs)

1. **Master VM (Good Specs)**
   - This will be the machine where Ansible is installed and run.
   
2. **Target VM (Medium Specs)**
   - This will be the machine where Nginx will be installed.

## Step 2: Setup Ansible on Master VM

### 1. **Make Setup Script Executable**

On the Ansible Master VM, navigate to the directory where your setup script is located and make it executable:
chmod +x ansible_setup_master.sh

## Step 3: Setup Ansible on Target VM

### 1. **Copy the Public Key from Master VM**

On the Master VM, retrieve the public SSH key to allow SSH access to the Target VM:

```bash
cat ~/.ssh/id_rsa.pub

Copy the output of this command, as you will need to paste it into the Target VM.

### 2. **Run Setup Script on Target VM**

On the Target VM, execute the `setup_ansible_target.sh` script, and paste the copied public key when prompted:

```bash
./setup_ansible_target.sh

This script will configure the Target VM to allow SSH connections from the Master VM and install the necessary packages for Ansible management.

##  Step 4: Validate the Connection Between Master and Target VM

1. Create an Ansible Inventory File
Create an inventory file (inventory.ini) on the Master VM to define the Target VMs. You can store this file in /etc/ansible/hosts or in a custom location (e.g., inventory.ini).

vi inventory.ini
[targets]
10.150.0.9
10.150.0.8
This file tells Ansible the IP addresses of the Target VMs (10.150.0.9 and 10.150.0.8).
### 3. **Test Connectivity Using Ansible**

Run the following command to test the connectivity from the Master VM to the Target VMs:

```bash
ansible all -i inventory.ini -m ping


## Step 5: Create a Playbook to Install Nginx on Both Servers

### Run the Playbook

Execute the playbook to install Nginx on the Target VMs:

```bash
ansible-playbook -i inventory.ini install_nginx.yml
