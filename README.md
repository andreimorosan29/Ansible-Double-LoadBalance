# Ansible-Double-LoadBalance
How to create an Ansible Playbook for Load Balancing 2 VMs in replication.

1. Testing the initial commit - Hello world!

TODO:

1. Ansible Playbook to install 3 Ubuntu 20.04 VMs.
2. Ansible Playbook for VMs initialization.
3. Ansible Playbook - Install & Configure NGINX
4. Ansible Playbook - Install & Configure NFS
5. Ansible Playbook - Install MariaDB
6. Ansible Playbook - Configure MariaDB Master VM
7. Ansible Playbook - Configure MariaDB Slave VM
8. Ansible Playbook - Configure NGINX Load Balancer VM

Changes:
1. Created install-vms-playbook.yml
2. Deleted the install-vms-playbook.yml - for now as it is a bit hard and we'll circle back around it later
3. Created:
    + update-upgrade-vms.yml --runs updates and upgrades on the VMs
    + inventory.ini --contains the information for the target VMs

    To run the playbook: 
    sudo ansible-playbook -i inventory.ini update-upgrade-vms.yml --extra-vars "ansible_sudo_pass=0000"
    + Added reboot after upgrade in the update-upgrade-vms.yml
    + Tried to learn and create snapshots for the VM, unfortunately not possible since I don't have vCenter on my poor man's setup
    + Commented potential additions for that

