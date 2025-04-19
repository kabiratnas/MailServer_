# Mail-Server

# Mail Server Automation with Ansible

This project automates the deployment and configuration of a basic mail server using Ansible. It installs Postfix, configures it using a Jinja2 template, and manages user creation through dedicated playbooks.

## Project Files

- `install.yml` – Installs required packages like Postfix.
- `configure.yml` – Configures Postfix using a templated config file.
- `user.yml` – Creates local mail users.
- `inventory.ini` – Specifies the server(s) to target.
- `postfix_main.cf.j2` – Jinja2 template for Postfix main configuration.
- `README.md` – Project documentation and usage guide.

## Requirements

- Ansible installed (`pip install ansible`)
- SSH access to target servers
- Debian-based OS (Ubuntu, etc.)
- DNS records (MX, A, SPF) configured for your domain

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/mail-server-ansible.git
   cd mail-server-ansible
   ```

2. **Edit `inventory.ini`**
   Add your mail server's IP or domain:
   ```
   [mailservers]
   your.server.ip ansible_user=your_ssh_username
   ```

3. **Run installation playbook**
   ```bash
   ansible-playbook -i inventory.ini install.yml
   ```

4. **Run configuration playbook**
   ```bash
   ansible-playbook -i inventory.ini configure.yml
   ```

5. **Run user creation playbook**
   ```bash
   ansible-playbook -i inventory.ini user.yml
   ```

## What’s Automated

- Mail server package installation
- Templated Postfix configuration (`main.cf`)
- Mail user provisioning (local system users)

## Optional Next Steps

- Add SSL/TLS for secure email transmission
- Install and configure Dovecot for IMAP/POP3
- Integrate DKIM and DMARC (e.g., OpenDKIM)
- Add webmail (Roundcube, RainLoop, etc.)
