---
layout: post
title: Cracking eAadhar password in 2 seconds with Maths
description: "Reducing cracking time from 92 to 2 seconds with maths."
modified: 25-10-2018
tags: [somdev sangwan, d3v, s0md3v, somdev]
image:
  path: /images/featured/aadhar.png
  feature: /featured/aadhar.png
---

This article is already kind of lengthy so let’s get straight to the point.

Every eAadhar letter is locked with a password which is a fixed string of following schema:

```
first_four_letters_of_name_in_uppercase + year_of_birth
```

<!--more-->

Basically there are 4 uppercase alphabets & 4 digits involved. So how many combinations can be generated from 4 uppercase alphabets and 4 digits? The answer is 2821109907456 and it would take 90 years to crack the password if we try 1000 combinations per second.

Ain’t nobody got time for that!

## Time for some maths & shit!

Opps! We just made a mistake here, we don’t have to calculate all the combinations because the password is in this form:

|([A-Z][A-Z][A-Z][A-Z])|([0–9][0–9][0–9][0–9])|
|---|---|
|(4 uppercase letters)  |    (4 digits)|
|       (Group 1)        |    (Group 2)|

The alphabets are in a group and lie before the digits which are also grouped so there’s no possibility that they can be mixed to form a combination like S2N65GE1 . So how many combinations are possible after considering that?

Lets calculate the number of combinations of 4 letters which can be formed by 10 digits i.e. 0-9 :

`(10)⁴ = 10000`
So there will be 10000 possible combinations. Great! Now lets calculate the same for alphabets.

`(26)⁴ = 456976`
And all the combinations of 10000 digit and 456976 alphabets combinations will be:

`456976 * 10000 = 4569760000`
And if we try 1000 combinations in 1 second we will need this much of time

```
4569760000 / 1000 = 4569760 seconds
or
52 days 21 hours 22 minutes and 40 seconds
```
Yay! We just decreased the time required from 92 years to 53 days!
The change is orgasmic but it’s still too much. What else can be done?

Here’s the catch, these are just not 4 alphabets and 4 digits, these are first letters of the name & year of birth of someone.

A human can live up to 100 years which means someone born in 1642 can’t be alive and hence can’t have an Aadhar card.
Time traveling is also impossible at the moment which means someone who is going to be born in 2594 can’t travel back to the time to get an Aadhar card.

So the combinations ranging from 0000–9999 aren’t valid. We just need the 1918–2018 range which covers humans of age 0 to 100.

So now the number of combinations and time required is:

```
456976 * 100 = 45697600 combinations
45697600 / 1000 = 45697.6 seconds
or
12 hours 41 minutes 37 seconds
```

That’s some really nice progress! It’s still too much tho. Can we go any lower than that? Yes we can but we will lose some of the accuracy but that doesn’t matter when you have to crack a lot of password and it’s actually better, you will read about it in the end.

Just like all the combinations of digits weren’t valid years of birth, similarly AAAA or PZVS aren’t valid four first for letters of an indian name.

So what would an attacker do? Well here’s what I did:

