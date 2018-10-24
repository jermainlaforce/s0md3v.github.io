---
layout: post
title: How I became a hacker and more...
description: "How I became a hacker and more..."
modified: 25-10-2018
tags: [somdev sangwan, d3v, s0md3v, somdev]
image:
  path: /images/featured/journey.png
  feature: journey.png
---

I don’t want to make it any longer by adding some introductory part so lets get straight to the point. Okay wait, I just want to tell you something, I am a noob. Let’s go now!

## Getting into infosec

So I am 19 years old at present and I was living a pretty boring life till the age of 15.

Then I got a computer, I “wasted” more than one year in playing games & social media which I kind of regret.

But one day, I decided to have some fun and I searched on google “How to hack facebook account” and I followed one of them which was about Phishing.

I created a phishing page after struggling for an hour and posted it on facebook with the caption, “This app lets you see who views your profile secretly” and about 5 people fell into that trap.

“Damn! This shit is lit”, I said to myself. When you do something new and it goes well, you  get excited about the possibilities and the same thing happened with me.

After this incident, I joined some facebook groups related to hacking bur they were full of spam.

I was very eager to learn hacking so I created my own group named “Ultimate Hackers” which I know sounds really very cringy. I started inviting people to join it whom I think had good knowledge.

One month passed and now I was aware of the very basics concepts like phishing, keylogging, RATs etc. I wanted to learn but I wasn’t sure “what” to learn and then I saw two guys arguing about something on a thread. They were using terms that I had never heard so what I did was that I noted down all those terms in a notebook. I picked one of those terms and searched about it on google and started reading about it but then there was other terms that I didn’t knew.

An idea came into my mind, I wrote down those terms as well and picked one of them to read about it and again noted down things I didn’t understand. I was learning a lot of new stuff this way and this time it was happening really fast because of the recursive nature of this methodology.

At the end of the day, I used to post what I learnt in my facebook group in my own words which people liked very much and the group started to grow very fast.

Apart from my inner desire, now there were people who supported me and asked me to write on various topics. Everyone wants to get appreciated for what they do, its basic human nature. Appreciation makes you work harder to satisfy expectations and the same thing happened with me.

I met some other genuine people and we became a team, “Team Ultimate” which I don’t think is a cringy name at all.

Anyways, everything was going extremely well, I started to explore web apps hacking but then something happened which changed my life, in a good way.

Well I was wandering around github and I found a XSS scanner written in python named XSSYA . I liked it, big ass banner & ability to retrieve PHPSESSID without even executing the payload . Yep, I know that’s the most autistic thing ever but I didn’t know much at that time so I thought its cool and I downloaded it.

But when I ran it, it threw some errors and I fixed them without any programming knowledge, thanks to stackoverflow and common sense.

So it was working now and I thought its open source and its license says anyone can modify and redistribute it so I changed the banner and the author name *self-facepalm*.

Somehow I managed to integrate it with another program named Damn Small XSS Scanner .

The final script was working fine and I was proud of this little achievement of mine so I created a github account and uploaded it.

I had no idea how but a website featured it and the original author of the tool found out that I am using his code. He opened an issue on github and told me that I am a fake guy and people saw that and some of them called me a script kiddie and a “copy-paster”.

You know that the smallest* unit of matter is an atom right? Take one electron out of it and split it into thousand parts and take one part of them and that’s the size of my ego and it got hurt :v

## A new start
My condition was like a injured lion *coughs* maybe that’s too much, a cheetah maybe? I just wanted to take off that weight off my chest and there was just one way to do it, learning XSS and python.

How I learned Python?

The best way to learn a programming language is to code in it. No book, youtube niggas or $99 courses can teach you programming, just fucking start writing code. Of course you need resources to learn from so here’s what I did to learn python

