
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



```python

# This is always a good idea
%load_ext autoreload
%autoreload 2
            
import os
import sys
module_path = os.path.abspath(os.path.join(os.pardir, os.pardir))
if module_path not in sys.path:
    sys.path.append(module_path)
    
from src.student_caller import one_random_student
from src.student_list import student_first_names
ds_west = student_first_names
```

    The autoreload extension is already loaded. To reload it, use:
      %reload_ext autoreload


## Base Type Object Methods

A method is a function that belongs to an object. And in Python, everyting is an object! Naturally, the methods that belong to a particular object can vary depending on the object's datatype.

### String Methods

Strings will show up constantly.  Most datasets we encounter will have some sort of strings.  And they can be messy.  Luckily, we have objects associated with our strings that help us get them into suitable, consistent form.

Here are some useful methods for strings:

- ```.upper()```: converts a string to uppercase
- ```.lower()```: converts a string to lowercase
- ```.capitalize()```: makes the first letter of a string a capital

Question: What's the difference between `.capitalize()` and `.title()`?


```python
one_random_student(ds_west)
```

    Ali


<details>
    <summary>
    Answer here
    </summary>
    .capitalize() capitalizes the first letter of a string;<br/>
        .title() capitalizes the first letter and each letter after a space
    </details>


```python
principal_first_name = 'clark'
principal_middle_initial = 'm'
principal_last_name = 'breTThauer'
principal_title = 'dr.'
```

There are some odd capitalizations in the principal's last name. Let's fix them.


```python
# .lower()
```


```python
#__SOLUTION__
# .lower()
principal_last_name.lower()
```




    'bretthauer'



Let's create a string representing the principal's full name and title, with correct capitalization.


```python
# .title()
```


```python
#__SOLUTION__
# .title()
full_name = principal_title + " " + principal_first_name + " " + principal_last_name
full_name.title()

```




    'Dr. Clark Bretthauer'



Notice that '+' is used to concatenate strings!

We can also use the .join() method to concatenate strings


```python
# .join()
[principal_title, principal_first_name, principal_last_name]
```




    ['dr.', 'clark', 'breTThauer']




```python
#__SOLUTION__
# .join()

' '.join([principal_title, principal_first_name, principal_last_name]).title()
```




    'Dr. Clark Bretthauer'



Here is a trick using a list comprehension (see below) to get the principal's initials.  


```python
''.join(name[0].upper() for name in [principal_first_name, 
                                     principal_middle_initial, 
                                     principal_last_name]
       )
```




    'CMB'



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


```python
# print = 'A bad idea'
# print
```


```python
# print(print)
```


```python
print('After the kernal has restarted, this will work again')
```

    After the kernal has restarted, this will work again


If we assign a string to the variable print, we overwrite the print's expected behavior in memory.  In order to retrieve print's original functionality, we need to restart our kernal.  


Two built in functions are used below to create a string representing the sum of the numbers 1 through 5


```python
' + '.join(str(num) for num in range(1, 6))
```




    '1 + 2 + 3 + 4 + 5'



#### f-Strings

f-Strings are a convenient way to bring variables into strings.  F-strings have numerous applications, from webscraping to SQL queries to writing the R-like formulas we will see in Phase 2.

Consider the scenario where you want to get data of every principal in a school district.  You have a list of last names, and you know the pattern of a url.  
`www.lakeviewhigh.edu/principal/<principal_last_name>/about/`


```python
principal_last_name
```




    'breTThauer'



We can use an f-string to interpolate the last name into the url. We insert the variable, which has to be a **string** into the curly braces.


```python
f"www.lakeviewhigh.edu/principal/{}/about/""
```


      File "<ipython-input-18-e64eb304cfd8>", line 1
        f"www.lakeviewhigh.edu/principal/{}/about/""
                                                    ^
    SyntaxError: EOL while scanning string literal




```python
#__SOLUTION__
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
for i in <fill_in>:
    print(f"https://www.cps.edu/schools/networks/network-{<fill_in>}/")
```


      File "<ipython-input-20-91db1d5da457>", line 1
        for i in <fill_in>:
                 ^
    SyntaxError: invalid syntax




```python
#__SOLUTION__
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

Let's read in an object which contains Chicago Public School districts and the schools associated with them. 


```python
import pickle

with open('./data/school_dict.p', 'rb') as read_file:
    schools = pickle.load(read_file)
```

The object schools is a dictionary, with a list associated with a district number.  Let's isolate district 1 and 2, and practice list methods with the first 5 schools in each list.


```python
district_1 = schools[1][:5]
district_2 = schools[2][:5]

```


```python
print(district_1)
print(district_2)
```

    ['ALBANY PARK', 'BATEMAN', 'BEARD', 'BEAUBIEN', 'BELDING']
    ['BOONE', 'BRENNEMANN', 'CLINTON', 'COURTENAY', 'DECATUR']



```python
# Add district_1 to district_2 so that we have one big list
# Note that this will alter district_2!


