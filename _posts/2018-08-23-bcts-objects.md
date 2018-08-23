---
layout: post
title: "Better Coding Through Shakespeare Part 7: Objects"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare]
show-avatar: false
bigimg: /img/BCTS_background.jpg
---

# Queen Margaret Loves Object-Oriented Programming

In *Henry VI*, Queen Margaret exclaims,

> Doth not the object cheer your heart, my lord?

It sure does, Maragaret. It sure does. 

Objects are great, and object-oriented programming is *fantastic*. And while I don't have the space in this series 
(let alone this section) to read you the riot act on object-oriented programming,
I do have enough space to answer two of the most important questions on classes.

First up...

## When Should You Use a Class?

There are many reasons to use classes!

Here's a useful (though wildly incomplete) list:
- To protect your data from accidental or incorrect manipulation
- To keep data items close to the functions that act on them
- To reduce code reuse
- To model life in code with fidelity
- To provide useful abstractions that make complex systems understandable
- And more!

But at the end of the day, all of these reasons reduce down to one: you have a rag-tag set of variables
(and optionally: functions) that would probably work better if you imposed a little structure. 

So something like this...


```python
def do_something(a, b, c):
    pass

def do_something_else(a, b, c):
    pass

def do_yet_another_thing(a, b, c):
    pass
```

Usually works better like this...


```python
class ABC_Thing(object):
    
    def __init__(self, a, b, c):
        self.a = a
        self.b = b
        self.c = c
        
    def do_something(self):
        pass
    
    def do_something_else(self):
        pass
    
    def do_yet_another_thing(self):
        pass
```

## How Big Should Classes Be?

To quote Robert C. Martin one last time,

>The first rule of classes is that they should be small. The second rule of classes is that *they
should be smaller than that*. [15]

But, we will ask for one last time in this series: just exactly how small *is* small?

Unlike functions, it's not productive to measure size in lines. A class might work with 20 (hopefully small) methods, or with two.

The only reliable way to corral the size of your classes is to look at how many *responsibilities* that class performs. 

Because like functions, a class *should only do one thing*.

For example...


```python
class Lamp(object):
    
    def turn_on(self):
        pass
    
    def turn_off(self):
        pass
    
    def convert_to_AC(self, direct_current):
        pass
    
    def convert_to_DC(self, alternating_current):
        pass
```

Now I'm no electrician, but I'd say that a lamp probably shouldn't know anything about converting different currents. That should probably be in a class called... uh... whatever it is you call the thing that converts currents.

Whatever it is called, the point remains the same: you shoulnd't be afraid to split up an overburdened class into a handful of smaller, cleaner classes.

## Conclusion

Objects are wonderful, particular in a language like python where *everything* is an object. 
If you're less than familiar with Python's object-oriented features or if you're laboring under the delusion
that Python isn't *really* an object-oriented language, then I'd encourage you to spend some in the [Python](https://docs.python.org/3/reference/datamodel.html)
[docs](https://docs.python.org/3/tutorial/classes.html).

Thanks for reading! I hope you'll tune in for the final installment of **Better Coding Through Shakespeare**. There's nothing left but the conclusion!

