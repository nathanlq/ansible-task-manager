# Ansible Task Manager for SpaceSheep HomeLab

## Overview

This repository contains Ansible playbooks and roles for managing the infrastructure and services of the SpaceSheep HomeLab. Each service is modularized into roles for ease of deployment, maintenance, and testing.

## Repository Structure

### **Key Directories and Files**

- `ansible.cfg`: Configuration file for Ansible, specifying inventory and roles paths.
- `inventories/hosts.ini`: Inventory file listing the groups and hosts in the infrastructure.
- `playbooks/`: Contains playbooks to deploy and test specific services.
  - `docker_install.yml`: Installs Docker on target hosts.
  - `glance_setup.yml`: Deploys and configures Glance.
  - `mlflow_setup.yml`: Deploys MLflow.
  - `monitoring_setup.yml`: Deploys Prometheus and Grafana.
  - `portainer_setup.yml`: Sets up Portainer and its agents.
  - `router_setup.yml`: Configures the Nginx Proxy Manager on the router.
  - `storage_setup.yml`: Deploys storage-related services like PostgreSQL, pgAdmin, Gitea, and Redis.
- `roles/`: Contains roles for each service. Each role includes:
  - `defaults/`: Default variables.
  - `tasks/`: Tasks for deployment and testing.
  - `files/`: Static files, such as configuration files.
  - `handlers/`: Handlers for restarting services.
- `vars/`: Centralized variables for the infrastructure (`storage.yml`).

## Inventory Structure

The `inventories/hosts.ini` file organizes the infrastructure into groups:
- `network_group`: Router and network-related hosts.
- `containers_group`: Hosts running containerized services.
- `storage_group`: Hosts managing storage-related services like PostgreSQL.
- `monitoring_group`: Hosts running monitoring tools (e.g., Prometheus, Grafana).
- `gpu_group`: Hosts with GPU capabilities for ML workloads.

## Roles

### **Available Roles**
- `docker`: Installs Docker on target hosts.
- `gitea`: Deploys and configures the Gitea service.
- `glance`: Deploys and configures Glance.
- `mlflow`: Sets up the MLflow tracking server.
- `node_exporter`: Deploys Node Exporter for Prometheus monitoring.
- `pgadmin`: Deploys pgAdmin for managing PostgreSQL.
- `portainer`: Deploys Portainer and its agents for container management.
- `postgres`: Sets up PostgreSQL databases.
- `prometheus_grafana`: Configures Prometheus and Grafana for monitoring.
- `redis`: Deploys the Redis stack, including RedisInsight.
- `router`: Configures the Nginx Proxy Manager on the network router.

## Usage

```bash
ansible-playbook -i inventories/hosts.ini playbooks/<playbook_name>.yml
```