```


```python
#__SOLUTION__
print(len(district_2))
district_2.extend(district_1)
len(district_2)
```

    5





    10




```python
one_random_student(ds_west)
```

    Josh



```python
# What would this code return?

district_1.append(district_2)
district_1
```




    ['ALBANY PARK',
     'BATEMAN',
     'BEARD',
     'BEAUBIEN',
     'BELDING',
     ['BOONE',
      'BRENNEMANN',
      'CLINTON',
      'COURTENAY',
      'DECATUR',
      'ALBANY PARK',
      'BATEMAN',
      'BEARD',
      'BEAUBIEN',
      'BELDING']]




```python
# Let's build a list of the characters of the all of the letters in district_2

school_names_joined = ''.join(district_2)
school_names_joined


```




    'BOONEBRENNEMANNCLINTONCOURTENAYDECATURALBANY PARKBATEMANBEARDBEAUBIENBELDING'




```python
# What does list(word) do?

list(school_names_joined)
```




    ['B',
     'O',
     'O',
     'N',
     'E',
     'B',
     'R',
     'E',
     'N',
     'N',
     'E',
     'M',
     'A',
     'N',
     'N',
     'C',
     'L',
     'I',
     'N',
     'T',
     'O',
     'N',
     'C',
     'O',
     'U',
     'R',
     'T',
     'E',
     'N',
     'A',
     'Y',
     'D',
     'E',
     'C',
     'A',
     'T',
     'U',
     'R',
     'A',
     'L',
     'B',
     'A',
     'N',
     'Y',
     ' ',
     'P',
     'A',
     'R',
     'K',
     'B',
     'A',
     'T',
     'E',
     'M',
     'A',
     'N',
     'B',
     'E',
     'A',
     'R',
     'D',
     'B',
     'E',
     'A',
     'U',
     'B',
     'I',
     'E',
     'N',
     'B',
     'E',
     'L',
     'D',
     'I',
     'N',
     'G']




```python
district_2.pop()

# What does this return?
# What does district_2 look like now?


```




    'BELDING'



### List Comprehension

List comprehension is a handy way of generating a new list from existing lists.

Suppose I want the district in the school names.


I can do this with list comprehension!

The syntax is: ```[ f(x) for x in [original list] ]```


```python
school_district_names = [school_name + '_2' for school_name in district_2]
```


```python
school_district_names
```




    ['BOONE_2',
     'BRENNEMANN_2',
     'CLINTON_2',
     'COURTENAY_2',
     'DECATUR_2',
     'ALBANY PARK_2',
     'BATEMAN_2',
     'BEARD_2',
     'BEAUBIEN_2']



# Individual Exercise:

Take 2 minutes, turn off your camera and create a list, using a list comprehension, of all the string lengths in district 4. In other words, create a new list comprised of the character lengths of all the school names in district 4.  Count spaces as a character.

Turn your camera back on when you are finished.


```python
# Your code here
district_4 = None
district_4_lengths = None
```


```python
#__SOLUTION__
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


```python
type(schools)
```


```python
# Use the .keys() method to print the keys of this dictionary!

# Use the .values() method to print the values of this dictionary!

# Below, we see that the items() method returns both keys and values which returns a tuple of keys and values:
# The code below prints the district number plus the first school in each district
# Since it is a tuple, item[0] accesses the first index of the tuple referring to the key(i.e. district)
# and item[1] refers to the 2nd index, i.e. the list of schools. 
# item[1][0] then refers to the first school in the list of schools of the district.
for item in schools.items():
    print(item[0], item[1][0])
    

```

    1 ALBANY PARK
    2 BOONE
    3 BRUNSON
    4 ALCOTT ES
    5 BEIDLER
    6 ARMOUR
    7 COOPER
    8 BRIGHTON PARK
    9 ARIEL
    10 ASHBURN
    11 BARTON
    12 ASHE
    13 ALDRIDGE
    14 DEVRY HS
    15 ALCOTT HS
    16 AIR FORCE HS


## Zipping

Zipping is a way of merging two arrays into one. The result can be cast as a list or as a dict.


```python
student_count = [197, 102, 105, 162]
district_2
```




    ['BOONE',
     'BRENNEMANN',
     'CLINTON',
     'COURTENAY',
     'DECATUR',
     'ALBANY PARK',
     'BATEMAN',
     'BEARD',
     'BEAUBIEN']




```python
zip(district_2, student_count)
```




    <zip at 0x1140c4608>




```python
for school, count in zip(district_2, student_count):
    print(school, count)
```

    BOONE 197
    BRENNEMANN 102
    CLINTON 105
    COURTENAY 162



