# Ansible Docker FFmpeg NGINX Project

This project automates the setup of Docker containers for FFmpeg and NGINX using Ansible. FFmpeg extracts frames from an HTTP stream, and NGINX displays the latest frame on the homepage.

## Project Structure

| File/Folder         | Description                                      |
|---------------------|--------------------------------------------------|
| `ansible.cfg`       | Ansible configuration file                       |
| `playbook.yml`      | Ansible playbook defining tasks and roles        |
| `roles/`            | Directory containing Ansible roles               |
| `roles/webserver/`  | Role for managing Docker containers and configs |
| `roles/webserver/tasks/` | Tasks directory within the webserver role   |
| `roles/webserver/templates/` | Templates directory within the webserver role |
| `roles/webserver/tasks/main.yml` | Main tasks file for the webserver role  |
| `roles/webserver/templates/nginx.conf.j2` | NGINX configuration template     |
| `roles/webserver/templates/update_frame.sh.j2` | Frame update script template |
| `inventory`         | Ansible inventory file defining target hosts    |


## Setup Instructions

Follow these steps to set up the project:

1. **Configure Ansible:**
   - Create or modify `ansible.cfg` with the appropriate configurations. Here is an example configuration:
     ```ini
     [defaults]
     inventory = INVENTORY_PATH
     remote_user = USER_NAME
     private_key_file = PRIVATE_KEY_PATH
     host_key_checking = no
     ask_pass = false
     ```

   - Update the `inventory` file with your server's details. Here is an example inventory:
     ```ini
     [webservers]
     web1 ansible_host=HOST_NAME_OR_IP ansible_user=USER_NAME ansible_ssh_pass=PASSWORD
     web2 ansible_host=HOST_NAME_OR_IP
     ```

2. **Run Ansible Playbook:**
   - Execute the playbook using the following command:
     ```sh
     ansible-playbook playbook.yml
     ```

3. **Wait for the Setup:**
   - Once the playbook execution is complete, Docker containers for FFmpeg and NGINX will be running on your server.

## Usage

After the setup, FFmpeg will continuously extract frames from the provided HTTP stream, and NGINX will display the latest frame on the homepage.

## Notes

- The project utilizes the `jrottenberg/ffmpeg` Docker image for frame extraction.
- NGINX uses the standard `nginx` Docker image for serving content.
- The `update_frame.sh` script updates frames every second.

## Parameter Configuration

Ensure that the following parameters in `ansible.cfg` and `inventory` are correctly configured:

- **`INVENTORY_PATH`**: Path to your inventory file.
- **`USER_NAME`**: The remote user name used to log into the servers.
- **`PRIVATE_KEY_PATH`**: Path to your SSH private key file (if using key-based authentication).
- **`HOST_NAME_OR_IP`**: The hostname or IP address of your servers.
- **`PASSWORD`**: Password for the remote user (if using password-based authentication).

You may need to configure either `ansible_ssh_pass` for password-based authentication or `private_key_file` for SSH key-based authentication in the `ansible.cfg` and `inventory` files respectively.

**PS**: If you only need to connect with SSH or password authentication, you should close some lines accordingly.