“ Learn python the hard way ” [Book]
This book is really good for getting started with python.
Codecademy [Online interactive course]. It gave me a glimpse of real world programming problems.
By modifying other’s tools (without putting them on github this time :p ). This part helped me the most, I learned a loooooot. I learned about different libraries and the way developers solved a particular problem and what not.
By writing my own tools from the scratch. Please don’t look at the source code of ReconDog because it was my first program that I wrote from the scratch
How I learned XSS?

Random Blogs (10%)
brutelogic.com.br (15%)
XSS Challenges (10%)
Looking at payloads & figuring out how they work (25%)
Learning HTML, Regex & JS + Experimenting (40%)
However my ego was somewhat satisfied but I didn’t stop after it, I kept learning new attacks and techniques. I learned new programming languages. I also started to explore OSINT, GeoINT & SE.

Let’s stop it right there and talk about some of my noobie achievements.

I have done stuff
Yep, that’s my only achievement so far. No hall of fame from beg *coughs* *under the breath: why do I say such controversial stuff* so I was saying I don’t have any hall of fames from bug bounties, no certification etc.

Btw the stuff I have done includes around 30 programs I have contributed to the community. Thanks for loving them, you made #1 python Github developer in India and #78 worldwide.

Six of them have been featured in Black Arch & others have been featured in some respected blogs & websites like hakin9 magazine, shodan, penetester academy, kitploit and 69 others :grinning:

I do security research. A good example of my work is Entropy, a WAF core prototype which is driven by mathematical algorithms. I will turn it in a fully working WAF once I have enough free time.

I am not a bug hunter but I have helped a lot of organizations to fix flaws in their websites without asking for a t-shirt :wink:

I have written 100+ articles on this blog i.e.teamultimate.in.

## Tips & Resource
Here are some pro *coughs* noob tips from my side:

- Note down & google unknown terms, recursively.
- Read the same thing from 5 different articles. When you read a blog, you learn what the writer knows but reading the same thing from 5 different articles lets you see the topic in consideration from different sides.
- When you are trying to learn a new programming language with the help of a video course or a book, you must write programs in it otherwise you won’t grasp anything. Programming is about innovation and problem solving.
- I have a request to all the beginners out there, please don’t get into bug bounty. If you are doing hacking for t-shirts or money, you are doing it wrong. Okay, do whatever you want to but please don’t call yourself a “security researcher”. Okay, do whatever the fuck you want but please don’t spam my facebook, linkedin and twitter with a….never mind, lets move on to the next one.
- Learn Regular Expressions. It is an amazing skill to have and it will make you better at various unix operations, bypassing security filters and will help you solve a lot of programming problems.
- Start a blog! Writing articles helps you question your knowledge. Some people will read it and will appreciate your work, it will make you feel better. Some will point out your mistakes or things you missed, it will make you better. So it’s a win-win deal!
- When you get trolled or humiliated for something, you always have two options. First one is to stay where you are and crush your self respect. The second one is to take it as a challenge, work hard and be better than the people who trolled you. I got trolled for Python and XSS right? Look at me now, I wrote XSStrike which is an XSS detection suite written in python. XSStrike is the best tool in its category and also has the most number of stars. And it will stay at the top unless someone’s ego gets hurt :wink:
- Blogs, documentations, white papers, presentations and slides are better than any hacking courses or books.
- Twitter is an awesome source for good reads and latest infosec related events. You can some of the good people in my following list .
Resources
I don’t believe in reinventing the wheel so instead of providing you a huge ass list of stuff I am leaving links which have huge ass lists of stuff :grinning:

https://github.com/Hack-with-Github/Awesome-Hacking \
https://github.com/EdOverflow/bugbounty-cheatsheet \
https://github.com/hardikvasa/awesome-programming \
https://github.com/sindresorhus/awesome \
https://github.com/s0md3v/AwesomeXSS \
https://github.com/jekil/awesome-hacking \
https://github.com/vitalysim/Awesome-Hacking-Resources \
https://teamultimate.in/ultimate-books

That’s all for now
Keep making & breaking things!
