---
layout: post
title:      "Coding like Brian Wilson"
date:       2018-07-31 01:29:22 +0000
permalink:  coding_like_brian_wilson
---


![](https://i.imgur.com/RkTSDC6.jpg)

I had a revelation upon finishing my Rails with JQuery Frontend project for Flatiron School:

**I am the Brian Wilson of coding.**

Now, for those don't who know, Brian Wilson is the troubled genius behind the classic pop/rock band The Beach Boys.  To be clear, I don't intend to claim any genius with regards to my coding abilities.  However, like the Brian Wilson of legend, I find that I conceive overly ambitious projects which take [too long to complete](http://www.one-line-at-a-time.com/out_of_the_black_lodge), I am easily *consumed* with their minute details, and I strive to see my visions realized *without compromise*, sanity be damned.  This project wasn't an exception, and while I'm very gratified by the [end results](https://github.com/jinstrider2000/fitness-tracker-rails), I'm realizing that unchecked personal ambition is a recipe for exhaustion.  But I'll get to that later.

## Don't Back Down

My project, *Fitness Tracker*, is something like a cross between Fitbit and Twitter.  You can log your daily food and exercise, connect to others on the platform via Twitter-like relationships, and see everyone's activity on a news feed.  The basics were all worked out in the project's previous iteration, and I simply had to redesign the back and front-ends to utilize JSON and Ajax.  However, mine was a problem of scale; the original, Rails-only *Fitness Tracker* was a gigantic project (for me), weighing in at approximately 2000 lines of original code (accounting for whitespace, and excluding migrations and Bootstrap elements that I copied and heavily modified for my purposes).  So, I had the daunting task of poring over that code again (essentially re-learning what I had made) and seeing how I could integrate the required changes, but I was up for it.

## Wouldn't It Be Nice

The biggest change I planned to implement was to make the news feed more dynamic.  The news feed items are a `has_many` property on the `user` model, and one of the requirements was that I display a similar property via Ajax.  I thought I'd go one step further and use Ajax to display *newly created feed items* once per minute.  This was quite a task for a novice like myself, and it required testing methods I had never previously employed (e.g. simultaneously running different instances of the app on multiple browsers to test creating news feed items on one, and observing those items dynamically populate on the other ones, etc).  Needless to say, implementing this new feature was really quite exciting, if a bit frustrating, and to make a now hackneyed observation: I experienced *flow*.

## Hang on to your Ego

Finally, all my work and retrospection have led me to these questions: Why do I do this to myself?  What am I trying to prove?  And to whom?  The honest answer is that I'm trying to prove to *myself* that I'm a good coder.  I'm not new to coding; I have a B.A. in Computer Science.  However, that hasn't exempted me from serious *imposter syndrome*.  So, the armchair psychologist in me *knows* that the complexity of my projects is at least partially motivated by inadequacy.  Yet, before I'm too self-effacing, I remember that Brian Wilson's beautiful *Pet Sounds* was at least partially motivated by the inadequacy he felt listening The Beatles' *Rubber Soul*. Either way, I know that you can't work like this forever, because if you do you'll burn yourself out (see The Beach Boys' *SMiLE*), but sometimes you **need** to test your limits.  And I'm glad I did, because now when I visit some websites, occasionally can honestly and confidently say, "Hey, I can code that".
