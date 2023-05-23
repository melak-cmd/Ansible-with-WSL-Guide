# Ansible with Windows Subsystem for Linux (WSL)

Here's a step-by-step guide to get you started:

Step 1: Install Windows Subsystem for Linux (WSL)

- Open PowerShell as Administrator.
- Run the following command to enable the WSL feature: `wsl --install`.
- Follow the prompts and restart your computer if necessary.
- Once WSL is installed, open the Microsoft Store, search for a Linux distribution (e.g., Ubuntu), and install it.

Step 2: Set up and configure your Linux distribution

- Launch the installed Linux distribution from the Start menu.
- Follow the initial setup instructions, such as creating a user account and setting a password.

Step 3: Install Ansible in WSL

- Update the package manager: `sudo apt update`.
- Install Ansible: `sudo apt install ansible`.

Step 4: Configure your Ansible inventory

- Create an inventory file to define your target hosts: `nano inventory.ini`.
- Add the IP addresses or hostnames of the machines you want to manage with Ansible. For example:
  
  ```
  [servers]
  server1 ansible_host=192.168.0.10
  server2 ansible_host=192.168.0.11
  ```
- Save and close the file (`Ctrl+X`, `Y`, `Enter` in nano).

Step 5: Write your Ansible playbook

- Create a playbook file to define your desired configuration: `nano playbook.yml`.
- Write your playbook using YAML syntax. Here's a simple example that installs the Apache web server:
  
  ```yaml
  ---
  - hosts: servers
    tasks:
      - name: Install Apache
        become: yes
        apt:
          name: apache2
          state: present
  ```
- Save and close the file.

Step 6: Run your Ansible playbook

- Execute your playbook with the `ansible-playbook` command: `ansible-playbook -i inventory.ini playbook.yml`.
- Ansible will connect to the target hosts specified in the inventory and execute the tasks defined in the playbook.

That's it! You now have Ansible set up in WSL and can use it to manage your target machines. 

Remember to adjust the playbook according to your specific requirements.

**Note:** If you want to manage Windows hosts using Ansible in WSL, you'll need to configure the hosts for WinRM and use the appropriate Ansible modules.
