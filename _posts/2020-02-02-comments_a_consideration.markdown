---
layout: post
title:      "Comments, A Consideration"
date:       2020-02-03 03:35:09 +0000
permalink:  comments_a_consideration
---


New programmers are often told that comments are vitally important for readability, and that's true, but sometimes it's hard to know what should be put into the comments. In this post, I'm going to cover two different strategies that I've found beneficial: the overview and the example.

I call a comment an overview if it's purpose is to explain what code does. Oftentimes, one has to think about what a line of code does after reading it, especially for more involved lines. That is, why they exist or what they do isn't always immediately clear. An easy way to solve this sort of problem is just to put a comment right above a confusing line or group of lines and describe what they do or how they fit into the purpose of their function. Here's a quick example of what I'm talking about:

```
    #checks to see if any of the characters in chars is included in str
    def self.one_of_include?(str, chars)
        #If there's no chars left to check, then none of the chars were in it
        if chars == []
            return false
        #If the first char is in str, we're done
        elsif str.include?(chars[0])
            return true
        end

        #Recursively calling the function after removing the first char
        chars.shift
        
        one_of_include?(str, chars)
    end
```

It's hopefully very clear what the function and each part of it does, probably so even without as many comments as there are, but I included them as an outline originally and didn't get rid of them after I had written the code. The idea here is to make reading the code unnecessary to understanding its function. You obviously don't need to include a paragraph about why your function works-I didn't in this example-but writing out how it works helps you plan out each line, and also helps notice errors when you compare what you want the line to do from the comment against the line itself.

The other strategy that I've developed is the example. By example, I mean including a literal input or output that could be expected. The reason for doing this is simple: you can't forget what format your data is in if you have an exemplar piece right in front of you. I started doing this after I forgot one too many times what *exact* structure I'm manipulating. Here's an example of this kind of comment in context:

```
    #takes date and time entries and generates a datetime object
    def self.generate_datetime(date, time)
        #examples of received date and time: date: "2019-12-15" time: "4:00"
        #example of datetime creation DateTime.new(2001,2,3,4,5,6) 
                                      #=> #<DateTime: 2001-02-03T04:05:06+00:00>
        date_info   = date.split("-")
        year        = date_info[0].to_i
        month       = date_info[1].to_i
        day         = date_info[2].to_i

        time_info = time.split(":")
        hour    = time_info[0].to_i
        minute  = time_info[1].to_i

        DateTime.new(year, month, day, hour, minute, 0)
    end
```

Here, I specify the format that the inputs come in, so that I know what order all the information comes in. This bit is obvious to me, since I wrote the code that uses this function, but it's always cleaner to just mention it. More importantly for me while I was coding is the second example. As a general rule, if I have to look up something in the documentation, and it's something that only needs a single line to explain, I'm going to copy over the example that they give me so that I don't have to switch between tabs a couple times while I'm building the function. In this case, I wasn't sure how to create a DateTime, so I just looked it up and copied over the format so that I had it on the page where I was coding.

These are just two strategies proven useful for me. Obviously, there are many different things that one can do, and probably cleaner ways to do what I do than I've shown, but the important thing to remember is that comments have two purposes. The first is the one that's talked about all the time: to help a reader of the code understand it better. The second one, I feel, is less often emphasized: to help the builder of the code focus their thoughts. As long as your comments are relevant and helpful to one of these two points, I would encourage you to put them in, until you've developed your own rhythm and strategies that you can exercise while you code.
