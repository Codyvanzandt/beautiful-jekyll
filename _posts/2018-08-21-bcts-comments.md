---
layout: post
title: "Better Coding Through Shakespeare Part 5: Comments"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare]
show-avatar: false
bigimg: /img/BCTS_background.jpg
---

# King John Regrets Commenting and You Should Too

In *King John*, John implores Hubert to,

> Forgive the comment that my passion made / Upon thy feature [10]

And honestly, he's got the right of things. We should all apologize after we comment.

Our good friend Robert explains why with starting clarity:

>The  proper  use  of  comments  is  to  compensate  for  our  failure  to  express  ourself  in
code. Note that I used the word 
failure. I meant it. Comments are always failures. [11]

It is worth repeating one more time: comments are always failures. We fail to express ourselves clearly in code, and so we leave a comment behind to mark that failure. Over time, that comment slowly forgets its purpose as the surrounding system evolves. And then one day, the comment looks up and realizes that it no longer means anything to anyone. It has no purpose. All it can do is wait to be deleted or replaced.

Almost brings a tear to your eye, doesn't it?

If only our programming language was more expressive -- if only we could, as Nick Carroway narrates at the end of *The Great Gatsby* "run faster, stretch out our arms farther...", then we might never need to comment again.

But we're not there yet.

There are still a few kinds of comments that we need.

## Dire Warnings


```python
# DONT CHANGE THIS NUMBER. If it isn't EXACTLY equal to 4, then - believe it or not - the San Andreas Fault will violently hemorrhage
# and cause San Francisco to topple helplessly into the Pacific.
b = 4
```

Occasionally, things like this happen. Systems aren't always as robust as we'd like them, and programmers who've erred leave warnings behind. They're often valuable, and not to be dismissed without at least a little investigation.

## Explaining Interfaces You Don't Own


```python
# This only works if you pass in the username in Pig Latin...
fetch_BookFace_messages(username="odycay anzandtvay")
```

We hope that all public APIs are well-documented and entirely unastonishing. But that's just not the case. Ocassioanlly, Alice-in-Wonderland-esque functions climb out of the rabbit hole and make their way into our systems. We can sputter and swear and jump up and down all we'd like, but there's nothing we can do to change the wonky code. All we can do is leave a comment and hope for the best.

Admittedly, the wonky code might one day changeand our comment will become unnecessary. But 'til then, a few words might save our colleagues loads of time and energy.

### Explaining the Truly Esoteric

Occasionally, you'll find yourself coding in the footsteps of someone with a skill set very different from your own. That previous coder might be, for example, a math PhD. And although she has long left the firm, she did provide a nice equation to help you understand their code:

\begin{align*}
 &a=12+7 \int_0^2
  \left(
    -\frac{1}{4}\left(e^{-4t_1}+e^{4t_1-8}\right)
  \right)\
\end{align*}



Alas, your degree isn't in math, so you don't haveno hope of making sense of this.

*However!*

Your erstwhile colleague also provided a nice, English description of this equation's purpose and implementation in a comment:


```python
# Here's exactly what the equation does and why...
# <insert clear explanation here>
```

Now you can impress your fellow developers at the next meeting with your lucid descriptions of complex computations. 

Hurray!

## Licenses, Test Files, Permissions, Primary Maintainers, and Other Necessities


```python
"""
Primary: Cody VanZandt
Permission Group: Blah Blah and Foo
Tests: /tests/ThingDoer.py
License: Creative Commons 4.0 Attribute
"""

def a_very_important_function(dog):
    return dog.bark()
```

This stuff is pretty important in systems with lots of developers. Some folks might even scrape and mine a large collection of it for its secrets. 

Not *all* such file statistics are useful (things like version number are generally best left to version control software), but a lot of them are. 
