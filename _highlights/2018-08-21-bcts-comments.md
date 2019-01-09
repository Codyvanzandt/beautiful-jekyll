---
layout: post
title: "Better Coding Through Shakespeare"
subtitle: "Part Five: Comments"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare, teaching]
show-avatar: true
bigimg: /img/BCTS_background.jpg
highlight: "BetterCodingThroughShakespeare"
---

# King John Regrets Commenting and You Should Too

In *King John*, John implores Hubert to,

> Forgive the comment that my passion made / Upon thy feature [10]

And honestly, he's got the right of things. We should all apologize after we comment.

Our good friend Robert explains why with startling clarity:

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
# DONT CHANGE THIS NUMBER. If it isn't EXACTLY equal to 4, then
# - believe it or not - the San Andreas Fault will hemorrhage
# and cause San Francisco to topple helplessly into the Pacific.
b = 4
```

Occasionally, things like this happen. Systems aren't always as robust as we'd like them, and programmers who've erred leave warnings behind. These little warnings are not to be dismissed out of hand.

## Explaining Interfaces You Don't Own


```python
# This only works if you pass in the username in Pig Latin...
fetch_BookFace_messages(username="odycay anzandtvay")
```

We weren't expecting BookFace's API to require Pig Latin usernames. But it does, and that's just the world we have to live in.

We always hope that public APIs are well-documented and entirely unastonishing. But that's just not the case. Ocassioanlly, Alice-in-Wonderland-esque functions climb out of the rabbit hole and make their way into our systems. We can sputter and swear and jump up and down all we'd like, but there's nothing we can do to change the wonky code. All we can do is leave a comment and hope for the best.

Admittedly, the wonky code might one day changeand our comment will become unnecessary. But 'til then, a few words might save our colleagues loads of time and energy.

### Explaining the Truly Esoteric

Occasionally, you'll find yourself coding in the footsteps of someone with a skill set very different from your own. That previous coder might be, for example, a math PhD. And although she has long left the firm, she did provide a nice equation to help you understand her code:

<figure>
  <center> 
    <img src="/img/crazy_math.gif" align="middle" alt="intimidating mathematics">
  </center>
</figure>


Alas, your degree isn't in math, so you have no hope of making sense of this.

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

This stuff is pretty important in systems with lots of developers. Its the kind of information that gets used *everywhere*. And unfortunately, there's not really a better way of embedding metadata into your code than, well, embedding metadata into your code. And so, we muddle through with  comments.

## Conclusion

Just so we're clear, I'm not against comments. A well-placed comment can be an incredible boon to a programmer in need. I am, however, against most comments. 

Alas, neither are languages nor our programming environments are expressive enough to communicate everything that needs to be said about our programs. And so we (rightfully) turn to comments to fill in the gaps. 

Perhaps one day we'll only write code in our code files, but until then, we'll muddle through.

Tune in next time as **Better Coding Through Shakespeare** turns its attention to the most underrated aspect of programming: [proper formatting.](/highlights/2018-08-22-bcts-formatting) Ignore it at your peril!

[10] Shakespeare, William. *King John* IV.iii

[11] Martin, Robert C. *Clean Code.* 54
