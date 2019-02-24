---
title: "Tryhackme Mr Robot Journey"
date: 2019-02-22T15:25:40+11:00
draft: true
---

## Tryhackme Mr Robot Journey

I attempted the Tryhackme Mr Robot Machine/CTF.

First off, I had to set up the network to deploy the Mr. Robot virtual machine.

I went to the access page and downloaded my configuration file and then downloaded the OpenVPN Source (in .zip file).

When I was following the commands given in INSTALL or README file:

* ./configure
* make
* make-install

During the ./configure command, it encountered errors.

configure: error: openssl check failed

I searched the error and found a stackoverflow article.

Ref: https://superuser.com/questions/371901/openssl-missing-during-configure-how-to-fix

I used the command suggested.

sudo apt-get install libssl-dev

However, even after installing that package, it still did not work.

Upon further inspection, the How to Connect? section, I saw that there was a difference between the general commands and the ones suggested.

Trying the other commands that were suggested. Replacing 'username' with the actual username.

sudo apt install openvpn
sudo openvpn username.ovpn

After entering those commands in, I successfully connected to the network.

Once I connected to the network, I deployed the machine to find the 3 keys.

I typed the ip address into the web browser and loaded the page up. At first I thought it was wrong, but after a second refresh of the page, I realised that the page was intentionally jet black for a reason.

I inspected the source code and started looking for vulnerabilities. There wasn't anything especially eye popping that showed any hints.

My first instinct was to check if robots.txt was configured correctly.

Going to my active machine's ip address followed by "/robots.txt", allowed me to find some hints.

There was 2 things listed:

* fsocity.dic
* key-1-of-3.txt

Navigating to the key-1-of-3.txt allowed me to get my first key for the challenge. I submitted that into the website and confirmed that it was correct.

Due to worrying about whether if was sufficient time for my connection, I added an extra hour.

Afterwards, I tried navigating to the second file fsocity.dic . It initiated a download for a C source code file. It was only a 6.9MB file, but due to slow network speeds with the vpn, it was estimated at a half an hour wait instead of a 2 second wait with the usual UTS network speeds. After reaching 1.8MB of the 6.9MB file, it failed to download. I tried it 2 more times, but I failed to download the file. Since the file could not be downloaded, I asked around the classroom to see if anyone else was attempting the same challenge and found out that Andy, one of my team members for my group project in the studio was attempting the same thing. So I asked to see if he could share the file with me and he was happy to do so. So I obtained the file through a temporary file share to not compromise the normal OS, leaving it only in Kali Linux OS.

After navigating back to the main ip address given, it has logged me into root@fsociety in a terminal.

It provided me with a few commands to use:

* prepare
* fsociety
* inform
* question
* wakeup
* join


After a few more attempts to operate with the website, it wouldn't load correctly.

Hence, I asked Darsh to see whether if there was a different way of going about it. Since there is a VM for Mr Robot, I was suggested to download the Mr Robot VM from Vulnhub and then reattempt it.

After downloading and loading the Mr Robot VM up, I started with a few commands that I learnt from the Deloitte Piper VM challenge.

ifconfig (check for ip address - inet)
nmap 192.168.92.128/24 (scan a subnet)

As a result of the nmap, I found a port 53 open for the domain on 192.168.92.2 .

nmap -sV 192.168.92.2

It did not find any service version with -sV flag.

When I was trying to get back to the same point for the robots.txt.

curl 192.168.92.2/robots.txt
curl http://192.168.92.2/robots.txt
curl 192.168.92.2:53/robots.txt

It didn't work. There was nothing to return. It was empty.

Hence, realising that there was no web due to no port 80 return on the nmap. I thought that there might have been something wrong with the network settings downloaded with the VM. When I checked it, it was Bridged, so I changed it to NAT and restarted the Mr Robot VM.

Afterwards I did another nmap and found the port 80 and port 443 open for 192.168.92.131 .

Afterwards, using curl again.

curl 192.168.92.131/robots.txt

I was able to succesfully return to seeing the robots.txt containing the two files: fsocity.dic and key-1-of-3.txt . This confirms that I was able to successfully connect to the Mr Robot VM.

Afterwards, I reattempt to get fsocity.dic file.
