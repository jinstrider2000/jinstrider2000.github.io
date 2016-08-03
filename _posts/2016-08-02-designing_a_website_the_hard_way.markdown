---
layout: post
title:  "Designing a website, the hard way"
date:   2016-08-01 20:55:55 -0400
---


I just made my first website, and man it was fun...and hard.  I made it for my church, "Love, Power and Grace" in the Bronx.  We're an old church that just celebrated 55 years of service this past month, but we've never had a website before (not a real one anyway. I do remember some old Geocities-"Dreamweaver-y" thing we tried in the late 90's/early 00's, *but I really wish I didn't*).  So, being an ambitious Learn student, I decided to take a break from my labs and put what I've learned so far into action, resulting in "http://lpgchurch.org"

## Sir, how much for a .org with a side of .com?

Early in the Learn curriculum you cover the basics of how the web works (i.e. HTTP/IP, DNS servers, purchasing domains, hosting, etc).  Being a church site, I figured it would be best to purchase a .org domain name, so I went to Google to see how to purchase one (mind you, I've never done any of this before).  The first result was GoDaddy, who was selling .org domains for $15.99 a year.  I decided that was fine, and being a novice who was rearing to get started, I wasn't going to shop around (they also sold .coms for $7.99.  Again, I wasn't inclined to look for better prices, which was probably stupid, I know).  So I walked away with lpgchurch.org and one-line-at-a-time.com, my custom domain for this blog.  First broken expectation: Call me naïve, but I always thought that purchasing a .org would require some sort of verification to see if the purchaser was, you know, *an organization*.  I started the process, but figured that eventually I'd get to some verification portion and would have to stop and get paperwork from the elders of the church: i.e. tax-exemption forms, incorporation information, *something*.  "Nope", said the Internet, "We believe you (or better yet, we don't care).  You're an organization...good for you!"  Ok, easier for me, I guess.

## The Host-ess with the Least-ess
For hosting my simple, first time website, I went to the cheapest (free) and simplest hosting service I could think of, Github Pages!  Learn automatically setup this blog on Github Pages under my username, so I figured I'd just create one under a new name.  Ultimately, I intend for lpgchurch.org to incorporate **everything** I learn about full-stack development, so I know it can't live on Github for long, but for now, it's enough.

## Layout is hard when you're blind
I didn't take Jonathan Grover's advice and diagram the site before starting.  I just thought about how the pages should look, and then tried to get the vague picture in my head to come out on the browser.  As I slowly learned, this *isn't* the way to make a website.  Organizing the nav bar, whether it should have a solid color or a gradient, whether a div should be floating left or right (or absolutely positioned), or whether a font should be bold or in italics; these considerations can be very time consuming, and in front of your keyboard with Sublime text open **shouldn't be the first time you've ever thought about them**.  I'm not a visual learner, so I don't usually think about visualizing problems to aide my understanding of them, but web design *is* visual, so now I realize that I have to fire up the visual part of my brain if want the develop a good workflow when creating front-end.

## A promising start
As I said before, I intend for lpgchurch.org to be much more than a simple website.  I'm not 100% sure, but as of now, I'm thinking of building it out as a church management platform for use by our church's leaders.  That would obviously necessitate some implementation of a SQL database (for church records), and a web programming framework like PHP or Ruby on Rails to utilize things like Twitter and Google APIs.  Now I'm not that far along in the curriculum yet, but I'm ready to keep working, to keep growing, and to keep making mistakes.  Useful mistakes, I hope.
