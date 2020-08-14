
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


```python
first_name = 'greg'
last_name = 'damico'
```


```python
# .capitalize()


```


```python
# .title()


```

Notice that '+' is used to concatenate strings!


```python
# .join()

'oo'.join('GREG')
```


```python
''.join(name[0] for name in [first_name, last_name])
```


```python
' < '.join(str(num) for num in range(1, 6))
```

#### f-Strings

f-Strings are a convenient way to bring variables into strings.


```python
fav_num = 42
adj = 'greatest'
print(f"I love {fav_num}. It's the {adj}!")
```

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


```python
list_1 = [1, 2, 4]

list_2 = [8, 16]
```


```python
# Add list_2 to list_1 so that we have one big list

# Note that this alters list_1!


list_1.extend(list_2)
list_1
```


```python
# What would this code return?

list_1.append(list_2)
```


```python
# Let's write a loop that will build a list of the characters of the
# string: 'supercalifragilisticexpialidocious'

word = 'supercalifragilisticexpialidocious'
char_list = []


```


```python
# What does list(word) do?

list(word)
```


```python
list_1.pop()

# What does this return?
# What does list_1 look like now?


```

### List Comprehension

List comprehension is a handy way of generating a new list from existing lists.

Suppose I start with a simple list.


```python
primes = [2, 3, 5, 7, 11, 13, 17, 19]
```

What I want now to do is to build a new list that comprises doubles of primes. I can do this with list comprehension!

The syntax is: ```[ f(x) for x in [original list] ]```


```python
prime_doubles = [x*2 for x in primes]
prime_triples = [x*3 for x in primes]
```


```python
prime_doubles
```


```python
print([x + 'hello' for x in word])
```

### Dictionary Methods

Here are some useful methods for dictionaries:

- ```.keys()```: returns an array of the dictionary's keys
- ```.values()```: returns an array of the dictionary's values
- ```.items()```: returns an array of key-value tuples


```python
zoo = {1: 'giraffe', 2: 'elephant', 3: 'monkey'}
```


```python
# Use the .keys() method to print the keys of this dictionary!

# Use the .values() method to print the values of this dictionary!


for item in zoo.items():
    print(item[0])
    

```

#### Dictionary Comprehension


```python
{k: v + ' monkeys' for k, v in zoo.items()}
```


```python
{k**2: v**2 for k, v in [(0, 1), (2, 3), (4, 5)]}
```

## Zipping

Zipping is a way of merging two arrays into one. The result can be cast as a list or as a dict.


```python
zip(primes, prime_doubles)
```


```python
dict(zip(primes, prime_doubles))
```

## Built-In Functions

Many useful functions are already built into Python:

- ```print()```: print the given string or variable's value
- ```type()```: returns the datatype of the argument
- ```len()```: returns the length of an array
- ```sum()```: returns the sum of the array's values
- ```min()```: returns the smallest member of an array
- ```max()```: returns the largest member of an array


```python
# What will this return?

max(6, 9, 7)
```

## While Loops

We have already seen 'for'-loops, where you use a loop and count the iterations by the some pre-specified number. But sometimes we don't know how many times we'll need to iterate!

Suppose I want to build a program that will take in a whole number and then tell me how many times 2 divides that number evenly. So e.g. 2 divides 4 twice but 10 only once (and 1536 nine times).

A good first start is to take the input number and start dividing by 2. But when do I stop? Answer: When I reach an odd number!


```python
# Let's code it!




```

## Nested Loops and List Comprehensions

We can put loops inside of other loops and list comprehensions inside of other list comprehensions. These come in handy especially when we have arrays inside of other arrays.


```python
phone_nos = [{'name': 'greg', 'nums': {'home': 1234567, 'work': 7654321}},
          {'name': 'max', 'nums': {'home': 9876543, 'work': 1010001}},
            {'name': 'erin', 'nums': {'home': 3333333, 'work': 4444444}},
            {'name': 'joél', 'nums': {'home': 2222222, 'work': 5555555}},
            {'name': 'ben', 'nums': {'home': 9999999, 'work': 8888888}}]
```


```python
# Exercise: from the above list, make a list of dictionaries where the key
# is the person's name and the value is the person's home phone number.



```

## Functions

This aspect of Python is _incredibly_ useful! Writing your own functions can save you a TON of work - by _automating_ it.

### Creating Functions

The first line will read:

'def' + _your function's name_ + '( )' + ':'

Any arguments to the function will go in the parentheses.

Let's try building a function that will automate our task of finding all the factors of 2 of a given number!


```python
# Let's code it!




```

### Calling Functions

To _call_ a function, simply type its name, along with any necessary arguments in parentheses.


```python
# Let's call it!

```

### Default Argument Values

Sometimes we'll want the argument(s) of our function to have default values.


```python
def cheers(person='aaron', job='data scientist', age=30):
    return f'Hooray for {person}. You\'re a {job} and you\'re {str(age)}!'
```


```python
cheers('greg', 'scientist', 80)
```


```python
cheers('cristian', 'git enthusiast', 93)
```


```python
cheers()
```

## Exercises:

1. Build a function that will take an input string and add '-totally' to the end of it.


```python

```

2. Build a function that will take in three numbers and return twice the smallest of the three.


```python

```

3. Build a function that will create a list, of user-specified length, of empty dictionaries.


```python

```

4. Build a function that will return the middle value (for odd-length) or middle two values (for even-length) of a string.


```python

```

5. Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a list of the integers that are divisible by 3.


```python

```

6. \*Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a dictionary whose keys are integers starting at 1 and counting up and whose values are the integers that are divisible by 3.


```python

```
