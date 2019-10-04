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

Replay requests quickly and  from any tool inside of ZAP

Perform manual testing

### Encode/Decode/Hash

Transforming encoded data into its canonical form

### Add on Marketplace

Power on addons only in case of need

### Useful OWASP ZAP addons:
Active Scanner rules
    
Passive Scanner rules
    
FuzzDB

# HUD Times
The HUD is a completely new way to interact with ZAP.

It overlays security information on top of the application you are testing and allows you to access key ZAP features.

It is easier for people new to security to understand but it also allows experienced penetration testers to focus on the application they 

are testing.

By default the HUD is injected into all of the HTML pages proxied through the ZAP desktop. You can turn it on and off easily using the 

button on the ZAP toolbar. It is not injected by default into pages proxied through ZAP when it is running in headless/daemon mode as that 

could break unit tests. This behaviour can be changed via the HUD options.

This tutorial will take you through the HUD features and explain how you can use them. 

## Obligatory Warning
ZAP is a security tool and therefore by design you can use it to attack web applications.

You should only use ZAP (and therefore also the HUD) on applications that you either own or have permission to attack.

The good news is that if you installed ZAP on your own machine then you do own this tutorial, so lets get started ... 
## HTTPS Upgrade
The HUD uses a service worker running on a custom 'zap' domain to communicate with ZAP. This will only work on target domains that support 

HTTPS.

When the HUD is enabled ZAP will redirect HTTP sites to HTTPS. If they do not support HTTPS then ZAP will handle the HTTP upgrade internally 

so that the browser communicates with ZAP via HTTPS while ZAP forwards the requests to the target over HTTP.

Most applications should be unaffected by the HTTPS upgrade, but if your application is broken by it then please report this as an issue 

supplying as many details as you can.

You can configure ZAP to only enable the HUD for domains that are in scope. This is only available via the ZAP desktop as by default no 

domains are in scope and therefore the HUD will not be available until the first domain is added. 


## The HUD Frames
The HUD overlays a set of frames on top of the target application, which in this case is this tutorial.

You can see 2 of the HUD frames on the left and right hand sides of this page. 

If you hover over any of the tools then you will see that they expand to show more information.

The tools are designed to take up as small amount of space as is practical, but it is possible that they could still obscure information 

that you want to see on the target page.

If that happens then you can hide these 2 frames by clicking on the green HUD icon near the bottom right of this page.

The icon will change to a grey colour and the HUD side frames will stay hidden until you click on that button again, even if you navigate to 

a new page.

## Alerts

ZAP reports potential security issues via alerts. Alerts can be raised by any components within ZAP, but they are most commonly raised by:

## Passive Scanning

ZAP passively scans all of the requests proxied through it or generated by components like the traditional and AJAX spiders. Passive 

scanning just involves looking at the raw requests and responses - nothing is changed so it is considered safe to use.

## Active Scanning
Active scanning attempts to find other vulnerabilities by using known attacks against the selected targets. Active scanning is a real attack 

on those targets and can put the targets at risk, so do not use active scanning against targets you do not have permission to test. 

## Page Alerts

Potential security issues on the page you are viewing will be shown as 'Page Alerts', which by default are shown on the left hand side. This 

allows you to just focus on the potential issues on your current page without being distracted by issues on other pages.

Alerts have an associated risk, and all alerts with the same level of risk are shown together:

High Level Page Alerts
Medium Level Page Alerts
Low Level Page Alerts
Informational Level Page Alerts 

The Page Alert tools show the number of alerts for each level of risk. You can click on any of them to see the list of alerts, the URLs that 

have each type of alert, and the full details for any specific alert.
## Site Alerts

The issues that apply to any of the pages on the site you are browsing will be shown as 'Site Alerts', which by default are shown on the 

right hand side. These will include all of the alerts on the current page you are viewing as well as the alerts on all of the other pages on 

the site.

The alerts are grouped by risk in the same way as Page Alerts:

High Level Site Alerts
Medium Level Site Alerts
Low Level Site Alerts
Informational Level Site Alerts 

As with Page Alerts you can click on any of the tools to see the list of alerts, the URLs that have each type of alert and the full details 

for any specific alert.
## History

There's another frame added to the bottom of every page, and that adds another set of tools that you can use.

