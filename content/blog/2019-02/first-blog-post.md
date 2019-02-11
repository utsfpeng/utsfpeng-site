---
title: "First Blog Post"
date: 2019-02-06T15:23:18+11:00
draft: true
---

## My very first experience with Markdown

I have not had any prior experience with writing markdown, but this is my first attempt at doing so.

It seems to follow a logical structure and have very intuitive and common sense based formatting, so it almost feels like natural language based format when writing. However, there are still a few things that I am trying to confirm, such as code formatting especially when I'm writing actual sections or pieces of code on the website.

In addition, I was also advised that I can write pure html as well, it may come especially handy for iframes and also other embedded based html code. Furthermore, I am still getting accustomed to creating tables.

Plans for how I am going to construct this website for UTS MIDAS Summer Studio 2019.

* Home = Home page
* Blog = Reflections (Weekly Reflections, as part of the requirements for Cyber Security Studio) + SLOs (Addressing all the Subject Learning Outcomes for the studio)
* Portfolio = End of Studio Deliverable
* About = Brief Summary about myself and the website.

Going to try and learn python and learn how to use Kali Linux to explore cyber security concepts.

```python
s = "Python syntax highlighting"
print s
```

```Python
x = "Hello"
y = "World"
print(x + y) #print fn, will show "Hello World"
```

---

### Some notes on Hugo

| Steps | Instructions |
|:--------:| -------------------------------------------------------------------------------------------------- |
| **1** | Install Hugo using either a package manager or download a pre-built binary and set PATH to bin folder |
| **2** | https://gohugo.io/getting-started/installing |
| **3** | Run Command Line/Terminal and type in ```hugo version``` or ```hugo help``` to verify if hugo is properly installed |
| **4** | To create a new site type in the command: ```hugo new site site-name``` |
| **5** | Add a Theme from  https://themes.gohugo.io/ and then navigate to the site-name folder. Type in ```git init``` and ```git submodule add https://github.com/theme-author/theme-name.git themes/theme-name``` |
| **6** | Edit your config.toml configuration file and add the theme to equal the theme-name ```echo theme = "theme-name" >> config.toml``` |
| **7** | Adding content follows a certain structure, based on content types. For example ```hugo new content/posts/my-first-post.md``` is equivalent to creating to adding new content in the 'content' folder of type 'post' and the content is called 'my first post'. The content is written in *.md which means markdown. Markdown is a simplified version of writing html to quickly add text-based content to a static website generator. Some other static website generators that use markdown include HackMD (more towards note-taking), MkDocs, Jekyll, Hexo...etc. |
| **8** | Optional: You can also define the type in the 'front matter' section at the start of your *.md file. It would look something like ```+++ ... type = "blog" ... +++``` |
| **9** | Open up the *.md file to write your content inside. It is in your 'site-folder/content/...*.md' If you do not know markdown, here's a cheatsheet: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lines |
| **10** | Once you have finished writing your content, you can check your website locally, using the command: ```hugo server -D```. The flag '-D' enables drafts. Once you have run the command, your site could be accessed with the web address: http://localhost:1313/ , which is just your normal localhost (127.0.0.0) with port 1313 |
| **11** | Once you have your theme loaded on and have it up and running with the basics, you can customise and tweak it to your own liking in the file: 'config.toml'. Some changes that you can make include things such as: baseURL, languageCode, title...etc. |
| **12** | Cool beans! Hugo in a nutshell! |

P.S. If you would like to further customise content sections, you can check out: https://gohugo.io/content-management/sections/
