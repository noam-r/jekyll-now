---
layout: post_page
title: Ecuador exposed
description: 
---

{:.english}
Privacy is no more for the citizens of Ecuador. Two systems containing all the information of all citizens of Ecuador had extremely poor security that only a regular web-browser was required to gain full access to the entire trove of data. Evidence was also found to show that at least one of the systems was exploited for months before being taken down by the authorities in Ecuador.

{:.english}
**Breach #1 - Novaestrat**

{:.english}
A lot [was written](https://www.zdnet.com/article/database-leaks-data-on-most-of-ecuadors-citizens-including-6-7-million-children/) about the first breach we discovered a few weeks ago, we won’t go over it again, just mention that during routine scans we’re running as part of a fun side-project, we stumbled upon an open elasticsearch instance that required no authentication and was accessible with nothing but a web browser, and exposed the data of ~20 million citizens of Ecuador.

{:.english}
Obviously having an unsecured database with no authentication just open to the web is not the best idea the fine people at a company called "Novaestrat" had, but after a few days of trying to reach the CERT (Computer Emergency Response Team) of Ecuador, they did an excellent job in taking it offline and finding the people behind it.

{:.english}
**Breach #2 - databook**

{:.english}
Surprisingly, the 2nd system we encountered was even worse. We got tipped about it by Andrés N. Robalino ([https://twitter.com/andras_io](https://twitter.com/andras_io)), a computer scientist and open-source contributor from Ecuador.

{:.english}
He received an anonymous tip on twitter, that the same data Novaestrat had, is also in the hands of databook.com.ec, and we started our investigation into it.

{:.english}
The domain hosting the system had the promising name "databook.com.ec", and looked like this:

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_0.png)
{: refdef}

{:.english}
We immediately identified the data on the screen as XML, and we knew the field names from the previous breach at NovaEstrat, so we knew we are onto something. That was a clue to do something very simple using a sophisticated hacking tool called a "web browser". 

{:.english}
By looking at the source of the image (it was [http://databook.com.ec/imagenes/webservice1.jpg](http://databook.com.ec/imagenes/webservice1.jpg)) We removed the file name (webservice1.jpg) and behold - all the files in the directory immediately became visible:

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_1.png)
{: refdef}

{:.english}
A quick look at a file called "xml.jpg" shows sample output from the system:

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_2.png)
{: refdef}

{:.english}
(The original image was not blurred, and all of the information was visible. We blurred it so prevent further privacy issues for this poor individual, who seems to be the husband of one of the company’s managers).

{:.english}
That’s a lot of data, but if you take a closer look at the image, you can see it has a URL. Any curious mind would try to type it and see if it works. And we did. And it did.

{:.english}
The website "databook-premium.com.ec" presented itself as a property rental site. Nothing about selling personal data of millions of citizens. The website was hosted on a server in Germany, and it was so for over a year.

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_3.png)
{: refdef}

Looking for proof the sites were linked, we checked the founders page of databook.com.ec

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_4.png)
{: refdef}

{:.english}
And the contacts page of databook-premium.com.ec

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_5.png)
{: refdef}

{:.english}
Clearly, the same people.

{:.english}
So far, using nothing but a web browser, we found access to live data of a specific person in Ecuador. One person you ask? Well, by changing the parameter "ced" in the URL (again, with nothing but a web browser) - we could get the details for any citizen in Ecuador in a convenient XML format. No passwords were required, nothing. Nice! 

{:.english}
But that’s not all. Oh no, we’re only getting started: by once again using a sophisticated hacking tool called a "web-browser", we figured that such a nice system must have some kind of front-end to make it easier for users to browse extremely private details of all citizens of Ecuador. And we were right.

{:.english}
By pointing our browsers to "/users", we saw a complete list of all users of the system. Thousands of them.

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_6.png)
{: refdef}

{:.english}
And what’s that on top you ask? A "Create User" button.

