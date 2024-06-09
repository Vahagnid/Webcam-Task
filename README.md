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
   - Create or modify `ansible.cfg` with the appropriate configurations.
   - Update the `inventory` file with your server's details.

2. **Run Ansible Playbook:**
   - Execute the playbook using the following command:
     ```
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




