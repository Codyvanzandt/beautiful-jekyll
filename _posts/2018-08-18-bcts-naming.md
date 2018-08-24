---
layout: post
title: "Better Coding Through Shakespeare Part 2: Naming Things"
image: /img/BCTS_background.jpg
tags: [programming, Python, Shakespeare, BetterCodingThroughShakespeare]
show-avatar: false
bigimg: /img/BCTS_background.jpg
---

# **Romeo Is a Dreadful Programmer**

In *Romeo and Juliet*, Romeo famoulsy opines...

> *What’s in a name? That which we call a rose*
>
> *By any other name would smell as sweet.* [1]

Now that might be a fine philosophy for Montagues and Capulets, but it's a *dreadful* way to approach programming.

**Names matter**. 

In specific, well-named variables, functions, and classes can significantly improve the readability and maintainability of a program.

For example... check out this function:


```python
def get_result(l):
    result = list()
    for i, j in l:
        if j > 40:
            result.append(i)
    return result
```

To quote Robert Martin,
> The problem isn’t the simplicity of the code but the *implicity* of the code. [2]

We know *what* this code does, but we have no idea *why* it's doing it. 

But if we do a little better job of naming things, this murky little function shines right up makes its intention perfectly clear:

```python
OVERTIME_CUTOFF = 40

def get_employees_with_overtime(employees_and_hours):
    employees_with_overtime = list()
    for employee_name, hours_worked in employees_and_hours:
        if hours_worked > OVERTIME_CUTOFF:
            employees_with_overtime.append(employee_name)
    return employees_with_overtime
```

Ah, that's better! We know *exactly* what this function and all of its variables are for. All we had to do was use good names.

Of course, you've got to be wondering, much like Romeo, "What's in a *good* name?" 

Fear not! I have tips aplenty. 

I can't guarantee that following these tips will make you as adept a namer as old Shakespeare,
but you're programs will read a great deal smoother.


## Tip 1: See Names as Opportunities to Add Context

Take a second to think before you jot down any old name for a variable. That name just might stick around for eternity. 

Seeing as there's an awful lot of time between now and eternity, you need to get it right. And your very first concern should be this:
_How can I name this variable in such a way that everyone coming after me will know exactly why this variable exists?_

Here's an example:

```python
s = 50000
```
That's dreadful. I have no idea what 50000 represents. 

```python
salary = 50000
```
This is much better! I now understand that 50000 is a salary, probably in the local currency.

```python
base_salary_USD = 50000
```
Fantastic! Now I have two additional (important!) pieces of information about this salary number.


## Tip 2: i,j,k (and Friends) Are Only For Indices

Single character loop variables (i, j, k, x, y, z, etc.) add almost no context. Because of convention, many programmers
aren't bothered by these names. But just because this is conventional doesn't mean it is any good.

Once you get more than a few lines of code away from these loop variables, you can easily lose track of what they
represent. What is `i` supposed to be? Who knows!

The only time you should use a single character loop variable is when you're looping over indices. And even then,
you should first ask yourself, "Should I really be looping over indices in the first place?"

Check out this example:

```python
office_locations = ["Houston", "Austin", "Dallas"]

for i in office_locations: # YUCK!
    pass 

for i, location in enumerate(office_locations): 
    pass

for location in office_locations: . 
    pass

```

The first example is a big swing-and-a-miss. The second example works, but *only if you actually need the indices*.
The third example is what you'll want in most cases.

## Tip 3: Don't Add Types If They Don't Add Information


```python
employee_name_string = "Robin" 
```
BAD! We already figured that the name was a string.


```python
employee_name_list = ["Robin", "Sam", "Alex"] 
```
This is fine as long as `employee_name_list` will *always* be a list...

```python
employee_names = ["Robin", "Sam", "Alex"].
```
This is likely the best option.



## Tip 4: Make Sure You Can Pronounce It


```python
cmpy_strt_adr = "100 Foo Street" 
```
Oh no. Oh no, no, no. This is the company street address, so you should write it as company_street_address.
I guarantee that if you write `cmpy_strt_adr`, programmers will pronounce it as "cumpy stert adder" until the
end of time.


## Tip 5: Variables and Classes are Nouns. Functions and Methods are Verbs.

```python
class GetEmployeeInfo(object): 
    
    def years_of_service_calculator(self): 
        pass
```

This is no good. Classes model things. And the only things that are verbs... are verbs. 
Additionally, everyone gets nervous calling a method that doesn't promise to *do* anything.
This is a swing-and-a-miss on both counts.

Compare with this little gem:

```python
class Employee(object): # GOOD!
    
    def get_years_of_service(self): 
        pass
    
```
Ah, much better!


## Tip 6: Pick Your Conventions and Stick with Them


```python
class Employee(object):
    
    def get_name(self): # A solid naming choice.
        pass
    
    def fetch_title(self): # fetch?
        pass
    
    def return_salary(self): # return? 
        pass
    
    def acquire_manager(self): # acquire? 
        pass
```
No one will remember which "get" synonym goes where. This can only lead to frustration. 
Just pick your verb and stick to it.


## Conclusion

Naming is difficult. 

There's a reason why companies pay marketing companies the big bucks to create catchy names. 
But as tricky as naming can be, it's always worth it to spend a little time coming up with a good name. 
You never know when that name might be the difference between adding a new feature, and introducing a new bug.

That's all for the ***Better Coding Through Shakespeare*** section on naming. Join me next time [as we take on functions!](/2018-08-19-bcts-functions)

[1] Shakespeare, William. *Romeo and Juliet.* II.ii

[2] Martin, Robert C. *Clean Code.* 18.
