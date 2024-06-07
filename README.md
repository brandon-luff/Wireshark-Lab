# Wireshark Lab Malware Analysis

## Overview

This report details the findings from a network forensics analysis conducted to investigate a malware infection on a Windows computer. The analysis was performed using packet capture files, and the results include identifying key events, the nature of the malware, and indicators of compromise.

## Analysis and Findings

### 1. Date and Time of Infection
- Date and Time: Fri 27 Jan 2017 22:54:59 GMT

  <img src="https://i.imgur.com/cNfeiat.png" />

- Methodology: The infection time was determined by following the HTTP stream of a suspicious website, tyu.benme.com, which was observed to install multiple Shockwave files on the machine.

### 2. MAC Address of the Infected Computer
- MAC Address: 5c:26:0a:02:a8

  <img src="https://i.imgur.com/HblACPz.png" />

- Methodology: By filtering for DHCP packets, I identified two devices on the network: the router and the infected machine. The MAC address of the infected machine was found under the Ethernet tab by looking at the source address.

### 3. IP Address of the Infected Computer
- IP Address: 172.16.4.193

  <img src="https://i.imgur.com/ZsKlyuT.png" />

- Methodology: The IP address of the infected machine was found under the IPv4 tab. This address was identified as belonging to the infected machine, being the only active device on the network during the infection.

### 4. Host Name of the Infected Computer
- Host Name: Stewie-PC

  <img src="https://i.imgur.com/SZs2GcC.png" />

- Methodology: The host name was discovered by examining DHCP packets and checking the hostname option.

### 5. Type of Malware
- Malware Type: Trojan, specifically Cerber Ransomware

  <img src="https://i.imgur.com/kNCJLPS.png" />

- Methodology: The malware type was determined through VirusTotal analysis of the malicious files. The HTTP stream analysis revealed a Trojan that deployed Ransomware, confirmed by finding the decryptor page for the ransomware at the IP address 198.105.121.50.

### 6. Name of the Malware
- Malware Name: Cerber

- Methodology: The name of the malware was determined by analyzing the HTTP stream for the IP address 198.105.121.50, associated with the Cerber ransomware decryptor page.

### 7. Exploit Kit Used
- Exploit Kit: RIG Exploit Kit

  <img src="https://i.imgur.com/3N77zDj.png" />

- Methodology: The exploit kit used to infect the computer was identified by uploading the malware sample to VirusTotal, which indicated the use of the RIG Exploit Kit.

### 8. Compromised Website
- Compromised Website: www[.]homeimprovement[.]com

- Methodology: The infection chain was traced back to the compromised website tyu.benme.com, which was likely accessed through a redirect from
  www[.]homeimprovement[.]com following a search for home improvement information.

### 9. User's Bing Search Prior to Infection
- Search Terms: Home improvement related searches

- Methodology: The user’s search history on Bing was reviewed, revealing searches related to home improvement, which led to visiting the compromised site.

### 10. Campaigns Using the Exploit Kit
- Campaigns: Details about the campaigns using the RIG Exploit Kit were referenced from McAfee’s blog on Cerber Ransomware, indicating multiple campaigns employing this exploit kit.

- Reference: McAfee Labs Blog on Cerber Ransomware

## Indicators of Compromise (IOCs)

### IP Addresses
- 104.28.18.74 (Home improvement site)
- 139.59.160.143
- 194.87.234.129
- 91.2.1.0 through 91.239.25.255 (Ransomware Check-ins)

### Domains
- tyu[.]benme[.]com (Delivered Trojan)
- www[.]homeimprovement[.]com (Compromised Site)
- p27dokhpz2n7nvgr[.]1jw2lx[.]top (Decryptor Site)

## Tools

  
