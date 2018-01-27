---
layout: post
title:      "Out of the Black Lodge"
date:       2018-01-27 09:43:14 -0500
permalink:  out_of_the_black_lodge
---


If you clicked into this blog post with *knowing* intrigue at the title, let me congratulate you on your good taste in television shows! *Twin Peaks* is a great show! Those of us who saw last year's *The Return* finally witnessed Agent Cooper's long awaited exit from the Black Lodge; the nightmarish alternate dimension in which he had been trapped for 25 years. When he emerged from the Lodge, he was, understandably, *changed*. The passage of time had left Cooper visibly wizened, *much quieter*, and ultimately wiser. Now, you should be asking yourself, what does this have to do with coding? (Which is, of course, the ostensible point of this entire blog.) Well, I just finished my Rails Portfolio Project, and what should have been a (at most) two week endeavor, **took much longer for me**. And not to sound too hyperbolic, but I too feel wizened, quieter, and wiser after my experience. My story isn't as exciting as Cooper's, but I invite you to read my *abridged* tale.

**Warning**: Deep cut *Twin Peaks* references ahead!

## Among the sycamore trees
![](https://media.giphy.com/media/SbaQGo5fdI50s/giphy.gif)

To save time on my Rails project, I figured I'd simply modify and augment my previous Sinatra project, *Fitness Tracker*. That app was a basic CRUD where you could log your exercise and food consumption. I thought, "I spent alot of time styling it (so that's done), and all I have to do is rejigger the code base for Rails and add a feature or two."  Simple right?

## Open the red curtain, enter The Lodge
![](https://unwrappingtheplastic.files.wordpress.com/2017/04/ba5d80eddd37ff9e9bb4debee8582c6e.gif)

The first feature addition was to have *Twitter-like* relationships to other users. I figured out the basics of that feature, on paper, fairly quickly. Then I thought, "Hmm, maybe I should try to put relationship status messages like Twitter does...". That's simple, you query the *relationships* join table for reciprocal relationships. Ok, but then I thought, "Well, If this were a large scale app, it would be a pain to hit the database twice *per every user in an index view*, just to put a "following each other" message in the user partial. So I figured a way to do it one query -- add a boolean column to *relationships* which reflects *reliably*<sup>1</sup> on every row whether the reciporal relationship exists in the table (you can manage this by declaring `before_*` hooks in the model). Ok, but then I thought, "Maybe it would be fun to add the blocking and muting functions of Twitter as well".  No problem, just add new models/tables and use Pundit for authorization. Ok, but then I thought...

## Falling
![](https://media.giphy.com/media/xUA7aQdu2mdFnOgptm/source.gif)

About **two months** in, I started to realize something was amiss. I had added all the aforementioned features, plus some others, and written and refactored code multiple times. I had tested the backend through `rails c -s` and everything seemed to work. But then I thought, "What if I want the website to display...*in Spanish*?" (!!) So I looked at the "Digger Deeper" (yes, indeed) section of the Rails Guide and read about I18n...

## Out of The Lodge
![](https://thegameofnerds.files.wordpress.com/2017/06/303-coop-sucked-in.gif?w=730)

I'm happy to say that the app is finished. I got *everything* I wanted into it, and it only took **4 months and 180 commits!** Now what do I have to say for myself, now that its done? What did I learn? First, I learned that you *need* to set hard personal deadlines so as to avoid *feature creep*. The temptation for bigger and better is always there, and that impulse might not be so bad, but in the real world -- the world of deadlines -- you can't always aim for the moon; you need to set reasonable goals, or you'll get lost in the weeds. Second, I learned that its sometimes good to test your limits. Now that might seem like an abrogation of the former lesson, but it isn't, its more like a balance to it. Its true that you can't always (reasonably) aim for the moon, but its good to try for it once in a while, and in my modest (in the grand scheme of things) case, I hit it.

## Mr. Jackpots
![](https://i.redd.it/6mstt19eagzy.gif)

I'm going to take a week off from coding before I move on to the Javascript portion of the curriculum. I need a break. I'm exhusted and grateful for the experience I had making this app, but I have, to use a gambling metaphor, blown my wad. I don't think I have the wherewithal to invest this much time and effort in a Flatiron project again, but I learned some valuable lessons on this project; lessons which, while they came at a high initial cost, I expect will pay greater dividends in my career. So, to quote Laura Palmer, "See you again in 25 years (hopefully sooner), meanwhile..."

![](https://78.media.tumblr.com/5a97c102f65f258fb8f9ca30eabef825/tumblr_oqsxdcaEGB1qbxh0uo1_500.gif)

<sup>1</sup>I don't know if my solution fully considers the readers/writers threading problem associated with *concurrent* database writes. Maybe Rails does this in the background? I don't know, look it up. Also, check out the app [here](https://github.com/jinstrider2000/fitness-tracker-rails). I worked hard on it, dammit! 
