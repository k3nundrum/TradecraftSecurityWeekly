OSINT & External Recon Pt. 2: Contact Discovery - Tradecraft Security Weekly # 26

https://bitbucket.org/LaNMaSteR53/recon-ng
https://github.com/laramies/theHarvester
https://github.com/mdsecactivebreach/LinkedInt
https://github.com/gojhonny/InSpy
https://weleakinfo.com/api/public
https://hashes.org/leaks.php
https://github.com/clr2of8/GatherContacts
https://www.blackhillsinfosec.com/gathering-usernames-from-google-linkedin-results-using-burp-suite-pro
https://github.com/jivoi/awesome-osint
https://0x00sec.org/t/osint-passive-recon-and-discovery-of-assets/6715
# External Recon for Contact Info
- Episode 8 covers external host discovery
- Now let's find some employees
- Why?
	- Potential phishing targets
	- Can be used during password attacks
	- Learn more about various roles employees have at an org
# LinkedIn
- Biggest resource for finding employee info
- They actively battle scraping of the site...
- THey are a number of tools for searching
- Employees gladly tell y ou about all kinds of things (security products they use, Database types, OS versions etc..)
# Breach Data
- Many employee email addresses can be found in public breach dumps
- Search through public dumps of breach data
	- Download leak data from hashes.org
	- https://hashes.org/leaks.php
- Publick Leak Search Engines
	- We Leak Info API
	- https"://weleakinfo.com/api/public
# Tools
- Recon-NG - bing_linkedin_cache module uses Bing's API to find LinkedIn users
- TheHarvester - Many recon modules including one that searches Google Results for LinkedIn users
- LinkedInt - Scrapes LinkedIn directly and also searches Hunter.io
- InSpy - Scrapes LinkedIn directly
# Recon-NG DEMO
go to Azure and sign up for bing search api key.
```
# recon-ng
workspaces add bhs
add companies
Black Hills Information Security
load bing_linkedin_cache
show options
set SUBDOMAINS us
run
show contacts
```
# TheHarvester DEMO
```
#python theHarvester.py -d "Black Hills Information Security" -b linkedin
```
# LinkedInt DEMO
```
python LinkedInt.py
Microsoft
ms.csv
n
microsoft.com
auto
```
# Some Other Recon-NG Modules
- recon/domains-contacts/whois_pocs 
	- Uses ARIN Whois to harvest POC data
- recon/domains-contacts/pgp_search
	- Searches the MIT public PGP key server for email addresses
- recon/companies-multi/github_miner
	- Uses Github API to enumerate repositories and member profiles
# Manually Harvesting LinkedIn Contacts
- Burp Plugin for scraping Google Search results
- https://github.com/clr2of8/GatherContacts
- https://www.blackhillsinfosec.com/gathering-usernames-from-google-linkedin-results-using-burp-suite-pro/
# For the Blue Team
- Do the same recon on your own org
- Discover who has creds readily available in public breaches



























