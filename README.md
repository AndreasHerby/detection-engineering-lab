# Detection Engineering Lab

I have created a home lab where real techniques used by attackers are simulated, detected through custom rules which are then fined tuned to raise less false positives. Each detection maps to a MITRE ATT&CK technique and is written using sigma - a vendor-neutral detection rule language. I then will create a writeup for each detection which will include the custom rules explained and any troubleshooting needed to fine tune the detection.

**Why did i choose this project?**

I am looking to break into blue-team/SOC placementss and internships, and detection engineering makes up a core piece of the work for those roles. I wanted to challenge myself to step outside of the usual offensive tooling projects and gain experience that mirrors the actual job. This gives me hands-on experience with SIEM, threat detection, MITRE ATT&CK framework and real troubleshooting experience along the way.

## Lab architecture overview

- **Endpoint (Windows 10/11 VM):** Sysmon + Wazuh agent + Atomic RedTeam
- **SIEM:** (Ubuntu 24.04 LTS - Desktop) running Wazuh
- **Attack generation:** [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team)

See [lab-setup](lab-setup.md) for how it's built and how to reproduce it.

## Detections

Every detection lives in [`detections/`](detections/) as a Sigma rule, with a matching writeup
in [`writeups/`](writeups/).

| Technique | Name | Tactic | Rule | Writeup |
|-----------|------|--------|------|---------|


## The workflow

Each detection follows the same loop:

1. **Pick** a technique from MITRE ATT&CK.
2. **Generate** the behavior safely with Atomic Red Team on the Windows endpoint.
3. **Write** a Sigma detection targeting the telemetry it produces.
4. **Tune** it against normal activity to cut false positives.
5. **Document** the technique, telemetry, logic, and tuning in a writeup.

## Repo structure

```
detection-engineering-lab/
├── README.md            <- you are here
├── lab-setup/           <- how the lab is built + reproducible notes
├── detections/          <- Sigma rules, one per technique
└── writeups/            <- a markdown writeup per detection
```

## About me

I am a Second-year cyber security student seeking placements and internships focusing on blue-team/SOC. This lab is actively in progress and providing me with hands-on experience - I am engineering detection rules to catch simulated attacker techniques on a victims system and writeups to explain the process of each one. 

