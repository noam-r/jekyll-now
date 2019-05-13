---
layout: post_page
title: How to fake a source of a Tweet
description: 
---

{:.english}
Twitter doesn’t provide a whole lot of metadata on users or tweets, likely for privacy and commercial reasons. This means that everything it *does* provide is important for the analysis of non-human behavior by varied entities - commercial, academic, and governmental.

{:refdef: style="text-align: center;"}
![twitter fake](/img/2019-05-13-1.png)
{: refdef}

{:.english}
**Tweet Source as an Indicator**

{:.english}
One of the best, unequivocal indicators of a user’s "authenticity" is their tweet source, namely, what service or application was used to generate it. A third-party app, which allows easy automation of tweets via the API, is a strong indicator that something fishy might be going on; a group of accounts all using the same distinct source and working in tandem may indicate the existence of a bot network; and, combined with other indicators, increases the probability that we’re not dealing with a so called “normal”, or “organic”, user. However, if the user tweets from an “official” app, be it Twitter’s own app or one by a respectable vendor,  it’s harder to decisively classify the user as suspicious. This is particularly important when trying to identify bot networks.

{:.english}
The paradigm is that using "official" apps for bot-network operators requires a much higher level of sophistication and/or resources. In the next few paragraphs I will show that this paradigm is false: it’s extremely easy to misrepresent an official source via a script, thus masquerading an automation-operation as a valid user, without utilizing expensive browser automation tools or human operators.


{:.english}
**Browser Automation and its Limitations**

{:.english}
A common way to tweet via the web is to simply use a web browser. This can be done by humans, obviously, but also by machines using tools like Selenium, Phantom JS, Puppeteer, and many others. While this is a valid option, it’s very expensive in terms of time and resources. In order to send a tweet, the operator must fire up their browser, navigate to the login page, enter the credentials, hope there’re no A/B tests running, click "New Tweet", fill it in, and click “Tweet”. The process takes around a minute a tweet, and any minor UI change breaks the code. The number of tweets that can be sent using this method depends on the computing power, which is not cheap. 

{:.english}
If only there were a way to tweet in under a second without the need for expensive RAM and CPU...

{:.english}
In order to comprehend how this can be achieved, it’s important to first understand the way Twitter checks if users have authorization to tweet. This is going to get a bit technical, but without it, it’ll be difficult to explain the bypass.

{:.english}
**How Twitter Authentication Works**

{:.english}
Twitter uses [OAuth 2.0](https://developer.twitter.com/en/docs/basics/authentication/overview/using-oauth), which is great. OAuth is basically a security mechanism that allows applications to authorize users without asking for their passwords. This mechanism works on two levels:

{:.english}
1. Identify the application requesting access

{:.english}
2. Identify the actual user

{:.english}
To identify the application, the app operators receive two parameters: a consumer key and a consumer secret. With these parameters they can generate a "[Bearer Token](https://tools.ietf.org/html/rfc6750)" that classifies each call to Twitter as a valid call from the specific application. Twitter knows “[for sure](https://developer.twitter.com/en/docs/basics/authentication/guides/bearer-tokens.html)” that only calls sent with this token are valid calls from the application, and each token can be attributed to a specific source. This is where we get our “Source” attribute on the meta-data for each tweet.

{:.english}
Next, Twitter needs to know which user is sending the tweet, so only the owner of the account (or someone with access to the username/password/2FA) can submit content under it. This is done using an "auth_token" created by verifying the user key and secret, much like the consumer key and secret process.

{:.english}
Combining the application authentication using bearer tokens and the user authentication using auth tokens, Twitter can safely assume that the user is using the application, and that the authentication process is successful and secure.

{:.english}
There is another test utilized by Twitter to minimize the risk of automation. This is done by using [CSRF tokens](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)), which are a common (and excellent) practice to make sure the call is coming from a valid website.

{:.english}
Layering these three methods allows Twitter to make sure the user is using their application (with the bearer tokens), that it’s actually the user (with the auth tokens), and in case of the Twitter website, that the call is coming from their website (with the CSRF tokens).

{:.english}
While these methods are great, their implementation by Twitter allows a novice operator to send tweets automatically by using scripts and have them appear as if they were sent through the Twitter website or application, thus allowing nefarious actors to programmatically send tweets that appear as if they were sent manually by legit users.

{:.english}
Another point worth emphasizing is that speaking to many shady "campaign operators" running Twitter networks, one learns that their account creation process is *not* automated. Some of them pay people in Nigeria $1 per account opened, some pay less in Russia, Central Asia, and the Far East, but the bottom line is that it’s done manually, including mobile authentication, which is required in most cases. The importance of this detail will become apparent shortly.

{:.english}
**How to Actually Do It**

{:.english}
In order to send a tweet, we can use the following code (variables appear in **bold**):

{: .acode}
>~$: curl 'https://api.twitter.com/1.1/statuses/update.json' \  
>-H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:65.0) Gecko/20100101 Firefox/65.0' \  
>-H 'authorization: Bearer **XXX**' \  
>-H 'x-csrf-token: **YYY**' \  
>-H 'content-type: application/x-www-form-urlencoded' \  
>-H 'Cookie: ct0=**YYY**; auth_token=**ZZZ**;' \  
>--data 'status=whatever'  

{:.english}
XXX is the authorization bearer. Although it sounds like complicated processes are required to get the official Twitter bearer, it’s actually loaded (semi-hardcoded) as part of the JSON webpack process (parameter ‘u’ in the screenshot below, which was taken from code that is loaded every time a browser loads twitter.com):

