---
layout: post
title:  Polymorphic Associations (ActiveRecord)
date:   2017-05-17 07:38:27 +0000
---

I just finished my Sinatra Portfolio project. It's called Fitness Tracker, and man did it take a **LONG** time to code. Too darn long!  But, it was time well spent, and very instructive. Firstly, I really wanted to test my ability to make a "nice" looking web app, so I used Bootstrap to get started, then added my own styling. This took some time initially, as I had never used Bootstrap before (beyond what's in the CSS portion of this curriculum, anyway), but once I overcame the learning curve, Bootstrap proved fairly simple (at least for my purposes).  Secondly, in a late-stage development, I decided to add a feature to my app that I couldn't figure out how to implement...that is, until I learned about polymorphic associations in ActiveRecord. So, what is a polymorphic association, and how did it fit my development needs?

## Conventional Thinking

First, let's discuss how ActiveRecord associations conventionally work. When you declare an ActiveRecord association using the normal naming conventions, you are declaring the unique "class" of object the association will except.  For example, in my app, I declared a *User* model that "has many" objects of class `Exercise` and `Food` associated with it:

```
class User < ActiveRecord::Base
    has_many :foods
    has_many :exercises
end
```

Conversely, the `Exercise` and `Food` models "belong to" a `User`:

```
class Exercise < ActiveRecord::Base
    belongs_to :user
end
```

Now, what I wanted was a way of keeping track of all the instances of `Exercise` and `Food` in *one* place. This way, when a user records a new exercise or meal, it will not only be recorded in the `exercises` or `foods` tables respectively, but also in a *generic* table that holds foreign keys to the two aforementioned tables.  This is where tofu comes in handy.

## Coding Tofu

Tofu is a bland, white bean curd which is usually found as a block at your local market. As foods go, you can't get more generic.  However, vegeterian cooks love tofu because of it's versatility -- it takes on the taste of whatever you cook with it.  I think of polymorphic associations in ActiveRecord as *coding tofu*.  Instead of declaring an association with a *unique* object class, we declare it *generically*, so to allow more than one type of object on a particular association.  For example:

```
class Achievement < ActiveRecord::Base
  belongs_to :activity, polymorphic: true
	validates_presence_of :activity
end
```

Notice that instead of declaring `belongs_to :exercise` or `belongs_to :food`, we write `belongs_to :activity, polymorphic: true`.  This declaration tells ActiveRecord that `activity` is *not* a unique O(bject)R(elational)M(odel) it should look for in the connected database and included classes, but is actually a generic container to hold *any* kind of object that declares an association with `Achievement`. So, in my case, the final definition of my `Exercise` class looked like this:

```
class Exercise < ActiveRecord::Base
    belongs_to :user
    has_one :achievement, as: :activity
    validates_presence_of :name, :calories_burned
end
```

The `Food` class was similar. So, there it is, polymorphic associations in ActiveRecord. This feature of ActiveRecord really came in handy for realizing my vision for my app.  So, thanks polymorphism, you rock! (But you also suck because you made me read TONS of StackOverflow threads to understand you :)