![photon](https://cdn-images-1.medium.com/max/800/1*EDcgFM7F2TH8PbClDEpqIQ.png)

I used my Photon to scrape names from a website which was basically a directory of Indian names and I found 3283 unique names! I used the following command to extract the first 4 letters and filtering out the duplicates

```bash
grep -oP ”^\w{4}” custom.txt | sort | uniq | dd conv=ucase
```

![sort](https://cdn-images-1.medium.com/max/800/1*PkZFVBnjIcnqKLawKjMSqg.png)

These are 1598 entries! There were many duplicates, for example the first four letters in the names Sanjeev & Sanjit are same.

> Are you thinking that 1598 prefixes are too low for a population of 1.6 billion? Yep, that’s kinda of true but these are not names, these are prefixes! The wordlist can be found here, feel free to search first four letters of your name in it and most likely you will get a match. If I had proper time, I would have scraped around 10000 names from different websites and I think that would make 3000 unique prefixes. But let’s consider it 1598 for now.

Anyway, let’s calculate the time required now

```
1598 * 100 = 159800 combinations
159800 / 1000 = 159.8 seconds
or
2 minutes 39.8 seconds
```

Hell yeah! Now what? The article promises that we can further reduce this time to 2 seconds but how?

First of all,2 minutes and 39.8 seconds is the time required to try all the combinations at a rate of 1000 combinations / second. But what if the 11th combination matches the password? or the last one? or the first?

So if we can somehow alter the probability of matching a password early in the combination list that would drastically reduce the required time.

Let’s use some facts for that!

According to this wikipedia entry

> India has more than 50% of its population below the age of 25 and more than 65% below the age of 35.

So instead of creating combinations with age 01–100, a smart move would be to try this:

```
25 - 01 (reversed because young ones are not likely to have an aadhar card)
25 - 35
36 - 100
```

So if we take the age statistics into account, the chance of matching the correct password in first `1598 * 25 = 39950` combinations is 50% which means we will crack half of the passwords in `39950 / 1000 = 39.95` seconds! And in the next `(1598 * 10) / 1000 = 15.8` seconds , we will have %15 more passwords! So basically we will have 65% of the passwords in 55.9 seconds . We have come a really long way!

Can we go any lower? Yes we can!

I have a list of 100 most popular Indian names and that’s just a google search away. So I can put those names earlier in the list and boost the probability of matching the password earlier.

You know what? 80% of India’s population is Hindu so if we put Hindu names earlier in the list then we will be able to crack 80% of the passwords without even trying the rest 20%.

So how much time did we managed to decrease with this approach overall? Let’s analyze!

We are using 100 most popular names earlier in the list, what that means? Let’s say India’s 15% population uses these names. I personally believe the percentage is more than that but let’s stay on the safe side. Well so we will be able to crack 15% passwords right away! And for 80% of the rest 85% names (100% - 15%) will be hindu names so that means we will be able to crack around 79% (considering 1% popular names aren’t hindu) names in the next 65% tries!

I am sorry! I forgot about the age thing? Let’s consider everything and try to calculate the time required to crack passwords of 100 people.

Lets divide them into groups first!

```
100 : Total People {
    50 : People 00-25yo{
        7 : People with popular name,
        43 : People without popular name {
            34 : Hindus,
            9 : Non-Hindus
            }
        }
    }
    15 : People 00-25yo{
        3 : People with popular name,
        13* : People without popular name {
            10 : Hindus,
            3 : Non-Hindus
            }
        }
    }
    45 : People 35-100yo{
        7 : People with popular name,
        38 : People without popular name {
            30 : Hindus,
            8 : Non-Hindus
            }
        }
    }
}
```
Now let’s create an algorithm to effectively crack passwords

![algorithm](https://cdn-images-1.medium.com/max/800/1*P2OgbzUtZS-02hXPl6JgvA.jpeg)

The numbers in red represent the priority of search space. For example, the combinations for people lying in group 1 will be tried first, then 2, then 3 and so on.

How much time it’s gonna take to crack passwords for all of them?

Instead of trying different combinations for a password. We will use sets of passwords suggested by the algorithm one by one on all passwords.

```
Phase #1

1 = 11 seconds for cracking 7 passwords
2 = 3 seconds for cracking 3 passwords
3 = 11 seconds for cracking 7 passwords

We have cracked password for 17 people so far, 83 people left.
Now remove all these combinations from the combination list and
try next set of combinations i.e. combinations for 4, 5 and 6.

Phase #2

4 = 54 seconds for cracking 34 passwords
5 = 16 seconds for cracking 10 passwords
6 = 47 seconds for cracking 30 passwords

Phase #3 (after deleting combinations for previous phase)

7 = 14 seconds for cracking 9 passwords
8 = 5 seconds for cracking 3 passwords
9 = 12 seconds for cracking 8 passwords

Total time taken: 11 + 3 + 11 + 54 + 16 + 47 + 14 + 5 + 12 = 173 seconds i.e. 2 minutes 13 seconds
Total passwords cracked: 100
Average time per password: 173/100 = 1.73 seconds
From 92.27 years to 1.73 seconds, it was an amazing journey. Wasn’t it?
```

## FAQ

### How would one get the PDF file in the first place?
A lot of PDF files have been indexed by search engines due to improper configuration of servers and hence are just a google search away!

Anyways, such critical information is supposed to kept safe in the server. For example, passwords are kept in hashed form so they are safe even when an attacker manages to get into the server but these PDF files can be cracked easily as I have described in my article.

### Don’t you think this much of estimation will cost you some accuracy?
Yep it surely will but a group of 10 lakh people doesn’t matter when you have 1.3 billion aadhar cards to crack.
