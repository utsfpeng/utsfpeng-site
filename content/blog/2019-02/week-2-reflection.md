---
title: "Week 2 Reflection"
date: 2019-02-17T21:18:55+11:00
draft: true
---

## Week 2 - Reflection (Sprint 2)

In the Cyber Security Summer Studio this week, our primary focus was on Web Application Security.

Firstly, we started off with a Scrum meeting around the room for each studio member on what we worked on, what we want to work on and our current obstacles. It was very interesting to find some studio members going above and beyond and have acquired such great amounts of experience in such a short period of time. Personally, I was working on Natas and wanted to finish Natas off and move onto the other resources that the studio facilitators (Larry, Darsh, Luke) have provided us with. My current obstacles were mainly technical issues with a bit of a time management issue. However, I hope to improve that moving forward by doing more research and also organising my time better with my schedule on my calendar and prioritisation. (SLO 4 + SLO 5)

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

Luke, one of our studio facilitators, gave a really good talk on the mindset involved in becoming a Cyber Security professional and the pursuit down the Cyber Security industry career path. He spoke about the ethical mindset that we should have when it comes to our objective that we want to achieve and also maintaining a certain attitude towards hacking. As ethical hackers, we are trying to identify security vulnerabilities but agree to work around the restrictions placed on us to not disrupt the target victim of our attacks and experimentation/testing that we perform. There is no such thing as an un-hackable/unexploitable system. When it comes to Cyber Security, it is not a matter of whether if it'll happen or not, but when will it happen and being as prepared for it as we can for a security vulnerability to occur or be taken advantage of. We were taught how we should look for exploits, in regards to following examples and recognising patterns by experience. It is a mix of time, patience and paranoia, with an unwavering side of curiosity and genuine interest in finding out how things work, done to the very core.

To acquire skills in the Cyber Security industry is quite difficult and we may have an adrenaline to try the things that we learn out on real-world situations. However, it comes back down to that mindset and attitude that we maintain towards doing things in the right place and time with consent and permission which makes all the difference. Luke and the other studio facilitators (Larry and Darsh) have recommended different avenues to build our skills and techniques. However, within this 4 week studio, it is quite tough to find enough time to do all of them. 

Researching on responsible disclosure, bug bounty programs and pondering about the thought of ethical hacking has allowed me to reflect on why I want to pursue a career in Cyber Security in greater depth.

The answer that I've come to choose for now is that I want to make a positive impact and ensure that my loved ones who use their usual daily services and infrastructure to be securely protected and not become a victim of a security vulnerability. In addition, I believe that the Cyber Security industry is a career path that I want to take since I love a good challenge and I love the thrill of researching and using my forte of breaking things for enhancing and improving the overall security of IT systems and services. I love the constant change and being able to work without a dull day where it is always the same thing would definitely be a dream job of mine. (SLO 5)

Afterwards, in our second session on Wednesday, we did something a bit different. We had a "free-for-all" which was a bit of a contrast to our usual Scrum meetings in the way that we were forced to go out of our comfort zone by our studio facilitators to interact with other studio members that we have had less to no interaction with, so we can become closer and more comfortable with each other. In an industry like Cyber Security, it is extremely important that we are comfortable with our colleagues and team members and feel comfortable in our learning environment since we are generally exposed to such sensitive and strict policies and code of conduct that it makes it very formal and restrictive that we may sometimes feel a bit uncomfortable. Hence, this activity really helped us to really get out and get comfortable with others around us and our environment since it will allow us to ask questions from each other a lot more easier. I did try and speak with someone that I spoke less with, but I feel that the room layout was a contributing factor to why it may not have worked as great as it could have due to some people sitting near the wall on the sides that made it feel sectioned off and hard to interact with, due to the physical barriers of chairs and monitors blocking off our view to reach out and interact without feeling a bit intimidated or feel that I am interrupting something. However, overall I was still very satisfied with the activity that encourages us to get out of our comfort zone and speak up, since I'm naturally a more shy and introverted person and I used to have a fear of social interactions (social anxiety). I recognise that this is something that I need to work on and transitioning into the workforce, I will need to become more open and outgoing to communicate efficiently and effectively with my peers and others around me.

I am looking forward to more industry representatives coming into our studio to speak and present since they have valuable experience and skills that they share in their talks and it makes me feel inspired and more motivated to pursue despite all the considerably difficult barriers to entering the Cyber Security industry. The industry itself is not as clear cut as other as other career paths since there isn't any defined way of reaching it, as everyone has their own story about how they entered into the industry. For example, our interaction with an industry representative last week, Robert Mitchell from Gitlab security gave us a real interesting perspective of how he almost accidentally went into the industry by mistake and took a liking to it, eventually. In addition, his experience with the beginning and rise of the Cyber Security industry was an extremely insightful perspective that I could not imagine before his presentation. I hope to learn from more industry professionals in the upcoming future that Larry and Darsh have planned. We were informed about topics of web pen-testing, red teaming and reverse engineering were coming up soon, with possibly the industry representatives that would be coming to our studio. As a student, I am really excited by the prospect of being able to meet and interact with these people and hear about their personal journey in Cyber Security.





References:

* OWASP 2018, Cross-Site Request Forgery (CSRF), OWASP, viewed 11 February 2019, <https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)>.
* OWASP 2018, Cross-site Scripting (XSS), OWASP, viewed 11 February 2018, <https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)>.
* OWASP 2015, DOM Based XSS, OWASP, viewed 11 February 2019, <https://www.owasp.org/index.php/DOM_Based_XSS>.
* OWASP 2015, Testing for Reflected Cross site scripting (OTG-INPVAL-001), OWASP, viewed 11 February 2018, <https://www.owasp.org/index.php/Testing_for_Reflected_Cross_site_scripting_(OTG-INPVAL-001)>.
