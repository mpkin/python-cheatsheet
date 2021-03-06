# Python 3 Cheatsheet
#### References:

These notes came from the following sources:

    INTRODUCING PYTHON (1st Edition)
    Bill Lubanovic
    O'Reilly 2015

### Strings

The `print()` function adds spaces between strings, and a newline at the end
```python
print(99,'bottles','would be enough.\n')   # 99 bottles would be enough
```

Strings can be enclosed by either single or double quotes
```python
a = 'snap'; print(a)            # snap
b = "crackle"; print(b,'\n')    # crackle
```

You can combine quotes so that strings can contain ' or "
```python
c = "and I said 'nay' to him"; print(c)     # and I said 'nay' to him 
d = 'a captive double quote (")'; print(d)  # a captive double quote (") 
```

You can also just use escape characters
```python
esc = "\"I did nothing!\" he said. \"Not that either! Or the other thing.\""
print(esc)
```
    "I did nothing!" he said. "Not that either! Or the other thing."

Triple quotes are useful for multiline strings without having to use \n (note that if you had used single quotes here, you would get an EOL error)
```python
multi = '''
Here is a multiline string
containing a double quote (")
'''; print(multi)
```
    Here is a multiline string
    containing a double quote (")

Empty strings can be created in a number of ways
```python
e = ''; 
f = ""; 
g = ''''''; 
h = """"""; 
```

Note that Python does not add spaces when concatenating strings, but the `print()` function does!
```python
duck  = 'Duck.'
goose = 'Goose.'
print(duck + duck + goose)
print(duck,duck,goose)
```
    Duck.Duck.Goose.
    Duck. Duck. Goose.

Blank strings are useful as a starting point for concatenation
```python
bottles = 99
base    = ''
base   += 'current inventory: '
base   += str(bottles)
print(base, '\n')
```
    current inventory: 99

You can duplicate strings with *
```python
start = 'Na' * 8
end   = 'Batman!'
print(start,end,'\n')
```
    NaNaNaNaNaNaNaNa Batman!

Yyou can extract a character from a string by specifying its offset, or slicing. The syntax is `[start:end:step]`
```python
letters = 'abcdefghijklmnopqrstuvwxyz'
print(letters[0])      #a
print(letters[-1])     #z
print(letters[11:15])  #lmno
print(letters[22:])    #wxyz
print(letters[-4:])    #wxyz
print(letters[22:-1])  #wxy
print(letters[22:-10]) #empty string!
print(letters[::7])    #ahov; start to end in steps of 7
print(letters[::-1])   #zyxwvutsrqponmlkjihgfedcba; backwards
```

You can split strings quite easily
```python
todos = 'get gloves,get mask,give cat vitamins,call ambulance'
print(todos.split(',')) # split by commas
```
    ['get gloves', 'get mask', 'give cat vitamins', 'call ambulance']
```python
print(todos.split())    # default is to split by spaces
```
    ['get', 'gloves,get', 'mask,give', 'cat', 'vitamins,call', 'ambulance']

Note the split behaviour for repeating separator strings
```python
splitme = 'a/b//c/d///e'
print(splitme.split('/'))
```
    ['a', 'b', '', 'c', 'd', '', '', 'e']
```python
print(splitme.split('//'))
```
    ['a/b', 'c/d', '/e']

How to join lists into a single string
```python
crypto_list = ['Yeti', 'Bigfoot', 'Loch Ness Monster']
crypto_string = ', '.join(crypto_list)
print('\nFound and signing book deals:', crypto_string)
```
    Found and signing book deals: Yeti, Bigfoot, Loch Ness Monster

How to create a paragraph out of a list
```python
para = ['line 1', 'line 2', 'line 3']
para_string = '\n'.join(para)
print(para_string)
```
	  line 1
	  line 2
	  line 3

Illustrating some general string functions
```python
poem = '''All that doth flow we cannot liquid name
Or else would fire and water be the same;
But that is liquid which is moist and wet
Fire that property can never get.
Then 'tis not cold that doth the fire put out
But 'tis the wet that makes it die, no doubt'''
print(len(poem))              #249
print(poem.startswith('All')) #True
print(poem.endswith('Fin'))   #False
word = 'the'
print(poem.find(word))        #73
print(poem.rfind(word))       #214  (reverse find)
print(poem.count(word))       #3
print(poem.isalnum())         #False (only letters or numbers?)
```

Strip characters from string
```python
setup = '\na duck goes into a bar...'
print(setup.strip('.'))    #a duck goes into a bar
```

Capitalize all the words
```python
print(setup.title())       #A Duck Goes Into A Bar...
```

Capitalize all letters
```python
print(setup.upper())       #A DUCK GOES INTO A BAR...
```

Uncapitalize all letters
```python
print(setup.lower())       #a duck goes into a bar...
```

Swap upper and lower case
```python
print(setup.swapcase())    #A DUCK GOES INTO A BAR...'
```

Text alignment
```python
print(setup.center(30))    # center within 30 spaces
print(setup.rjust(30))     # right justify
print(setup.ljust(30))     # left justify
```

String replacement
```python
print(setup.replace('duck','marmoset'))
```
    a marmoset goes into a bar...

String replacement up to 100 times
```python
print(setup.replace('a ','a famous ', 100))
```
    a famous duck goes into a famous bar...

### Lists
```python
empty_list = [ ]
weekdays = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
big_birds = ['emu', 'ostrich', 'cassowary']
first_names = ['Graham', 'John', 'Terry', 'Terry', 'Michael']
```

You can also make an empty list with the list() function
```python
another_empty_list = list()
print(another_empty_list)   # []
```

Convert a string to a list
```python
print(list('cat'))   # ['c', 'a', 't']
```

Convert a tuple to a list
```python
a_tiple = ('ready', 'fire', 'aim')
print(list(a_tiple))
```
    ['ready', 'fire', 'aim']

Access/assign elements in a list
```python
marxes = ['Groucho', 'Chico', 'Harpo']
print(marxes[0])  #Groucho
print(marxes[-1]) #Harpo
marxes[2] = 'Wanda'
marxes;  #['Groucho', 'Chico', 'Wanda']
```

Lists of lists
```python
small_birds = ['hummingbird', 'finch']
extinct_birds = ['dodo', 'pigeon']
all_birds = [small_birds, extinct_birds, 'macaw']
all_birds; all_birds[0]; allbirds[1][0];
```
    [['hummingbird', 'finch'], ['dodo', 'pigeon'], 'macaw']
    ['hummingbird', 'finch']
    'dodo' 
    
Slicing
* think of indices as pointing between elements
```     +---+---+---+---+---+
     | A | b | c | d | e |
     +---+---+---+---+---+
     0   1   2   3   4   5
    -5  -4  -3  -2  -1
```
```python
marxes = ['Groucho', 'Chico', 'Harpo']
marxes[0:2]   # ['Groucho', 'Chico']
marxes[::2]   # ['Groucho', 'Harpo']  (stepsize=2 right)
marxes[::-2]  # ['Harpo', 'Groucho']  (start at end and go left)
marxes[::-1]  # ['Harpo', 'Chico', 'Groucho']  (reverse the list)
```

Append single element to end of list
```python
marxes = ['Groucho', 'Chico', 'Harpo']
marxes.append('Zeppo'); marxes
```
    ['Groucho', 'Chico', 'Harpo', 'Zeppo']

Append single element at specific point in list
```python
marxes = ['Groucho', 'Chico', 'Harpo']
marxes.insert(3, 'Gummo'); marxes
marxes.insert(10, 'Karl'); marxes  # offset beyond end of list inserts at end
marxes.insert(0, 'Bobbo'); marxes  # offset 0 inserts at beginning of list
```
    ['Groucho', 'Chico', 'Gummo', 'Harpo']
    ['Groucho', 'Chico', 'Gummo', 'Harpo', 'Karl']
    ['Bobbo', 'Groucho', 'Chico', 'Gummo', 'Harpo', 'Karl']
   
Delete single element of a list   
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Gummo', 'Zeppo']
del marxes[2]; marxes
del marxes[-1]; marxes
```
    ['Groucho', 'Chico', 'Gummo', 'Zeppo']
    ['Groucho', 'Chico', 'Gummo']

Delete single element of list by name
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Gummo', 'Zeppo']
marxes.remove('Gummo'); marxes
```
    ['Groucho', 'Chico', 'Harpo', 'Zeppo']
   
Get item from list and delete using pop()   
* note that `pop(0)` returns head of the list, `pop(-1)` returns tail
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Zeppo']
marxes.pop()   # 'Zeppo'
marxes;        # ['Groucho', 'Chico', 'Harpo']
marxes.pop(1); # 'Chico'
marxes;        # ['Groucho', 'Harpo']
```
  
Get index of item in list by name
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Zeppo']
marxes.index('Chico')  # 1
```
  
Combine/merge lists
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Zeppo']
others = ['Gummo', 'Karl']
marxes.extend(others); marxes;  # alternatively, marxes += others
```
    ['Groucho', 'Chico', 'Harpo', 'Zeppo', 'Gummo', 'Karl']
    
Check for element in list
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Zeppo']
'Groucho' in marxes  # True
'Bob' in marxes      # False
```

Count occurances of element in a list
```python
marxes = ['Groucho', 'Chico', 'Harpo', 'Zeppo']
marxes.count('Harpo')  # 1
```

Convert elements of list to string
```python
marxes = ['Groucho', 'Chico', 'Harpo']
', '.join(marxes)  # 'Groucho, Chico, Harpo'
```

Sort a list
```python
marxes = ['Groucho', 'Chico', 'Harpo']
sorted_marxes = sorted(marxes)  # creates a copy
sorted_marxes; # ['Chico', 'Groucho', 'Harpo']
marxes.sort()  # overwrites original list
marxes;        # ['Chico', 'Groucho', 'Harpo']
numbers = [2, 1, 4.0, 3]
numbers.sort(reverse=True)  # reverse sort
numbers;       # [4.0, 3, 2, 1]
```

Get length of list
```python
marxes = ['Groucho', 'Chico', 'Harpo']
len(marxes)  # 3
```

Copy a list
* note that if you just use `b=a` then `b` and `a` will point to the same object in memory, which you probably don't want
```python
a = [1, 2, 3]
b = a.copy()
c = list(a)
d = a[:]
```

### Tuples

* tuples are just immutable lists and elements can't be added or deleted after the tuple is defined

```python
empty_tuple = ()
one_marx    = ('Groucho')                    # ('Groucho',)
marx_tuple  = ('Groucho', 'Chico', 'Harpo')  # ('Groucho', 'Chico', 'Harpo')
a, b, c = marx_tuple
a  # 'Groucho'
b  # 'Chico'
c  # 'Harpo'
```

Swap values/strings using tuples
```python
password = 'swordfish'
icecream = 'tuttifrutti'
password, icecream = icecream, password
password  # 'tuttifrutti'
icecream  # 'swordfish'
```

Convert list to tuple
```python
marx_list  = ['Groucho', 'Chico', 'Harpo']
tuple(marx_list)  # ('Groucho', 'Chico', 'Harpo')
```

### Dictionaries

Converting tuples/lists to dictionaries
```python
# Convert a list (of two-item lists) to dict
alphabet1 = [ ['a', 'b'], ['c', 'd'], ['e', 'f'] ]
dict(alphabet1)  # {'c': 'd', 'a': 'b', 'e': 'f'}

# Convert a list (of two-item tuples) to dict
alphabet2 = [ ('a', 'b'), ('c', 'd'), ('e', 'f') ]
dict(alphabet2)  # {'c': 'd', 'a': 'b', 'e': 'f'}

# Convert a tuple (of two-item lists) to dict
alphabet3 = ( ['a', 'b'], ['c', 'd'], ['e', 'f'] )
dict(alphabet3)  # {'c': 'd', 'a': 'b', 'e': 'f'}

# Convert a tuple (of two-character strings) to dict
alphabet4 = [ 'ab', 'cd', 'ef' ]
dict(alphabet4)  # {'c': 'd', 'a': 'b', 'e': 'f'}

# Convert a list (of two-character strings) to dict
alphabet4 = ( 'ab', 'cd', 'ef' )
dict(alphabet4)  # {'c': 'd', 'a': 'b', 'e': 'f'}

```

Add or change item by key
```python
pythons = { 'Chapman':'Graham', 'Cleese':'John', 'Idle':'Eric', 'Jones':'Terry', 'Palin':'Michael', }
pythons['Gilliam'] = 'Gerry'  # add an item
pythons['Gilliam'] = 'Terry'  # change an item
pythons
```
    {'Cleese': 'John', 'Gilliam': 'Terry', 'Palin': 'Michael','Chapman': 'Graham', 'Idle': 'Eric', 'Jones': 'Terry'}

Repeated entries are clobbered
```python
pythons = {'Graham':'Chapman', 'John':'Cleese', 'Eric':'Idle', 'Terry':'Gilliam', 'Michael':'Palin', 'Terry':'Jones'}  # first Terry gets clobbered
pythons
```
    {'Terry':'Jones', 'Eric':'Idle', 'Graham':'Chapman', 'John':'Cleese', 'Michael':'Palin'}

Combine dictionaries
```python
pythons= { 'Chapman':'Graham', 'Cleese':'John', 'Gilliam':'Terry', 'Idle':'Eric', 'Jones':'Terry', 'Palin':'Michael', }
others = { 'Marx':'Groucho', 'Howard':'Moe' }
python.update(others)  # entries will be mixed together
```

Combining dictionaries with repeated entries will cause the second to overwrite the first
```python
first  = { 'a':1, 'b':2 }
second = { 'b':'platypus' }
first.update(second)
first  # { 'b':'platypus', 'a':1 }
```

Remove entries
```python
others = { 'Marx':'Groucho', 'Howard':'Moe' }
del others['Marx']

# remove all entries
others.clear()
others;  # {}
```

Test for a key in dictionaries
```python
others = { 'Marx':'Groucho', 'Howard':'Moe' }
'Marx' in python  # True
```

Get item in dictionary
```python
others = { 'Marx':'Groucho', 'Howard':'Moe' }
others.get('Marx', 'not in dict!')  # 'Groucho'
```

Get all keys in a dictionary
```python
letters = {'a':'b', 'c':'d', 'e':'f'}
letters.keys()        # dict_keys(['a', 'c', 'e'])
list(letters.keys())  # ['a', 'c', 'e']
```
Get all values in a dictionary
```python
letters = {'a':'b', 'c':'d', 'e':'f'}
list(letters.values())  # ['b', 'd', 'f']
```

Get all key-value pairs in a dictionary
```python
letters = {'a':'b', 'c':'d', 'e':'f'}
list(letters.items())  # [('a','b'), ('c','d'), ('e','f')]
```

Assigning and copying dictionaries
```python
# using = will create a pointer to the dictionary, basically
letters = {'a':'b', 'c':'d', 'e':'f'}
letters2 = letters
letters['g'] = 'h'
letters2  # {'a':'b', 'c':'d', 'e':'f', 'g':'h'}

# to actually copy a dictionary, use copy()
letters = {'a':'b', 'c':'d', 'e':'f'}
letters2 = letters.copy()
letters['g'] = 'h'
letters2  # {'a':'b', 'c':'d', 'e':'f'}
letters   # {'a':'b', 'c':'d', 'e':'f', 'g':'h'}
}
```

### Sets

* sets are fundamentally just a sequence of values

Creating sets (sets are unsorted, like dictionary keys)
```python
empty_set = set()
even_numbers = {0, 2, 4, 6, 8}
even_numbers # {0, 8, 2, 4, 6}
```

Convert string, list, tuple, dictionary to set (discards duplicates)
```python
letters = set('letters') # string to set
letters  # {'l','e','t','r','s'}
deers = set(['Dasher','Dancer','Prancer','Mason-Dixon']) # list to set
deers  # {'Dancer','Dasher','Prancer','Mason-Dixon'}
albums = set( ('Ummagumma', 'Echoes', 'Atom Heart Mother') ) # tuple to set
albums  # {'Ummagumma','Atom Heart Mother','Echoes'}
colors = set( {'apple':'red', 'orange':'orange', 'cherry':'red'} ) # dict to set (values discarded)
colors  # {'apple','cherry','orange'}
```

Intersection, union, difference, xor, subset, proper subset
```python
a = {1,2}
b = {2,3}
a & b              # {2}  INTERSECTION
a.intersection(b)  # {2}  INTERSECTION
a | b              # {1,2,3}  UNION
a.union(b)         # {1,2,3}  UNION
a - b              # {1}  DIFFERENCE
a.difference(b)    # {1}  DIFFERENCE
a ^ b                   # {1,3}  XOR
a.symmetric_difference  # {1,3}  XOR
a <= b             # false  SUBSET
a.issubset(b)      # false  SUBSET
a < b              # false  PROPER SUBSET
a >= b             # false  SUPERSET
a.issuperset(b)    # false  SUPERSET
a > b              # false  PROPER SUPERSET
```

Test for values in a set
```python
# create a dict
drinks = {
...     'martini': {'vodka', 'vermouth'},
...     'black russian': {'vodka', 'kahlua'},
...     'white russian': {'cream', 'kahlua', 'vodka'},
...     'manhattan': {'rye', 'vermouth', 'bitters'},
...     'screwdriver': {'orange juice', 'vodka'}}

for name, contents in drinks.items():
        if 'vodka' in contents and not ('vermouth' in contents or
...        'cream' in contents):
            print(name)
# screwdriver
# black russian
```

Find common values in a set
```python
for name, contents in drinks.items():
        if contents & {'vermouth', 'orange juice'}
            print(name)
# screwdriver
# martini 
# manhattan

# exclude some values
for name, contents in drinks.items():
        if 'vodka' in contents and not contents & {'vermouth', 'cream'}
            print(name)
# screwdriver
# black russian
```

### Combining Data Structures

```python
# start with three lists
marxes  = ['Groucho', 'Chico', 'Harpo']
pythons = ['Chapman', 'Cleese', 'Gilliam', 'Jones', 'Palin']
stooges = ['Moe', 'Curly', 'Larry']

tuple_of_lists = marxes,python,stooges
tuple_of_lists  # (['Groucho', 'Chico', 'Harpo'],['Chapman', 'Cleese', 'Gilliam', 'Jones', 'Palin'],['Moe', 'Curly', 'Larry'])

list_of_lists = [marxes, pythons, stooges]
list_of_lists  # [['Groucho', 'Chico', 'Harpo'],['Chapman', 'Cleese', 'Gilliam', 'Jones', 'Palin'],['Moe', 'Curly', 'Larry']]

dict_of_lists = {'Marxes':marxes, 'Pythons':pythons, 'Stooges':stooges}
dict_of_lists  # {'Stooges': ['Moe', 'Curly', 'Larry'],'Marxes': ['Groucho', 'Chico', 'Harpo'],'Pythons': ['Chapman', 'Cleese', 'Gilliam', 'Jones', 'Palin']}
```