```python
dict(zip(district_2,student_count))
```




    {'BOONE': 197, 'BRENNEMANN': 102, 'CLINTON': 105, 'COURTENAY': 162}



## While Loops

We have already seen 'for'-loops, where you use a loop and count the iterations by the some pre-specified number. But sometimes we don't know how many times we'll need to iterate!

Suppose I need to choose a certain number of schools (say 10) from  a list.  I can set a variable as a counter, and create a while loop which will add 1 to that counter with each pass through the loop.


```python
# What will the print statement below print out?
one_random_student(ds_west)
```

    Angie



```python
school_count = 0

while school_count < 10:
    dist_4_schools = schools[4]
    print(dist_4_schools[school_count])
    
    school_count += 1

print(school_count)
```

    ALCOTT ES
    AUDUBON
    AVONDALE-LOGANDALE
    BARRY
    BELL
    BLAINE
    BRENTANO
    CHASE
    DARWIN
    FRANKLIN
    10


Now let's think of a scenario where we would like to iterate through the school list of a district, sum the populations of the schools, and stop when the sum exceeds a certain number.  


```python
district_3_schools = schools[3]
district_3_pops = [129,107,167,103,111,137,145,
 107,198,183,132,100,120,162,
 116,146,137]

```


```python
sample_school_populations = 0
school_index = 0

while sample_school_populations < 1000:
    sample_school_populations += district_3_pops[school_index]
    school_index+=1

print(sample_school_populations)
```

    1006


How can we update the code to stop before 1000?


```python
one_random_student(ds_west)
```

    Jonathan



```python
#__SOLUTION__
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


```python
school_count = 0

while school_count < 10:
    dist_4_schools = schools[4]
    
    if dist_4_schools[school_count][0] == 'B':
        break
        
    print(dist_4_schools[school_count])
    
    school_count += 1

print(school_count)
```

    ALCOTT ES
    AUDUBON
    AVONDALE-LOGANDALE
    3


Wherever we encounter **continue**, the code will return to the top of the loop it is moving through.


```python
school_count = 0

while school_count < 10:
    dist_4_schools = schools[4]
    
    if dist_4_schools[school_count][0] == 'B':
        school_count += 1
        continue
        
    print(dist_4_schools[school_count])
    
    school_count += 1


```

    ALCOTT ES
    AUDUBON
    AVONDALE-LOGANDALE
    CHASE
    DARWIN
    FRANKLIN


# Nested for loops

Lets imagine we have a dictionary where each key is a school district, and each value is a school population number.  


```python
with open('./data/school_pop_dict.p', 'rb') as read_file:
    school_pop_dict = pickle.load(read_file)
```


```python
print(school_pop_dict[1][:10])
```

    [295, 748, 614, 477, 534, 170, 278, 806, 583, 834]


Let's iterate through the districts, add up the school populations, and print out the total populations in each district.

To do so, our top level for loops interates through the keys (our districts) sequentially. 

For each district, the inner loop iterates through the list associated with each district, summing all of the populations.



```python
for district in school_pop_dict:
    district_population = 0
    for pop in school_pop_dict[district]:
        district_population += pop
    print(district, district_population)
```

# Round Robin

We can update the above code to store our data in a dictionary by instantiating a dictionary outside of the outer loop.



```python
one_random_student(ds_west)
```

    Sindhu



```python

# Instantiate dictionary here 

for district in school_pop_dict:
    district_population = 0
    for pop in school_pop_dict[district]:
        district_population += pop
    # assign summed district populations to the dictionary here
    
print(district_population_dict)
```

    {1: 19251, 2: 12011, 3: 7334, 4: 16177, 5: 15301, 6: 13163, 7: 10489, 8: 11525, 9: 11925, 10: 17828, 11: 15426, 12: 16208, 13: 16983, 14: 10428, 15: 13406, 16: 10128}



```python
#__SOLUTION__
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


```python
with open('./data/nested_schools_dict.p', 'rb') as read_file:
    nested_schools_dict = pickle.load(read_file)
```


```python
nested_schools_dict[1]
```




    {'ALBANY PARK': 922,
     'BATEMAN': 714,
     'BEARD': 774,
     'BEAUBIEN': 986,
     'BELDING': 874,
     'BRIDGE': 355,
     'CANTY': 289,
     'CLEVELAND': 645,
     'DEVER': 461,
     'DIRKSEN': 562,
     'EDGEBROOK': 892,
     'EDISON': 172,
     'EDISON PARK': 956,
     'FARNSWORTH': 250,
     'GARVY': 160,
     'GRAY': 721,
     'HAUGAN': 626,
     'HENRY': 713,
     'HIBBARD': 523,
     'HITCH': 480,
     'MURPHY': 987,
     'NORTH RIVER': 911,
     'NORWOOD PARK': 684,
     'ONAHAN': 148,
     'ORIOLE PARK': 502,
     'PETERSON': 928,
     'PORTAGE PARK': 706,
     'PRUSSING': 273,
     'REINBERG': 908,
     'SAUGANASH': 576,
     'SCAMMON': 737,
     'SOLOMON': 413,
     'STOCK': 934,
     'VOLTA': 552,
     'WILDWOOD': 956}



