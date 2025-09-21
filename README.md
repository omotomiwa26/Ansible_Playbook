# Ansible Playbook Collection for Web Infrastructure Automation

This repository contains a comprehensive collection of Ansible playbooks for automating the deployment and management of web servers and applications. The playbooks are designed to be idempotent, reusable, and adaptable for various Linux distributions and application stacks.

From basic server configuration to deploying multi-tier applications and managing dynamic content, these examples serve as a practical guide to real-world infrastructure automation with Ansible.

## Table of Contents

- [Prerequisites](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/README.md)

- [How to Use](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/README.md)

- Playbook Reference

- 01. [Create a Single Directory](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/01-create-directory.yml) 

- 02. [Create Multiple Directories](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/02-create-multiple-directories.yml)

- 03. [Configure an Apache Virtual Host](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/03-configure-httpd-vhost.yml)

- 04. [Deploy an E-commerce Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/04-deploy-ecommerce-app.yml)

- 05. [Deploy a Food Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/05-deploy-food-app.yml)

- 06. [Set a Maintenance Page](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/06-set-maintenance-page.yml)

- 07. [Perform General Ubuntu Server Configuration](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/07-configure-ubuntu-server.yml)

- 08. [Install Web Servers on Multiple OS](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/08-install-webservers-multi-os.yml)

- 09. [Deploy a Static HTML Website](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/09-deploy-static-website.yml)

