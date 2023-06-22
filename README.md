# Django Web Server Configuration

This Ansible playbook automates the setup and configuration of a Django web server. It installs the necessary packages, sets up a virtual environment, clones a Django project repository, configures Supervisor and Nginx, and performs other required tasks.

## Prerequisites
Before running this playbook, make sure you have:

1. Ansible installed on your local machine or control node.
2. SSH access to the target server(s) with sudo privileges.
3. The necessary server IP address or hostname.

## Playbook

The playbook is written in YAML and is used by Ansible to define a set of tasks to be executed on the target hosts. In this case, the playbook is named "Configure Django Web Server" and has the following structure:

The playbook targets all hosts (hosts: all) and requires elevated privileges (become: true).

The playbook consists of multiple tasks that perform various configuration steps for setting up a Django web server.

Each task is defined with a name and utilizes different Ansible modules to carry out specific actions. Some of the tasks include updating the apt cache, installing packages, creating a virtual environment, cloning a Git repository, installing Python dependencies, configuring Supervisor and Nginx, and running Django management commands.

## Usage
1. Clone this repository to your local machine:
    
    ```sh
    git clone https://github.com/Ilievski-Daniel/configure-django-web-server
    ```

2. Enter the django-web-server directory:

    ```sh
    cd django-web-server
    ```

3. Update the inventory file ```inventory.ini``` with your server details. 

    Modify the IP addresses/hostnames of your targer servers & also the ```server_public_ip``` variable.

4. Update the Ansible configuration file ```ansible.cfg```.

    Modify the ```private_key_file``` && ```inventory``` variables, the ```private_key_file``` should be path to the Private SSH Key that is used to connect to the server/s, and the ```inventory``` variable should point to your ```inventory.ini``` file that contains the servers.

5. Run the playbook using the following command:

    ```sh
    ansible-playbook configure_django_web_server.yml
    ```

6. Once the playbook execution is complete, you can access your Django application by navigating to ```http://<server_public_ip>``` in your web browser.

    You should be able to see the Django administration page, that is the configuration that I have put so that nginx redirects users from ```/``` to ```/admin```.

## GitHub Actions Workflow

- The provided GitHub Actions workflow is used to automate the process of checking the formatting of the Ansible playbook using Ansible Lint. The workflow is triggered on push and pull request events for all branches.
<br>

-   Here's an overview of the workflow:
    - The workflow runs on an Ubuntu environment (runs-on: ubuntu-latest).
    - It includes several steps:
    - Checking out the repository using the actions/checkout action.
    - Setting up Python version 3.x using the actions/setup-python action.
    - Installing Ansible Lint by running the pip install ansible-lint command.
    - Running Ansible Lint to check the formatting of the configure_django_web_server.yml playbook.

<br>

-   By including this workflow in your repository, it ensures that any changes made to the playbook are automatically validated for proper formatting.

## Contact
For any questions or inquiries, please contact: [Daniel Ilievski](https://www.linkedin.com/in/danielilievski/)