## Round Robin: Let's make a list of schools with student bodies less than 500.


```python
one_random_student(ds_west)
```

    Jonathan



```python
# Your code here
```


```python
low_pop_schools = []

for district in nested_schools_dict:
    # Fill in the line below to iterate through each school associated with each district
    for school in 'fill_in':
        # Fill in the line below to access the school population associated with each school key
        if 'fill_in' < 500:
            low_pop_schools.append(school)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-70-b1828417b063> in <module>
          5     for school in 'fill_in':
          6         # Fill in the line below to access the school population associated with each school key
    ----> 7         if 'fill_in' < 500:
          8             low_pop_schools.append(school)


    TypeError: '<' not supported between instances of 'str' and 'int'



```python
#__SOLUTION__
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


```python
# Let's code it!
def district_schools(dist_num, schools_dictionary):
    
    '''
    parameters
    dist_num: The number of the school district to be used as a dicitonary key in schools_dictionary
    schools_dictionary: ad dictionary with keys equal to school districts and values equal to school names
    
    returns:
    a list of schools for the given district number
    '''
    print(dist_num)
    
    return schools_dictionary[dist_num]

```

### Calling Functions

To _call_ a function, simply type its name, along with any necessary arguments in parentheses.


```python
# Let's call it!
district_schools(3,schools)
```

    3





    ['BRUNSON',
     'BURBANK',
     'DEPRIEST',
     'ELLINGTON',
     'FALCONER',
     'HANSON PARK',
     'HAY',
     'LELAND',
     'LOCKE J',
     'LOVETT',
     'LYON',
     'NASH',
     'NORTHWEST',
     'PRIETO',
     'SAYRE',
     'SCHUBERT',
     'SPENCER',
     'YOUNG ES']



When a function is called, it executes all code up to the **return** statement.  Whatever is returned can be passed into a variable, and stored in memory.


```python
district_3_schools = district_schools(3,schools)
```

    3


### Default Argument Values

Sometimes we'll want the argument(s) of our function to have default values.


```python
def district_schools(dist_num, schools_dictionary=schools):
    
    '''
    parameters
    dist_num: The number of the school district to be used as a dicitonary key in schools_dictionary
    schools_dictionary: ad dictionary with keys equal to school districts and values equal to school names
    
    returns:
    a list of schools for the given district number
    '''
    print(dist_num)
    return schools_dictionary[dist_num]
```


```python
district_schools(2)
```

    2





    ['BOONE',
     'BRENNEMANN',
     'CLINTON',
     'COURTENAY',
     'DECATUR',
     'DISNEY',
     'FIELD',
     'GALE',
     'HAYT',
     'JAMIESON',
     'JORDAN',
     'KILMER',
     'MCCUTCHEON',
     'MCPHERSON',
     'NEW FIELD',
     'RAVENSWOOD',
     'STONE',
     'SWIFT',
     'WATERS']



# Pair Program: A full function

Create a function that has two parameters:  
  - district  
  - the nested_schools_dict dictionary  
    
The function should do two things.  
  - Return a dictionary of all schools within the given district with a student body less than 500. The keys are the school names, the values are the school pops.  
  - Print a statement that reads `<school_name> has <x_number> of students`. Use an f-string for the print statement.


```python
def low_pop_schools():
    """
    paramaters:
    district: a school district to be used as a key in the nested school dictionary
    schools: a nested dictionary with each district as a key, paired with a dictionary of school names and school pops
    
    returns:
    low_pop_schools: a dictionary of schools with populations under 500 
    with school name as keys and school populations as values
    """
    
    low_pop_schools = {}
    # Your code here
    
    return low_pop_schools
```


```python
low_pop_schools(1)
```

    BRIDGE has 355 students
    CANTY has 289 students
    DEVER has 461 students
    EDISON has 172 students
    FARNSWORTH has 250 students
    GARVY has 160 students
    HITCH has 480 students
    ONAHAN has 148 students
    PRUSSING has 273 students
    SOLOMON has 413 students





    {'BRIDGE': 355,
     'CANTY': 289,
     'DEVER': 461,
     'EDISON': 172,
     'FARNSWORTH': 250,
     'GARVY': 160,
     'HITCH': 480,
     'ONAHAN': 148,
     'PRUSSING': 273,
     'SOLOMON': 413}




```python
#__SOLUTION__
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
