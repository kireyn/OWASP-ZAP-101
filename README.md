# OWASP-ZAP-101

Set up your own OWASP ZAP for fun and profit.

# What we need:

## OWASP_Zed_Attack_Proxy_Project

https://github.com/zaproxy/zaproxy/wiki/Downloads

## Mozilla Firefox or Google Chrome

https://www.mozilla.org/en-US/firefox/new/ 

https://www.google.com/chrome/

Use special Browser Profile for testing, thus preventing you from leaking your creds. 

## Useful extensions:

### Wappalyzer  

https://www.wappalyzer.com/

### FoxyProxy or TunnelSwitch

https://getfoxyproxy.org/

https://chrome.google.com/webstore/detail/tunnelswitch/nfpphleklkamlblagdkbkomjmaedanoh

### Cookie Editor or EditThisCookie

https://add0n.com/cookie-editor.html

https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=ru

### User-Agent Switcher or User-Agent Switcher for Chrome

https://addons.mozilla.org/en-US/firefox/addon/uaswitcher/

https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg?hl=ru

 # What we are going to play with:

## OWASP_Juice_Shop_Project

https://www.owasp.org/index.php/OWASP_Juice_Shop_Project

## How to set up your own playground: 

### Ubuntu VM:

Download Ubuntu Server 18.04.1 LTS

https://www.ubuntu.com/download/server

### In terminal:

sudo -i

apt update

apt upgrade

ifconfig

Install Docker
    
Run docker pull bkimminich/juice-shop
   
Run docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
   
Browse to http://localhost:3000 (on macOS and Windows browse to http://192.168.99.100:3000 if you are using docker-machine instead of the native docker installation)

### Windows 

Install OWASP_Zed_Attack_Proxy_Project

https://github.com/zaproxy/zaproxy/wiki/Downloads

Install Docker
    
Run docker pull bkimminich/juice-shop
   
Run docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
   
Browse to http://localhost:3000 (on macOS and Windows browse to http://192.168.99.100:3000 if you are using docker-machine instead of the native docker installation)

# Let's play: 
### Site Tree

Focus on specific sites

Focus  on specific functions

Visualize attack  surface

Set "Scope" to filter or other tools

### Spider 

Spidering will find you all the linked content: Pages, scripts and images, ...

Content discovery is finding unlinked content by either guessing or brute force  

### Active Scan

Automatically scan and  fuzz all traffic for common vulnerabilities  

### Fuzzer

Set up robust, automated/scripted testing easily

"Fuzz" parameters, paths, etc, etc

Bruteforce Passwords

Content discovery with lists

Iterating ID's, etc, etc

++

### Request Editor

Replay requests quickly and  from any tool inside of Burp

Perform manual testing

### Encode/Decode/Hash

Transforming encoded data into its canonical form

### Add on Marketplace

Power on addons only in case of need

### Useful OWASP ZAP addons:
Active Scanner rules
    
Passive Scanner rules
    
FuzzDB

## Useful lists:

https://github.com/danielmiessler/SecLists

https://github.com/fuzzdb-project/fuzzdb

# What you are going to read after:

https://leanpub.com/ltr101-breaking-into-infosec

https://leanpub.com/web-hacking-101

https://www.amazon.co.uk/Web-Application-Hackers-Handbook-Exploiting/dp/1118026470/

https://www.owasp.org/images/1/19/OTGv4.pdf

https://www.amazon.co.uk/Mastering-Modern-Web-Penetration-Testing/dp/1785284584/

https://portswigger.net/web-security

https://www.bugcrowd.com/hackers/bugcrowd-university/

https://www.hacker101.com/







