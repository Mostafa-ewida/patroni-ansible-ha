# Patroni Ansible HA

This repository provides Ansible playbooks and roles to automate the deployment of a highly available PostgreSQL cluster using Patroni, etcd, and HAProxy.

## Features

- Automated installation and configuration of PostgreSQL, Patroni, etcd, and HAProxy
- Cluster bootstrapping and password management
- Systemd service management for Patroni
- Health and status verification steps for all cluster components

## Structure

- `group_vars`: contain the nessecary variables to function
- `roles/etcd`: etcd installation and configuration
- `roles/postgres`: PostgreSQL and Patroni setup
- `roles/haproxy`: HAProxy setup for load balancing
- `playbook.yml`: Main playbook to orchestrate the cluster deployment

## Prerequisites
Before running the playbook, ensure you have the following:

1. Ubuntu servers (22.04 recommended) for all cluster nodes

2. Ansible (2.9+) installed on your control machine

3. Network connectivity between all nodes

4. SSH access configured from the Ansible control node to all target nodes with sudo privileges

5. Python 3 installed on all nodes

## Usage

1. **clone the reposatory on the ansible host**  
   ```sh
   git clone https://github.com/Mostafa-ewida/patroni-ansible-ha.git
   ```
   ```sh
    cd patroni-ansible-ha
   ```
2. **Prepare your inventory file**  
   Define your hosts under `[etcd]`, `[postgres]`, and `[haproxy]` groups.

3. **Customize variables**  
   Edit group_vars  as needed for your environment.

4. **Run the playbook**

   ```sh
   ansible-playbook -i inventory.ini playbook.yml
   ```
6. **Get Postgres Credentials**  
    The script randomly generates two passwords one for the super user and one for the replication user
    you can find the Credentials in a yaml file `/tmp/patroni-credentials.yml` on the  `ansible host`

## Verification

After deployment, just observe the playbook runs verification steps to check the health and status of etcd, Patroni, and HAProxy on all nodes, and make sure everything is running smoothly.

##
