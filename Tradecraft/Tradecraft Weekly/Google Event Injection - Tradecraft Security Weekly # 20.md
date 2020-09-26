Google Event Injection - Tradecraft Security Weekly # 20

https://www.blackhillsinfosec.com/google-calendar-event-injection-mailsniper/
# History
- One day got a calender alert for a flight that wasn't his
- A coworker has sent their flight details in an email
- Google thought the itenerary was mine and automatically added to my calender
- This was the start of the research....
# Event Injection
- An email isn't necessary at all though
- Simply add a Google user to an event and select not to notify them
- Google will automaticaly add that event to their calender
- This can present a very unique situation for phishing...
# Event Injection & SE
- Here are a few ideas:
	- Include a link to a conference call site but have it pointing to a credential page
	- Include a malicious attachment "agenda"
	- Have victims navigate to a fake Google Auth page and collect creds
# Event Injection
- Events get even more fun when you use the Google API
- It's possible to make it look like a user already accepted an invitation
- ...they never received an invite though.
- This bypasses the setting for not auto-adding events to G-calender
# Mailsniper DEMO
```
powershell.exe -exec bypass
PS> Import-Module .\MailSniper.ps1
PS> Get-Help Invoke-InjectGEventAPI - Examples
PS> Invoke-InjectGEventAPI - PrimaryEmail attackerbutspoofedasanimportancompanyexecutive31337@gmail.com -AccessToken 'akdjfhksdhjfaklshjfksdjhfkasdjhfksdhdsfhkasdjfhdkasflhjsdkfhjdfhjk' -Targets "hacktheearp@gmail.com" -StartDateTime 2017-11-02T13:00:00 -EndDateTime 2017-11-02T13:30:00 -EventTitle "All Hands Meeting" -EventDescription "Required: Please first review the Meeting Agenda
>> https://phish-site.com/agenda
>> _________________________________
>> You can dial in using your phone.
>> United States: +1 (555) 534-2178
>> Access Code: 234-283-521 " -EventLocation "Https://global.gotomeeting.com/join/0123456789"
```
