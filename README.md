# MailShield SOC/SOAR Lab

**Enterprise email security SOC & SOAR lab demonstrating synthetic email
analysis, detection engineering, Splunk, Shuffle automation, IOC enrichment,
risk scoring, and incident response in an isolated environment.**

Status: In progress - built step by step, documented as I go.

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
- **StackEdit** - in-browser Markdown editing, live preview, and GitHub-ready documentation

## Repository structure

- `data/` - synthetic email dataset and derived Splunk-ready event data
- `splunk/` - detections, queries, dashboards, config
- `shuffle/` - SOAR workflows
- `docs/` - full write-ups (architecture, detections, incidents, threat
  hunting, MITRE mappings, lessons learned, troubleshooting)
- `diagrams/` - architecture and flow diagrams

## Progress log

- [x] Dataset inspected and organised (`data/synthetic_emails/`)
- [x] Data ingested into Splunk
- [x] Detection 1: Reply-To Domain Mismatch
- [x] Detection 2: External Sender + Urgency Language
- [x] IOC enrichment workflow (CASE-04)
- [x] Risk scoring model (CVSS-aligned, 0.0-10.0)
- [ ] Shuffle automation
- [x] Incident response write-ups (CASE-04 complete, CASE-01/02/03 pending)
- [ ] Threat hunting exercises
- [ ] MITRE ATT&CK mapping

## Connect with Me

-  Portfolio: [justjeff211.github.io](https://justjeff211.github.io/)
-  LinkedIn: [Mojalefa L. Letsoara](https://www.linkedin.com/in/mojalefa-l-letsoara283b5a211/)

This README will be filled in properly as each step is completed.
