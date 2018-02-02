# Ansible Kafka

[![Build Status](https://travis-ci.org/jaytaylor/ansible-kafka.svg?branch=master)](https://travis-ci.org/jaytaylor/ansible-kafka)
[![Galaxy](https://img.shields.io/badge/galaxy-jaytaylor.kafka-blue.svg)](https://galaxy.ansible.com/list#/roles/4083)

An ansible role to install and configure [kafka](https://kafka.apache.org/) distributed pub/sub messaging queue clusters.


## How to get it

Add to your playbooks requirements.yml:

    - src: https://github.com/jaytaylor/ansible-kafka

and then run:

    ansible-galaxy install -r requirements.yml --ignore-errors

Or if you just want to grab this role and start using it:

    cd my-playbook-folder/roles
    git clone https://github.com/jaytaylor/ansible-kafka.git
    cd -

## How to use it

Once the role is installed, configure it from your playbook file (e.g. playbook.yml).

Example:

```yml
    ---
    - hosts: [all]
      roles:
        - {
          role: "ansible-kafka",
          kafka_hosts: "{{ groups.kafka | list }}",
          kafka_zookeeper_hosts: "{{ zookeeper_hosts | list }}"
          kafka_version: 0.11.0.2,     # Kafka version override.
          kafka_scala_serverion: 2.10 # Scala version override.
        }
```

Where `kafka_hosts` and `zookeeper_hosts` are both defined variables
(e.g. in group_vars/all), and contain the list of hosts to use.

## Important Note

If you are using this role from the ansible-galaxy website, make sure you use "jaytaylor.kafka" for the role name (rather than "ansible-kafka").

## Role variables

- `kafka_hosts` - list of hosts in the cluster.
- `kafka_zookeeper_hosts` - list of zookeeper hosts for the cluster.
- `kafka_broker_id` - Integer uniquely identifying the broker, by default one will be generated for you either by this role or by kafka itself for versions >= 0.9.
- `kafka_generate_broker_id` - Flag controlling whether to generate a broker id, defaults to `yes`.

## License

BSD

## Author

Jay Taylor

[@jtaylor](https://twitter.com/jtaylor) - [jaytaylor.com](http://jaytaylor.com) - [github](https://github.com/jaytaylor)
