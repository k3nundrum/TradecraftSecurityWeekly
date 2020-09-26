Black Hat & DEF CON 2017 - Tradecraft Security Weekly #13

# Kali Linux Revealed
- New book from Offsec
- Hard copy free pdf
- New Kali Linux Certified Professional cert
- configuring and hardening kali
# Portia
- By Trustwave SpiderLabs
- Automated tool for performing privilege escalation and lateral movement in a domain
- Python script that leverages other PowerShell scripts like Inveigh, KeeThief, PowerUpSQL, Invoke-Mimikatz etc...
- https://github.com/SpiderLabs/portia
# IsThisLegit & Phinn
- By DUO
- IsThisLegit is a Chrome extension for reporting phishing in a GSuite environment
- Has analyst dashboard
- Phinn is a Chrome extension that trys to identify "Google Login Page" phishing based off the rendered page
- https://duo.com/blog/new-open-source-phishing-tools-isthislegit-and-phinn
# Revoke-Obfuscation
- Daniel Bohannon & Lee Holmes
- PowerShell obfuscation detection framework
- Rapidly measure obfuscation across many scripts
- Relies on feature extraction and comparison instead of IOCs or RegEx matching.
- https://github.com/danielbohannon/Revoke-Obfuscation
# EAPHammer
- By Gabriel Ryan (@s0lst1c3)
- Toolkit for performing targeted evil twin attacks agains WPA2-Enterprise networks
- Minimal manual configuration
- Leverages a slightly modified version of hostapd-wpe
- Built-in Responder
- Can perform "Hostile Portal" attack to LLMNR/NBNS poison
- https://github.com/s0lst1c3/eaphammer
# Kwetza
- By Chris Le Roy (@brompwnie)
- Infecting existing Android apps with a meterpreter payload
- Easily inject payloads into a target application
- Can use the default permissions of the app or inject additional permissions for more functionality
- https://github.com/sensepost/kwetza
# Koadic
 - By zerosum0x0
 - Windows post-explotiation tool similar to Meterpreter/Empire
 - Mostly just uses Windows Script Host (JScript/VBScript)
 - Can serve payloads in memory using mshta, regsvr32, rundll32
 - A number of pivoting/post-exploitation modules
 - https://github.com/zerosum0x0/koadic
# sRDI
- By Nick Landers (@monoxgas)
- Shellcode implementation of Reflective DLL Injection
- Has functionality to convert DLL's to shellcode
- Can load into memory with C#
- Can convert DLL with PowerShell to be loaded with Invoke-Shellcode
- https://github.com/monoxgas/sRDI
# Yasuo
- By @0xsauby
- A scanner for vulnerable 3rd party web apps
- Find common apps like Apache, Tomcat, JBoss etc..
- Written in Ruby
- Uses Nmap to port scan
- Can brute force logins
- https://github.com/0xsauby/yasuo
# VaporTrail
- By Larry Pesce and Galen Alderson
- Data exfiltration over FM radio tool
- Uses a Raspberry Pi and wire to send data
- RTL-SDR to receive
- https://vaportrail.io
# Printer Exploit Kit (PRET)
- By Ruhr University Bochum - Network and Data Security
- Tool for assessing and exploiting printers
- Supports PostScript, PJL, and PCL
- Can access the printer's file system, manipulate print jobs, or cause damage to the device
- https://github.com/RUB-NDS/PRET
# WarHorse
- By Ralph May (@ralphte1)
- Automated command and control deployment
- Using cloud services like AWS or Digital Ocean various tools can be spun up quickly
- Deploys docker containers
- Spin up Cobalt Strike, Metasploit etc. across various cloud services





