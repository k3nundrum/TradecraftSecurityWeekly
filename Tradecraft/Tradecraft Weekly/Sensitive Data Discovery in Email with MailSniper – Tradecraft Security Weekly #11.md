Sensitive Data Discovery in Email with MailSniper – Tradecraft Security Weekly #11

https://github.com/dafthack/MailSniper
Office365 Compliance Search https://msitpros.com/?p=3678
# Hunting for Sensitive Data
- MailSniper
- Post-exploration pillage sensitive data from mailboxes
- Gather credentials, insider intel, network architecture info
- Written in PowerShell
- In some cases can be run remotely across the Internet against external OWA/EWS servers
# Searching One Mailbox
- Invoke-SelfSearch
- Searches the curent user's mailbox for certain terms
- Might be an interesting priv esc vector.
```
PS> Invoke-SelfSearch -Mailbox user@domain.com - ExchHostname mail.domain.com -Remote
```
# Searching All Mailboxes
- Invoke-GlobalMailSearch
- Search all mailboxes
- Use regexes to find things like cc#s
- Search an entire org for scada,ics,databases,fund transfer systems etc...
```
PS> Invoke-GlobalMailSearch -ImpersonationAccount currentuser -ExchHostname Exch1 -OutputCsv global-mail-search.csv
```
# DEMO
Single Mailbox
```
C:\ powershell.exe -exec bypass
PS> Import-Module .\MailSniper.ps1
PS> Invoke-SelfSearch -Mailbox juno.exclipse@galacticempireinc.com -ExchHostname mail.galacticempireinc.com -Remote - OutputCsv testemails.csv
```
Global Search after you are DA
```
PS> Invoke-GlobalMailSearch -ImpersonationAccount jeclipse -ExchHostname deathstar-mail.corp.empire.com -OutputCsv global-mail-test.csv
```
# O365 Compliance Search
- Invoke-SelfSearch works for O365
- But what if you need to search EVERY O365 mailbox?
- Compliance Search!
- Office365 has a built-in function to search for terms and provide a report
- Can also search SharePoint
- See https://msitpros.com/?p=3678
# For the Blue Team
- Search your org for email conversations where employees are sharing sensitive information
- Use compliance search with O365


