---
type: post
title: CORS, SOP & crossdomain.xml For Dummies
description: Cross Origin Resource Sharing & Same Origin Policy explained.
modified: 27-10-2018
tags: [cors, sop, basics, concept]
image:
    path: /images/featured/sop-cors-crossdomain.png
    feature: /featured/sop-cors-crossdomain.png
---

Things were really simple when webpages were static. Write some text, add images, add links and serve it to your users.<br>
Then JavaScript came into existence and it made webpages dynamic.
<!--more-->
Now webpages had animations, cool drop down menus and shit, now they could even make request to some other webpage without user interaction.
Yeah that's fun but then some smart ass guy thought what if we use JavaScript on bad.com to steal data from good.com where user is logged in.
Now you know where that "Cross" in Cross Site Scripting came from.

## Same Origin Policy

Well then some other smart ass proposed that we should setup a restriction on these cross domain requests on the browser level.
He said we will call it Same Origin Policy and it won't let JavaScript make request to a webpage which isn't hosted on the same domain.
Here's how it works

**moth.example.com**: Ayy bruh! Can I fetch `light.json` from `lamp.example.com` real quick?<br>
**Browser**:

![we don't do that here meme](https://i.redd.it/zw17doei2h211.jpg)

Now lets see which pages can be accessed by `https://moth.example.com/moth.html`

|Resource|Result|Reason|
|--------|------|------|
|https://moth.example.com/dir/moth.html|<span style="color: #2ecc71">Successs</span>|Same Host, Port, Protocol|
|https://bad.com/moth.html|<span style="color: #e74c3c">Failure</span>|Different Host|
|https://sub.example.com/dir/moth.html|<span style="color: #e74c3c">Failure</span>|Different Host|
|http://moth.example.com/dir/moth.html|<span style="color: #e74c3c">Failure</span>|Different Protocol|
|https://mothexample.com:80/dir/moth.html|<span style="color: #e74c3c">Failure</span>|Different Port|

## Cross Origin Resource Sharing

Things were secure again but it raised a problem, a big one. This restriction was applied to stop bad guys for making cross domain requests but it was no longer possible to make requests from `goodBoy.example.com` to `goodGirl.example.com`.<br>
To make things good again, they introduced something called Cross Origin Resource Sharing. The idea was simple, let developers choose whom they want to share their resources with. If the developers wants share data between `goodBoy.example.com` and `goodGirl.example.com`, let him do so.<br>
For this purpose, he will need to setup a new header on `goodGirl.example.com` as follows:

`Access-Control-Allow-Origin: goodBoy.example.com`

That's it!

### How CORS works?

Step 1. You visit `goodBoy.example.com` in your browser<br>
Step 2. The website tries to load data from `goodGirl.example.com`<br>
Step 3. Your browser makes a request to `goodGirl.example.com`<br>
Step 4. `goodGirl.example.com` returns the response including the following HTTP header:<br>

`Access-Control-Allow-Origin: goodBoy.example.com, money.example.com, bigDick.example.com`

Step 5. Browser checks if `goodBoy.example.com` is in the allowed domains list<br>
Step 6. Yes it is in that list, the response now can be used by the JavaScript<br>

## crossdomain.xml

Unfortunately, JavaScript isn't the only technology which needs to make cross domain requests within a browser.
There are some web clients such as adobe flash which need to do the same.

A guy suggested to standardize another header with the name<br>
`Allow-All-The-Web-Client-Requests-From-These-Domains:`<br>
He was beaten up by asian because the header name was too long ;)

Well, instead of using a seperate header this time, they decide to use a file named `crossdomain.xml` which should be located in root of the host just like `robots.txt`

Here's `https://facebook.com/crossdomain.xml` for example:

```xml
<?xml version="1.0"?>
<!DOCTYPE cross-domain-policy SYSTEM "http://www.adobe.com/xml/dtds/cross-domain-policy.dtd">
<cross-domain-policy>
	<site-control permitted-cross-domain-policies="master-only" />
	<allow-access-from domain="static.xx.fbcdn.net" />
	<allow-access-from domain="static.connectproject.org" />
	<allow-access-from domain="static.whatsapp.net" />
	<allow-access-from domain="static.0.facebook.com" />
	<allow-access-from domain="static-0.facebook.com" />
	<allow-access-from domain="z-1-static.xx.fbcdn.net" />
	<allow-access-from domain="z-m-static.xx.fbcdn.net" />
	<allow-access-from domain="z-p3-static.xx.fbcdn.net" />
	<allow-access-from domain="z-p4-static.xx.fbcdn.net" />
	<allow-access-from domain="static.facebook.com" />
	<allow-access-from domain="static.xx.fbcdn23dssr3jqnq.testonion" />
	<allow-access-from domain="static.xx.fbcdn23dssr3jqnq.onion" />
	<allow-access-from domain="xwf-static.xx.fbcdn.net" />
</cross-domain-policy>
```

It's similar to the `Access-Control-Allow-Origin`, when a web client is running in your browser and it tries to make request to some another domain,
your browser checks if that domain's `crossdomain.xml` specification allows that.

So yeah, that's pretty much it.<br>
Also, Marvel is better than DC.
