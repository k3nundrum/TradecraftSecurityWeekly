Password Spraying Windows Active Directory Accounts – Tradecraft Security Weekly #5

https://github.com/dafthack/DomainPasswordSpray
https://www.rapid7.com/db/modules/auxiliary/scanner/smb/smb_login

# More Accounts = More Privs
- Having access to more AD account creds leads to more privileges on the network
- Allows for additional access to various network resources like shares, email, and other systems
- Using tools like BloodHound it can be very easy to determine escalation paths to DA

# Account Lockout Policies
- Most orgs typically set an account lockout policy to prevent brute force attacks
- Typical lockout policy might lockout accounts after 5 attempts in 30 mins
- Password spraying gets around this restriction by performing less authentication attempts than the lockout policy in the observation window

# Password Spraying
- Password spray all domain user accounts
- Try:
	- SeasonYear (Spring2017)
	- Password123
	- CompanyName123
	- etc...
- Some tools to password spray:
	- DomainPasswordSpray.ps1
	- SMB_login module from msf
# Demo
spray
```
C:\powershell.exe -exec bypass
PS> Import-Module .\DomainPasswordSpray.ps1 -Password Spring2017
```
get userlist
```
PS> Get-DomainUserList
```
MSF when not connected to domain and after enumerated a userlist.
```
msf> use auxiliary/scanner/smb/smb_login
msf> set RHOSTS targetip
msf> set SMBDomain corp.empire.com
msf> set SMBPass Spring2017
msf> set USER_FILE /root/Desktop/userlist.txt
```
# For the Blue Team
- Alert on password spraying attempts
- Perform internal password sprays to weed out poor passwords
- Increase password policies to prevent weak passwords


































