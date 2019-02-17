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

Responsible Disclosure Programs are a security vulnerability disclosure model that allows security researchers or individuals who have discovered a vulnerability to notify the affected organisation/individual without any legal repercussions under a policy that protects the vulnerability reporter.

Many organisations have participated as a way to prevent security vulnerabilities to be exposed to the public by individuals for criminals to take advantage. Instead, it allows individuals to notify the affected organisation privately to allow time for the issue to be fixed/patched before it is disclosed to the public. Many high-profile organisations have responsible disclosure policies set in place to allow security vulnerability to be disclosed to them without legal repercussions, some of these organisations include:

* CERT Australia (https://www.cert.gov.au/critical-infrastructure-big-business/report-incident/vulnerability-disclosure-policy)
* Australia Post (https://auspost.com.au/about-us/about-our-site/responsible-disclosure)
* Ikea (https://www.ikea.com/au/en/responsible-disclosure/index.html)
* MYOB (https://www.myob.com/au/about/security/report-security-vulnerability)

Bug bounty programs are an incentivised responsible disclosure program that provides monetary benefits for security researchers that find security vulnerabilities and formally report it through a bug bounty program under the pretense that they would provide a write-up that allows the vulnerability to be replicated/reproduced, so that the affected organisation can fix it privately before releasing it publicly (if consent is given).

In regards to ethical hacking, it is a concept that identifies that not everyone who finds a security vulnerability is a black-hat hacker who would use it for a malicious purpose. In fact, most security vulnerabilities nowadays are discovered by accident and not on purpose, it is people who want to actually do good to disclose such security vulnerabilities to the affected organisations as part of their feeling of social responsibility to ensure that it is fixed and remains more secure for others.

It is the mindset that differentiates ethical and unethical hacking.

Ethical hackers seek to improve and enhance the security for the greater good while on the other hand, unethical hackers seek to either cause damage or benefit from security vulnerabilities and weak security.

Researching on responsible disclosure, bug bounty programs and pondering about the thought of ethical hacking has allowed me to reflect on why I want to pursue a career in Cyber Security in greater depth.

The answer that I've come to choose for now is that I want to make a positive impact and ensure that my loved ones who use their usual daily services and infrastructure to be securely protected and not become a victim of a security vulnerability. In addition, I believe that the Cyber Security industry is a career path that I want to take since I love a good challenge and I love the thrill of researching and using my forte of breaking things for enhancing and improving the overall security of IT systems and services. I love the constant change and being able to work without a dull day where it is always the same thing would definitely be a dream job of mine. (SLO 5)



References:

* OWASP 2018, Cross-Site Request Forgery (CSRF), OWASP, viewed 11 February 2019, <https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)>.
* OWASP 2018, Cross-site Scripting (XSS), OWASP, viewed 11 February 2018, <https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)>.
* OWASP 2015, DOM Based XSS, OWASP, viewed 11 February 2019, <https://www.owasp.org/index.php/DOM_Based_XSS>.
* OWASP 2015, Testing for Reflected Cross site scripting (OTG-INPVAL-001), OWASP, viewed 11 February 2018, <https://www.owasp.org/index.php/Testing_for_Reflected_Cross_site_scripting_(OTG-INPVAL-001)>.
