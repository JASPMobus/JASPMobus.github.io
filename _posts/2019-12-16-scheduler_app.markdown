---
layout: post
title:      "Scheduler App"
date:       2019-12-16 22:36:59 +0000
permalink:  scheduler_app
---


The inspiration for this project is the EagleSoft software from Patterson, which we use in the dental office that I'm working at right now. I knew that I couldn't make a better one (certainly not in two weeks), but the idea of a scheduling app was something that I could design and advance fairly quickly because I use scheduling software all the time.

I knew that I wanted to have a hierarchy of user types, with admins able to edit everything and basic users only able to edit themselves and their own appointments, and I created two intermediate types, providers and schedulers, with different basic tasks; providers are the only user-type that appointments can be scheduled with, and schedulers have basically all edit privileges that aren't reserved solely for admins.

This unfortunately left a lot of pages requiring user-type checks to display only information appropriate for a certain type of user to see, but I managed it. Below, I'll show you a couple screens of the same appointment as viewed by its user and an admin, respectively.

![User viewing their own appointment](https://i.imgur.com/Mp6Yv6k.png) ![Admin viewing the same appointment](https://i.imgur.com/w5hRN6J.png)

As you can see, there's a lot of differences! There are also a lot of things that users aren't allowed to view at all, like the service masterlist:

![Services page](https://i.imgur.com/YMa6GNr.png)


The basic structure of the project is that users can make appointments with providers (which are users with a their kind variable set to "provider"), and they can have services attached to them. Services are copies of StandardServices (mostly because when they were the same class, I was getting too many issues and I decided to split them up). I also made a helper class called Temporal to help with checking availabilities and other time-related issues.

The one other thing I wanted to share, mostly because I'm really proud about being able to make it, even if only simply, is the schedule page:

![Schedule page](https://i.imgur.com/ZyqBkEv.png)

The blacked-out regions mark where appointments are already scheduled for the providers (whether with clients or with themselves as an acting-client), and the others have a link to make an appointment starting at the given time with that provider:

![Scheduling an appointment from a schedule page link](https://i.imgur.com/xN8Ne4V.png)

If you're interested in looking at in in detail,  [here's the Github link!](https://github.com/JASPMobus/scheduler)


