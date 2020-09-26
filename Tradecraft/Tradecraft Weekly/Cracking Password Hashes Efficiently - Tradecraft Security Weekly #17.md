Cracking Password Hashes Efficiently - Tradecraft Security Weekly #17

http://www.dafthack.com/blog/howtocrackpasswordhashesefficiently
https://hashcat.net/wiki/doku.php?id=example_hashes
# What are password hashes?
- A one-way mathematical function is performed against a cleartext value
- Easy to generate but (hopefully) hard to reverse
- The hash is then stored
- On login the password is hashed then checked against the stored value
# Cracking Methods
- Brute Force
	- Try all possible combinations
- Dictionary
	- Use a wordlist of common passwords
- Hybrid
	- Word + Mask
- Rainbow Tables
	- Pre-computed lists
# Prep Wordlists
- Crackstation
	- 1.4 billion words
- RockYou
	- 14 million words
- Cain
	- 306,000 words
- Usernames
	- List of usernames from the hashes
- Custom
	- Generated from scraping target website
# Crack Efficiently
- Start with straight dictionary attacks
- Append characters to your wordlist
	- wordlist + (?a)
	- wordlist + (?a?a)
	- wordlist + (?a?a?a)
	- wordlist + (?d?d?d?d)
- Prepend characters
	- (?a) + wordlist
	- etc...
- Mangle your wordlist
	- 1337speak
- Run through rainbow tables
- Brute Force
	- Ex. try all possible combos of 8 chars
- Smart Brute Forcing
	- Brute force each character position differently
	- Example
		- -1 ?u -2 ?u?| -3 ?| -4 ?a
		- ?1?2?3?3?3?3?3?3?3?a
- Try combining different wordlists together
	- wordlist1.word1 + wordlist2.word1
	- wordlist1.word2 + wordlist2.word1
- Re-ingest the cracked passwords and go through the entire process again
- Get some baselines for your typical cracking times for certain hash types and script out the whole process so you don't have to manually
# Some Password Cracking Tool
- John the Ripper
	- Standard CPU-based password cracker
- Rcrack
	- For use with rainbow tables
- Pyrit
	- Great for precomputing rainbow tables for wireless WPA2 PSKs
- Hashcat
	- Extremely versatile password cracker that supports GPU cracking
# Hashcat cracking a kerb ticket DEMO 
```
./hashcat.bin --help
./hashcat64.bin -m 13100 -a 0 kerb-ticket.txt ../password-lists/rockyou.txt --force
./hashcat64.bin -m 13100 -a 6 kerb-ticket.txt ../passwordlist/rockyou.txt ?a --force
```
# For the Blue Team
- make stronger password policies
- Perform password cracking exercises
- Ensure hashes are being stored using a strong hashing algorithms