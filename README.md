# Detection Engineering Lab

A home lab where I simulate real attacker techniques and write, tune, and document the
detections that catch them. Each detection maps to a specific [MITRE ATT&CK](https://attack.mitre.org/)
technique, is written in vendor-neutral [Sigma](https://github.com/SigmaHQ/sigma) format, and
comes with a writeup explaining the telemetry it relies on and the false positives I tuned out.

> **Why this project?** Detection engineering is the day-to-day work of blue teams and SOCs —
> take a known attacker behavior, figure out what telemetry it generates, write logic to catch
> it, then reduce false positives. This repo is my attempt to do that work end to end.

<!-- TODO: add a screenshot or diagram of your lab here. A picture of the SIEM catching an
attack is the single most compelling thing a visitor can see. Put the image in an /images
folder and reference it like: ![Lab overview](images/lab-overview.png) -->

## Lab architecture

<!-- TODO: fill in your real setup. Example below. -->

- **Endpoint (Windows 10/11 VM):** Sysmon + Windows Event Logs, forwarded to the SIEM
- **Endpoint (Linux VM):** auditd / journald, forwarded to the SIEM
- **SIEM:** Wazuh (single-node) for log collection, search, and alerting
- **Attack generation:** [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team)

See [`lab-setup/`](lab-setup/) for how it's built and how to reproduce it.

## Detections

Every detection lives in [`detections/`](detections/) as a Sigma rule, with a matching writeup
in [`writeups/`](writeups/).

| Technique | Name | Tactic | Rule | Writeup |
|-----------|------|--------|------|---------|
| T1059.001 | PowerShell download cradle | Execution | [rule](detections/T1059.001-powershell-download-cradle.yml) | [writeup](writeups/T1059.001-powershell-download-cradle.md) |
<!-- Add a row per detection as you go. Aim for 8-12 well-documented ones. -->

## The workflow

Each detection follows the same loop:

1. **Pick** a technique from MITRE ATT&CK.
2. **Generate** the behavior safely with Atomic Red Team.
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

<!-- TODO: one or two lines. Who you are, what you're studying, what you're looking for.
e.g. "Second-year Computer Science student focused on blue-team security. Open to
security internships for summer 2027." Link your LinkedIn if you have one. -->
