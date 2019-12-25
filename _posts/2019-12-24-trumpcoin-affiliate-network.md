---
layout: post_page
title: The Trumpcoin Fake News Affiliate Netowrk
description: 
---

{:.english}
As we barrel toward the 2020 elections, and with impeachment proceedings underway, we are now uncovering a disinformation campaign that has gone unnoticed since 2016. 

{:.english}
We’ve all heard a lot about the disinformation campaign around the 2016 US Election, spreading fake-news and hate, and tearing the great American nation apart, the supposed evil-doers behind it, and the international intrigues and conspiracies that fueled the whole thing. 

{:.english}
Today, my colleague Ran Locar and I are disclosing  the details of this and its motivation: Money.

{:.english}
What we found is a network of dozens of blogs and websites with classic fake-news content (Muslims are raping children, a Flesh eating parasite is being spread by ISIS, Crooked Hillary, etc.; More on that later). Many of the websites are nearly identical, using similar templates, and a lot of meta-data in common.

{:.english}
There were also facebook pages that were purchasing advertisements on the social network for hundreds of thousands of dollars, and that were shut down after our disclosure.

{:.english}
If you’re not into the technical details, you can scroll  down to the TL;DR section at the end.

{:.english}
**Identifying the Cluster**

{:.english}
Earlier this month, Steffan Watkins, a Canadian OSINT researcher, [tweeted](https://twitter.com/steffanwatkins/status/1201270727674077184?s=12) about a “news aggregator” that had popped up, and concluded that ‘Sites like these should be blacklisted”. We were intrigued, and decided to look into this.

{:.english}
Once we had a single domain lead, we started to look at various indicators to see what else we could find. For example, calling the `wp-json/wp/v2/users` would return the same user, “93jd2wd”, for many of the platforms:

{:refdef: style="text-align: center;"}
![metadata1](/img/2019-12-24/image11.png)
{: refdef}

{:refdef: style="text-align: center;"}
![metadata2](/img/2019-12-24/image12.png)
{: refdef}

{:.english}
Beside the common username, all the ‘news’ sites we encountered, and the commercial sites they directed traffic to, shared the same IP address, as we found with the help of [Security Trails](https://securitytrails.com/list/ip/8.39.235.185).

{:refdef: style="text-align: center;"}
![security trails](/img/2019-12-24/image17.png)
{: refdef}

{:.english}
Manually reviewing all the sites on that machine allowed us to discover more domain names participating in the same scheme.

{:.english}
The famous “cyber-necrophilia rule” states that there is never just one corpse, so we had to dig a little deeper.

{:.english}
By analyzing the calls from the sites we found (a fancy way of saying that we looked at the traffic), we found a common AWS S3 bucket, called “splitpagesimagesdfg”, that served static files for many of these websites. Luckily, and following the cyber-necrophilia rule to a T, the bucket was open, and exposed thousands of files conveniently organized by the websites they serve, in a total of 146 directories. Before you start crying “Is that all?” - it’s not the only bucket we found.

{:refdef: style="text-align: center;"}
![view source](/img/2019-12-24/image19.png)
{: refdef}

{:.english}
We went over the directories one by one, identifying the source of each directory and matching it to a website. Many of the websites were regular junk affiliate stuff for “seducing” men and women like “SupremeSexualStamina.com”, “FemaleMindControlSystem.com”, and “ErectionMasterySystem.com”, pushing e-books and useless products to naive men and women through various affiliate networks. 

{:.english}
Some were about “surviving the apocalypse”, with affiliate links to e-books teaching about weapons, military batteries, special knives, and living in the woods (“CrisisSurvivalCenter.com”, “SystematicSurvival.com”, “Military Battery Reconditioning system”, “PowerOutPrepper.com” etc.). Others were about various money-making schemes, like “PhoneMoneyMethod.com”, “FinancialFreedomMembers.com”, etc. 

{:.english}
And some were built to push “Freedom coins”, with the President’s face on them.

{:.english}
**What are Affiliate Networks?**

{:.english}
Before we get into the dirty details, let’s take a minute to understand how affiliate networks work. Basically, they are a subset of the online advertising industry where people, or businesses are compensated for a sale they product for another business entity. Amazon, for example, has been running an affiliate network since the late 1990’s.

{:.english}
The basic premise is, the more quality traffic the affiliate can deliver, the more sales they’ll drive, and consequently, the more commissions they’ll make. Sounds simple, right?

{:.english}
There are many techniques used to accomplish this. One of them is giving a “limited time offer”, pressuring the user to buy whatever it is NOW. Some use fear for persuasion:

{:refdef: style="text-align: center;"}
![fear](/img/2019-12-24/image15.png)
{: refdef}

{:.english}
Some are selling a dream of a flat-stomach or a voodoo trick to make every man and/or woman fall in love with you. The words “magic”, “loophole”, and vague promises of scientific methods, are present in many of these:

{:refdef: style="text-align: center;"}
![pseudo methods](/img/2019-12-24/image5.png)
{: refdef}

{:.english}
Others peddle patriotism in order to push their products, harnessing the fear and hate sowed by powerful malicious parties to make a profit. These are the ones we’ll be focusing on.

{:.english}
**The Freedom Scheme**

{:.english}
What the network we’ve identified would do is generate a traffic stream of Trump-supporters, and send them to an online-store that sells stuff with Trump’s face on it.

{:refdef: style="text-align: center;"}
![the freedom store](/img/2019-12-24/image2.png)
{: refdef}

{:.english}
Trump hats, posters portraying Trump as Rambo, but mainly Trump coins labeled “Liberty Coins”, because hey - who doesn’t love liberty?

{:.english}
Every affiliate with common sense knows that you sell diets to people with weight issues, sell “seduction” techniques to people with no social skills, and in general - you have got to find the right audience to make money. The same goes with Trump merchandise. You won’t sell it at a democratic convention, so you need to find your audience in other places, and that’s exactly what the people who were behind this operation did.

{:.english}
They needed to provide some value in order to prepare their potential customers to the idea that they must take out their wallet and spend money. But how do you do that? You pretend to be a news outlet, and since other parties, supposedly from the infamous “troll factory” in Russia, already invested heavily in suspending all sense of criticism in their target audience, the task seems doable. So they went for it.

{:.english}
For example, in 2016, thetruthreporter.com popped up a modal [asking](https://web.archive.org/web/20160112092333/http://thetruthreporter.com/) its users “USA Should Not Be Under Sharia Law - Click ‘Like’ If You Agree”; republifacts.com [listed](https://web.archive.org/web/20160616022112/http://republifacts.com/) “10 Hillary Scandals The Liberal Media Hides From You”; americanonlinetimes.com, also operated by the same network, went further with the “facts” and [published](https://web.archive.org/web/20161025184257/http://americanonlinetimes.com/) stories like “Elementary School In THIS STATE Bans Valentine’s Day – It OFFENDS MUSLIMS!” and “Muslim migrants in Germany rape Russian child for 30 hours, then get ‘massacred’ by angry Russians in reprisal”; rightsidepress.com [cried](https://web.archive.org/web/20180223234811/https://rightsidepress.com/2017/07/28/crooked-hillary-get-by-again/) “Crooked Hillary Gets By Again”; onlineconservativepress.com [warned](https://web.archive.org/web/20161119100706/http://onlineconservativepress.com/) that “DEMS Considering New DNC Chairman, One with Strong Ties to Radical Islam”; digitallibertyvoice.com [told](https://web.archive.org/web/20160115082945/http://digitallibertyvoice.com/) its readers that “Thanks To ISIS, A Flesh-Eating Parasite Is Sweeping Through Syria”, and that there’s a toy plane that makes plays a muslim prayer. 

{:.english}
Chilling, right? There are a lot more examples, but you get the idea.

{:.english}
**Looking into the Domains**

{:.english}
While some of the domains wisely employed whois privacy, a feature that prevents us from knowing who had registered them, many of them didn’t, so we found a hefty list of domains all purchased by the same individual. It is important to note that the same individual’s name also appeared on several S3 buckets we identified as related to this operation.

{:refdef: style="text-align: center;"}
![jackson.lin](/img/2019-12-24/image6.png)
{: refdef}

{:.english}
This individual, “[Jackson Lin](https://domainbigdata.com/nj/Eh4Q4jYS7Va4kb5TtbYifg)”, along with the company “[Extreme Wisdom](https://domainbigdata.com/nj/ir8Rqg5n-0X6kwEKcCNyCA)” (really, that’s the name of the company, we are not making this up), registered dozens of websites over a few years, the same domains we connected to the S3 bucket. On these domains they installed various platforms to generate traffic for quite a few affiliate programs. Some of these domains were targeting right-wing Americans, taking advantage of the work (supposedly) done by foreign entities to remove the critical element of reading content online, and spreading fake-news in order to get them to buy Trump branded merchandise.

{:.english}
Jackson.lin84 is tied to the bucket above, listed as the owner of the media, which is used on multiple sites running on that same machine. He is also an active affiliate marketer:

{:refdef: style="text-align: center;"}
![jackson.lin google](/img/2019-12-24/image16.png)
{: refdef}

{:.english}
An affiliate marketer, who in spite of his blazing patriotism, does not refrain from sending American jobs to the Philippines:

{:refdef: style="text-align: center;"}
![job listing](/img/2019-12-24/image9.png)
{: refdef}

{:.english}
Some of the sites, like http://www.trumpvictorycoin.org/ link to multiple domains, which establishes a link between them:

{:refdef: style="text-align: center;"}
![mixup](/img/2019-12-24/image1.png)
{: refdef}

{:.english}
And

{:refdef: style="text-align: center;"}
![mixup](/img/2019-12-24/image7.png)
{: refdef}

{:.english}
While some of the sites selling Trump merch (as well as the ‘news’ sites) mention that they are not part of the Trump campaign, but rather ‘simply supporters’, others claim the goods sold are a ‘donation’ to ‘help support the president’:

{:refdef: style="text-align: center;"}
![mixup](/img/2019-12-24/image5.png)
{: refdef}

{:.english}
**The Company**

{:.english}
So who is profiting from all this? One of the companies connected to this network is called Click Wu LLC, and operates from Huntsville, AL. This company appears on the [contact us](https://thefreedom.store/store/index.php?route=information/contact) page on The Freedom Store. According to [records](https://opencorporates.com/companies/us_al/541-811), the agent name for this company is “Jeffry P Wu” from 10127 Shades Road, Huntsville, Alabama.

{:.english}
This company runs several online properties to sell and distribute pro-Trump merchandise, and benefitted from the fake-news websites that were used to send traffic their way.

{:.english}
**Facebook**

{:.english}
On the Facebook Ad Library we found a few of the network’s properties that were being advertised. Overall it seems that over $276,000 was spent on Facebook alone by organizations looking to promote it: 

{:refdef: style="text-align: center;"}
![facebook ads](/img/2019-12-24/image13.png)
{: refdef}

{:.english}
This website spread fake news like “[Saudi Arabia Is About To Behead 6 School Girls For Acting Indecently With Their Male Friends](https://libertyvoicereport.com/saudi-arabia-is-about-to-behead-6-school-girls-for-acting-indecently-with-their-male-friends/)”, already [debunked by Politifact](https://www.politifact.com/punditfact/statements/2017/nov/29/religionmindcom/fake-news-girls-saudi-arabia-will-be-beheaded-danc/) with the wonderful “pants on fire” rating. For this specific property, LibertyVoiceReport.com, the organization registered as the payer is called “Piton Performance Marketing”:

{:refdef: style="text-align: center;"}
![piton performance maerketing](/img/2019-12-24/image20.png)
{: refdef}

{:.english}
...which seems to be related to the  pitonperformance.com domain, which in turn leads, based on the Skype username and email on the website, to an individual called “Chris Norwood”, who coincidentally owns a [strikingly similar](https://chrisnorwood.io/) website.

{:.english}
It seems that Facebook took the easy path here, and while showing who actively paid for the ad, allowed bypassing it very easily by hiring a marketing company to add the ads to the platform, thus keeping the actual advertiser hidden in the shadows. This is especially important with political ads, and even more so when the content is inciting fake news.

{:.english}
After Facebook were made aware of the operation, they shut down 13 pages that were promoting it, after a total of $276,387 were spent on them by the advertisers.

{:.english}
**Not Just a Business - A Misleading Business!**

{:.english}
In addition to their misleading advertising practices, it seems Click WU LLC also allegedly mislead their buyers by including hidden charges on their bills, while claiming the products are ‘Free! Pay only S&H!’

{:refdef: style="text-align: center;"}
![bizpedia](/img/2019-12-24/image8.png)
{: refdef}

{:.english}
**But Wait! There’s More!**

{:.english}
Remember the cyber-necrophilia rule we talked about earlier? The technical operation behind this network was less than excellent, to use polite language. Other than the poor opsec, the unmasked domain purchasing, the lack of security on the various S3 buckets, and the lack of protection on the “members only” materials sold for hefty sums, they also neglected to protect the identity and privacy of their customers, exposing details of over 75,000 customers who bought stuff on their stores.

{:.english}
They also forgot a video of one of the operators, showing a few of the network properties:

{:refdef: style="text-align: center;"}
![jacky](/img/2019-12-24/image14.png)
{: refdef}

{:.english}
This video is titled “Jacky”, and shows that this person manages various domains which are part of the network, with admin access to the affiliate platform and the FTP servers. 

{:.english}
**TL;DR**
We found a network of dozens of websites operated by an affiliate marketer. Some of the websites pushed pro-Trump/anti-Clinton fake-news meant to use patriotism in order to sell unofficial Trump merch to Trump supporters. The technical aspects of the operation allowed us full visibility into not only the operators, but also the unwitting customers.

{:.english}
The network is definitely not dead. It keeps spending money to get traffic, and based on a few assets we found on their infrastructure, it seems that they’re looking forward to the coming elections as well:

{:refdef: style="text-align: center;"}
![trump2020](/img/2019-12-24/image18.png)
{: refdef}

{:.english}
It’s sad to say, but the future of the coming elections is very much in the hands of corporations like Facebook and Google, that have the power to stop the spreading of fake news. 

{:.english}
Let’s hope they don’t continue dropping the ball.
