Refer
```bash https://github.com/genzgurukul/dynatrace_practice/blob/main/Basic_Setups/04.Managing%20Dynatrace%20OneAgent%20Deployment%20using%20Ansible.md
```
# Setting Up Dynatrace OneAgent Using an Ansible Playbook

This guide provides step-by-step instructions for setting up Dynatrace OneAgent using an Ansible playbook. The instructions assume the deployment is on Linux servers.

## Prerequisites

1. **Dynatrace Account**  
   - Ensure you have access to your Dynatrace environment.  
   - Obtain the installation script URL from your Dynatrace environment.

2. **Ansible Control Node**  
   - Verify that Ansible is installed and configured on your control machine.

3. **Target Hosts**  
   - Ensure the target Linux machines have SSH access from the Ansible control node.

   Example setup:
   - Ansible control machine: Manages the playbook execution.
   - Target hosts: Linux servers where Dynatrace OneAgent will be installed.

## Create API Token on Dynatrace with PaaS Integration - Installer Download Scope

1. **Go to Dynatrace Console**  
   Navigate to:  
   `Settings` → `Access Tokens` → `Generate a Token`

2. **Choose Scope**  
   Select the scope:  
   **PaaS integration - Installer download**

3. **Copy the API Token**  
   Once generated, copy the **API Token** for use in your automation or setup.


## Installation Script URL
Obtain the OneAgent installation script URL from your Dynatrace environment. For example:

```bash
https://<environment-id>.live.dynatrace.com/api/v1/deployment/installer/agent/unix/default/latest?Api-Token=<token>&arch=x86


### Step 1: Test Ansible Connection to the Hosts
Run the following command to verify the connection to all target hosts:

```bash
ansible all -m ping -i inventory.ini

### Step 2: Run the Ansible Playbook
Execute the following command to deploy the Dynatrace OneAgent on the target hosts:

```bash
ansible-playbook dynatrace_oneagent.yml -i inventory.ini --extra-vars "@vars.yml"


### Explanation of Tasks

1. **Install Required Tools**  
   Ensures `curl` and `tar` are installed on the target hosts to support the installation process.

2. **Download the Installer**  
   Downloads the Dynatrace OneAgent installer script to the `/tmp` directory.

3. **Run the Installer**  
   Executes the installer script with the required parameter:  
   - `APP_LOG_CONTENT_ACCESS=1`: Enables log monitoring.

4. **Start and Enable Service**  
   Ensures the `oneagent` service is running and configured to start automatically on boot.

5. **Clean Up**  
   Deletes the installer script from the `/tmp` directory to save space and enhance security.

