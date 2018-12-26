---
layout: post
title: The Thin Data Pipe
date: 2015-05-09T01:45:26+02:00
summary:    The cost of being connected.
categories: thoughts random
thumbnail: plug
tags:
 - idea
 - thought
---
![Diskettes](/images/diskettes_stack.png) I recollect a time, seven or
so years back, I was at a place where I celebrated the successful
download of a 10MB installation file. I would compress it
([WinRar](www.rarlab.com)), chop it up and then save it to several
1.44MB diskettes!

We have progressed well since that time but I still find myself using a
thin pipe to tape to the internet!

A Tinkeror’s Necessity
----------------------

For any *‘Tinkeror’* internet access is an indespensable assay but, the
average Joe has to tinker more to get ahead. With the boom and
proliferation of FOSS tools, ability to download at will is largely a
given, the means, quite the contrary - for my part of the world. The
connections to the interweb are there and the speeds are reasonable. The
challenge is what you trade for to get your data chunk. Some great
geo-toys even assume you’re always connected to the internet. Well,
thanks to initiatives like the [Smart
Cape](http://www.capetown.gov.za/en/Library/Pages/SmartCapeAccess.aspx),
I can budget the 500MB data allocation per month to download only
critical programs to my ‘workbench’ or trusty S4 Mini mobile phone. But
wait, I need to

```
$ rake deploy
```

to have my latest blog post published, and that requires some data
currency. Thanks to git, I don’t need to push a file horde, just a
simple markdown text file and a few pics. The 150MB/ month I get from my
[Service Provider](http://www.mtn.co.za) atomises within four days of
receiving it - provided I decide to be conservative about visiting
Facebook. Trouble starts when I need that 729MB [Landsat 8
file](libra.developmentseed.org) to check out what is happening this
rainy season with the once disastarous [Tokwe-Mukorsi
Dam](https://github.com/erickndava/tokwe-mukorsi).

![Landsat Data Download](/images/landsat_7_download.png)

I could download just the bands I need but, even that would deplete my
monthly quota by (\~59MB x 3) 35% for a true colour band combination.
This is too much to sacrifice just for one project. Work arounds have to
be fathomed, working with a D-Link 3G 21Mbps, USB Modem and Mobile phone
(Mobile hotspot functionality).

#### \# Wait For Night

I’m sure am not the only tinkeror who sacrifices sleep now and then.

> Work all night, Sleep all day, Wake up at 8pm really confused

–
[@lyzidiamond](https://twitter.com/lyzidiamond/status/594658391617863680?=03)

![MTN Night Express](/images/mtn_night_data.png)At night, one can get a
bit of reasonably prized data. I ran a USSD request on my service
provider (07 May 2015) and got ‘Night Express’, 1GB for R10. Remember
this will be chowed by a single landsat scene multiband image and would
cost me a few hours of snooze.

An alternative service provider has a similar data deal:

But there is a catch, I get to sleep a bit later. Yay! ![Cell C Night
Data](/images/cellc_night_data.png)

#### \# Sip or Chow & Work

There are 101 restaurants and Cafes with ‘Free-Wifi’ access. But having
to trade 50MB/ day for your phone number and email address is a bit too
much. Don’t even start on the idea of moving from Cafe to Cafe until a
project is done. Sipping on a cup of coffe for two hours! Really?

Google Search is like a pencil and scrap pad. I transfer mental notes to
there. More often than not I have typed *Define:{Mind drift idea here}*
in that nifty search box. The thought that my browser is connected to
the interweb never occurs in all of this.

#### \# A Mesh Of All

Well, a 40Mbit/s ADSL line in the house, enabling one to read ‘Done!’
after a repository clone command simultaneously with the lifting of the
finger off the ‘Enter’ key would be ideal. Until then, patience and data
budgets remain the order of the day for the average Joe.


