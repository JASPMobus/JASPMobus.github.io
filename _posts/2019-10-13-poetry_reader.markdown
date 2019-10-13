---
layout: post
title:      "Poetry Reader"
date:       2019-10-13 18:29:56 +0000
permalink:  poetry_reader
---


My final project for the second course I took in programming in college was an analyzer of works of writing that correlated adjectives and nouns together. The whole class had been working around the problem of randomly generating poetry, and random combinations of words could yield phrases such as "the white blackness" or other nonsense. That course's focus on poetry inspired the Poetry Reader project that was the first project I worked on during my Flatiron School Course.

The project was designed to be focused on scraping, and the first thing I thought of was scraping poems off of the Poetry Foundation's website. I investigated the site a bit and found that their poem's webpages all had a number in them, presumably their index in the system that they store poetry in. For instance, the url for G. K. Chesterton's "Lepanto" is https://www.poetryfoundation.org/poems/47917/lepanto.

This led me to the question of how to get the url of a poem on Poetry Foundation, since I certainly couldn't guess these numbers. My first instinct was to look for pages that should contain links to a poem, so I looked to see whether I could go to a poet's page and they'd have a link to all of their works, and fortunately, they did!

![The bottom of G. K. Chesterton's page on the Poetry Foundation Website](https://i.imgur.com/CEYxoBI.png)

Even more fortunately, an author's url was simple to generate given only their name, it simply starts with https://www.poetryfoundation.org/poets/ and ends with their name with any periods removed and spaces replaced with hyphens. As seen above with https://www.poetryfoundation.org/poets/g-k-chesterton. With this, I had a first step: I had to ask for a poet's name first, and then go to their page and find all of their poems. I did this using Open URI and Nokogiri, the tools that we were introduced to in the course. They're very easy to use and I'd recommend them for initial dabblings in scraping.

(For understanding how to ask for certain css selectors in Nokogiri, I found [this tutorial](http://ruby.bastardsbook.com/chapters/html-parsing/) very helpful)

So now, I could finally access the poem's pages. There's one problem that prevents some poems from being read, though: some are put into their website as pdfs in JSTOR, which I couldn't read from the page.

![The page for e. e. cummings's Two Little Whos](https://i.imgur.com/4zpcg3H.png)

I made sure that my program didn't offer these poems as an option, since they were not able to be read by it. It took a little bit to make sure that all of my pages were being found properly, and that poems could be read properly, but in the end I had made a program that could ask for a poet and poem and print out the poem, which was exactly what I wanted.

If you're interested in seeing how it turned out, here's [a link to the rubygems page of my project.](https://rubygems.org/gems/poetry_reader/)
