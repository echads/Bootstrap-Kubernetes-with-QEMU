## Bootstrap Kubernetes with Ansible

# Summary
This project leverages Ansible and Proxmox to build a four node cluster with Linux Containers (LXC)

# Requirements
1) A configured Proxmox server
2) Ability to provision DNS records
3) Ansible 2.7.0+. Known incompatibility with a previous build. 

# Instructions

1) Modify the vars files with values specific to your environment.
2) Provision internal DNS A records for the IP Addresses & hostnames you defined for your nodes.
3) Update the inventory file to reflect your DNS records.
3) `ansible-playbook -e @Vars/vars.yml -i Inventories/Kubernetes_LXC.ini site.yml`
4) ???
5) Profit

# Tips

1) If the playbook fails when trying to install openssh-server and throws a weird `yum` error, it's likely your containers don't have network connectivity.
2) To easily delete all of the deployed resources, execute the `delete_all_resources.yml` playbook. 
3) It's possible that the `delete_all_resources.yml` playbook will fail to unload the overlay module if it is currently in use. 