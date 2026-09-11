# Progress log

This document will be used to keep record of how the project is progressing and what I will work on next.

## Complete

- Configured a two-VM lab using VirtualBox on an isolated NAT network
- Built an Ubuntu SIEM running Wazuh. I chose this for the easy setup and it includes a manager, indexer and dashboard.
- Built the second VM running windows 11. This will be the endpoint and i enrolled it as a Wazuh agent then verified it was active.
- Verified events flowing into the SIEM
- Installed Sysmon onto Windows endpoint with SwiftOnSecurity config for more relevant logs
- Installed Atomic Red Team on Windows endpoint to simulate attack processes
- Generated the first attack technique using Atomic Red team. Powershell download cradle - generated and confirmed.
- Sysmon event forwarding to the SIEM is working - this was fixed by configuring the Wazuh agent to forward the correct channel (Microsoft-Windows-Sysmon/Operational) and by fixing the Wazuh manager failure so the agent connections are not refused. **See full screenshots and explanation in trouble shooting log**
- Pipeline tested and verified end to end - the powershell download-cradle command correctly captured by Sysmon, forwarded by the Wazuh agent and properly received by the manager so the threats/events were visible on the dashboard (Wazuh already has a built-in detection rules so it was flagged under MITRE Ingress Tool Transfer)

![Download cradle command](images/test-command.png)

![Download cradle log in Wazuh](images/download-cradle-log.png)


## In progress

- Writing the first Sigma detection rule - refer to Next

## Next

1. Create first Sigma detection - this will be for the download cradle and will target the data.win.eventdata.commandline field and search for matches to Net.WebClient/DownloadString
2. Configure the sigma detection in Wazuh as a custom rule and validate the rule firing
3. Investigate false positives against regular Powershell usage
4. Complete full detection write up along with troubleshooting logs along the way
