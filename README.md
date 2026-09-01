OT/ICS Monitoring Lab with ELK and Ansible

An educational OT/ICS laboratory that automates the deployment of a monitoring environment using Ansible, Docker, ELK, Zeek, Filebeat and OpenPLC.

The project collects network information from simulated Modbus/TCP communication and forwards it to Elasticsearch for analysis in Kibana.

Architecture

OpenPLC / Modbus TCP -> Zeek
Zeek -> JSON network logs
JSON network logs -> Filebeat
Filebeat -> Logstash
Logstash -> Elasticsearch
Elasticsearch -> Kibana

Components

Ansible – automated installation and configuration
OpenPLC – simulated industrial controller
Zeek – monitoring of Modbus/TCP network traffic
Filebeat – collection and forwarding of logs
Logstash – log processing
Elasticsearch – data storage and indexing
Kibana – data exploration and visualisation
Docker Compose – deployment of the ELK stack

Requirements

Ansible control machine
Linux host for the ELK stack
Linux OT endpoint accessible through SSH
Docker and Docker Compose
Ansible collections community.docker and ansible.posix

Configuration

Set the ELK server and OT endpoint addresses in inventory.
Set the monitored network interface and network range in group_vars/all.yml.
Verify that filebeat_logstash_host points to the Logstash instance reachable from the OT endpoint.

Deployment

ansible-galaxy collection install community.docker ansible.posix

ansible-playbook -i inventory playbook.yml --ask-become-pass

Security notice

This repository represents an isolated educational laboratory. Authentication and production security controls are intentionally simplified and the configuration should not be exposed directly to the Internet.
