Ansible Role
=========

Ansible role for [RabbitMQ consumer](https://github.com/abrararshad/rmq-consumer)
```
ansible-galaxy install abrararshad.rabbitmq_consumer
```

Role Variables
--------------

```
rmq_config_app_env: ''
rmq_config_app_run_command: ''
rmq_config_server: ''
rmq_config_user: ""
rmq_config_pass: ""
rmq_config_exchange_name: ''
rmq_config_queue: ''
```
Command to run which will receive rabbitmq queue
```
rmq_config_app_run_command: 'drush do-something'
```

All variables in [main.yml](defaults/main.yml)

Example
----------------

```
---
---
- name: 'RMQ Consumer Setup'
  hosts: "all"  
  roles:
    - name: rabbitmq_consumer
      vars:
        rmq_config_app_env: "dev"
        rmq_config_app_run_command: 'drush do-something'
        rmq_config_server: '{{ hostvars["rabbitmq"]["ansible_all_ipv4_addresses"] | first }}'
        rmq_config_user: "{{ app_rabbitmq_user_name }}"
        rmq_config_pass: "{{ app_rabbitmq_user_pass }}"
        rmq_config_port: 5672
        rmq_config_exchange_name: 'jobs'
        rmq_config_exchange_type: 'direct'
        rmq_config_queue: 'req'
        rmq_config_queue_auto_delete: False
        rmq_config_jobs_limit: 6
```

License
-------

BSD