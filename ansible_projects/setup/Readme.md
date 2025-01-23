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
