# DShield Internship Portfolio

Portfolio for my SANS ISC Internship, showcasing the setup and analysis of a DShield honeypot, integration with ELK Stack, and Cyber Threat Intelligence (CTI) using OpenCTI.

## Overview
- **DShield Setup**: Deployed a honeypot on AWS EC2 (`52.15.172.140`), overcoming Raspberry Pi networking challenges.
- **Log Analysis**: Analyzed `webhoneypot-2025-06-03.json` to identify top attacker IPs and exploit patterns.
- **ELK Stack**: Planned log parsing with handler’s pipeline for Kibana visualizations.
- **OpenCTI**: Integrated IOCs (e.g., source IPs) for CTI analysis.
- **Report**: Drafted "Attack Observation" report, inspired by ISC diary.

## Directory Structure
- `docs/`: Draft report and setup guide.
- `scripts/`: Shell scripts for log analysis and ELK config.
- `logs/`: Sanitized log snippets.
- `visualizations/`: Graphs (e.g., top 10 IPs).