The History tab shows all of the requests that have been made by your browser since you opened this page. These can be requests for 

resources like images or JavaScript files, or they can be API requests.

If new pages are requested after the page loads then the tab will show a count of these requests - if you see that keeps going up then that 

will probably indicate that the page is making a series of API requests.

You can click on the tab or on the arrow button on the right hand side to show and hide the list of the requests, and you can click on any 

of the requests to see full details of the requests and responses.

The green HUD icon will now also hide all of the tabs in this frame in case they are obscuring content as well.
## WebSockets
The WebSockets tab shows all of the WebSockets requests that have been made by your browser.

If new messages are sent or received after the page loads then the tab will show a count of these messages - if you see that keeps going up   

then that you will know that the page is still sending or receiving them.

You can click on the tab or on the arrow button on the right hand side to show and hide the list of the messages, and you can click on any 

of the messages to see the full details.

WebSocket messages can either be text or binary. Once you have selected a text message you will also be able to replay the request with any 

changes to the contents that you like. This is not currently supported for binary messages. 

ZAP builds up a hierarchical site tree based on the URLs that your browser accesses.

The Sites tool , which by default is on the right hand side, allows you to view the sites tree for all of the URLs that ZAP is aware of. 

Click on the '[ + ]' and '[ - ]' controls to expand and contract the branches.

You can also click on any of the URLs in the sites tree to see the request and response made for that URL.

## Scope

The Scope tool shows you whether the page your are viewing is 'in scope', in other words if it is part of the site you are testing.

When you start using the HUD no pages will be in scope, so the icon will always be grey. To add or remove the current site from scope click 

on the scope tool. The scope icon will change to: when you are viewing a URL that is in scope.

The HUD will only allow you to use tools like the spider and active scanner on sites that are in scope. The scope tool also makes it easy to 

see when you navigate off your target site. 
## Enable Fields
However if you click on the 'Show / Enable' tool then the icon will change to and you will now be able to type in all of the fields. You can 

then try changing fields that the developers might have thought could not be changed. Clicking on the 'Show / Enable' tool again will return 

the field to their previous states, but the text you typed will still be in the fields.

Fields enabled by this tool will be outlined in blue so that you can easily identify them.

It is worth noting that some fields may still be disabled if they use JavaScript to prevent them from being modified, you will see how you can still change these values later in this tutorial.
Show Fields
The 'Show / Enable' tool will make all of the hidden fields visible and allow you to change them. As the fields are normally hidden the 

'Show / Enable' tool shows a count of the number of hidden fields. So if you see that this count is ever greater than zero then you will 

know that the page has that number of hidden fields in it.

Fields revealed by this tool will be outlined in purple so that you can easily identify them.
## Break
When testing a site there are many times when it is useful to be able to change requests 'on the fly' - you can do this using the 'Break' 

tool.
When you click the 'break' tool you will see that the button changes to and this means that all requests to and from your browser will be   

intercepted by ZAP. When you then submit the form (or navigate to another page) you will be shown a dialog that contains the request that 

has been sent by the browser. You can change any part of the request before it is submitted to the site, including the values set via the 

form, and then select either:

Step: to submit this request and then break on the next request or response
Continue: to submit this request and turn the 'break' tool off
Drop: to prevent the request from being sent to the site or the response from being received by the browser

Break works with both HTTP and WebSocket messages.
## Resend
You can resend and change requests that have previously been sent by your browser or ZAP. This applies to all of the requests you can see in 

the HUD, whether via the History tab, the Sites tree or one of the alerts.

When you display a request you will see 2 options:

## Replay in Console

This will submit the request, along with any of your changes, and show the response in the Response tab. This allows you to try different 

inputs and see how it affects the raw HTML.

## Replay in Browser

This will submit the request, again along with any of your changes, but in this case the response will be displayed in the browser as HTML. 

This works for POST requests as well as GET requests.
Spider
ZAP has 2 spiders that allow you to automatically explore web sites. The 'Spider' tool starts the 'traditional' spider. This crawls all of 

the web pages and follows all of the links that it can find. It is fast but it will not be able to follow links defined using JavaScript.

When you click on the 'Spider' tool a dialog will be displayed which allows you to start the spider. You will not be able to spider sites 

