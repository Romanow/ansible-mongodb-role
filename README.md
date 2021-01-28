# Ansible MongoDB role

This role installs MongoDB database and configure security and Replica Set.
Role installs MongoDB using apt-get 

### Requirements
* Ubuntu 20.04
* Ansible 2.10
* Python 3
* Ansible Collection `community.mongodb`

### Variables
```yaml
mongodb_version: 4.4
 
mongodb_port: 27017
# MongoDB user and group to configure ownership of config files
mongodb_user: mongodb
mongodb_group: mongodb

mongodb_replica_set_enabled: no # enabled replication
mongodb_replica_set_name: rs0 # replica set name
# replica set members: all hosts in group 'mongodb' except current host
# mongodb_replica_set_members: "{{ groups.mongodb | map('extract', hostvars, 'ansible_host') | product(['27017']) | map('join', ':') }}"
mongodb_replica_set_members: []

mongodb_key_file: /etc/mongodb.key
mongodb_data_path: /var/lib/mongodb/
mongodb_log_path: /var/log/mongodb/
mongodb_home_dir: /home/ansible

admin:
  name: superuser
  password: root
  roles:
    - root

users: []
```