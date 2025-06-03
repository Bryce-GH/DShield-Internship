# DShield Honeypot Setup Guide

## Raspberry Pi Attempt
- Purchased Vilros Raspberry Pi 5 Starter Kit.
- Installed Raspberry Pi OS Lite via Imager.
- Faced “Missing /var/log/dshield.log” due to unexposed IP.

## AWS EC2 Setup
- Deployed t2.micro instance.
- Installed DShield: `git clone https://github.com/DShield-ISC/dshield`.
- Configured Security Group:
  - TCP 12222 (SSH, restricted to my IP).
  - TCP 80 (web, open).
- Verified logs: `/srv/db/webhoneypot-2025-06-03.json`.
- Used `scp -i dshield.pem -P 12222 ubuntu@<ec2-ip>:/srv/db/webhoneypot-2025-06-03.json .` to transfer logs.

## Challenges
- IP Passthrough on Orbi RBR750P/AT&T BGW320-500 conflicted with family network.
- EC2’s simpler networking resolved issues.
