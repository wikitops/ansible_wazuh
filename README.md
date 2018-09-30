# Ansible : Playbook Wazuh

The aim of this project is to deploy the Wazuh Server and agent on a Vagrant instance based on Linux.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

*   [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
*   Update the Vagrant file based on your computer (CPU, memory), if needed
*   You must have download the ubuntu Xenial64 vagrant box :

```bash
$ vagrant box add https://app.vagrantup.com/ubuntu/boxes/xenial64
```
*   The Elasticsearch database needed by the Wazuh Server is not provisioned by this playbook, it has to be done before running it
*   The Kibana web console needed by the Wazuh Server is not provisioned by this playbook, it has to be done before running it
*   In distrbuted mode, all the remote servers have to be up and running and the Ansible host file updated

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Build Environment

Vagrant needs to init the project to run and build it :

```bash
$ vagrant up
```

After build, you can check which virtual machine Vagrant has created :

```bash
$ vagrant status
```

If all run like it is expected, you should see something like this :

```bash
$ vagrant status

Current machine states:

wazuh-server01                   running (virtualbox)
wazuh-agent01                    running (virtualbox)
```

#### Deployment

This playbook has some dependencies to other roles that must be downloaded before executing the playbook :

```bash
$ ansible-galaxy install -r requirements.yml
```

This command should download the Java, NodeJS roles from Wikitops Github account to the local role path.

To deploy Solr on Vagrant, you just have to run the Ansible playbook wazuh.yml with this command :

```bash
$ ansible-playbook wazuh.yml
```

If eveything run as expected, you should have Wazuh installed and running on your Vagrant instances.
The Elastic stack should be configured. In Kibana, a new section named Wazuh should appear.

#### Destroy

To destroy on what Vagrant has created, just run this command :

```bash
$ vagrant destroy
```

## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the Apache License, Version 2.0. For the full text of the license, see the LICENSE file.
