---
title: "Natas Journey"
date: 2019-02-13T18:04:57+11:00
draft: true
---
## Natas Journey

### Natas 0

Natas 0 presented a description stating "You can find the password for the next level on this page."

First instinct was to look in the source code for hints.

Found the password written in plain-text within HTML comment tags.

### Natas 1

Natas 1 presented a challenge with right-click being blocked. On Google Chrome, I used Developer Tools --> Inspect Element to circumvent the issue and checked the source code.

Found the password written in plain-text within HTML comment tags like the previous level.

### Natas 2

Natas 2 stated "There is nothing on this page."

Checked Source Code and found a random image source pointing to a path: "files/pixel.png".

Checked the pixel.png file and found nothing. So went directory traversing back up into the "files" directory and it listed the index, which revealed a users.txt file.

natas3 password was written in plain-text.

### Natas 3

Just like the previous challenge, Natas 3 stated "There is nothing on this page."

Within the Source Code, HTML Comments claim "...Not even Google will find it this time..."

Challenge Accepted!

{{< figure src="/img/natas/natas3-1.PNG">}}

Besides finding it directly using Google, if we check "robots.txt"...

{{< figure src="/img/natas/natas3-2.PNG">}}

It shows that there is a Disallow for a path to "/s3cr3t/".

Once we check natas3.natas.labs.overthewire.org/s3cr3t , there is an index of the directory which lists a file called "users.txt".

Upon accessing the file, natas4 password is listed in plain-text.

### Natas 4

Natas 4 presented the description "Access disallowed. You are visiting from ... while authorised users should come only from "http://natas5.natas.labs.overthewire.org/". Along with a refresh page link next to it.

Upon inspection of the Source Code, I found that the refresh page link was a reference to index.php.

However, trying to research how to compromise that proved unsuccessful.

I tried to test the different ways that I could utilise the refresh page link to make the website think that I was visiting from natas5. After looking at different areas around the site, I found myself looking at the network activity and tried to find a clue there.

Very later on, after looking at the headers and noticing that every single time I click the refresh page link, I find the "index.php" file request headers has a field called "referer". I wondered if changing that would let me imitate that I was accessing as an authorised user from natas5.

{{< figure src="/img/natas/natas4-1.PNG">}}

I searched up how to edit and resend a HTTP GET request on Google Chrome.

Resources that I found advised me that copy as fetch would allow the HTTP request to be sent from the Google Chrome Developer tools --> Console.

{{< figure src="/img/natas/natas4-2.PNG">}}

I did manage to successfully get a HTTP response back with a status code: 200 (OK), but the response had a list of parameters that were hidden and I tried to dig into each one until the end, but I couldn't find any answer that indicated the natas5 password.

Afterwards, I was advised to use the burp suite, but told it was an over-kill for the task at hand, so I googled and found that fiddler was a good alternative.

After looking at a few tutorials, I found out how to use the fiddler for sending HTTP GET requests and was able to find the natas5 password using the WebView feature on the HTTP response.

### Natas 5

Natas 5 presented the description "Access disallowed. You are not logged in".

Upon checking through Source Code all the way to checking the HTTP GET Requests. In the request header, the cookie shows "...loggedin=0".

{{< figure src="/img/natas/natas5-1.PNG">}}

What if we changed it to a 1 ?

Going back to fiddler, I made the adjustment "loggedin=1" and sent the HTTP GET request again and using the WebView feature on the HTTP response, the natas6 password is displayed.

### Natas 6

Natas 6 presented a text-label "Input secret:" followed by a text-box (text-field) and a submit button.

There was also a View sourcecode link, so pressing it displayed the actual source code of the website.

A include statement caught my eye and upon using the path "/includes/secret.inc", the secret was written in plain-text wrapped around by php tags.

Upon inserting the secret into the text-field, I received the natas7 password.

### Natas 7

Natas 7 presented 2 links to: Home & About.

These pages had descriptions that described it was a home page and about page.

The source code revealed a hint about the natas 8 password stored in the path: /etc/natas_webpass/natas8 .

{{< figure src="/img/natas/natas7-1.PNG">}}

What I found interesting was how the pages were being called from a filename, which lacked any sanitisation for the path to be manipulated.

{{< figure src="/img/natas/natas7-2.PNG">}}

Hence, attempting to insert the path where natas 8 passwsord was stored, resulted in successfully retrieving the password.
