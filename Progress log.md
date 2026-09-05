# Progress log

This document will be used to keep record of how the project is progressing and what I will work on next.

## Complete

- Configured a two-VM lab using VirutalBox on an isolated NAT network
- Built an Ubuntu SIEM running Wazuh. I chose this for the easy setup and it includes a manager, indexer and dashboard.
- Built the second VM running windows 11. This will be the endpoint and i enroled it as a Wazuh agent then verified it was active.
- Verified events flowing into the SIEM
- Installed Sysmon onto Windows endpoint with SwiftOnSecurity config for more relevant logs
- Installed Aomtic Red Team on Windows endpoint to simulate attack processes
- Generated the first attack technique using Atomic Red team. Powershell download cradle - to finish

## In progress

- Sysmon event forwarding to SIEM needs troubleshooting because the events are not being shown on the Wazuh dashboard even after the Red Team Attack has been generated. I will see manually if Sysmon is storing the events or not and if they are why are they not being shipped when the wazuh agent is active?
- Goal: Powershell download-cradle events to appear in Wazuh dashboard

## Next

1. Validate Sysmon events are shipped and appear in the SIEM correctly and make sure to take screenshots for the repo
2. Create the first Sigma detection for the powershell download-cradle)
3. Confirm if the sigma detection is firing once the Red Team Attack is generated
