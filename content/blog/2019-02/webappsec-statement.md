---
title: "Webappsec Statement"
date: 2019-02-15T01:49:06+11:00
draft: true
---
## Web Application Security - Problem Statement

For submission on Friday 15-02-2019

### Current Problem Statement on WebAppSec

In Web Application Security, my goal is to learn how to identify common web vulnerabilities and develop a habit/mindset on checking for them first, so that I can do something akin to a process of elimination and work out what flaws and vulnerabilities that a website may have.

Currently, I still feel that I do not have a grasp on what to look for and haven't developed the habit or "muscle-memory" for discovering common web vulnerabilities. As such, I don't have a logical order of doing the basic steps to eliminate the potential likelihood that common vulnerabilities may exist.

In order to close this knowledge gap, my solution is to start off working on the Natas challenges till I reach the end (if possible) and potentially look at the other resources suggested (WebGoat, Web for Pentester, Shellter Labs and Root Me). In addition, I might try working on Hack The Box and Try Hack Me (Mr Robot), when I feel that I have the basics down and feel comfortable that my skill level can attempt it.


In Natas so far, I've went through a few levels and discovered a pattern of:

1. Checking the source code
2. Checking the robots.txt
3. Looking at the network activity
4. Checking the request headers

As documented in my "Natas Journey" blog post, there are a few web app vulnerabilities which were a result of misconfigurations, such as allowing Directory Traversal to an index of the parent directory, CSRF (Cross-Site Request Forgery) by editing the original HTTP GET requests and re-sending them and also human error/negligence such as Access Controls not being properly implemented.

In Natas 5 challenge, even if you're not logged in, just by changing the cookie, the website can be accessed. As a scenario, this can be potentially very dangerous as it bypasses the login completely. Therefore, you transition from an unauthenticated user to an authenticated user and can potentially gain access.

Hence, by applying my limited technical skills in cyber security can result in finding such flaws in the design if a website was to use a similar design as the one that I tested, it would be putting the website at risk. If a business was to run a website with such flaws, it can potentially cause severe financial and reputational loss.

An example of why this might be the case: Imagine if you were an online bank and a user transferred funds to an account on a public computer. Even if the user logged off the bank website, an individual with ill intent can go on the computer and edit the cookie (like in Natas Level 5) and change that one parameter and log-in as if they were the user and transfer the funds in the account elsewhere. If this was discovered, the online bank would most likely end up in the closure of the business since it would cause irreparable damage to the bank's reputation and immeasurable financial loss for compensating the customer, but also face legal action from a number of stakeholders that result in astronomical amounts of fines and penalties that would need to be paid out, causing an unsustainable business.

This type of scenario can be avoided by avoiding sensitive information being placed in cookies and validating all information placed in the cookies. In OWASP Top 10 Application Security Risks of 2017, Broken Authentication and Sensitive Data Exposure is the 2nd and 3rd most common risk that occurs, respectively. Therefore, it is highly important that cyber security is considered from the very first step, instead of the last step of the development process that still commonly occurs in the web development industry.

Consequently, I believe it is extremely important for me to develop the ability to detect common security vulnerabilities in websites since even the smallest errors can cause major problems and repercussions. 
