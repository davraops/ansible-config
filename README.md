# Ansible Configuration Management

This repository contains Ansible playbooks, roles, and inventories for setting up a web server, database server, and load balancer.

## Usage

### Prerequisites

- Install Ansible: Follow the [Ansible installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) to install Ansible on your local machine.

### Running the Playbooks

1. **Clone the repository:**

    ```sh
    git clone https://github.com/davraops/ansible-config.git
    cd ansible-config
    ```

2. **Run the Web Server Playbook:**

    ```sh
    ansible-playbook -i inventories/production/hosts playbooks/webserver.yml
    ```

3. **Run the Database Server Playbook:**

    ```sh
    ansible-playbook -i inventories/production/hosts playbooks/dbserver.yml
    ```

4. **Run the Load Balancer Playbook:**

    ```sh
    ansible-playbook -i inventories/production/hosts playbooks/loadbalancer.yml
    ```

### Customizing for Your Environment

- **Inventories:** Edit the `inventories/production/hosts` or `inventories/staging/hosts` files to match the actual hostnames or IP addresses of your servers.
- **Templates:** Modify the templates in the `roles/webserver/templates` and `roles/loadbalancer/templates` directories if you need to customize the configurations for Nginx and HAProxy.

## License

This project is licensed under the MIT License.
