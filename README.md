# MailShield SOC/SOAR Lab

**Enterprise email security SOC & SOAR lab demonstrating synthetic email
analysis, detection engineering, Splunk, Shuffle automation, IOC enrichment,
risk scoring, and incident response in an isolated environment.**

Status: 🚧 In progress - built step by step, documented as I go.

## What this project demonstrates

`Synthetic Emails -> Splunk -> Detection -> Alert -> IOC Enrichment ->
Risk Scoring -> Shuffle Automation -> Incident Response -> Documentation`

## Toolset

- **Splunk** - SIEM, ingestion, detection engineering, alerting
- **Shuffle** - SOAR automation
- **VirusTotal** - IOC enrichment (IPs, domains, URLs, hashes)
- **Talos Intelligence** - reputation lookups
- **AbuseIPDB** - IP abuse history
- **CyberChef** - decoding/analysing email artefacts
- **Git/GitHub** - version control and portfolio

## Repository structure

- `data/` - synthetic email dataset and derived Splunk-ready event data
- `splunk/` - detections, queries, dashboards, config
- `shuffle/` - SOAR workflows
- `docs/` - full write-ups (architecture, detections, incidents, threat
  hunting, MITRE mappings, lessons learned, troubleshooting)
- `diagrams/` - architecture and flow diagrams

## Progress log

- [x] Dataset inspected and organised (`data/synthetic_emails/`)
- [ ] Data ingested into Splunk
- [ ] Detection 1: Reply-To Domain Mismatch
- [ ] Detection 2: External Sender + Urgency Language
- [ ] IOC enrichment workflow
- [ ] Risk scoring model
- [ ] Shuffle automation
- [ ] Incident response write-ups
- [ ] Threat hunting exercises
- [ ] MITRE ATT&CK mapping

This README will be filled in properly as each step is completed.