{:.english}
Again, no passwords were necessary to view all of this information. Absolutely nothing. Anyone with a web-browser could SEE all of the existing users of the system, and anyone with a web browser could CREATE a new user. For a system that is holding such valuable data - that must be a record in irresponsibleness. Nowhere, Never, is this an acceptable practice. Nowhere, except Ecuador, apparently.

{:.english}
So we’ve created a user, since, remember, nothing prevented us from doing so, and it was so welcoming. After using the new user details to log in - we were greeted by a grey screen with a text box. By typing in any "cedula" (id number), a lovely output was presented (again, we blurred out some of the details to prevent further privacy issues, but since this is the president we guess it’s OK):

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_7.png)
{: refdef}

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_8.png)
{: refdef}

{:.english}
So this is how customers of the system see the data. And it’s A LOT of data. Down at the bottom, using family data, they are even nice enough to build a family tree - spouse, children, parents, uncles and aunts. If you wonder about the possible uses of this kind of data?

{:.english}
Look no further than the [https://demo.databook.com.ec](https://demo.databook.com.ec) page:

{:refdef: style="text-align: center;"}
![image alt text](/img/2019-09-27/image_9.png)
{: refdef}

{:.english}
"Our mission is to help companies improve their marketing strategies, decrease credit risk, and maximize their commercial processes, intelligently using social, demographic, economic and genealogic data". Then they are literally saying ‘Family tree for collections’ (bottom line, middle). And if you don’t pay your bills, we’ll pay your Aunt Lizzy a vizzy!

{:.english}
Nearly all people urinate in the pool, but these guys do it from the diving board.

{:.english}
However - it’s still not enough. By doing a simple google search (again, nothing but a web-browser) we found that someone else found this back in January of 2019 and posted a [short code snippet](https://pastebin.com/jv2puzL5) that automatically creates a user, allowing anyone to log in. It is safe to assume that whoever published this snippet used it to gain access to the system, and most probably sent it to other people as well.

{:.english}
By using various methods and techniques we will not be able to disclose at this point, we were able to find further data:

{:.english}
* The first time the system was accessed was on December 9th, 2013. That means that the data of all of the people in Ecuador was being sold by the owners of this platform for almost 6 years before we contacted the government to shut it down. 

* There were 4168 users in the system with valid login credentials. The same credentials can be used by multiple people, and as we’ve seen - the data was accessible even without logging in (by accessing the XML directly), so it is safe to assume that many thousands of people had complete access to the system for many years.

* Information in the system was updated until (at least) August of 2019, including monthly actual salaries for millions of citizens of Ecuador. This is not old data, but fresh, continuously updating data from various official sources.

* There were 263,348,202 employment records, which means the (almost) complete employment history for all citizens was available, including salaries.

* A total of 20,391,705 citizens were accessible by the system. Since the total number of citizens of Ecuador is approximately 17.37 million people, it’s safe to assume some are dead, but the numbers seem slightly too large to explain the discrepancy by deceased people alone. If we were citizens of Ecuador, we would ask the government if any of the surplus people in the database voted in the last election.

* There were also 24,070,332 cell phones, 6,116,076 telephone numbers, and 4,352,773 email addresses. Enough to spam everyone in the country for a very long time.

{:.english}
**And it doesn't end here**

{:.english}
Since the first data breach was detected on Novaestrat, we’ve been in contact with some wonderful activists from Ecuador, who were kind enough to give us some history of privacy issues in the country, and did some mapping work of similar systems. As it turns out, there were more systems like the 2 we uncovered, and since the initial publication they went into "maintenance mode". 

{:.english}
It is not common for us to be able to make such an impact on the lives of millions, and we really hope the impact will be positive, and that the government of Ecuador begin to take the privacy of its citizens much more seriously. It is rarely good to leave private data in the hands of "marketing" companies, as their interests are not in line with the interests of the people whose data they hold.

{:.english}
We will continue to monitor privacy issues around the world as part of our little side-project we’re doing in our spare time, but it is really in the hands of the people to demand that their governments protect their privacy, and prevent "for-profit" organizations from capitalizing on their data.