{:refdef: style="text-align: center;"}
![bearer token in the twitter source code](/img/2019-05-13-0.png)
{: refdef}

{:.english}
We can simply take the Bearer token from there. a simple JavaScript button on the operator’s browser bookmarks’ menu should be enough to extract it, and since we already established that many operations are using humans to open accounts, this can be done as part of the same process. Now we are sending our request as the Twitter official web client, and this is what will appear as the "Source" in the tweet metadata visible to API users.

{:.english}
Next, YYY, the CSRF-token, appears identically in two places: in the cookie with the crumb name "ct0", and as a header called “x-csrf-token”. This, too, can be extracted with javascript from the browser.

{:.english}
Finally, ZZZ, the "auth_token", which appears in the cookie and again can be taken with a single JavaScript command. In fact, one does not even need JS to extract these values, as they are sent with every call from the user. So it suffices to follow a single transaction between a logged-in Twitter user and the Twitter server.

{:.english}
Once we have all three parameters, we store them in our database (they are static and don’t change, as far as we can tell after a few weeks of testing), and whenever we want to send a tweet without the hassle of opening a browser, we simply construct an HTTP call with those headers and set the body to "text=[whatever I want to tweet]".

{:.english}
You can use different IP addresses, different user agents, different machines, and the calls still goes through, no matter how many tweets you send. I tested dozens of tweets with the same parameters and different content; all of them went through without any problems, and all appear to be sent from the Twitter web platform.

{:.english}
By simply changing the bearer token we can change our source. For example, when we use the bearer token from the old Twitter UI, the source appears as "source": Twitter Web Client, and when using the bearer token from the new Twitter UI, it appears as Twitter Web App. The same CSRF and Auth tokens are used, and the only different parameter is the bearer token, which is given "for free" from the JavaScript code on the official Twitter websites.

{:.english}
These methods were tested on tweets, but the same exact measures can be used to retweet, like, follow, and perform any other action.

{:.english}
**Implications**

{:.english}
Seeing how easy it is to automate tweeting with a fake source should raise the alarm for organizations relying on the "source" of the tweets as a strong indicator for tagging, and subsequently confronting, users or bot-networks. The “source” needs to be treated as a “false-positive” prone parameter, and the “official” Twitter app source should no longer be used as a signal to lower the suspicion of automation and/or inorganic activity. 

{:.english}
**Why This Is an Issue**

{:.english}
Obviously, this practice goes against Twitter’s own terms of service, but it’s much more than that. A legitimate client needs to go through a verification process as a developer, and again for each application, so Twitter knows who’s doing what on its platform. Using these methods makes the entire process redundant, since the malicious actor masquerades themselves as official apps. This also bypasses many of the "rate limits" imposed on application operators, as Twitter limits users, but not its own apps and clients.

{:.english}
It also prevents the company from blocking malicious applications’ access, which is something that can, and is, easily deployed against normal app developers who break the rules. 

{:.english}
But the impact here is much larger than simply following Twitter’s rules (or defying them). Twitter’s data is used for research by thousands of organizations around the globe to identify malicious activities that harm the public interest, such as election tampering, pump-and-dump schemes, and the spreading of fake news. By allowing this hack to exist, Twitter severely cripples the ability of researchers around the world to detect automation in activities performed on the social platform.

{:.english}
**What Twitter Can Do to Mitigate This**

{:.english}
On paper, Twitter is acting exactly as it should. Using known, trusted, and open technologies for authentication, creating an stable and robust API for developers and researchers, and in general doing everything "by the book". 

{:.english}
They require four different keys to use their API, which is the correct way to do things, but they also leave the master key in plain sight, literally in the code loaded every time a user opens their browser to use the application, thus making the entire design redundant. This is like leaving the house key under the carpet, or rather, above the carpet.

{:.english}
It’s important to emphasize that this hack doesn’t breach users‘ security and privacy, but as we demonstrated,it does allow automation of information spreading via the platform. We emphasize one needs (legitimate) access to a user to obtain its tokens.

{:.english}
To fix this, Twitter can do several things:

{:.english}
1. Apply single-use CSRF tokens, or at least use time sensitive tokens, depending on the design that wish to use, thus even if a hacker takes a token, they cannot simply replay it with a different tweet text, or at least not for longer than a few minutes. 

{:.english}
2. Use sessions properly. Twitter actually already has sessions (a crumb called "_twitter_sess" already exists in the cookie), but it’s not mandatory for interaction with the website. There are many ways sessions can be used to prevent automation, and it will make the attacker’s life much harder.

{:.english}
3. This may be a paradigm change, but maybe it’s not the best idea to have end-users communicate directly with the API - the same API that is used by application developers. The reason is that it requires bypassing a major authentication mechanism by neglecting the consumer key and consumer secret, and simply publishing the bearer tokens in plain sight. By wrapping the API with a website-compatible mechanism, there will be no need to bypass the proper authentication mechanism.

{:.english}
The research was conducted by Noam Rotem and Ron Asherov. We reached out to twitter via email and online forms on their website prior to the publication in order to see if this is of interest to them, but received no response.

{:.english}
This issue was also discussed in the popular (Hebrew) podcast [Cyber Cyber](https://podcasti.co/minisites/cyber/) hosted by Noam Rotem and Ido Kenan.

