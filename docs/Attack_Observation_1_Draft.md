# Attack Observation 1 Draft
I initially approached the BACS 4499 ISC Internship with the idea of utilizing a Raspberry Pi to host the DShield Honeypot. I had fond memories of programming an Arduino during my Electrical Engineering undergraduate program, and sought to rekindle that inspiration. I purchased a Raspberry Pi 5 Complete Starter Kit from Vilros[1], and truly enjoyed the hands-on assembly process. Within an hour, I had successfully assembled and booted up the tiny computer with the pre-loaded Raspberry Pi desktop OS.

I then switched gears to configuring my DShield Sensor on my Raspberry Pi. I started by downloading the Raspberry Pi Imager on my local machine, and followed the DShield-ISC GitHub instructions[2] to install the Raspberry Pi OS Lite. I struggled to follow along with the “RaspberryPiInstall” YouTube video[3] until I noticed that it was posted over five years ago! 

Eventually, I was able to successfully load the OS and install DShield from GitHub, but I was immediately met with the “Missing /var/log/dshield.log” error. I recognized that I was facing a common issue for students, and that the host IP wasn’t properly exposed to the internet. This led me down the rabbit hole of configuring internet settings to enable an IP Passthrough from my modem to my router, which was challenged by the fact that my family was dependent on the network staying up. My research into the BGW320-500 modem and Orbi RBR750P router led me to conclude that my issues relate to Double NAT (Network Address Translation) or port forwarding challenges.

After many trials and tribulations, I made the decision to pursue an alternative approach and created an AWS account. Within 30 minutes of the decision, I had successfully spun up a t2.micro EC2 instance, installed DShield[4], and verified that my first Web Honeypot Logs successfully populated in my Internet Storm Center account[5]. As a former AWS employee, I laughed at how easily I could spin up cloud resources; I suppose there is a reason that AWS controls over 33% of the entire market[6]. Exposing my sensor to the internet was trivial in comparison to the issues I navigated within my home network. I also added a Security Group and formatted an inbound rule to accept SSH traffic from the newly configured port 12222, restricting the source to my local IP address in accordance with AWS best practices.

Getting the DShield Sensor up and running on AWS was a crucial first step toward my success in this internship. I will continue troubleshooting my modem/router settings in order to expose my Raspberry Pi to the internet, but don’t intend to let networking challenges take away from my larger goals.

After meeting with my mentor handler and learning about his DShield-SIEM implementation[7], I plan to deploy my own ELK Stack in an Ubuntu VM in order to collect and parse the Honeypot logs. Additionally, I have a larger goal of integrating with the OpenCTI platform[8] and applying Cyber Threat Intelligence (CTI) to my log analysis.

[1] https://vilros.com/products/vilros-raspberry-pi-5-complete-starter-kit?srsltid=AfmBOorYKU8QL3kxdTQcJKGzmJr4t3zY2ZYF6QTUHxpGFvTYJGYWX_Pj
[2] https://github.com/DShield-ISC/dshield/blob/main/docs/install-instructions/Raspbian.md
[3] https://youtu.be/fMqhoNnyvmE?si=R2ckKEsmNiBoSNRC
[4] https://github.com/DShield-ISC/dshield/blob/968d65ddf3c88858749437353fc9bbb1e650ae66/docs/install-instructions/AWS.md
[5] https://isc.sans.edu/myweblogs/#
[6] https://www.statista.com/statistics/967365/worldwide-cloud-infrastructure-services-market-share-vendor/#:~:text=In%20the%20fourth%20quarter%20of,with%2010%20percent%20market%20share
[7] https://github.com/bruneaug/DShield-SIEM
[8] https://filigran.io/solutions/open-cti/
