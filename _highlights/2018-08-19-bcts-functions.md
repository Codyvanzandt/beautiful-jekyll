---
layout: post
title: "Better Coding Through Shakespeare"
subtitle: "Part Three: Functions"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare, teaching]
show-avatar: true
bigimg: /img/BCTS_background.jpg
highlight: "BetterCodingThroughShakespeare"
---

# **Hermia Would Make a Good Function**

In *A Midsummer Night's Dream*, Helena says of Hermia...

> And though she be but little, she is fierce. [3]

Just the qualities we want in a function: little and fierce.

Programs made up of small, powerful functions are easier to understand, easier to test, and easier to maintain.

Check out this big ol' function. No need to get too involved with it. It is, after all, fake. But glance through it and get the gist.


```python
def promote_employee(employee, new_title):
    
    # give the employee his new title, adding 'Senior' or 'Junior' if necessary
    if employee.years_of_service > 10:
        fully_udated_title = "Senior " + new_title
    elif employee.years_of_service < 2:
        fully_udated_title = "Junior " + new_title
    employee.title = fully_udated_title
    
    # compute the employee's new salary
    new_salary_bracket_min, new_salary_bracket_max = human_resources.get_salary_bracket(new_title)
    if employee.salary <= new_salary_bracket_min:
        new_salary = new_salary_bracket_min
    elif employee.salary >= new_salary_bracket_max:
        new_salary = new_salary_bracket_max
    else:
        new_salary = ( new_salary_bracket_min + new_salary_bracket_max ) / 2.0
    employee.salary = new_salary

    # compute the employee's new 401k matching
    if human_resources.is_role_401k_eligible(new_title):
        new_max_401k_matching = human_resources.get_max_401k_matching(new_title)
        min_401k_matching = human_resources.get_company_minimum_401k_matching()
        if employee.matching_401k == 0:
             new_matching_401k = min_401k_matching
        else:
            new_matching_401k = min(new_max_401k_matching, employee.matching401k + 0.01)
    else:
        new_matching401k = 0
    employee.matching_401k = new_matching_401k

    # compute the new stock compensation
    stock_level_1, stock_level_2, stock_level_3 = human_resources.get_stock_levels(new_title)
    if employee.tenure > 20:
        new_stock_total = stock_level_3
    elif employee.tenure > 10:
        new_stock_total = stock_level_2
    else:
        new_stock_total = stock_level_1
    employee.stock = new_stock_level

    return employee
```

That's one *long* function. It isn't terribly easy to read, the logic of each individual part obfuscates the function's larger goal, and there are control-flow statements everywhere. The comments help *a little*, but they shouldn't be necessary. 

In short, this function *isn't* short, and it *isn't* clear.

Now check out this nice little function...


```python
def promote_employee(employee, new_title):
    update_title(employee, new_title)
    update_salary(employee, new_title)
    update_401k_matching(employee, new_title)
    update_stock(employee, new_title)
    return employee
```

Now *that* is readable! 

There's not a single if-statement, every line of code communicates its purpose, and you can tell right away what promoting an employee entails.

True story: I sent this snippet to my mother, a retired paralegal with zero coding experience, and asked her to tell me what she thinks is going on. She immediately wrote back:

> Well, you're trying to promote an employee. So you give him his new title, salary, 401k matching, and stock, right? [4]

The code is just that clear.

To be fair, I refactored away a lot of code. The details of, for example, `update_title` aren't here. But it isn't too hard to imagine what happened. Each logic block from our gigantic function ended up in its *own* little function. I pieced the little functions together, and *viola!* The new function is far from perfect, but it is a signifncant improvement.

Now that you're jiving with the idea that functions should be small (at least, I hope you are), let's get down to business: what does "small" mean, exactly?

## How Small is "Small?" 

To quote Robert C. Martin on it,

> The first rule of functions is that they should be small. The second rule of functions is that
*they should be smaller than that*. [5]

Very clever. But how small is "smaller than that?" 

Honestly, there isn't a universally-accepted measure of "small."  However, I'd wager that almost every student in Martin's tradition (Martians?) would agree that 20 lines is usually too big. 

But I imagine that you want some hard-and-fast guidelines. You're right to ask for them, so here you go!

These statistics come from roughly 15000 lines of Ruby code written by Martin Fowler. 

 - 59% of his functions are less than three lines
 - 75% of his functins are less than five lines
 - 93% of his functions are less than ten lines [6]

If you're looking for a software engineer to emulate, Martin Fowler is as good a choice as anyone. He's a recognized leader in the field of software engineering and one of the original authors of the [*Manifesto for Agile Software Development*](http://agilemanifesto.org/).

The next big question, of course, is how do you write functions that are *that tiny?*


## Functions Should Do One Thing 

To quote Robert C. Martin again,

> Functions should do one thing. They should do it well. They should do it only. [7]

Odds are good that if you follow those three rules, your functions will naturally run just a few lines in length. 

But how do you know when you function is doing one thing? 

Here's a fool-proof heuristic: try to extract another meaningful function out of it. If you can, then the original function was not doing one thing.

It's a cheeky, I know, but it cannot fail. 

To illustrate, let's take another look at our promotion function.


```python
def promote_employee(employee, new_title):
    update_title(employee, new_title)
    update_salary(employee, new_title)
    update_401k_matching(employee, new_title)
    update_stock(employee, new_title)
    return employeee
```

Can we extract out another meaningful function? I think so. 

I think that salary, 401k, and stock are related updates that can be extracted out into an `update_compensation` function. 

Take a look:


```python
def promote_employee(employee, new_title):
    update_title(employee, new_title)
    updated_compensation(employee, new_title)
    return employee
```

Now *that* is a clean function!

Reading it, you immediately understand what happens when you promote an employee:
- You update their title
- And you update their compensation

If you're curious about what *exactly* goes into updating an employee's title or compensation, you're welcome to go look. But you're not *forced* to slog through the gory details if you don't want to. The *intention* of the function is separate from its *implementation*, and readers can choose to interact with your code at their preferred level of abstraction. 

Lastly, the code is modular, testable, and readable - all because your functions are small do just one thing. 

## Conclusion

I know it's shocking to imagine 15000 lines of code made up of tiny five-line functions. It *does* sound a little silly.
But humor me: give it a try. Code up a gaggle of little functions. Name them accurately, test them well, then let them loose.
I think you'll see the difference. 

Regardless, I hope to see you in the next section of **Better Coding Through Shakespeare** - [we're taking on arguments!](/2018-08-20-bcts-arguments)

[3] Shakespeare, William. *A Midsummer Night's Dream.* III.ii

[4] Thanks, Mom!

[5] Martin, Robert C. *Clean Code.* 34

[6]  Fowler, Martin. https://martinfowler.com/bliki/FunctionLength.html 

[7]  Martin, Robert C. *Clean Code.* 35

