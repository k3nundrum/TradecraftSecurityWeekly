OSINT & External Recon Pt. 1 - Host Discovery - Tradecraft Security Weekly #8

Recon-ng: https://bitbucket.org/LaNMaSteR53/recon-ng
Datasploit: https://github.com/DataSploit/datasploit
Spiderfoot: http://www.spiderfoot.net/ 
Censys: https://censys.io/ 
Shodan: https://www.shodan.io/ 
Threatcrowd: https://www.threatcrowd.org/ 
HackerTarget: https://hackertarget.com/
Netcraft: https://www.netcraft.com/
enumall: https://github.com/jhaddix/domain
# External Network Attack Surface
- External hosts are on the frontline and are potentially the entry point an attacker needs
- Locate external assets using OSINT
- No need to portscan
- Often find legacy ranges that may have been forgotten
- Determining what hosts actually belong to an organization can be tricky sometimes
# OSINT Host Discovery
- Search Engines
	- google dorks
		- Site:domain.com - site:www.domain.com etc...
- Brute force DNS
	- mail.domain.com
	- wiki.domain.com
	- sharepoint.domain.com etc...
- Whois lookups for Netblock "customer" or "org" name
- Autodiscover OWA or O365
- Searcg portscan databases
	- Shodan, Censys.io
	- Bonus: you get hosts and ports
- Look at certificates for other hostnames and domains
- Do reverse DNS lookups on netblock ranges
- Check for other vhosts on the same IP
- Search other OSINT sites like threatcrowd, hackertarget,netcraft etc..
# OSINT Tools
- Keep in mind some of the services these tools hit require API keys that might not be free
	- Recon-ng
	- Spiderfoot
	- Datasploit
# DEMO
```
# recon-ng
> workspaces add targetname
[test] >add domains
> microsoft.com
> show domains
> show modules
> use recon/domains-hosts/brute_hosts.py
> show info
> run
> show hosts
```
# For the Blue Team
- Do OSINT on your own org to determine what assets are easily discoverable by attackers






























