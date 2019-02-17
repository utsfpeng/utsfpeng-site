---
title: "Week 2 Reflection"
date: 2019-02-17T21:18:55+11:00
draft: true
---

## Week 2 - Reflection (Sprint 2)

In the Cyber Security Summer Studio this week, our primary focus was on Web Application Security.

We were introduced to some of the most common web application security vulnerabilities that currently exist, which include: CSRF (Cross Site Request Forgery), XSS (Cross Site Scripting) and SQLi (Structured Query Language Injection).

CSRF is an attack that forces the user to perform an unwanted action and generally uses state-changing requests since it requires tricking a victim to click on a link or execute an action on behalf of the attacker while the user is authenticated. Since the user is already authenticated with their credentials on the site with their session cookie, it would try and make the user do actions such as changing a password or performing a transaction without the user's knowledge.

XSS has 3 main types: Stored, Reflected and DOM.

Stored XSS is when a malicious scripts are injected into a website, such as when you post a forum post with a script, but the forum posting feature allows any user input and it does not escape, sanitise or validate user input. Every new visitor of that forum would be attacked by that malicious script.

Reflected XSS is when an injected script is reflected off the server such as an error message prompt or search result or any other type of response that includes some or all of the input in its response. It only impacts users who open a malicious link or 3rd party webpage. However, it is non-persistent, so upon refreshing multiple times, it would not affect them since it is based on a single HTTP response.

DOM XSS is when the attack payload is executed as a result of modifying the DOM (Document Object Model) environment used by the original client.

SQLi is a type of code injection using SQL Statements placed into user input fields which are unsanitised, can cause it to spit out information and data stored in the databases that are behind web apps.

We were also tasked with researching responsible disclosure programs and bug bounty programs and the significance of ethical hacking and its importance.



References:

* OWASP 2018, Cross-Site Request Forgery (CSRF), OWASP, viewed 11 February 2019, <https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)>.
* OWASP 2018, Cross-site Scripting (XSS), OWASP, viewed 11 February 2018, <https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)>.
* OWASP 2015, DOM Based XSS, OWASP, viewed 11 February 2019, <https://www.owasp.org/index.php/DOM_Based_XSS>.
* OWASP 2015, Testing for Reflected Cross site scripting (OTG-INPVAL-001), OWASP, viewed 11 February 2018, <https://www.owasp.org/index.php/Testing_for_Reflected_Cross_site_scripting_(OTG-INPVAL-001)>.
