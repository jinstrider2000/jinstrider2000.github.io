---
layout: post
title:  "OMG, they found me?!? (A CLI Data Gem story)"
date:   2016-10-03 20:23:33 +0000
---


I just finished my CLI Data Gem project!  It took some time, but I got it done and I'm very proud of it.  It's called **RomLoader**, and it scrapes freeroms.com (a video game emulation site) to list all the videogames they serve there and allows you to *download any game straight to your home directory*.  This project was such a pleasure that I intend to expand upon it in my post-Flatiron future, but for now I need a break from it -- firstly, because I need to move on in the curriculum, and secondly, because during the testing phase of development I received the *greatest fright of my (coding) life!*  But more on that later.

## Brain Storming
I really didn't know what to do for the CLI Data Gem project to start.  I knew it had to scrape a website or utilize a public API, and that it had to display at least two tiers of information.  At first, I thought I'd just list the nutritional facts for foods off of some website, really as something just to fulfill the requirements and move on.  And then it hit me...video game roms!  I've downloaded a great deal of them over my life; sometimes for reasons of nostalgia and other times to discover a great game that I missed the first time around.  One of my favorite games, Chrono Trigger for the SNES, is a great example of the latter.  So, with a clearer vision and a palpable since of excitement, I attended an online planning session for the project.

## Avoid anything with Javascript, etc...
At the session with Corrine, she advised all of us to not mess with any websites containing extensive Javascript or Ajax, as it might be hard to extract the information you want if it's contained in a script, and (in the case of Ajax) the info retrieved might be too transient to be useful anyway.  Ok, check.  Also, I was personally advised that my video game rom downloader idea might be too ambitious for this assignment, and that I should pare it down to a more manageable size, maybe not indexing *every* game on the site (there are over ten thousand).  Ok, double check.  So, with all this in mind, I went along to freeroms.com to figure out what css properties I'd need to scrape what I wanted.  I got everything but the download link; the most essential part.  The link was there when I inspected it, and the following css should've gotten at it:

`game_info.css("td#rom > a").attribute("href").value`

I proceeded to use pry to see what was actually inside the Nokogir element returned by `game_info.css("td#rom")`...and my heart sank.  It was a script (sigh), containing something called CDATA.  It just looked like gobbledygook; a long, red string of nonsense.  However, I could make out one thing clearly within the jumble: the download url I needed.  So, I proceeded to look up Nokogiri docs to see what methods a CDATA object had that might help me extract the url.  I found nothing, no CDATA#get_url, not anything.  To my chagrin, it seemed that this CDATA object just held the text of the script that generated the download button on the site, and that if I wanted that url, I'd have to go in after it.  So, I came up with this:

`/http:\/\/.+(\.zip|\.7z)/.match(game_info.css("td#rom > script").first.children.first.text`

And out came the url.  I had it!  So, with the first bit of advice Corrine gave discarded, I figured I might as well go for broke.  So I scraped **all** of freeroms.com's pages, over ten thousand in all.  It took almost the length of *High Noon* to finish (I watched it while I waited).  Afterwards, I checked to see if any of the hashes I had created with the scraped info were missing the download url, and there were five.  I checked those games out on the site, and it turned out that those pages were all missing the download button, so it looked like there was nothing to scrape either way.  The hard part was done, and I felt so accomplished having finished that scraping class.  Then, tomorrow came...

## OMG, they found me?!?
The next day, I started writing the other classes for the Gem, and when I was done, I tried a dry run of everything working together.  It was broken, as I expected, but this was unexpectedly broken.  **My scraper wasn't scraping anything anymore!** My mind raced.  "Oh my God, they looked at their server logs and saw that some IP address requested every page on their website, **twice!**" (I did it twice, I forgot to mention that).  "They must think I'm trying to take all their roms and set up another rom site!?!"  Or, "Maybe they thought I was some game publisher web crawling to see if their old games were on the site to request that they be taken down!"  I actually started to feel anxious, so I spoke to my wife.  What could I do?!?  I had no other ideas, and the thought of all that work...

She calmed me down, and she encouraged me to look at the pages again.  But I knew it was no use.  They had put their rom download script within something so complicated that I'd never get at it again.  Then I saw this:

`<td id="romss">`

Yes!  They had taken the script out of `<td id="rom">` and put it in `<td id="romss">`.  All wasn't lost.  I fixed it and tried my test again, but this time **every game had a download link!**  "Oh, they did it to correct the missing buttons", I thought.  So I went to the site to see...but the buttons still weren't there!  One of the games missing the button was Balloon Fight for the NES.  You couldn't download it from their site (still can't), but my program held a link in it's possession.  So I tried it:

`system("curl -Og# \"#{game.download_url}\"")`

And this came out:

![Imgur](http://i.imgur.com/xetBSjO.png)

Praise the Lord!  Now I can sleep.

P.S.  If you're interested, you can get RomLoader going to https://rubygems.org/gems/romloader or https://github.com/jinstrider2000/romloader-cli-gem or by typing `$ gem install romloader` in Bash. 
