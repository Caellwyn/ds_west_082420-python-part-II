
# More Python Essentials!

In this notebook, we will play around with more fundamental Python tools.  We won't be able to cover everything: Python has vast abilities and many, many methods to learn.  That is one great think about programming, and data science: You will never be bored because of lack of new things to learn.


Below, we will learn about
  - Base type object methods  
  - Built in Functions  
  - F-strings  
  - List Methods  
  - List comprehensions  
  - Dictionary methods  
  - While loops   
  - Functions  
  
We will begin to use some real data from Chicago public schools. (The student body counts that are found at the bottom of the notebook are randomly created, but the districts and the school names are accurate).


## Base Type Object Methods

A method is a function that belongs to an object. And in Python, everyting is an object! Naturally, the methods that belong to a particular object can vary depending on the object's datatype.

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

There are some odd capitalizations in the principal's last name. Let's fix them.


```python
# .lower()
principal_last_name.lower()
```




    'bretthauer'



Let's create a string representing the principal's full name and title, with correct capitalization.


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



Here is a trick using a list comprehension (see below) to get the principal's initials.  

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

Here is a list of the [built-in functions](https://docs.python.org/3/library/functions.htmlhttps://docs.python.org/3/library/functions.html)

You are no doubt already familiar with at least one of the built in functions (print) but you probably haven't given it much thought.  It is a fundamental tool that comes built in with Python, with a prescribed set of behaviors assigned to it.  These behaviors can be overwritten, but that is not a good idea.  

If we assign a string to the variable print, we overwrite the print's expected behavior in memory.  In order to retrieve print's original functionality, we need to restart our kernal.  


Two built in functions are used below to create a string representing the sum of the numbers 1 through 5

#### f-Strings

f-Strings are a convenient way to bring variables into strings.  F-strings have numerous applications, from webscraping to SQL queries to writing the R-like formulas we will see in Phase 2.

Consider the scenario where you want to get data of every principal in a school district.  You have a list of last names, and you know the pattern of a url.  
`www.lakeviewhigh.edu/principal/<principal_last_name>/about/`

We can use an f-string to interpolate the last name into the url. We insert the variable, which has to be a **string** into the curly braces.


```python
print(f"'www.lakeviewhigh.edu/principal/{principal_last_name.lower()}/about/")
```

    'www.lakeviewhigh.edu/principal/bretthauer/about/


## Individual Exercise: Turn off you camera, and take 3 minutes to work through the following problem

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


Let's read in an object which contains Chicago Public School districts and the schools associated with them. 

The object schools is a dictionary, with a list associated with a district number.  Let's isolate district 1 and 2, and practice list methods with the first 5 schools in each list.


```python
print(len(district_2))
district_2.extend(district_1)
len(district_2)
```

    5





    10



### List Comprehension

List comprehension is a handy way of generating a new list from existing lists.

Suppose I want the district in the school names.


I can do this with list comprehension!

The syntax is: ```[ f(x) for x in [original list] ]```

# Individual Exercise:

Take 2 minutes, turn off your camera and create a list, using a list comprehension, of all the string lengths in district 4. In other words, create a new list comprised of the character lengths of all the school names in district 4.  Count spaces as a character.

Turn your camera back on when you are finished.


```python
district_4 = schools[4]
district_4_lengths = [len(school) for school in district_4]
print(district_4_lengths)
```

    [9, 7, 18, 5, 4, 6, 8, 5, 6, 8, 7, 6, 7, 8, 9, 14, 4, 7, 8, 5, 9, 6, 6, 11, 8, 5, 8, 6, 13]


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

Now let's think of a scenario where we would like to iterate through the school list of a district, sum the populations of the schools, and stop when the sum exceeds a certain number.  

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

**Break and continue** are two commands which allow us to alter how me move through our loops.  

Wherever we enounter **break**, the code will exit the loop it is moving through.

Wherever we encounter **continue**, the code will return to the top of the loop it is moving through.

# Nested for loops

Lets imagine we have a dictionary where each key is a school district, and each value is a school population number.  

Let's iterate through the districts, add up the school populations, and print out the total populations in each district.

To do so, our top level for loops interates through the keys (our districts) sequentially. 

For each district, the inner loop iterates through the list associated with each district, summing all of the populations.


# Round Robin

We can update the above code to store our data in a dictionary by instantiating a dictionary outside of the outer loop.



```python
# We can update the above code to store our data in a dictionary.

district_population_dict = {}

for district in school_pop_dict:
    district_population = 0
    for pop in school_pop_dict[district]:
        district_population += pop
    district_population_dict[district] = district_population
    
print(district_population_dict)
```

    {1: 19251, 2: 12011, 3: 7334, 4: 16177, 5: 15301, 6: 13163, 7: 10489, 8: 11525, 9: 11925, 10: 17828, 11: 15426, 12: 16208, 13: 16983, 14: 10428, 15: 13406, 16: 10128}


# Practice with nested dictionaries

The object below is a dictionary with keys which represent a school district. The values associated with the keys are themselves dictionaries, whose keys are school names, and values are school populations.

## Round Robin: Let's make a list of schools with student bodies less than 500.


```python
low_pop_schools = []

for district in nested_schools_dict:
    for school in nested_schools_dict[district]:
        if nested_schools_dict[district][school] < 500:
            low_pop_schools.append(school)

print(low_pop_schools)
```

    ['BRIDGE', 'CANTY', 'DEVER', 'EDISON', 'FARNSWORTH', 'GARVY', 'HITCH', 'ONAHAN', 'PRUSSING', 'SOLOMON', 'BOONE', 'CLINTON', 'DECATUR', 'DISNEY', 'FIELD', 'GALE', 'HAYT', 'KILMER', 'NEW FIELD', 'RAVENSWOOD', 'SWIFT', 'WATERS', 'ELLINGTON', 'HAY', 'LELAND', 'LYON', 'SAYRE', 'ALCOTT ES', 'BLAINE', 'FRANKLIN', 'GOETHE', 'HAMILTON', 'HAWTHORNE', 'INTER-AMERICAN', 'JAHN', 'MANIERRE', 'MAYER', 'MONROE', 'NETTELHORST', 'REILLY', 'CHOPIN', 'FARADAY', 'FRAZIER PROSPECTIVE', 'HUGHES C', 'KELLMAN', 'MASON', 'MELODY', 'MITCHELL', 'MOOS', 'PENN', 'STOWE', 'TILTON', 'WARD L', 'BROWN W', 'BURR', 'DETT', 'IRVING', 'JACKSON A', 'OTIS', 'PRITZKER', 'PULASKI', 'SMYTH', 'SUDER', 'GARY', 'KANOON', 'MADERO', 'OROZCO', 'PEREZ', 'RUIZ', 'WHITNEY', 'WHITTIER', 'BRIGHTON PARK', 'CALMECA', 'DALEY', 'DAVIS N', 'EDWARDS', 'EVERETT', 'EVERGREEN', 'HERNANDEZ', 'SAWYER', 'SHIELDS', 'SHIELDS MIDDLE', 'BRONZEVILLE CLASSICAL', 'BURKE', 'CARNEGIE', 'DOOLITTLE', 'DRAKE', 'FISKE', 'KOZMINSKI', 'MURRAY', 'BARNARD', 'BLAIR', 'CLAREMONT', 'EBERHART', 'GRIMES', 'HEARST', 'KELLER', 'KELLOGG', 'MORRILL', 'OWEN', 'RICHARDSON', 'TWAIN', 'COOK', 'CUFFE', 'FULTON', 'GREEN', 'JOPLIN', 'KERSHAW', 'LANGFORD', 'MAYS', 'PARKER', 'RANDOLPH', 'RYDER', 'WENTWORTH', 'BOUCHET', 'BURNSIDE', 'COLES', 'DIXON', 'EARHART', 'MCDADE', 'NEW SULLIVAN', 'PARK MANOR', 'PARKSIDE', 'RUGGLES', 'WASHINGTON H ES', 'BENNETT', 'BRIGHT', 'CLAY', 'DUBOIS', 'FERNWOOD', 'GARVEY', 'GRISSOM', 'HALEY', 'HIGGINS', 'MOUNT VERNON', 'OWENS', 'POE', 'SHOOP', 'SMITH', 'TAYLOR', 'DEVRY HS', 'LAKE VIEW HS', 'LINCOLN PARK HS', 'MATHER HS', 'NORTHSIDE LEARNING HS', 'STEINMETZ HS', 'UPLIFT HS', 'VAUGHN HS', 'VON STEUBEN HS', 'ALCOTT HS', 'CURIE HS', 'DOUGLASS HS', 'JUAREZ HS', 'MANLEY HS', 'NORTH-GRAND HS', 'OGDEN ES', 'PROSSER HS', 'SIMPSON HS', 'SOCIAL JUSTICE HS', 'WESTINGHOUSE HS', 'WORLD LANGUAGE HS', 'ENGLEWOOD STEM HS', 'HARPER HS', 'JEFFERSON HS', 'JULIAN HS', 'KENNEDY HS', 'LINDBLOM HS', 'SPRY HS']


## Functions

This aspect of Python is _incredibly_ useful! Writing your own functions can save you a TON of work - by _automating_ it.

### Creating Functions

The first line will read:

'def' + _your function's name_ + '( )' + ':'

Any arguments to the function will go in the parentheses.

Let's try building a function to get the schools in a district

### Calling Functions

To _call_ a function, simply type its name, along with any necessary arguments in parentheses.

When a function is called, it executes all code up to the **return** statement.  Whatever is returned can be passed into a variable, and stored in memory.

### Default Argument Values

Sometimes we'll want the argument(s) of our function to have default values.

# Pair Program: A full function

Create a function that has two parameters:  
  - district  
  - the nested_schools_dict dictionary  
    
The function should do two things.  
  - Return a dictionary of all schools within the given district with a student body less than 500. The keys are the school names, the values are the school pops.  
  - Print a statement that reads `<school_name> has <x_number> of students`. Use an f-string for the print statement.


```python
def low_pop_schools(district, schools=nested_schools_dict):
    
    
    low_pop_schools = {}
    for name, pop in nested_schools_dict[district].items():
        if pop < 500:
            print(f'{name} has {pop} students')
            low_pop_schools[name]=pop

    return low_pop_schools

```

## Practice Exercises:
Here are a few exercises to do on your own time to practice building functions.

1. Build a function that will take an input string and add '-totally' to the end of it.

2. Build a function that will take in three numbers and return twice the smallest of the three.

3. Build a function that will create a list, of user-specified length, of empty dictionaries.

4. Build a function that will return the middle value (for odd-length) or middle two values (for even-length) of a string.

5. Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a list of the integers that are divisible by 3.

6. \*Build a function that will take in a list of lists of integers - default: \[[1, 2], [34, 27], [45, 13]\] - and return a dictionary whose keys are integers starting at 1 and counting up and whose values are the integers that are divisible by 3.
