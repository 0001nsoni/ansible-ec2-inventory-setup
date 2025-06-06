# Ansible EC2 Inventory Setup

This repository contains an Ansible inventory configuration for managing AWS EC2 instances, primarily focused on development (`devserver`) and production (`prodserver`) environments.

## 📁 File Structure:
ansible-ec2-inventory-setup/
│
├── hosts.ini # Ansible inventory file
├── keys/
│ └── neerajj.pem # SSH private key for EC2 access (not committed)

## 📋 Example Inventory: `hosts.ini`

```ini
[devserver]
server_1 ansible_host=13.203.228.246

[prodserver]

[devserver:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ec2-user
ansible_ssh_private_key_file=/home/ec2-user/keys/neerajj.pem
```
🚀 Usage
1. Clone the Repository
git clone https://github.com/your-username/ansible-ec2-inventory-setup.git
cd ansible-ec2-inventory-setup
2. Copy the .pem Key to Your Remote Server
Use the scp command to securely copy your SSH private key to the EC2 instance:
scp -i /path/to/neerajj.pem /path/to/neerajj.pem ec2-user@13.203.228.246:/home/ec2-user/keys/neerajj.pem
🔒 Ensure the permissions on the server for the key are restricted:
chmod 400 /home/ec2-user/keys/neerajj.pem
3. Test the Connection
ansible -i hosts.ini devserver -m ping
4. Run a Playbook
ansible-playbook -i hosts.ini your-playbook.yml
🔐 Security Notice
Do NOT commit your private key (.pem) to the repository.

Add keys/ or the .pem file to .gitignore:
echo "keys/" >> .gitignore
📌 Notes
Make sure your EC2 instance allows SSH from your IP.

Update the ansible_host with your EC2 instance’s public IP or DNS.

Make sure Python 3 is installed on the remote EC2 instance.

🛠 Managed with ❤️ using Ansible.

---

Let me know if you'd like this turned into a template repo or zipped structure!







