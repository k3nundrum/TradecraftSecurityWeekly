Linux Privilege Escalation - Tradecraft Security Weekly # 22

https://www.exploit-db.com/searchsploit/
https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/
http://www.securitysift.com/download/linuxprivchecker.py
https://github.com/rebootuser/LinEnum
https://www.vulnhub.com/
https://www.rebootuser.com/?p=1623
# Situational Awareness
- Ok you have a shell.
- Depending on how you got there you might not be 'root'
- System/User Info
```
uname -a
env
whoami
history
pwd
```
- Who else has logged in?
```
who
w
last
```
- Are you in the sudoers file?
```
sudo -l 
cat /etc/sudoers
```
- Other super users?
```
grep -v -E "^#" /etc/passwd | awk -F: '$3 == 0 { print $1}'
```
- Network info
```
ifconfig -a
netstat -antup
lsof -i
```
# Vulnerable OS?
- Get kernel version from `uname -a`
- Use searchsploit to search exploitdb for local privesc exploits
```
searchsploit kernel 2.6 linux | sort -n
```
- Very important!!! Review the code before running it
- Compile/Run
# Vulnerable Services?
- Enumerate services/software
```
ps aux
ps -ef
```
- Look for services running as a privileged user
- List versions of installed software
```
dpkg -l
rpm -qa
httpd -v
mysql --version
python --version
ruyb -v 
etc...
```
- Determine if any have vulnerabilites you exploit using searchsploit again
# Look for Interesting Files
- SUID files?
```
find / -perm -u=s -type f 2>/dev/null
```
- Password hashes?
```
cat /etc/shadow
```
- Any files you can overwrite that get run by root?
- Check jobs/tasks
```
ls -la /etc/cron*
```
- SSH keys in current or other user directories?
```
ls -la ~/.ssh/
```
- Look for cleartext creds in files for various scripts, DB's config files etc...
```
find . -type f -maxdepth 4 | xargs grep -i "password"
```
# Linux Privesc Scripts
- LinuxPrivChecker.py
	- http://www.securitysift.com/download/linuxprivchecker.py
- Unix-privesc-check
	- https://github.com/pentestmonkey/unix-privesc-check
- LinEnum
	- https://github.com/rebootuser/LinEnum
- LinPeas
	- https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS
# For the Blue Team
- keep your distros updated!
```
apt-get update && apt-get upgrade
```