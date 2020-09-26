Evading Network-Based Detection Mechanisms - Tradecraft Security Weekly - # 24

Nmap Evasion Options - https://nmap.org/book/man-bypass-firewalls-ids.html
ProxyCannon - https://www.shellntel.com/blog/2016/1/14/update-to-proxycannon
# Network Detection Overview
- The internet is noisy
- Direct scanning against external or internal infrastructure is noisier though
- Most IDS pick up basic Nmap scans relatively quick
- Org are getting better at detecting/blocking password sprays
- Some web portals have it built-in now to shun multiple failed attempts
# Why Evade Detection
- Evading detection can be slow
- Real attackers have all the time in the world
- A shunned scan or credential attack typically means you aren't winning
- Determining detection thresholds can be really eye opening to an org
- Note: You can always spin up more hosts to test from if you get burned
# How to Evade Detection?
- Two things typically matter when you look at evasion:
	- Timing in between requests
	- Requests per IP
- Slowing your scans down is a must
- Being able to manipulate your source IPs will help as well
- Packet Fragmentation
# Tools for Evasion
- Nmap
	- Timing options T1: Sneaky (waits 15 seconds) or T0:Paranoid (waits 5 minutes)
	- Packet Fragmentation (-f)
	- A number of other options (https://nmap.org/book/man-bypass-firewalls-ids.html)
- Proxycannon (from ShellIntel) 
	- https://github.com/ShellIntel/scripts
	- Can spin up 20 Amazon EC2 instances to proxy scans through
	- Can rotate public WAN IP of nodes.