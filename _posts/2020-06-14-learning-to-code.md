---
layout: post
show-post: true
title: Learning to Code for Computational Humanities Research
---

Here's a super short summary of this long-ish post:

> You need to learn to code to do this kind of work. Specifically, you should learn the [Python programming language](https://www.python.org/) by auditing [these courses](https://www.coursera.org/specializations/computer-fundamentals),
then learn data science by auditing [these courses](https://www.coursera.org/specializations/data-science-python). If you prefer books, read [this one](https://greenteapress.com/wp/think-python-2e/) then [this one](https://www.amazon.com/Python-Data-Analysis-Wrangling-IPython/dp/1491957662/).
You should also read [this](http://www.karsdorp.io/python-course), [this](http://walshbr.com/textanalysiscoursebook/), [this](https://github.com/sgsinclair/alta/blob/915579fc1c6926b8fcb2a38f95349a2d6cba00b5/ipynb/ArtOfLiteraryTextAnalysis.ipynb), and [this](https://r4thehumanities.home.blog/) to learn how humanistic data science works.
Definitely read [this journal](https://culturalanalytics.org/) and [this one](https://academic.oup.com/dsh). If you have questions, <a href="mailto:cody.a.vanzandt@gmail.com">email me</a> -- I'd love to hear from you.

*Whew!* Now that that's done, take a breath and then check out the rest of this post for all of the tasty detail, explanation, and nuance!

## Should You Learn to Code?

I'll start off boldly: yes. 

Computational humanities research is super idiosyncratic, and the existing tools will only get you so far. 
I *guarantee* that you will pose questions that cannot be answered without building your own tools. And for that, you'll need to code.

And if by some miracle you never need to build a single tool and can instead rely entirely on tools built by others, you still have a scholarly obligation to understand how those tools work.
Without the ability to read code, you have no way to verify for yourself that the tools are behaving how you'd like. That's a problem.

So, if you want to do computational humanities research, you *must* learn to code.
Luckily, coding is immensely enjoyable, deeply satisfying, and absurdly useful -- so claiming that you *must* learn to code is hardly condemning
you to some terrible fate. There's every chance that you could fall in love and find yourself a cherished lifelong hobby.

## Given All That, What Kind of Coding Should You Learn?
You'll want to get comfortable with the [Python](https://www.python.org/) programming language. 
It's tricky to say exactly how comfortable is *comfortable*, but to use spoken language as a metaphor, you should be aiming for "I can hold down a conversation" and not "I'm basically a native speaker".

A single semester-length course in Python is enough to get the fundamentals under your fingers. 
After a second course, you'll be quite comfortable with the language.
You can replace "course" with "quality textbook" and get similar results, as long as you commit to working through the coding exercises. 

After picking up basic Python, you're ready to enter into the wide, *wide* world of data science.
Traditional Python-centric data science books and courses can provide an excellent foundation, although you'll likely
want to supplement these resources with a book or course that focuses specifically on analyzing humanities data.
Our data tend to be somewhat quirkier than what our STEM and social science colleagues work with. 
Similarly, we tend to have different goals, interpretive processes, and evidentiary standards. It's worth learning how these
differences affect the standard data science workflow. 

N.B.: Other folks might recommend you learn the R programming language instead of Python.
There's a longstanding "Python vs. R" debate, the details of which aren't relevant to someone who just wants to learn how to code.
They're both excellent languages with different strengths and weaknesses. Many digital humanists use both. I use both. 
You should learn one and then (optionally) pick up the other one later. I recommend that you start with Python. It's more flexible, more widely used,
and it has better offerings for common digital humanities tasks like social network analysis and natural language processing.

## What Specific Learning Resources Should You Use?

#### Python Fundamentals

My go-to recommendation for learning Python (and programming in general) is Rice University's [Fundamentals of Computing](https://www.coursera.org/specializations/computer-fundamentals) Coursera Specialization.

This Specialization does an excellent job of teaching Python,
and it really shines at teaching essential computational problem-solving skills that you can carry with you across programming languages and disciplines.
The lecture-videos are split up into small, digestible chunks and the coding projects are both enjoyable and rigorous. 

The Specialization is broken up into seven short courses, each lasting four or five weeks.
The courses are offered on-demand and require a few hours of study per week to keep up with the recommended pace, although you're free to move faster or slower.
You can hand Coursera some money and enroll in the Specialization, or you can audit all of the individual courses for free (!).
Folks who pay get their work graded and receive a Coursera-backed certificate of achievement at the end of the Specialization. 
Other than that, there's no difference between auditors and paying students.

Fun Fact! This Specialization is based on the first two courses in Rice's Computer Science major: COMP 140 and COMP 182.
I took those courses as an undergrad and can confirm: the online offerings are *quite* similar. 
The in-person courses have more projects and assignments, but other than that, you're getting the real deal.
These courses have served me *really* well through the years, and I feel super confident in recommending them to you!

If, however, you prefer book-learning, give Allen B. Downey's (free!) book [Think Python](https://greenteapress.com/wp/think-python-2e/) a try!
Downey has a rare talent for explaining technical concepts in clear, energetic prose without sacrificing accuracy. 
His book also has plenty of exercises, although they're not as comprehensive or challenging as the Rice projects.

#### Python Beyond the Fundamentals

If you find that you *really* enjoy Python and you want to dive deep, you should check out Luciano Ramalho's [Fluent Python](https://www.amazon.com/Fluent-Python-Concise-Effective-Programming/dp/1491946008).
It's a true Python *tour de force*, and although it isn't free, your library ought to have a copy (or an eBook). 

#### Python Data Science Fundamentals

After you're comfortable with Python, you'll want to pick up data science. 

My go-to recommendation here is the University of Michigan's [Applied Data Science with Python](https://www.coursera.org/specializations/data-science-python) Coursera Specialization.
You'll learn the whole data science workflow: acquiring, cleaning, manipulating, visualizing, modeling data.
You'll also get experience with natural language processing and social network analysis, both of which are staples of computational humanities research.
It's similar in structure to Rice's Python Specialization, and you choose between auditing for free or forking over some cash for graded projects.

If you'd prefer a book, I think the best introductory data science text is [Python for Data Analysis](https://www.amazon.com/Python-Data-Analysis-Wrangling-IPython/dp/1491957662/).
It isn't free, but it *is* sufficiently popular that your library ought to have a physical copy, an eBook subscription, or both!

#### Python Data Science Beyond the Fundamentals

Once you're ready to move past the basics, you should check out Aurélien Géron's [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow](https://www.amazon.com/Hands-Machine-Learning-Scikit-Learn-TensorFlow/dp/1492032646).
Again, it isn't free, but your library likely has a copy!

#### Humanistic Data Science

For data science books specifically written for humanists, you'll want to check out Folgert Karsdorp's [Python Programming for the Humanities](http://www.karsdorp.io/python-course/),
Brandon Walsh & Sarah Horowitz's [Introduction to Text Analysis](http://walshbr.com/textanalysiscoursebook/),
and Stéfan Sinclair & Geoffrey Rockwell's [The Art of Literary Text Analysis](https://github.com/sgsinclair/alta/blob/915579fc1c6926b8fcb2a38f95349a2d6cba00b5/ipynb/ArtOfLiteraryTextAnalysis.ipynb).

I'd also enthusiastically recommend Andrew Piper's [The Fish and the Painting](https://r4thehumanities.home.blog/).
It uses R instead of Python (and it's a work-in-progress), but it's still a must-read for Python folks.
*The Fish and the Painting* focuses on the *conceptual framework* for humanistic data science rather than the nuts and bolts of programming languages and algorithms.
It's excellent.

You should also check out a few journals where humanistic data science-y work gets published. 
The #1 must-read journal is [Cultural Analytics](https://culturalanalytics.org/).
The journal is dedicated to computationally-inflected humanities work, plus it's open-access!
[Digital Scholarship in the Humanities](https://academic.oup.com/dsh) should also be on your list.
It draws lots of computational work, but it's a different crowd and vibe than *Cultural Analytics*.
DHS seems more popular with folks whose primary disciplinary training is in computer science, whereas CA seems more popular with folks who trained primarily in a humanities discipline.
[Digital Humanities Quarterly](http://www.digitalhumanities.org/dhq/) is also worth checking out. It publishes all sorts of DH work, not just the computational bits.


## The End?

Those are my recommendations! I won't be so bold as to claim that they constitute the *optimal* path to learning humanities data science,
but they certainly constitute a *good* path! If I had to re-learn from the ground up, this is how I'd do it.

Feel free to <a href="mailto:cody.a.vanzandt@gmail.com">email me</a> with your questions and comments!
I'm particularly happy to answer questions and offer advice for folks who are starting out in humanities data science.