- 10. [Deploy a Dynamic Website from a Template](https://github.com/omotomiwa26/Ansible_Playbook/blob/main          10-deploy-dynamic-website-from-template.yml)

- 11. [Demonstrate Ansible Variable Usage](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/11-demonstrate-variable-usage.yml)

- 12. [Deploy an HTML Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/12-deploy-html-app.yml)

- 13. [Deploy a PHP Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/13-deploy-php-app.yml)

- 14. [Deploy an Angular Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/14-deploy-angular-app.yml)

- 15. [Add a File to a Directory](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/add_file_to_dir.yaml)

- 16. [Ensure a Directory Exists](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/create_dir.yml)

## Prerequisites

Before running these playbooks, ensure you have the following set up:

1. Ansible Control Node: A machine with Ansible installed (preferably a Linux environment like WSL/Ubuntu).
    
2. Managed Nodes: One or more target servers accessible via SSH.

3. SSH Key Access: Your control node's SSH public key should be in the `authorized_keys` file on all managed nodes.

4. Inventory File: A configured `inventory.ini` file that lists your managed nodes, connection details, and any required variables.

## How to Use

To execute any playbook from this collection, run the `ansible-playbook` command from the root of this repository, specifying the playbook file and your inventory file.

```md
# Example of running a playbook
ansible-playbook 14-deploy-angular-app.yml -i inventory.ini
```

You may need to use the `--become` or `-b` flag if the playbook requires administrative (sudo) privileges.

## Playbook Reference

01. [Create a Single Directory](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/01-create-directory.yml)

- Purpose: A foundational playbook that ensures a single directory exists on the target server.
- Tasks: Uses the `ansible.builtin.file` module to create `/home/ec2-user/new_dir`. The `state: directory` parameter makes this operation idempotent.

02. [Create Multiple Directories](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/02-create-multiple-directories.yml)

- Purpose: Demonstrates targeting different hosts and groups within a single `ansible-playbook` run to create multiple directories.

- Tasks: Contains multiple plays that create a series of directories (`new_dir_1`, `new_dir_2`, etc.) on different nodes and groups defined in the inventory.

03. [Configure an Apache Virtual Host](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/03-configure-httpd-vhost.yml)

- Purpose: Sets up a basic Apache (httpd) virtual host configuration.

- Tasks: Typically involves copying a virtual host configuration file to `/etc/httpd/conf.d/` and restarting the `httpd` service to apply the changes.

04. [Deploy an E-commerce Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/04-deploy-ecommerce-app.yml)

- Purpose: Deploys the files for a sample e-commerce application.

- Tasks: Copies application files from a local source directory to the web server's document root on the target machine (e.g., `/var/www/html/ecomm`).

05. [Deploy a Food Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/05-deploy-food-app.yml)

- Purpose: Deploys the files for a sample "food" application.

- Tasks: Copies application files to the web server's document root on the target machine (e.g., `/var/www/html/food`).

06. [Set a Maintenance Page](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/06-set-maintenance-page.yml)

- Purpose: Puts a website into "maintenance mode" by replacing its `index.html` with a temporary maintenance page.

- Dependencies: Requires the `Maintenance-page.html` file in the repository.

- Tasks: Uses the `ansible.builtin.copy` module to overwrite the live `index.html` with the contents of `Maintenance-page.html`.

07. [Perform General Ubuntu Server Configuration](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/07-configure-ubuntu-server.yml)

- Purpose: Executes a series of common configuration tasks for a new Ubuntu server.

- Tasks: Can include creating users, updating packages (`apt upgrade`), installing common utilities, and setting security policies.

08. [Install Web Servers on Multiple OS](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/08-install-webservers-multi-os.yml)

- Purpose: A powerful example of cross-platform automation. This playbook installs and enables a web server on both Red Hat-based and Debian-based Linux distributions.

- Tasks:

    - Uses conditional logic (`when: ansible_os_family == 'RedHat'`) to install the `httpd` package using yum.

    - Uses conditional logic (`when: ansible_os_family == 'Debian'`) to install the `apache2` package using `apt`.

    - Ensures the appropriate service is started and enabled on boot.

09. [Deploy a Static HTML Website](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/09-deploy-static-website.yml)

- Purpose: Deploys a simple, static HTML website.

- Dependencies: Requires the `static-page.html` file.

- Tasks: Copies the `static-page.html` file to the web server's document root and names it index.html.

10. [Deploy a Dynamic Website from a Template](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/10-deploy-dynamic-website-from-template.yml)

- Purpose: Demonstrates the power of templating by creating a dynamic HTML file based on variables.

- Dependencies: Uses the `dynamic-template.j2` Jinja2 template file.

- Tasks: Processes the `dynamic-template.j2` template, injecting Ansible facts or variables (like the server's IP address or hostname) into it, and deploys the resulting file to the web root.

11. [Demonstrate Ansible Variable Usage](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/11-demonstrate-variable-usage.yml)

- Purpose: An educational playbook designed to show different ways to define and use variables in Ansible (e.g., from inventory, `vars` section, or facts).

- Tasks: Typically uses the `ansible.builtin.debug` module to print the values of various variables.

12. [Deploy an HTML Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/12-deploy-html-app.yml)

- Purpose: Deploys a multi-file HTML application.

- Dependencies: Uses files from the `html/` directory.

- Tasks: Copies the entire contents of the local `html/` directory to the web server's document root.

13. [Deploy a PHP Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/13-deploy-php-app.yml)

- Purpose: Deploys a PHP-based application.

- Dependencies: Uses files from the `php/` directory.

- Tasks: Copies the contents of the `php/` directory to the web root. May also include tasks to ensure PHP and required extensions are installed.

14. [Deploy an Angular Application](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/14-deploy-angular-app.yml)

- Purpose: Deploys a compiled Angular single-page application (SPA).

- Dependencies: Uses the built application files from the `angular/dist` directory (or similar).

- Tasks: Copies the static assets (HTML, JS, CSS) from the Angular project's build output directory to the web server's document root.

15. [Add a File to a Directory](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/add_file_to_dir.yaml)

- Purpose: A basic playbook to create a single file with specific content inside an existing directory.

- Tasks: Uses the `ansible.builtin.copy` module with the content parameter to create a file.

16. [Ensure a Directory Exists](https://github.com/omotomiwa26/Ansible_Playbook/blob/main/create_dir.yml)

- Purpose: A simplified version of `01-create-directory.yml`, focused purely on the existence of a directory.

- Tasks: Uses the `ansible.builtin.fil`e module with `state: directory`.
