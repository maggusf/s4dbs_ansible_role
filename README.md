# Ansible Role: Speedgain for Databases via Podman

## Overview

This Ansible role installs Speedgain, a performance observability tool for databases, using Podman containers. It is designed to be run on a local machine, leveraging Podman for containerization and Ansible for orchestration.

## Requirements

- **Ansible**
- **Podman**
- **Python**
- **Podman Python Library**

## Role Variables

This role supports the following variables (vars/main.yml), which you can override in your playbook or inventory files:

- **`s4dbs_base_dir`**: Base directory for SpeedGain installation. Default is `/opt/s4dbs`.
- **`postgres_volume_path`**: Path for PostgreSQL data volume. Default is `{{ s4dbs_base_dir }}/postgres`.
- **`s4dbs_secret_password`**: Secret password for SpeedGain. Default is `MySuperSecretPassword`.
- **`timescaledb_image_tag`**: Tag for the TimescaleDB image. Default is `2.11.2-pg13`.
- **`s4dbs_collector_image_tag`**: Tag for the SpeedGain Collector image. Default is `1.7.0`.
- **`s4dbs_service_image_tag`**: Tag for the SpeedGain Service image. Default is `1.7.0`.
- **`s4dbs_grafana_image_tag`**: Tag for the SpeedGain Grafana image. Default is `1.7.0`.
- **`s4dbs_frontend_image_tag`**: Tag for the SpeedGain Frontend image. Default is `1.7.0`.
- **`nginx_image_tag`**: Tag for the NGINX image. Default is `1.27`.
- **`pdb_user`**: PostgreSQL user. Default is `postgres`.
- **`pdb_host`**: Hostname for the PostgreSQL service. Default is `s4dbs_postgres`.
- **`pdb_port`**: Port for the PostgreSQL service. Default is `5432`.
- **`pdb_db_name`**: Name of the PostgreSQL database. Default is `speedgain`.
- **`collector_loglevel`**: Log level for the SpeedGain Collector. Default is `DEBUG`.
- **`service_loglevel`**: Log level for the SpeedGain Service. Default is `INFO`.

### CPU and Memory Limits per Container

- **`s4dbs_postgres_cpus`**: CPU allocation for PostgreSQL container. Default is `4`.
- **`s4dbs_postgres_memory`**: Memory allocation for PostgreSQL container. Default is `16G`.
- **`s4dbs_collector_cpus`**: CPU allocation for SpeedGain Collector container. Default is `4`.
- **`s4dbs_collector_memory`**: Memory allocation for SpeedGain Collector container. Default is `0G`.
- **`s4dbs_service_cpus`**: CPU allocation for SpeedGain Service container. Default is `1`.
- **`s4dbs_service_memory`**: Memory allocation for SpeedGain Service container. Default is `0G`.
- **`s4dbs_grafana_cpus`**: CPU allocation for SpeedGain Grafana container. Default is `2`.
- **`s4dbs_grafana_memory`**: Memory allocation for SpeedGain Grafana container. Default is `4G`.
- **`s4dbs_frontend_cpus`**: CPU allocation for SpeedGain Frontend container. Default is `1`.
- **`s4dbs_frontend_memory`**: Memory allocation for SpeedGain Frontend container. Default is `1G`.
- **`s4dbs_reverse_cpus`**: CPU allocation for SpeedGain Reverse Proxy container. Default is `1`.
- **`s4dbs_reverse_memory`**: Memory allocation for SpeedGain Reverse Proxy container. Default is `1G`.

## Dependencies

This role does not have any additional role dependencies.

## Example Playbook

Here’s a basic example of how to use this role in an Ansible playbook:

```yaml
---
- name: Manage s4dbs containers
  hosts: localhost
  become: yes
  roles:
    - s4dbs
```

## Usage

To run the playbook using this role, use the following command:

```bash
ansible-playbook -i localhost, -c local play_role_s4dbs.yaml
```

## License

This role is licensed under the MIT License.

## Author Information

This role was created in 2024 by [Markus Fraune]. 
