---
layout: post
show-post: true
title: Advent of Code 2020: The First Puzzle
subtitle: Hey, Look! A Simple Problem! (Not!)
---

The first [Advent of Code question](https://adventofcode.com/2020/day/1) question of the holiday season is a variation
on a tried-and-true first-round software engineering interview question:

> Given a list of `numbers` and a `target` number, find a pair of numbers in `numbers`
> that sums to `target`.

It isn't a huge algorithmic head-scratcher, it has a roomy solution space with optimization opportunities aplenty,
and it takes just a spattering of code to get a workable solution. In short, it's an excellent question for easing
both interviewer and interviewee into the swing of things -- which is a *critical* step too often skipped.

But believe it or not, there's a rather beastly amount of complexity hiding just beneath the surface of this supposedly "simple"
programming problem. Keep reading for a comically in-depth look at what is supposed to be the least complex puzzle of the Advent of Code season.

## The Naive Solution

Naively, we might loop through every pair of numbers (`a,b)` in `numbers`, returning `(a,b)` whenever
`a + b == target`. 

```python
def naive_solution(numbers, target):
    for a in numbers:
        for b in numbers:
            if a + b == target:
                return a, b
```

This is a perfectly fine solution. Solid and dependable -- it's the used Honda Civic of the solution-space. 
It's probably the most *readable* solution one could write, and dang it, readability counts! 
It counts A LOT. In fact, here's a controversial opinion: I would give an interviewee full credit for this solution
if they argued that its readability and simplicity could make it preferable, in some situations, to a more efficient
and less readable solution.

Now, given all of that, how could this solution be more computationally efficient?

## The Naive Itertools Solution

This solution is *almost* the same as the Naive Solution, but instead of building the pairs `(a,b)` yourself,
we lean on a piece of fast and reliable code 
built right into Python: the combinations function from the itertools module:

```python
import itertools

def naive_itertools_solution(numbers, target):
    for a, b in itertools.combinations(numbers, 2):
        if a + b == target:
            return a, b
``` 

This is another solid and dependable Honda Civic of a solution, but it's the brand new model rather
than the old faithful clunker. But to be honest, I actually prefer the clunker.
Using itertools here introduces additional complexity (in the form of the itertools module) without meaningfully
improving the computationally efficiency. And given a choice between two similarly efficient solutions,
we're almost always better served by picking the less complex, more obvious, more readable one.

## The Efficient Data-Structure-y Solution

Now let's get more efficient! We can pick up lots of speed by reducing the number of times that we
loop over `numbers`.  Previously, we had to loop through every possible combination of `(a,b)`, but
there was really no need to do that. Because once we have a given `a`, we know that there's only
one possible `b` such that `a + b == target`. 
All we need is a way to check that possible `b` is in `numbers` without having to loop over `numbers` all over again.

Any data structure that provides fast "lookups" will work.
Python's dictionary and set data structures both fit the bill, although the set is probably the better choice.
Dictionaries map keys to values, and while the numbers in `numbers` would clearly serve as keys, it
isn't clear what we'd use for values. There's really no need to store anything other than keys,
so there's really no need to use a dictionary. So we'll use a set.

Once we've turned `numbers` into a set, we can then loop through every possible `a` and quickly
check whether the corresponding `b` is in `numbers`:

```python
def set_solution(numbers, target):
    numbers_set = set(numbers)
    for a in numbers:
        if (b := (target-a)) in numbers_set:
            return a, b
```

It's a speedy solution, for sure! Something of a Camaro by comparison to the earlier Honda Civics.
It's also reasonably readable, assuming you're familiar with the bit of Python shenanigans I used
in the fourth line: `(b := (target-a))`. 

This little number `:=` is the recently(ish) introduced "walrus" operator:
* It performs assignment (e.g., it assigns the value of `target - a` to the variable `b` )
* But it is also creates an expression (e.g., it "replaces" `(b := (target-a))` with the
 newly created variable `b`).
*  Oh, and it also looks like a walrus's face: `:=`

There's no need to use the walrus here, but it's a fancy and fun little feature worth knowing about!

## The Efficient Data-Structure-y Itertools-y Solution

Lets change the problem such that we need to find *three* numbers `(a,b,c)` that add up to `target`
instead of two. In this case, we can combine our set-based and itertools-based solutions to solve
the problem in a readable and efficient way.

Instead of looping through every possible `a` and then checking our set for the corresponding `b`, we can loop through
every possible `(a,b)` and check our set for the corresponding `c`. Nifty, right?
We can generate all possible combinations of `(a,b)` using our old friend from the itertools module: combinations.
Then all we have to do is check if the corresponding `c` is in `numbers` using the same "turn `numbers` into a set" trick
from earlier.

```python
import itertools

def set_itertools_solution(numbers, n):
    numbers_set = set(numbers)
    for a, b in itertools.combinations(numbers, 2):
        if (c := (n-a-b)) in numbers_set:
            return a, b, c
```

This solution is speedy, readable, even a little fancy! To continue beating my car metaphor into the ground,
this solution is a fully-loaded Camaro with a custom paint-job. Or, uh, something like that.
I don't actually know that much about cars. But I know what I like, and I really like this solution! 
But, I hear you saying, didn't we earlier reject the itertools module because it introduced unnecessary complexity 
at the expense of readability? Why yes, yes we did. But I think itertools actually *increases* the readability in this case,
even if it *decreased* readability earlier.
Let me explain.

In the Naive Solution, the combinations function was replacing a couple of nested for-loops.
But those nested for-loops were the *heart* of the Naive Solution. And not only that, they were the
*painfully simple* heart of the solution. Nested for-loops looping over a list? That's the bread and butter 
of basic Python. In fact, they're a near-universal pattern that exists in all but the most capital-F Function programming languages.
Itertools? Not so much. Itertools is a well-known module, for sure. But it just can't compete on simplicity with two nested for-loops when those
for-loops make up the core of the solution.

For example... Quick! What's the name of the second argument to the combinations function?
Did you correctly guess "r"? Yeah, me neither. Does the combinations function make combinations with replacement?
Uh, no? Maybe? And wait, did we want combinations, or did we actually want permutations? 
See -- it's just too much complexity for such a simple solution.

But in the Efficient Data-Structure-y Itertools-y Solution, itertools combinations actually *improves* readability.
Critically, the creation of all pairs `(a,b)` is no longer the heart of the solution. The heart of *this* solution is in checking
whether `(n-a-b)` is in the set of `numbers`. The computation of the pairs is a necessary distraction from the heart of
the solution, and therefore, we should try and minimize that distraction as best we can.
A multiline, double-indented nested for-loop? That's a serious distraction that we're forcing up our readers.
But a one-line itertools solution? All of its distracting complexity is hidden 
away in the itertools documentation, far from the real focus of the solution: the set-checking.

## The Efficient Generic Data-Structure-y Itertools-y Solution

For our last trick, we'll complicate the problem further than was required by the original Advent of Code question.
Instead of finding a pair or a triple of numbers from `numbers` that adds up to `target`, what if pass another argument
to our function, `n`, and then find the `n` numbers in `numbers` that add up to `target`?

This solution is almost identical to the previous solution, at least structurally. 
If we're looking for triples `(a,b,c)`, then we generate all the pairs `(a,b)` and look for `c` in the set.
If we're looking for quadruples `(a,b,c,d)`, then we generate all triples `(a,b,c)` and look for `d` in the set.
Or in generally, if we're looking for `n` numbers, then we generally all combinations of size `n-1` and look for the the
last number in the set.

```python
import itertools

def generic_set_solution(numbers, target, n):
    numbers_set = set(numbers)
    for candidates in itertools.combinations(numbers, n-1):
        if (final_candidate := (target - sum(candidates))) in numbers_set:
            return *candidates, final_candidate
```

And there you have it folks, a nice, generic, efficient, readable solution! 
To afflict you with one final ill-conceived car metaphor, this is a fully-loaded, custom-painted Camaro that, uh.... also doubles as a boat?
Well, anyway, it's mighty flexible. Maybe even... too flexible? 

This is a cute and tidy solution, to be sure, but is it really worth all of the abstraction and cleverness?
Probably not. It might be too generic to be immediately obvious. Additionally, it isn't *quite* as efficient as it pretends to be. 
Generating combinations is fast when you're only generating doubles or triples, but it can get really laborious really quickly.
By allowing callers of this function to use arbitrary values of `n`, we're opening them up to a lot of potential pain.
And worst of all, the itertools combinations function obscures these dangers! It looks so speedy and fast, but there's a 
ponderously slow monster lurking underneath the surface. Yikes. Big yikes.

## The End

So there you have it, folks: an in-depth (and maybe even comically in-depth) look at what is presumably the simplest problem
of Advent of Code 2020. If you take anything away from this deep dive, it's that even simple of programming challenges
can be icebergs hiding mountains of complexity just below the waterline. If you're not careful, you could end up piloting your computational
Titanic right down into the cold dark depths. Or... something. 
I'll freely admit that the car/boat metaphors have completely gotten away from me.

So, uh, on that note...

Happy Holidays, folks! And good luck with the rest of the Advent of Code!










