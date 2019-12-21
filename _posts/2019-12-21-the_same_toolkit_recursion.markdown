---
layout: post
title:      "The Same Toolkit: Recursion"
date:       2019-12-21 21:43:41 +0000
permalink:  the_same_toolkit_recursion
---


Due to the close relationship between mathematics and computer science, many strategies that are used in mathematical proofs have programming equivalents. The first one that I noticed specifically is the correlation between recursive functions and proofs by induction.

A recursive function is a function that calls itself. Many people who are just picking up programming don't even think to try it, because the idea of not using a word in its own definition has been ingrained in them throughout their schooling. Let me give you a simple example here:

```
def countdown(num)
  if num==0
    puts "Liftoff!"
  else
    puts num
		
    countdown(num-1)
  end
end
```

There are three main parts that you can see in this function: the termination condition, the action, and the recursive call. The termination condition is seen when the countdown function ```puts "Liftoff!"``` when we get to 0. I call this the termination condition because that's when the function call ends. The action is what you do on each step (because if you aren't doing anything when you call the function, you probably shouldn't call the function). Here, that is just ```puts num``` The recursive call is the part that really separates a recursive function from other types: this is when the function calls itself, as with our ```countdown(num-1)``` It's important to note, though, that when we do a recursive call *we are taking one step closer to the termination condition.* If we didn't do this, then the function would never reach the termination condition, and we'd have an infinite loop of a function calling itself. This is why we're calling countdown on num-1 for the next step.

Now, there's clearly an equivalent function without using recursion in this case:

```
def countdown(num)
  while num>0 do
    puts num
	
	  num-=1
  end

  puts "Liftoff!"
end 
```

But recursion is another strategy that you may want to use if you're thinking about solving a problem by taking several small steps. In some cases, you may find that it can solve the problem faster, or perhaps more readably.

Proofs by induction are similarly structured, except that they usually builds up from a base instead of down to one. They have three steps, too: the base case, the induction hypothesis, and the inductive step. Let me give you a simple proof to look at as an example.

Fact 1 (transitivity): If a < b and b < c, then a < c.

Theorem: If a1 < a2 < ... < an, then a1 < an.

Proof: by induction on n

Base Case: let n=2

Then a1 < a2.

Induction Hypothesis: Let a1 < a2 < ... < ak imply a1 < ak for some positive integer k.

Inductive Step: let n=k+1.

Then a1 < a2 < ... < ak < a(k+1). Since a1 < a2 < ... < ak, by the Induction Hypothesis, a1 < ak. Since a1 < ak and ak < a(k+1), by Transitivity, a1 < a(k+1).

QED

So, the structure and language might seem a little bizarre to you, but I made sure to label the important parts for you. In the base case, the idea is to address the smallest situation where your proof holds. In this case, I chose to use the case where there's only two things to compare. Here, the conclusion was already reached upon stating the initial condition, so I didn't have to do any extra work. The next part is the induction hypothesis, this is were you suppose that the theorem holds for some general case. The third part, the inductive step, is where you prove that the theorem holds for the case immediately subsequent to the case assumed to work in the induction hypothesis. These two parts together show that for any case where the theorem holds, the next case does, and since we know it holds for the first presented case, if holds for every case beyond and including the base case. Obviously, this isn't a particularly enlightening theorem. In fact, it was as simple as I could make it while still having all of the requisite parts, but hopefully that gives you at least some idea of how induction works.

You may see the relationship between recursive functions and proofs by induction without me having to expound on it, but if you don't, let me try and go over it explicitly: Both of them have a definite case that you're solving manually (the termination condition for recursive functions and the base case for proofs by induction), and both of them show you how to go from one step to the next (the recursive call for recursive functions and the inductive step with proofs by induction). In this way, the only real difference is in the structure (recursive functions are written in code and proofs by induction in "math-speak"). Obviously, the way recursive functions pare down the initial input and proofs by induction build up from the base case are another difference, but that's more about what you're trying to do with the tool, rather than what tool you use.
