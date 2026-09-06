# Lab setup

The purpose of this document is to explain how the detection engineering lab was created so it can be reproduced with consistent results. At a fundamental level, it is comprised of a two-VM lab on an isolated network on a single host machine.

## Lab architecture

![Overview diagram of lab architecture](images/LabSetupDiagram.png)   

| Host | OS | Role | Key software |
|------|----|------|--------------|
| SIEM | Ubuntu 24.04 LTS (Desktop) | Log collection, detection, search | Wazuh (manager, indexer, dashboard) |
| endpoint | Windows 11 Enterprise Evaluation | Victim endpoint + attack generation | Sysmon, Wazuh agent, Atomic Red Team |

## Networking

A regular NAT network provided internet access to both virtual machines but isolates them from one another. This NAT network puts them on the same shared private network so they can communicate to each other. This allows for the windows agent to ship its logs across to the SIEM on the ubuntu machine. This was verified initially by pinging the SIEM on the windows endpoint.


