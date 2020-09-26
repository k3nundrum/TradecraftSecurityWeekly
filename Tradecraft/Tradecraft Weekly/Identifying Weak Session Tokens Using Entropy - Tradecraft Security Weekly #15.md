Identifying Weak Session Tokens Using Entropy - Tradecraft Security Weekly #15

https://nvisium.com/blog/2015/07/09/intro-to-burpsuite-part-vi-burpsuite/
https://www.owasp.org/index.php/Session_Management_Cheat_Sheet#Session_ID_Entropy
# Session Token Overview
- What is a session token?
- Unique identifier assigned to an authenticated session
- Usually set on the first login
- Hopefully they expire
- Sessions can be hijacked if the tokens are not kept safe
- Should be random and long.
# Session Attacks
- Cross-Site Scripting
- Cross-Site Request Forgery
- Session Fixation
- Man-in-the-Middle
- Session Brute Forcing
- more...
# Brute Forcing Sessions
- Entropy - A calculation using statistics for predicting the quality of randomness
- Session tokens can be generated in many ways
- Sometimes those tokens can be predicted based off of poor randomness
- Some steps to discover poor entropy
	- Gather a large sample of tokens
	- Analyze the entire sample set for frequency and position
	- Determine the exploitability of the session token
- Burp Sequencer FTW
# For the blue team
- Generate session tokens that are at least 128 bits with 64 bits of entropy
- Don't roll your own session management frameworks.