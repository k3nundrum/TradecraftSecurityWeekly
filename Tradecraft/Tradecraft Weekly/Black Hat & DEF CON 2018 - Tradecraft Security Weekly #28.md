Black Hat & DEF CON 2018 - Tradecraft Security Weekly #28

# ZigDiggity
- ZigBee Pentest Toolkit (Bishop Fox)
- Introduces previously unpublished attack patterns
- Ack Attack - Attemps to cause Zigbee endpoint devices to malfunction
- Rejoin Blackhole Attack - A method of replying to request beacons to force endpoint devices to try to connect to a user-specified PAN ID
- Designed to be used with KillerBee Card
- https://github.com/BishopFox/zigdiggity
# Humble Chameleon
- Tool designed to MITM services that have multi-factor - Forrest Kasler
- Written in Node.js
- Uses two domains to hide malicious content
- Secondary domain with phishing page only triggered with certain web request
- https://github.com/claissg/humble_chameleon
# WHID Injector
- USB Human Interface Device (HID) with a WiFi chip - Luca Bongiorni
- Allows keystrokes to be sent via WiFi to a target machine
- Allows interactive commands and scripts to be run remotely
- ~$16
- https://github.com/whid-injector/WHID
# Chiron
- An IPv6 Security Assessment Framework - Antonios Atlasis
- IPv6 Scanner, proxy, attack modules etc..
- Allows for easily crafting arbitrary IPv6 headers chain to help evade IDS/IPS, firewalls or other security devices
- Incorporates it's own IPv6 sniffer
- https://github.com/aatlasis/Chiron
# ExchangeRelayX
- An NTLM relay tool to provide an OWA-like interface to EWS - William Martin (@quickbreack)
- Trick user into navigating to attacker server
- NTLM auth is relayed to EWS
- OWA-like interface for: reading emails, sending emails, GAL access, etc...
- https://blog.quickbreach.io/one-click-to-owa/
- https://github.com/quickbreach/ExchangeRelayX
# hideNsneak
- Assists in managing attack infrastructure for penetration testers - Mike Hodges (@rmikehodges)
- Quickly setup various cloud services
- VMs, Domain Fronting, Cobalt Strike servers, API gateways and firewalls
- Remote installations of Burp Collaborator, Cobalt Strike, Socat, LetsEncrypt, GoPhish, and SQLMap
- https://github.com/rmikehodges/hideNsneak
# Trommel
- Sifts through embedded device files to identify potential vulnerable indicators - CERT
- Some examples: SSH keys, SSL keys, IP addresses, URLs, email addresses, shell scripts, web server binaries, config files, db files, specific binaries (i.e. Dropbear, BusyBox etc), shared object library files, webapp scripting variables, and Android APK file permissions
- https://github.com/CERTCC/trommel
# Cache Poisoning & Param Miner
- New technique for identifying cache poisoning on websites - James Kettle
- Send a request that causes a malicious cached response for other users of the site
- Use Param-Miner to find unkeyed inputs 
- Explore potential exploits, get them cache
- https://github.com/PortSwigger/param-miner
- https://portswigger.net/blog/practical-web-cache-poisoning
# Merlin
- A cross-platform post-exploitation HTTP/2 Command & Control server and agent written in golang - Russel Van Tuyl (@Ne0nd0g)
- Added support for QUIC protocol
- QUIC = Google's Quick UDP Internet Connection
- Potential to evade detection by not using standard TCP protocols for C2
- https://github.com/Ne0nd0g/merlin
# ADRecon
- Extracts various artifacts out of an AD environment - Prashant Mahajan
- PowerShell tool that uses Microsoft RSAT or talks to DC via LDAP
- Obtains various info: forest, domain, trusts, password policy, users, OUs, LAPS passwords, bitlocker recovery keys etc...
- https://github.com/sense-of-security/ADRecon