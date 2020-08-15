
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



```python
ds_west = ['Mitsy', 'Captain Trevor', 'Bruce' ]

# This is always a good idea
%load_ext autoreload
%autoreload 2
            
import os
import sys
module_path = os.path.abspath(os.path.join(os.pardir, os.pardir))
if module_path not in sys.path:
    sys.path.append(module_path)
    
from src.student_caller import one_random_student
```



## Methods

A method is a function that belongs to an object. And in Python, most things are objects! Naturally, the methods that belong to a particular object can vary depending on the object's datatype.

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

    Bruce


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


```python
# .lower()
```


```python
#__SOLUTION__
# .lower()
principal_last_name.lower()
```




    'bretthauer'




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




```python
''.join(name[0].upper() for name in [principal_first_name, principal_middle_initial, principal_last_name])
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


```python
' + '.join(str(num) for num in range(1, 6))
```




    '1 + 2 + 3 + 4 + 5'



#### f-Strings

f-Strings are a convenient way to bring variables into strings.

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


      File "<ipython-input-17-e64eb304cfd8>", line 1
        f"www.lakeviewhigh.edu/principal/{}/about/""
                                                    ^
    SyntaxError: EOL while scanning string literal




```python
#__SOLUTION__
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
for i in <fill_in>:
    print(f"https://www.cps.edu/schools/networks/network-{<fill_in>}/")
```


      File "<ipython-input-21-91db1d5da457>", line 1
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


```python
import pickle

with open('./data/school_dict.p', 'rb') as read_file:
    schools = pickle.load(read_file)
```


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
# Add list_2 to list_1 so that we have one big list

# Note that this alters list_1!

print(len(district_1))
district_1.extend(district_2)
len(district_1)
```

    5





    10




```python
# What would this code return?

district_1.append(district_2)
```


```python
# Let's write a loop that will build a list of the characters of the all of the letters in district_2

school_salad = ''.join(district_2)
school_salad


```




    'BOONEBRENNEMANNCLINTONCOURTENAYDECATUR'




```python
# What does list(word) do?

list(school_salad)
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
     'R']




```python
district_2.pop()

# What does this return?
# What does district_2 look like now?


```




    'DECATUR'



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




    ['BOONE_2', 'BRENNEMANN_2', 'CLINTON_2', 'COURTENAY_2']



### Dictionary Methods

Here are some useful methods for dictionaries:

- ```.keys()```: returns an array of the dictionary's keys
- ```.values()```: returns an array of the dictionary's values
- ```.items()```: returns an array of key-value tuples


```python
type(schools)
```




    dict




```python
# Use the .keys() method to print the keys of this dictionary!

# Use the .values() method to print the values of this dictionary!

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




    ['BOONE', 'BRENNEMANN', 'CLINTON', 'COURTENAY']




```python
zip(district_2, student_count)
```




    <zip at 0x107d9d108>




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

    Mitsy



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

    Mitsy



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

Let's iterate through the districts, add up the school populations, and print out the total populations in each district



```python
for district in school_pop_dict:
    district_population = 0
    for pop in school_pop_dict[district]:
        district_population += pop
    print(district, district_population)
```

    1 19251
    2 12011
    3 7334
    4 16177
    5 15301
    6 13163
    7 10489
    8 11525
    9 11925
    10 17828
    11 15426
    12 16208
    13 16983
    14 10428
    15 13406
    16 10128


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



# Practice with nested dictionaries


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



## Let's make a list of schools with student bodies less than 500.


```python
### Round Robin
one_random_student(ds_west)
```

    Bruce



```python
# Your code here
```


```python
#__SOLUTION__
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
#__SOLUTION__
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
