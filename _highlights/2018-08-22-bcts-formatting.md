---
layout: post
title: "Better Coding Through Shakespeare"
subtitle: "Part Six: Formatting"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare, teaching]
show-avatar: false
bigimg: /img/BCTS_background.jpg
highlight: "BetterCodingThroughShakespeare"
---

# Petruchio Needs Better Formatting

In *The Taming of the Shrew*, Gremio says to Petruchio,

> You are too blunt. Go to it orderly [12]

Well let me tell you, going about things in an orderly manner isn't just good advice for Petruchio. 
It's *essential* advice for developers.

You see, poor formatting can hamstring your readers just as easily as poor design.

If no one knows where to look for anything, the task of understanding what's actually happening grows more difficult.

You (and everyone who reads your code) will be grateful if you spend a litte time thinking about your formatting.

And here's the first question you should consider...

## How Long Should a File Be? 

The short answer? Eh... I'm not entirely sure.

Just long enough and not any longer, I think. 

1000 lines is usually too many, and a single line is usually too few. 
In truth, file length isn't the sort of thing you should optimize. 
You should instead ask yourself "In one sentence, what is this file doing?" 
If you can't answer that question without a slough of commas and conjuctions, 
then you're file is too long. See, files - just like functions - should only do one thing.

## Where Should I Put Things?

Ah, now this question is much easier!

I am, unsurprisingly, a huge fan of Robert C. Martin's answer...

>We would like a source file to be like a newspaper article. The name should be simple
but explanatory. The name, by itself, should be sufficient to tell us whether we are in the
right  module  or  not.  The  topmost  parts  of  the  source  file  should  provide  the  high-level
concepts and algorithms. Detail should increase as we move downward, until at the end
we find the lowest level functions and details in the source file. [13]

That is a fantastic simile: a source file is a like a *newspaper article*.

Let's look an example of this done *really* wrong:


```python
def add_report_content(empty_report):
    content = get_report_content()
    full_report = empty_report + content
    return full_report

def make_unformatted_report():
    return "An unformatted report"

def format_report(unformatted_report):
    return unformatted_report.format()

def make_report_base():
    unformatted_report = make_unformatted_report()
    return format_report(unformatted_report)

def get_report_content():
    return "Some content."

def make_report():
    report_base = make_report_base()
    finished_report = add_report_content(report_base)
    return finished_report
```

How obvious is this program's flow? Can you glance through it and tell me how these functions work together? Which functions depend on which other functions?

It's not obvious. 

Sure, you can probably look around and figure out that everything starts with `make_report`, but the file leads you on a merry chase - up and down, and up and down, and... Eh. It's a mess.

Compare with this...


```python
def make_report():
    report_base = make_report_base()
    finished_report = add_report_content(report_base)
    return finished_report

def make_report_base():
    unformatted_report = make_unformatted_report()
    report_base = format_report(unformatted_report)
    return report_base

def make_unformatted_report():
    return "An unformatted report"

def format_report(unformatted_report):
    return unformatted_report.format()

def add_report_content(empty_report):
    content = get_report_content()
    full_report = empty_report + content
    return full_report

def get_report_content():
    return "Some content."
```

Now that's *much* better!

What does this file do? It's right at the top: it makes a report with `make_report`.

You can follow the logic of `make_report` first through `make_report_base` and then through `add_report_content`. Each of which is located (along with its dependent functions) in order right below `make_report`.

It's just like a well structured essay:
- Thesis (`make_report`)
    - Topic 1 (`make_report_base`)
        - Support for Topic 1 (`make_unformatted_report`)
        - Support for Topic 1 (`format_report`)
    - Topic 2 (`add_report_content`)
        - Support for Topic 2 (`get_report_content)

### Do Not Line Up Your Assignments

Lastly, a minor and perhaps controversial suggestion.

Let's say you have a big ol' load of assignment statements...


```python
def some_function():
    a_second_long_variable = 5
    short_var = 1
    an_extremely_long_variable_name = 6
    longer_variable = 3
    also_short = 2
    an_even_longer_variable = 4
    return "Boo! Terrible!"
```

So you think to yourself, 

"Gee, those staggered assignment statements sure look ugly. Let me fix that up..."


```python
def some_function():
    a_second_long_variable =          5
    short_var =                       1
    an_extremely_long_variable_name = 6
    longer_variable =                 3
    also_short =                      2
    an_even_longer_variable =         4
    return "Boo! Terrible!"
```

Ah! That's much better!

Except... it isn't better at all. It's worse.

Firstly, you missed the point. The problem isn't that loads of staggered assignments right in a row look ugly. The problem is that you have loads of staggered assignments. Don't try to hide that issue under a fresh coat of paint; fix it. 

Secondly, you forgot what assignment statements are really about. You've drawn the eye away from the assignments and towards the giant list of values. But *assignment* is the important thing here, not the giant list of values.

And finally, this non-traditional assignment plays tricks on the mind. If I didn't know better, I *might* think for a crazy second that `short_var` is equal to a large amount of whitespace followed by a `1`. 

Weird.

## Conclusion

That's a wrap on formatting! There's nothing especially *challenging* about it, but so many programmers still
end up sending hideously formatted code out into the wild. Don't count yourself among them! Spend those
extra few moments formatting your code; you'll thank yourself for it later.

Thanks for joining me in my disucssion of formatting. Keep reading on as **Better Coding Through Shakespeare**
heads into the homestretch with [a section on classes!](/2018-08-23-bcts-objects)

[12] Shakespeare, William. *The Taming of the Shrew* II.i

[13] Martin, Robert C. *Clean Code.* 77
