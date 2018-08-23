---
layout: post
title: "Better Coding Through Shakespeare Part 4: Arguments"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare]
show-avatar: false
bigimg: /img/BCTS_background.jpg
---

# **Don Adriano Doesn't Understand Arguments**

In *Love's Labor's Lost*, Don Adriano exclaims,

> Come hither, come hither. How did this argument begin? [8]

He's confused, and that's perfectly understandable. Arguments complicate code. There's no way around it. They make testing, understanding, and debugging code more difficult, and that difficulty grows *exponentially* in the number of arguments included.

Naturally, our friend Robert C. Martin agrees:

> The  ideal  number  of  arguments  for  a  function  is
zero (niladic). Next comes one (monadic), followed
closely  by  two  (dyadic).  Three  arguments  (triadic)
should be avoided where possible. More than three
(polyadic)  requires  very  special  justification — and
then shouldn’t be used anyway. [9]

As far as I'm concerned, that's the best answer to "How many arguments should my function take?"

The big question is, then, "How do I write functions like that?"

Fear not! Here are a few tips that'll help you create smart, safe, understandable arguments.

## Make Your Arguments Classy

You might be writing a function like this...


```python
def manipulate_3D_point(x, y, z):
    # Do something nifty
    pass
```

Any function that needs to know about a point sitting in 3D space will need *at least* three arguments: x, y, and z. But that's not a stellar start to writing functions with only a few arguments.

What's a programmer to do?

Well, since `x`, `y`, and `z` are all necessary to make a 3D point, they should be bound up in a 3D point class!


```python
class Point_3D(object):
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z
        
def manipulate_3D_point( a_3D_point ):
    # Do something nifty
    pass
```

*Much* better! You're function has all the information it needs, you've minimized your argument list, and I'd even argue that you added significant clarity to your code by adding a simple little class. (Note: for Pythonic fun with classes that simply bind data together, check out Python's [namedtuple](https://docs.python.org/3/library/collections.html#collections.namedtuple).

Granted, this example is pretty obvious. But the point remains (pun intended): when your argument list starts to grow, some of your arguments are likely related enough to make a coherent class.

## Make Sure Arguments Don't Come OUT of Functions

Arguments are confusing enough. But arguments that come *out* of functions are even worse.

At this point you should be a little confused. Don't arguments go *into* functions by definition? Why yes. They do. But if you're not careful, they can surprise you (and everyone else) by coming back *out* of your functions. Let me illustrate.

Imagine that you're reading some (icky) code, and you stumble across this little gem:

```python
text = extend_text( text, extend_value )
```

This line of code looks like it probably...
- Takes a text and another value as arguments
- Extends the text using `extend_value`
- ...and then returns text again.

So text goes *in*, and then comes back *out*. Yuck.

This works significantly better as
```python
text.extend( value )
```
Ah, much better! `value` goes *in*, `text` comes *out*, and no one is surprised.

### Flags are for Countries, Not for Programmers

Programmers *love* passing flags to functions. 

Like so...


```python
class SomeCrazyData(object):
    def output_data(self, as_CSV):
        if as_CSV:
            # Output the data as CSV
            return some_CSV
        else:
            # Output the data as JSON
            return some_JSON
```

Look how simple! Now you can get `output_data` to return the data in CSV *or* JSON format. All you have to do is pass a boolean flag and WHAM! You're done!

But this function makes me feel really uneasy.

- `as_CSV` is a boolean. If its value is `True`, then it returns a CSV. If its value is the *opposite* of `True`, then it returns... Uh... Well I guess it returns the opposite of a CSV. Whatever that is. I haven't the foggiest idea.
- Functions do one thing! But... This function does two things. One for the `True` case and another for the `False` case. That's unfortunate.
- The function's name and arguments don't tell me what I can use the function for! To figure that out, I have to rely on good documentation (Ahahahahaha! Yeah right...) or look around inside the function until I figure it out.

To recap, we have a function with an ambiguous argument that does two things without making it clear from its definition what those two things are. 

Yuck.

It's a much better idea to do something like this:


```python
class SomeCrazyData(object):
    def output_data_as_CSV(self):
        # Output the data as CSV
        return some_CSV
    def output_data_as_JSON(self):
        # Output the data as JSON
        return some_JSON
```

Do yourself a favor: don't use flags unless you *absolutely* have to.

### Leave "None" Alone!

None is so tempting. But it's usually a sub-optimal idea.

It is a value that represents the absence of any value. And that alone should make you feel weird.

You cannot iterate through None. You cannot cannot use it as a function. It has no attributes, and it has no methods. All None will ever do for you is raise the exception "AttributeError: 'NoneType' object has no attribute..."

If you return it from a function, it will force every caller of your function to perform None-checks. If they forget a check, they risk an AttributeError. 

If you pass it into a function, (especially as a default argument), you'll obfuscate your logic with None-checks and doom your helper functions to the same fate.

And yet, None still gets used because it is convenient. It has no features: all you can do with it is ask "Are you None?" 

Given its simple featurelessness, folks use None to store all kinds of random information: Did I ever set this variable? Did I call this function? Did I succeed in some task? *All* sorts of things. 

They're all a mistake. There is *always* a better way to signal your intention than with a None.

You could...
- Raise an exception (potenially in a try-except block) to signal that something invalid happened
- Ditch the default argument. If an argument doesn't have a sensible default, then why are you trying to force one on it?
- Use a sensible, non-mutable default: a custom "empty" class or an enum.
- Re-architect your functions and logic so that they don't need None. Your code will almost certainly be more robust as a result.

Just try not to use None.

If you're still not convinced, consider for a moment that Turing award-winning computer scientist Tony Hoare [believes that None (aka: the null refernece) is a mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare). And he invented it.

## Conclusion

Be careful with arguments. They're so simple on the surface, but they can wreak havoc if you let them run unchcked through your code. You don't have to necessarily agree with my (rather controversial) stances on None and booleans, but you should absolutely take a moment or two to think through the impact that your arguments will have on your functions.

I hope to see you for the next section of **Better Coding Through Shakespeare** where we'll unpack one of the most underrated parts of programming: proper formatting! Ignore it at your peril!

[8] Shakespeare, William. Love's Labor's Lost. III.i

[9] Martin, Robert C. Clean Code. 40
