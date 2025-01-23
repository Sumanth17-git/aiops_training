Here’s a step-by-step guide to setting up Dynatrace OneAgent using an Ansible playbook. This playbook assumes you are deploying the OneAgent on Linux servers.
Prerequisites
Dynatrace account: Ensure you have access to your Dynatrace environment and have the installation script URL.
Ansible control node: Ensure Ansible is installed and configured on your control machine.
Target hosts: These should be Linux machines with SSH access from the Ansible control node.
Installation script URL: Obtain the OneAgent installation script URL from your Dynatrace environment. For example:
https://<environment-id>.live.dynatrace.com/api/v1/deployment/installer/agent/unix/default/latest?Api-Token=<token>&arch=x86
