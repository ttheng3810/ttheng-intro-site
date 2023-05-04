---
title: "Attempting 'Python Exercises for Kids'"
date: 2022-12-24
slug: "attempting-python-exercises-for-kids"
description: "I gave a try on the Python exercises as listed in John Regehr's blog post."
keywords: ["exercise","python"]
draft: false
tags: ["code"]
math: false
toc: true
---

## Background

One day, I was casually looking for Python-related blog posts using [Blog Surf](https://blogsurf.io/). I then stumbled upon a blog post titled [*Python Exercises for Kids*](https://blog.regehr.org/archives/1300), published on John Regehr's blog [_Embedded in Academia_](https://blog.regehr.org/).

This posts lists seven Python exercises which, according to the author, have been given to his then-11-year-old child. I found them interesting and decided to try them out myself as a fun coding practice, and to see if I can do better than an 11-year-old.

I gave a try on some of them, and here they are.

## Fibonacci

*Task*: Print the [Fibonacci series](https://en.wikipedia.org/wiki/Fibonacci_number).

This is a classic exercise in understanding looping (recursion and iteration).

The following variants of code, all of which are iterative, include one that generates [the generalised version of Fibonacci series](https://en.wikipedia.org/wiki/Generalizations_of_Fibonacci_numbers#Fibonacci_integer_sequences).

```python
'''Prints the Fibonacci series infinitely, one second at a time.
Keyword arguments:
    a_0 -- int: the first initial value of the series (defaults to 1).
    a_1 -- int: the second initial value of the series (defaults to 1).
'''
from time import sleep

def fibonacci(a_0=1, a_1=1):
    print(a_0)
    print(a_1)
    while True:
        a_2 = a_0 + a_1
        print(a_2)
        sleep(1.0)
        a_0, a_1 = a_1, a_2


'''
Prints the Fibonacci series up to a specified term limit.
Keyword arguments:
    limit -- int: the maximum number of terms to be printed.
    a_0 -- int: the first initial value of the series (defaults to 1).
    a_1 -- int: the second initial value of the series (defaults to 1).
'''
def fibonacci_term(limit: int, a_0=1, a_1=1):
    if limit <= 0:
        raise ValueError("The term limit must be at least 1.")
    count = 0
    while count < limit:
        if count == 0:
            print(a_0)
        if count == 1:
            print(a_1)
        elif count > 1:
            a_2 = a_0 + a_1
            print(a_2)
            a_0, a_1 = a_1, a_2
        count += 1


'''
Prints the Fibonacci series up to a specified value limit.
Keyword arguments:
    limit -- int: the maximum accepted value to be printed.
    a_0 -- int: the first initial value of the series (defaults to 1).
    a_1 -- int: the second initial value of the series (defaults to 1).
'''
def fibonacci_value(limit: int, a_0=1, a_1=1):
    if limit < max(a_0, a_1):
        raise ValueError("The value limit must be greater than the larger initial value.")
    print(min(a_0, a_1))
    print(max(a_0, a_1))
    a_2 = 0
    while a_2 < limit:
        a_2 = a_0 + a_1
        if a_2 <= limit:
            print(a_2)
        a_0, a_1 = a_1, a_2
```

## Binary Printer

*Task*: Print the non-negative binary integers in increasing order.

Regehr notes that representation choices may need to be applied in the implementation, in this case the representation of integers in binary form.

```python
'''Prints the non-negative binary integers in increasing order 'non-stop', one second at a time.'''
from time import sleep

def print_bin(num=0):
    print(f'{num:b}')
    sleep(1.0)
    num += 1
    print_bin(num)


'''Prints the non-negative binary integers in increasing order, up to a specified maximum value (in base 10).

Keyword arguments:
    max -- int: maximum decimal value to be printed.
'''
def print_bin_until(max: int):
    if max < 0:
        raise ValueError("The maximum value must be at least 0.")
    for num in range(max+1):
        print(f'{num:b}')
        # sleep(1.0)
        # optional pause
```

## Palindrome Recogniser

*Task*: Determine whether a given sentence is palindromic with respect to alphabets. For example, ```A man, a plan, a canal — Panama!```, as provided in the blog post, is palindromic.

Some string manipulations are involved in the implementation.

I'd say that my implementation here is fairly naive, as it doesn't pass the test of putting longer palindromic strings, such as [this 15 139-word palindrome](http://norvig.com/pal1txt.html). Perhaps I could write a more effective implementation if time allows.

```python
'''
Determine whether a sentence is palindromic in terms of alphabets.
Returns a string response output.

Keyword arguments:
    string -- str: input sentence.
'''
def is_palindromic(string: str) -> str:
    alphabets_lower = "abcdefghijklmnopqrstuvwxyz"
    alphabet_only = "".join(tuple(filter(lambda char: char in alphabets_lower, string.lower())))
    if alphabet_only == "":
        return "There are no alphabets in your input."
    if alphabet_only == alphabet_only[::-1]:
        return "Yes, it's palindromic."
    else:
        return "No, it's not palindromic."
```
