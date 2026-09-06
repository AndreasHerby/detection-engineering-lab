# Lab setup

The purpose of this document is to explain how the detection engineering lab was created so it can be reproduced with consistent results. At a fundamental level, it is comprised of a two-VM lab on an isolated network on a single host machine.

## Lab architecture

![Overview diagram of lab architecture](images/LabSetupDiagram.png)   

### Windows endpoint
(the victim)
- Atomic Red team generates attack
- Sysmon records events into Windows Event log
- Wazuh agent ships logs

### Ubuntu SIEM
(Wazuh)
- Wazuh manager
- Wazuh indexer
- Wazuh dashboard

## Machines

### Ubuntu SIEM

I created a SIEM using Ubuntu 24.04 LTS Desktop (using a more minimal version would have been more resource efficient in retrospect). The most important piece of software is Wazuh which provides a log collection, detection and searching along side a user friendly GUI: Wazuh manager, indexer and dashboard.

This allows me to receive logs on the Ubuntu SIEM, evaluate that against a set of detection rules i create and then store those detections for easy access later.

### Windows 11 endpoint

This acts as the victim end point where atomic red team is used to generate simulated attacks on the endpoint. These are recorded and stored by Sysmon and then the Wazuh agent ships these directly to the Ubuntu SIEM. So, this is used to generate activity and ship the logs which can then be used to create tailored detections rules to automate the flagging process. 