that are not in scope, but the dialog will detect that and give you the option to add the site to the scope.

When the spider is started the tool will show how far the spider has progressed. As the tutorial is very small this will not take very long 

at all, but for larger sites it may take much longer. The status is maintained when you navigate to different pages so you can carry on 

exploring the site while the spider is running. You will be able to see all of the pages that the spider has found via the Sites tree. If 

you click on the Spider tool while it is running then you will be given the option to stop it. You may well see alerts being raised after 

you start the spider as ZAP passively scans all of the URLs it finds. 
## Ajax Spider
The 'Ajax Spider' tool starts the 'ajax' spider. This launches browsers that are able to handle links defined using JavaScript. It is much 

slower than the 'traditional' spider but it will be able to handle sites that make heavy use of JavaScipt much more effectively.

When you click on the 'Ajax Spider' tool a dialog will be displayed which allows you to start the ajax spider. You will not be able to ajax 

spider sites that are not in scope, but the dialog will detect that and give you the option to add the site to the scope.

The start dialog allows you to select either Firefox or Chrome. You will need to have these browsers installed in order to be able to use 

them. If you select the 'headless' option of either browser then they will be started in 'headless' mode so you will not see them running. 

This is usually the best option as this prevents new browsers from popping up on your screen. If you think the ajax spider is not handling 

your site correctly then try launching the non headless versions - that will allow you to see what the browsers are doing.

When the ajax spider is started the tool will only show you that it is running - it does not currently show how far it has progressed. As 

with the traditional spider you will be able to see all of the pages that the ajax spider has found via the Sites tree. If you click on the 

Ajax Spider tool while it is running then you will be given the option to stop it. You may well see alerts being raised after you start the 

ajax spider as ZAP passively scans all of the URLs it finds. 
## Active Scan
The 'Active Scan' tool attempts to find other vulnerabilities by using known attack vectors against the current site. As with the spider you 

can only run an active scan on sites that are in scope. It will attack all of the URLs that ZAP knows about for the site. These could have 

been discovered via manual browsing or the spider. It will not be able to attack any pages that it does not yet know about, so its best to 

explore a site thoroughly before starting the active scanner.

When started the icon changes to and, like the Spider tool, the Active Scan tool will show how far it has progressed and will allow you to 

stop it if you click on it again. It will also raise alerts, which you will be able to see via the alert notifications or any of the alert 

tools.
## Attack Mode
The 'Attack Mode' tool performs the same attacks as an Active Scan but works in a subtly different way.

Instead of attacking the URLs known at the time it is started, it attacks any URLs that are in scope as soon as they are discovered. It does 

not show any progress because it stays active with the icon until is is stopped.

This mode is especially useful for testing a sub section of a large site - when it is enabled it will only attack the in scope URLs that you 

visit as you explore them and will not attack any parts of the site that you do not use. So unlike the Active Scan, which you typically 

start after you have explored the site, it's usually better to enable the Attack Mode before you start exploring the site. 
Tool Configuration
You have control of which tools are shown and where in the side panels they appear.

To add a tool click on the green plus icon at the bottom of either of the side panels. You will be shown a list of all of the tools that are 

not currently visible. Select one of them for it to be added to the bottom of the relevant panel.

To remove one of the side panel tools, right click on it. You will be shown a dialog with the option to remove it from the panel along with 

any other options available for the tool.

You can move tools by removing them and re-adding them in the order you would like. We do plan to implement a drag and drop interface to 

make this easier! 



## HTML Report
The HTML Report tool shows the standard ZAP HTML report in a new window or tab (depending on your browser's configuration).

It is not shown by default so you will need to add it to a panel as described in the Tools Configuration tutorial page. 

HUD Configuration
The HUD configuration options are available via the gear icon near the bottom right of this page.

The options currently supported are:

Reset Configurations to Default: resets the HUD configuration including the layout of the tools
Take the HUD Tutorial: launches this tutorial again
Show the Changelog: shows a summary of the changes in this release of the HUD 

If either the HUD Tutorial or the Changelog have changed since you last looked at them then a red exclamation icon will be shown after them. 

The gear icon at the bottom of each page will also have the red exclamation icon overlayed on top of it . The exclamation icons will be 

removed once you have viewed the changes. 
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







