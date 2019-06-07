# Vodafone-WiFi
Bash script to automatically connect/refresh connections to Vodafone-WiFi hotspots in italy. This script allows you to automatically login or refresh connections to Vodafone-WiFi hotspots which are free for users who have an internet subscription with vodafone and enable in their router the option to share their unused bandwidth through a secondary wifi hotspot that has the standard name "Vodafone-WiFi". When you allow to share your bandwidth, you get login credentials to connect to other people's hotspots. When you first connect to a Vodafone-WiFi hotspot your operating system detects it by trying to connect to a random website and should be redirected accordingly by the server on the router. For vodafone this happens by redirecting on the first http request to a page having the URL https://it.portal.vodafone-wifi.com/jcp/it?res=welcome with some parameters that are the mac address of the router "nasid" the router ip address "uamip" the router port "uamport" your device mac address "mac" and a random generated challenge. In case of any missing parameters or if they are wrong i found out that you get a 404 Not Found response even if the URL is correct. After getting the required parameters the url that does the login is the same as before but with res=login with the parameters attached plus your login info. In order to use this script you just need to setup the username, password and directory variables, the username and password need to have special characters url encoded (that is @ in the username is %40). You can find online tools that url encode your password if you search on google. More info: according to the places i have used this the vodafone station router gives a lease of 600 seconds or 5 minutes so you need to use some kind of watchdog to keep the wireless connection up (i use travelmate on openwrt), second you should run this as often as 5 minutes or 10 minutes (personally i run it every 5 minutes just in case). This script was written using ubuntu 18.04 and tested on it and openwrt 18.06.2, all you need is wget anda shell like bash or ash. This should work on any unix system with a shell and wget(not tested).