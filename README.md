# Ansible Kafka

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
          kafka_hosts: "{{ groups.kafka | join(':9092,') }}:9092",
          zookeeper_hosts: "{{ zookeeper_hosts }}"
          kafka_version: 0.8.2.1,     # Kafka version override.
          kafka_scala_serverion: 2.10 # Scala version override.
        }
```

Where `kafka_hosts` and `zookeeper_hosts` are both defined variables
(e.g. in group_vars/all), and contain comma-delimited lists of host:port pairs.

Example host:port pair format:

    host1:port,host2:port,...,hostN:port

## Important Note

If you are using this role from the ansible-galaxy website, make sure you use "jaytaylor.kafka" for the role name (rather than "ansible-kafka").

## Role variables

- kafka_hosts - Comma separated list of host:port pairs in the cluster, defaults to 'ansible_fqdn:9092' for a single node.
- zookeeper_hosts - Comma separated list of host:port pairs.

## License

BSD

## Author

Jay Taylor

[@jtaylor](https://twitter.com/jtaylor) - [jaytaylor.com](http://jaytaylor.com) - [github](https://github.com/jaytaylor)

