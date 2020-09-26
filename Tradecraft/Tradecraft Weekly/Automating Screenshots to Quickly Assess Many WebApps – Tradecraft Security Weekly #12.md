Automating Screenshots to Quickly Assess Many WebApps – Tradecraft Security Weekly #12

https://github.com/ChrisTruncer/EyeWitness
https://bitbucket.org/al14s/rawr/wiki/Home
https://github.com/breenmachine/httpscreenshot
https://bitbucket.org/LaNMaSteR53/peepingtom/src/master/
https://github.com/dafthack/PowerWebShot
# Large External Attack Surface
- Common scenario for an external pentest is to face a large attack surface
- Have commonly tested orgs with multiple /16 net ranges or larger
- Portscan indicates many web servers
- Would be very inefficient to manually open a browser page for each site
- But... automating screenshots can help us quickly discover interesting items
# Internal WebApps
- Can be very useful on internals as well
- Locate internal web portals like wiki's, SharePoint, security appliances, etc...
- Look for vulnerable outdated web servers like Tomcat, HP System Management Homepage,etc
- Locate printers or other network devices; likely still using default creds
# Tools
- EyeWitness
	- can be used in Docker container
- Rawr
	- Searchable html report; threat matrix
- httpscreenshot
	- Works really well; can brute sub-domains too
- Peeping Tom
	- Discontinued but its lanmaster53's so its probably awesome
- PowerWebShot
	- PowerShell but currently has problem with sites w/ cert issues
# EyeWitness docker DEMO
```
docker build --build-arg user=$USER --tag eyewitness .
docker run --rm -it -v /root/Desktop/EyeWitness-Results:/tmpEyeWitness eyewitness -f /tmp/EyeWitness/30-sites.txt --headless --threads 5 --timeout 20
```
