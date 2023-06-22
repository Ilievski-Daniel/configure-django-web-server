# Django Web Server Configuration

This Ansible playbook automates the setup and configuration of a Django web server. It installs the necessary packages, sets up a virtual environment, clones a Django project repository, configures Supervisor and Nginx, and performs other required tasks.

## Prerequisites
Before running this playbook, make sure you have:

1. Ansible installed on your local machine or control node.
2. SSH access to the target server(s) with sudo privileges.
3. The necessary server IP address or hostname.

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

## Playbook Tasks

The playbook performs the following tasks:

1. Updates the apt cache on the target server(s).

2. Installs the python3-venv package.

3. Creates a virtual environment for the Django application.

4. Activates the virtual environment.

5. Installs the python3-pip package.

6. Clones the Django application repository from the specified URL.

7. Installs the project dependencies from the requirements.txt file.

8. Installs Gunicorn as the application server.

9. Sets the server_public_ip variable.

10. Overwrites the settings.py file with the provided Jinja template.

11. Installs the Supervisor package.

12. Creates the gunicorn.conf file using the provided Jinja template.

13. Creates the /var/log/gunicorn directory.

14. Runs supervisorctl reread to update Supervisor configuration.

15. Runs supervisorctl update to apply the changes.

16. Restarts the Supervisor service.

17. Overwrites the default Nginx configuration using the provided Jinja template.

18. Reloads the Nginx service to apply the changes.

19. Runs the Django migration command.

20. Collects static files for the Django application.

21. Restarts the Nginx service.

## Contact
For any questions or inquiries, please contact: [Daniel Ilievski](https://www.linkedin.com/in/danielilievski/)