---
layout: post
title: Mass Cracking Cybrary Accounts
description: "Many benign issues don't add up to be benign."
modified: 06-02-2019
tags: [cracking]
image:
  path: /images/featured/mass-cracking-cybrary-accounts.png
  feature: /featured/mass-cracking-cybrary-accounts.png
---

**TL;DR** Cybrary leaks usernames from multiple endpoints, has no restrictions on password strength, has xml-rpc enabled which makes it a good target for password spray attacks.
<!--more-->
I told Cybrary about this about 8 months ago and they said it's fine, I understand why they think it's not an issue. People don't care much about usernames because one still needs a password to access accounts. They are nice people tho, they offered me some in-site benefits for my efforts which I denied because courses suck ass, I am more of a white paper guy.

**Honest TL;DR** A 19 year old kid making a big deal out of wordpress misconfigurations and password policy of a famous website.

Enough tl;drs, now, let's get straight to the point.

### Enumerating Usernames
We will be using two endpoints to enumerate usernames,
- `/wp-json/wp/v2/users/` Lists users registered on the website
- `/wp-json/wp/v2/comments/` Lists comments made by users

Both these endpoints support two amazing arguments, `per_page` and `page`.
- `per_page` Number of results returned for one request (max 100)
- `page Page` number of the results (Just like google search results)

Wait a second, why are we using the `/comments` endpoint when we can enumerate usernames via `/users` endpoint?
Interestingly, Cybrary has only 11,500 users according to the `/users` endpoint. It's not possible to list the users after page #115. For the `/comments` endpoint, the last page is #221 which gives us 22,100 more usernames. Maybe these usernames are of people who create courses, I don't know.\
Considering the fact that a single user can make multiple comments and a username can appear in both type of results, let's say we can enumerate 15,000 usernames in total. That's just 1% of Cybrary's userbase. What about the rest of the users? Don't worry, I have one more trick ;)

`wordpress-website.com/?author=id`

The above endpoint is present in every wordpress installation unless the owner has manually configured his server to block requests to this endpoint with .htaccess or some WAF.
Start with replacing id with 0 and then 1, 2, 3, 4 and so on. The request will be redirected to author page of the corresponding id of following form

`wordpress-website.com/author/username`

So the rest of the users can be enumerated by this method. Now let's move on to the next step,

### Cracking Passwords
Brute-forcing is considered to be the last thing to try because it's not very efficient. You could spend days trying all combinations of length 10 while the actual password is of 11 characters. That's probably what Cybrary's security team thinks as well.\
Okay, here's a fun fact, Cybrary doesn't enforce any password policy. So yeah, it's possible to have a password of even 1 character, there's no restriction at all .I don't know what to say about this man, this is just ridiculous.\
Another fun fact, people are fucking dumb. 3–4% people are using 123456 as their password.
These 10 passwords were most used by people in 2018:

- 123456
- password
- 123456789
- 12345678
- 12345
- 111111
- 1234567
- sunshine
- qwerty
- iloveyou

Anyways, instead of attacking one user at a time, we will do something called a Password spray attack. It's nothing fancy, you just have to try a small amount of passwords on multiple accounts. Obviously we will use the most common passwords to get a better hit rate.\
Approximately 8% people use one of these top 19 most common passwords which means 8 out of 100 or let's say at least 5 for the sake of uncertainty. We have a good chance of cracking 5 accounts every 100 tries!\
One more thing, Cybrary also has the XML-RPC interface enabled which provides a minimal interface to log into wordpress website and much more. There's nothing special about it except how fast it is than the normal wordpress login because it's a lower level interface and returns way less data than the standard wordpress login. It is always located at the root of a wordpress installation (if enabled) in following form

`wordpress-website.com/xmlrpc.php`

### Step by Step guide

- Enumerate users and their unique IDs via /users and /comments endpoints
- Store the enumerated data in enumerated.json
- Enumerate users via ?author= endpoint while skipping the IDs present in enumerated.json
- Get your Top 10 password list
- Pick the first password and try it on all the accounts via the xml-rpc interface
- Do it for all the passwords.
- ?????
- Profit!

![69](/images/featured/mass-cracking-cybrary-accounts.png)

A dedicated hacker can try the Top 100 or Top 1000 to crack up to crack a larger number of accounts which will obviously require more resources. I hope the folks at Cybrary are reading this and they will fix the mentioned issues as soon as possible.

**Disclaimer:** I am not responsible for the shit you do with this information.
