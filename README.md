## Automated Server Configuration with Ansible
Infrastructure as Code (IaC) for System Updates, Nginx, and NFS Deployment

This master playbook automates server provisioning for the vmnet0 host group, ensuring consistent environments across development and production systems.

#### 🚀 Features
System Updates & Upgrades: Applies security patches and updates packages.

Nginx Web Server: Installs and configures Nginx as a reverse proxy.

NFS Shared Storage: Sets up centralized file sharing across servers.

#### 🛠 Playbook Structure
yaml
Copy
- name: Master Playbook
  hosts: vmnet0           # Target server group
  become: true            # Execute tasks with sudo privileges
  gather_facts: true      # Collect system information pre-execution
  tasks:
    - name: Include Update and Upgrade Playbook
      ansible.builtin.include_tasks: update-upgrade-vms.yml

    - name: Include Install Nginx Playbook
      ansible.builtin.include_tasks: install-nginx-all-vms.yml

    - name: Include Install and Configure NFS
      ansible.builtin.include_tasks: install-nfs-with-shared-folder.yml
#### 📦 Prerequisites
Ansible 2.10+

SSH access to target servers in vmnet0 group

Sudo privileges on target machines

#### ⚙️ Usage
Clone this repository:


Copy
<code>git clone https://github.com/your-username/ansible-server-config.git</code> <br>
Update inventory.ini with your server IPs/hostnames.

Run the playbook:


Copy
<code>ansible-playbook -i inventory.ini master-playbook.yml</code>  

#### 🌟 Key Technical Details
Aspect	Implementation
Modularity	Reusable subtasks via include_tasks
Security	Privilege escalation with become: true
Idempotency	Safe for repeated runs (no unintended changes)
Shared Storage	NFS configuration for cross-server collaboration

#### 💡 Why This Matters
Infrastructure as Code (IaC): Eliminates manual server setup errors.

DevOps Best Practices: Demonstrates automation, consistency, and scalability.

Enterprise Use Cases:

Rapid deployment of web servers (Nginx)

Secure shared storage for logs/data (NFS)

System hardening through automated updates

#### 📂 Included Task Files
update-upgrade-vms.yml: Handles package updates and cache cleanup.

install-nginx-all-vms.yml: Deploys Nginx and ensures service persistence.

install-nfs-with-shared-folder.yml: Configures NFS server/client roles and shared directories.

#### 📝 Contribution & Feedback
Contributions welcome! Open an Issue for bug reports or a Pull Request for improvements.

License: MIT
