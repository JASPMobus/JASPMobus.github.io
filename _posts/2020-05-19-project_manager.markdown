---
layout: post
title:      "Project Manager"
date:       2020-05-20 02:23:52 +0000
permalink:  project_manager
---


One thing that I've seen recommended a lot throughout the videos I've seen and articles I've read for new programmers to try and build is a project management app. In the third section of my programming course at Flatiron School, that was exactly what I decided to make.

The first step I went about was drawing up an outline of what sort of models and associations I would need. For the purposes of this project, I decided on a very simple layout, with only three models: Project, Task, and User, having learned that overcomplication was not a benefit in creating an app from my Scheduler app. Projects and Users both have many of the other through Tasks, which is to say that projects have many people working on tasks for them, and users can work on tasks for multiple projects at the same time. I also added a foreign key owner_id to projects in order to future-proof the app, in case I wanted to start adding restrictions on privileges for editing projects and related tasks at some point in the future.

With a rough outline of my project manager app done, I started on the most new if not the most difficult part of the app: allowing users to sign in through other websites. I chose to use GitHub as the site I'd add on as the primary focus of this feature, since the project manager is focused on coding projects as a consequence of being one of my creations, although I suppose none of its actual infrastructure necessarily implies such.

I had a bit of difficulty setting up OmniAuth with Devise to work with GitHub. The issue, as far as I understand it having solved it, was that the gems' versions weren't synced up correctly at some point, and adding in the gem "omniauth-oauth2" fixed the issue. If you're having trouble where everything should be matching up correctly, but isn't, that's what worked for me.

It took me a while to realize that I had to add some code in order to get User to store names, since by default, only email is included as the identifier for users in the form, and I logged into my app through GitHub. It was one of the last issues I resolved, because I forgot to test it until the end. I'd recommend to anyone allowing users to log in through other apps to check first to make sure that you can log in through your own app first, with all values being stored correctly.

Because tasks are all linked to projects, and only really make sense in the context of projects, I nested them under projects, so that urls to view them would only ever appear through them (e.g. "/projects/1/tasks/1", never "/tasks/1"). The only url that starts with "tasks" is "/tasks/mine", where a user can view all of the tasks assigned to them, broken down by project.

It was a lot of fun to make the app, especially using it once it was working well enough to plan out my next step. If you want to take a look at it, it can be found here: https://github.com/JASPMobus/ProjectManager.
