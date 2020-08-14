
# More Python Essentials!

## Methods

A method is a function that belongs to an object. And in Python, most things are objects! Naturally, the methods that belong to a particular object can vary depending on the object's datatype.

### String Methods

Here are some useful methods for strings:

- ```.upper()```: converts a string to uppercase
- ```.lower()```: converts a string to lowercase
- ```.capitalize()```: makes the first letter of a string a capital

Question: What's the difference between `.capitalize()` and `.title()`?

<details>
    <summary>
    Answer here
    </summary>
    .capitalize() capitalizes the first letter of a string;<br/>
        .title() capitalizes the first letter and each letter after a space
    </details>

Notice that '+' is used to concatenate strings!

#### f-Strings

f-Strings are a convenient way to bring variables into strings.

### List Methods

Here are some useful methods for lists:

- ```.append()```: adds an element to the end of a list
- ```.pop()```: removes an element from the list
- ```.extend()```: adds multiple elements to the end of a list
- ```.index()```: returns (first) place in list where argument is found
- ```.remove()```: removes element by value

Question: What's the difference between ```.remove()``` and ```del```?

<details>
    <summary>
        Answer here
    </summary>
    .remove() removes an element by value;<br/>
    del removes an element by position

### List Comprehension

List comprehension is a handy way of generating a new list from existing lists.

Suppose I start with a simple list.

What I want now to do is to build a new list that comprises doubles of primes. I can do this with list comprehension!

The syntax is: ```[ f(x) for x in [original list] ]```

### Dictionary Methods

Here are some useful methods for dictionaries:

- ```.keys()```: returns an array of the dictionary's keys
- ```.values()```: returns an array of the dictionary's values
- ```.items()```: returns an array of key-value tuples

#### Dictionary Comprehension

## Zipping

Zipping is a way of merging two arrays into one. The result can be cast as a list or as a dict.

## Built-In Functions

Many useful functions are already built into Python:

- ```print()```: print the given string or variable's value
- ```type()```: returns the datatype of the argument
- ```len()```: returns the length of an array
- ```sum()```: returns the sum of the array's values
- ```min()```: returns the smallest member of an array
- ```max()```: returns the largest member of an array

## While Loops

We have already seen 'for'-loops, where you use a loop and count the iterations by the some pre-specified number. But sometimes we don't know how many times we'll need to iterate!

Suppose I want to build a program that will take in a whole number and then tell me how many times 2 divides that number evenly. So e.g. 2 divides 4 twice but 10 only once (and 1536 nine times).

A good first start is to take the input number and start dividing by 2. But when do I stop? Answer: When I reach an odd number!

## Nested Loops and List Comprehensions

We can put loops inside of other loops and list comprehensions inside of other list comprehensions. These come in handy especially when we have arrays inside of other arrays.

## Functions

This aspect of Python is _incredibly_ useful! Writing your own functions can save you a TON of work - by _automating_ it.

### Creating Functions

The first line will read:

'def' + _your function's name_ + '( )' + ':'

Any arguments to the function will go in the parentheses.

Let's try building a function that will automate our task of finding all the factors of 2 of a given number!

### Calling Functions

To _call_ a function, simply type its name, along with any necessary arguments in parentheses.

### Default Argument Values

Sometimes we'll want the argument(s) of our function to have default values.

## Exercises:

1. Build a function that will take an input string and add '-totally' to the end of it.

2. Build a function that will take in three numbers and return twice the smallest of the three.

3. Build a function that will create a list, of user-specified length, of empty dictionaries.

4. Build a function that will return the middle value (for odd-length) or middle two values (for even-length) of a string.

5. Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a list of the integers that are divisible by 3.

6. \*Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a dictionary whose keys are integers starting at 1 and counting up and whose values are the integers that are divisible by 3.
