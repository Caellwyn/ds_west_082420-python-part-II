
# More Python Essentials!

In this notebook, we will play around with more fundamental Python tools.  We won't be able to cover everything: Python has vast abilities and many, many methods to learn.  That is one great think about programming, and data science: You will never be bored because of lack of new things to learn.

Below, we will learn about
  - Base type object methods  
  - F-strings  
  - Built in Functions  
  - List Methods  
  - list comprehensions  
  - Dictionary methods  
  - While loops   
  - Functions  




## Methods

A method is a function that belongs to an object. And in Python, most things are objects! Naturally, the methods that belong to a particular object can vary depending on the object's datatype.

### String Methods

Strings will show up constantly.  Most datasets we encounter will have some sort of strings.  And they can be messy.  Luckily, we have objects associated with our strings that help us get them into suitable, consistent form.

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
# .lower()
principal_last_name.lower()
```




    'bretthauer'




```python
# .title()
full_name = principal_title + " " + principal_first_name + " " + principal_last_name
full_name.title()

```




    'Dr. Clark Bretthauer'



Notice that '+' is used to concatenate strings!

We can also use the .join() method to concatenate strings


```python
# .join()

' '.join([principal_title, principal_first_name, principal_last_name]).title()
```




    'Dr. Clark Bretthauer'



## Built-In Functions

Many useful functions are already built into Python:

- ```print()```: print the given string or variable's value
- ```type()```: returns the datatype of the argument
- ```len()```: returns the length of an array
- ```sum()```: returns the sum of the array's values
- ```min()```: returns the smallest member of an array
- ```max()```: returns the largest member of an array
- ```str()```: converts the variable from its current type to a string
- ```range()```: returns an iterable that allows looping through a set of numbers

#### f-Strings

f-Strings are a convenient way to bring variables into strings.

Consider the scenario where you want to get data of every principal in a school district.  You have a list of last names, and you know the pattern of a url.  
`www.lakeviewhigh.edu/principal/<principal_last_name>/about/`

We can use an f-string to interpolate the last name into the url. We insert the variable, which has to be a **string** into the curly braces.


```python
print(f"'www.lakeviewhigh.edu/principal/{principal_last_name.lower()}/about/")
```

    'www.lakeviewhigh.edu/principal/bretthauer/about/


## Individual Exercise: Turn off you camera, and take 4 minutes to work through the following problem

You would like a list of all Chicago Public Schools in each district.  The urls for the data have an easy pattern:  
https://www.cps.edu/schools/networks/network-1/  
https://www.cps.edu/schools/networks/network-2/  

The numbers before the final forward slash increase consecutively. 
The **objective** is to print out a list of all of the network urls with an f-string.

Hint: You will have to fill in the code below with two built in methods from above.


```python
for i in range(1,17):
    print(f"https://www.cps.edu/schools/networks/network-{str(i)}/")


```

    https://www.cps.edu/schools/networks/network-1/
    https://www.cps.edu/schools/networks/network-2/
    https://www.cps.edu/schools/networks/network-3/
    https://www.cps.edu/schools/networks/network-4/
    https://www.cps.edu/schools/networks/network-5/
    https://www.cps.edu/schools/networks/network-6/
    https://www.cps.edu/schools/networks/network-7/
    https://www.cps.edu/schools/networks/network-8/
    https://www.cps.edu/schools/networks/network-9/
    https://www.cps.edu/schools/networks/network-10/
    https://www.cps.edu/schools/networks/network-11/
    https://www.cps.edu/schools/networks/network-12/
    https://www.cps.edu/schools/networks/network-13/
    https://www.cps.edu/schools/networks/network-14/
    https://www.cps.edu/schools/networks/network-15/
    https://www.cps.edu/schools/networks/network-16/


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

Suppose I want the district in the school names.


I can do this with list comprehension!

The syntax is: ```[ f(x) for x in [original list] ]```

### Dictionary Methods

Here are some useful methods for dictionaries:

- ```.keys()```: returns an array of the dictionary's keys
- ```.values()```: returns an array of the dictionary's values
- ```.items()```: returns an array of key-value tuples

## Zipping

Zipping is a way of merging two arrays into one. The result can be cast as a list or as a dict.

## While Loops

We have already seen 'for'-loops, where you use a loop and count the iterations by the some pre-specified number. But sometimes we don't know how many times we'll need to iterate!

Suppose I need to choose a certain number of schools (say 10) from  a list.  I can set a variable as a counter, and create a while loop which will add 1 to that counter with each pass through the loop.

How can we update the code to stop before 1000?


```python
sample_school_populations = 0
school_index = 0

while sample_school_populations + district_3_pops[school_index]  < 1000:
    sample_school_populations += district_3_pops[school_index]
    school_index+=1

print(sample_school_populations)
```

    899


# Break and Continue

# Nested for loops

Lets imagine we have a dictionary where each key is a school district, and each value is a school population number.  

Let's iterate through the districts, add up the school populations, and print out the total populations in each district


## Functions

This aspect of Python is _incredibly_ useful! Writing your own functions can save you a TON of work - by _automating_ it.

### Creating Functions

The first line will read:

'def' + _your function's name_ + '( )' + ':'

Any arguments to the function will go in the parentheses.

Let's try building a function to get the schools in a district

### Calling Functions

To _call_ a function, simply type its name, along with any necessary arguments in parentheses.

### Default Argument Values

Sometimes we'll want the argument(s) of our function to have default values.

# Practice with nested dictionaries

## Let's make a list of schools with student bodies less than 500.


```python
low_pop_schools = []

for district in nested_schools_dict:
    for school in nested_schools_dict[district]:
        if nested_schools_dict[district][school] < 500:
            low_pop_schools.append(school)

```

# Pair Program: A full function

Create a function that has two parameters:  
  - district  
  - the nested_schools_dict dictionary  
    
The function should do two things.  
  - Return a dictionary of all schools with a student body less than 500. The keys are the school names, the values are the school pops.  
  - Print a statement that reads "<school_name> has <x_number> of students". Use an f-string for the print statement.


```python
def low_pop_schools(district, schools=nested_schools_dict):
    
    
    low_pop_schools = {}
    for name, pop in nested_schools_dict[district].items():
        if pop < 500:
            print(f'{name} has {pop} students')
            low_pop_schools[name]=pop

    return low_pop_schools

```

## Exercises:

1. Build a function that will take an input string and add '-totally' to the end of it.

2. Build a function that will take in three numbers and return twice the smallest of the three.

3. Build a function that will create a list, of user-specified length, of empty dictionaries.

4. Build a function that will return the middle value (for odd-length) or middle two values (for even-length) of a string.

5. Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a list of the integers that are divisible by 3.

6. \*Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a dictionary whose keys are integers starting at 1 and counting up and whose values are the integers that are divisible by 3.
