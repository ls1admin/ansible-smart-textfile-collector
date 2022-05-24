# Ansible Role: ansible-smart-textfile-collector

Installs prometheus smartmon.sh script and sets up cron job for scheduling.

## Requirements
Node exporter needs to be already installed with the textfile collector enabled.
```yaml
- hosts: group
  roles:
    - role: ls1admin.ansible-smart-textfile-collector
```

## Role Variables
```yaml
script_dir: /opt/node-exporter-textfile-collector-scripts
textfile_dir: /var/lib/node_exporter
commit_hash: 4bb930b565879696245f006e737b9e1ce6b3bd6d

# interval
cron_minutes: "0"
cron_hours: "*/6"
```
* `script_dir` directory to download scripts into
* `textfile_dir` directory for the textfile scripts (configured in Node Exporter)
* `commit_hash` commit hash of node-exporter-textfile-collector-scripts repo (https://github.com/prometheus-community/node-exporter-textfile-collector-scripts)
* `cron_minutes`, `cron_hours` execution frequency

# Example Playbook
```yaml
- hosts: group
  roles:
    - role: cloudalchemy.prometheus.node-exporter
    - role: ls1admin.ansible-smart-textfile-collector
      vars:
        cron_minutes: "*"
        cron_hours: "*"
```
