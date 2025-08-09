# LAMP Stack Deployment using Ansible Role

This project automates the installation and configuration of **LAMP Stack** (Linux, Apache, MySQL/MariaDB, PHP) on a target server using Ansible Roles.

## Prerequisites
- Linux/Mac/WSL environment  
- Python 3 installed  
- Ansible installed → `sudo apt update && sudo apt install -y ansible`  
- SSH access to target server  
- Private key file (`.pem` or `.key`) for login  
- Internet access on target server  

## Steps to Deploy
1. **Clone the Repository**  
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
## Edit Inventory File (inventory.ini) with your server details:

[webserver]
<SERVER_IP> ansible_user=<USERNAME> ansible_ssh_private_key_file=<PATH_TO_KEY>

## Example:

[webserver]
54.210.12.34 ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/my-key.pem

## Optional Edits

Change PHP, Apache, MySQL versions in lamp_role/defaults/main.yml
Customize default PHP page in lamp_role/templates/index.php.j2

## Run the Playbook

ansible-playbook -i inventory.ini site.yml

## Verify
Open browser → http://<SERVER_IP>
You should see the PHP info page or your custom page.

## Project Structure

lamp_role/
├── defaults/main.yml     # Default variables
├── vars/main.yml         # Role-specific variables
├── tasks/main.yml        # Install LAMP tasks
├── handlers/main.yml     # Restart services
├── templates/            # Jinja2 templates
├── files/                # Static files
├── meta/main.yml         # Metadata
inventory.ini              # Inventory file
site.yml                   # Main playbook
