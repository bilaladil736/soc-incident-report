# Wazuh SOC Lab — Incident Investigation Report

A hands-on SOC analyst project: building a Wazuh SIEM lab, simulating an attack, investigating the alerts, and producing a professional incident report.

## Project Summary

I built a complete Wazuh SIEM environment from scratch and conducted a real investigation of a simulated privilege escalation attempt against a monitored Linux endpoint.

The deliverable is the incident report, not the tool.

## Environment

Component | Role
---|---
Wazuh 4.14.7 (OVA) | Manager, Indexer, Dashboard
Kali Linux | Monitored endpoint (Wazuh Agent)
VMware Workstation | Virtualization platform

Both VMs run on a NAT network for agent-to-manager communication.

## Attack Scenario

Simulated a local privilege escalation attempt by running repeated su - root commands with incorrect passwords on the Kali endpoint. This is consistent with MITRE ATT&CK technique T1110.001 (Brute Force: Password Guessing).

## Investigation Outcome

- 30 authentication failure alerts detected within 24 hours
- 3 correlated rules fired per attempt: 5301, 5503, 5557
- Full forensic detail captured: raw log line, agent ID, decoder chain, timestamps
- MITRE ATT&CK mapping confirmed: Password Guessing (T1110.001)

## Repository Contents

README.md — This file
report/incident-report.md — Full incident report
setup/lab-setup.md — How the lab was built
screenshots/ — Evidence captured during the investigation

## Key Findings

Classification: True Positive — Local Privilege Escalation Attempt
Severity: Low (no successful authentication observed)
Source: Local tty session on the Kali agent
Target: root account

## Skills Demonstrated

- SIEM deployment (Wazuh Manager, Indexer, Dashboard)
- Agent enrollment and management
- Log analysis and alert triage
- MITRE ATT&CK technique mapping
- Incident documentation and reporting
- Security recommendations based on findings

## Full Report

See report/incident-report.md for the complete incident investigation.

## Tools Used

- Wazuh 4.14.7
- Kali Linux
- VMware Workstation
- MITRE ATT&CK Framework
