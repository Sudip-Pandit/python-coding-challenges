# 🐍 PYTHON FUNDAMENTALS MASTERY GUIDE

## Part 2: Lists, Tuples, Sets, Dictionaries, Lambda Functions & Advanced Operations

**Complete Reference with 200+ Practical Examples**

---

## TABLE OF CONTENTS

1. [LISTS - Complete Guide](#lists)
2. [TUPLES - Complete Guide](#tuples)
3. [SETS - Complete Guide](#sets)
4. [DICTIONARIES - Complete Guide](#dictionaries)
5. [LAMBDA FUNCTIONS - Complete Guide](#lambda)
6. [COMPREHENSIONS - List, Dict, Set](#comprehensions)
7. [FUNCTIONAL PROGRAMMING - Map, Filter, Reduce](#functional)
8. [ADVANCED TECHNIQUES](#advanced)
9. [INTERVIEW PATTERNS](#patterns)
10. [PRACTICE PROBLEMS](#practice)

---

# LISTS - COMPLETE GUIDE {#lists}

## What is a List?

A list is an **ordered, mutable collection** that can contain elements of different types.

### Creating Lists

```python
# Empty list
empty_list = []
empty_list = list()

# List with elements
numbers = [1, 2, 3, 4, 5]
mixed = [1, "string", 3.14, True, None]

# Using list constructor
numbers = list(range(1, 6))  # [1, 2, 3, 4, 5]
numbers = list("abc")         # ['a', 'b', 'c']

# Nested lists
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

### List Indexing and Slicing

```python
fruits = ['apple', 'banana', 'cherry', 'date', 'elderberry']

# Indexing (0-based)
print(fruits[0])      # 'apple'
print(fruits[-1])     # 'elderberry' (last element)
print(fruits[-2])     # 'date' (second to last)

# Slicing [start:end:step]
print(fruits[1:4])      # ['banana', 'cherry', 'date']
print(fruits[:3])       # ['apple', 'banana', 'cherry']
print(fruits[2:])       # ['cherry', 'date', 'elderberry']
print(fruits[::2])      # ['apple', 'cherry', 'elderberry']
print(fruits[::-1])     # ['elderberry', 'date', 'cherry', 'banana', 'apple']

# Assign with slicing
fruits[1:3] = ['blueberry', 'coconut']
print(fruits)  # ['apple', 'blueberry', 'coconut', 'date', 'elderberry']
```

### List Methods - Adding Elements

```python
numbers = [1, 2, 3]

# append() - Add single element at end
numbers.append(4)
print(numbers)  # [1, 2, 3, 4]

# extend() - Add multiple elements
numbers.extend([5, 6, 7])
print(numbers)  # [1, 2, 3, 4, 5, 6, 7]

# insert() - Add element at specific index
numbers.insert(2, 99)
print(numbers)  # [1, 2, 99, 3, 4, 5, 6, 7]

# Difference: append vs extend
list1 = [1, 2, 3]
list1.append([4, 5])
print(list1)  # [1, 2, 3, [4, 5]] - nested list

list2 = [1, 2, 3]
list2.extend([4, 5])
print(list2)  # [1, 2, 3, 4, 5] - flattened

# + operator (creates new list)
list3 = [1, 2] + [3, 4]  # [1, 2, 3, 4]
```

### List Methods - Removing Elements

```python
numbers = [1, 2, 3, 2, 4, 2, 5]

# remove() - Remove first occurrence of value
numbers.remove(2)
print(numbers)  # [1, 3, 2, 4, 2, 5]

# pop() - Remove and return element at index (default: last)
last = numbers.pop()
print(last, numbers)  # 5 [1, 3, 2, 4, 2]

first = numbers.pop(0)
print(first, numbers)  # 1 [3, 2, 4, 2]

# clear() - Remove all elements
numbers.clear()
print(numbers)  # []

# del statement
numbers = [1, 2, 3, 4, 5]
del numbers[1]
print(numbers)  # [1, 3, 4, 5]

del numbers[1:3]
print(numbers)  # [1, 5]
```

### List Methods - Finding Elements

```python
numbers = [1, 2, 3, 2, 4, 2, 5]
fruits = ['apple', 'banana', 'cherry']

# index() - Get index of first occurrence
index = numbers.index(2)
print(index)  # 1

# count() - Count occurrences
count = numbers.count(2)
print(count)  # 3

# in operator
print(2 in numbers)      # True
print(10 in numbers)     # False
print('banana' in fruits)  # True

# find() equivalent - using loop
def find_all(lst, value):
    return [i for i, x in enumerate(lst) if x == value]

indices = find_all(numbers, 2)
print(indices)  # [1, 3, 5]
```

### List Methods - Sorting and Reversing

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
words = ['zebra', 'apple', 'mango', 'banana']

# sort() - In-place sorting
numbers.sort()
print(numbers)  # [1, 1, 2, 3, 4, 5, 6, 9]

# sort with reverse
numbers.sort(reverse=True)
print(numbers)  # [9, 6, 5, 4, 3, 2, 1, 1]

# sort with key function
words.sort(key=len)
print(words)  # ['apple', 'mango', 'zebra', 'banana']

# sort with custom key
words.sort(key=lambda x: x[1])  # Sort by second character
print(words)  # ['zebra', 'mango', 'apple', 'banana']

# reverse() - In-place reverse
numbers = [1, 2, 3, 4, 5]
numbers.reverse()
print(numbers)  # [5, 4, 3, 2, 1]

# sorted() - Returns new sorted list
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
sorted_numbers = sorted(numbers)
print(sorted_numbers)  # [1, 1, 2, 3, 4, 5, 6, 9]
print(numbers)  # [3, 1, 4, 1, 5, 9, 2, 6] - original unchanged

# reversed() - Returns iterator
for num in reversed(numbers):
    print(num, end=' ')  # 6 2 9 5 1 4 1 3
```

### List Methods - Other Operations

```python
numbers = [1, 2, 3, 2, 4]

# copy() - Shallow copy
numbers_copy = numbers.copy()
numbers_copy.append(5)
print(numbers, numbers_copy)  # [1,2,3,2,4] [1,2,3,2,4,5]

# Shallow vs Deep copy
import copy
nested = [[1, 2], [3, 4]]
shallow = nested.copy()
deep = copy.deepcopy(nested)

shallow[0][0] = 99
print(nested, shallow)  # [[99,2],[3,4]] [[99,2],[3,4]] - both affected
print(deep)  # [[1,2],[3,4]] - unaffected

# sum(), min(), max(), len()
numbers = [1, 2, 3, 4, 5]
print(sum(numbers))  # 15
print(min(numbers))  # 1
print(max(numbers))  # 5
print(len(numbers))  # 5

# all(), any()
print(all([True, True, True]))   # True
print(all([True, False, True]))  # False
print(any([False, False, True]))  # True
print(any([False, False, False])) # False
```

### List Comprehension

```python
# Simple comprehension
squares = [x**2 for x in range(5)]
print(squares)  # [0, 1, 4, 9, 16]

# With condition
evens = [x for x in range(10) if x % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8]

# With transformation and condition
result = [x*2 for x in range(10) if x % 2 == 0]
print(result)  # [0, 4, 8, 12, 16]

# Nested comprehension
matrix = [[i+j for j in range(3)] for i in range(3)]
print(matrix)
# [[0, 1, 2], [1, 2, 3], [2, 3, 4]]

# Flattening nested list
nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [x for row in nested for x in row]
print(flat)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# With else clause
result = [x if x % 2 == 0 else 0 for x in range(5)]
print(result)  # [0, 0, 2, 0, 4]
```

---

# TUPLES - COMPLETE GUIDE {#tuples}

## What is a Tuple?

A tuple is an **ordered, immutable collection** that can contain elements of different types.

### Creating Tuples

```python
# Empty tuple
empty = ()
empty = tuple()

# Single element tuple (comma required!)
single = (1,)
single = 1,

# Multiple elements
coordinates = (10, 20)
mixed = (1, "string", 3.14, True, None)

# Tuple unpacking
a, b, c = (1, 2, 3)
print(a, b, c)  # 1 2 3

# Tuple with no parentheses
point = 1, 2, 3
print(point)  # (1, 2, 3)

# Creating from other sequences
numbers_tuple = tuple([1, 2, 3, 4])
string_tuple = tuple("abc")
print(numbers_tuple, string_tuple)  # (1, 2, 3, 4) ('a', 'b', 'c')
```

### Tuple Indexing and Slicing

```python
colors = ('red', 'green', 'blue', 'yellow', 'purple')

# Indexing
print(colors[0])      # 'red'
print(colors[-1])     # 'purple'

# Slicing
print(colors[1:3])    # ('green', 'blue')
print(colors[:2])     # ('red', 'green')
print(colors[::2])    # ('red', 'blue', 'purple')
print(colors[::-1])   # ('purple', 'yellow', 'blue', 'green', 'red')

# Immutability - tuples cannot be modified
# colors[0] = 'pink'  # TypeError: 'tuple' object does not support item assignment
```

### Tuple Methods

```python
numbers = (1, 2, 3, 2, 4, 2, 5)
fruits = ('apple', 'banana', 'cherry')

# count() - Count occurrences
print(numbers.count(2))  # 3
print(fruits.count('apple'))  # 1

# index() - Get index of first occurrence
print(numbers.index(2))  # 1
print(fruits.index('banana'))  # 1

# len(), min(), max(), sum()
print(len(numbers))  # 7
print(min(numbers))  # 1
print(max(numbers))  # 5
print(sum(numbers))  # 19

# in operator
print(2 in numbers)  # True
print('apple' in fruits)  # True
```

### Tuple Unpacking

```python
# Simple unpacking
point = (10, 20)
x, y = point
print(x, y)  # 10 20

# Unpacking with more values
point = (10, 20, 30)
x, y, z = point
print(x, y, z)  # 10 20 30

# Using * to capture remaining values
first, *middle, last = (1, 2, 3, 4, 5)
print(first, middle, last)  # 1 [2, 3, 4] 5

# Swapping values
a, b = (5, 10)
a, b = b, a  # Elegant tuple unpacking
print(a, b)  # 10 5

# Return multiple values
def get_coordinates():
    return (10, 20)

x, y = get_coordinates()
print(x, y)  # 10 20

# Unpacking in loops
pairs = [(1, 2), (3, 4), (5, 6)]
for x, y in pairs:
    print(f"x={x}, y={y}")
```

### Named Tuples

```python
from collections import namedtuple

# Define a named tuple
Point = namedtuple('Point', ['x', 'y'])
Coordinate = namedtuple('Coordinate', 'x y')  # Space-separated also works

# Create instances
p = Point(10, 20)
print(p.x, p.y)  # 10 20
print(p[0], p[1])  # 10 20 (still indexable)

# With defaults
Person = namedtuple('Person', ['name', 'age', 'city'], defaults=[None, None, 'Unknown'])
person = Person('Alice')
print(person)  # Person(name='Alice', age=None, city='Unknown')

# Very useful for function returns
def get_user_info():
    User = namedtuple('User', ['id', 'name', 'email'])
    return User(1, 'John', 'john@example.com')

user = get_user_info()
print(user.name, user.email)  # John john@example.com
```

### When to Use Tuples

```python
# 1. As dictionary keys (lists cannot be keys)
user_cache = {}
user_cache[(1, 'admin')] = {'name': 'John', 'permissions': ['read', 'write']}

# 2. Function return values
def divide(a, b):
    return (a // b, a % b)

quotient, remainder = divide(10, 3)

# 3. Protecting data from accidental modification
def get_immutable_config():
    return ('production', 'https://example.com', 5000)

# 4. Using with set operations (lists can't be in sets)
coordinates = {(0, 0), (1, 1), (2, 2)}

# 5. Slight performance improvement (tuples are faster than lists)
# when you're not modifying the data
```

---

# SETS - COMPLETE GUIDE {#sets}

## What is a Set?

A set is an **unordered, mutable collection of unique elements**. Perfect for membership testing and removing duplicates.

### Creating Sets

```python
# Empty set (must use set(), not {})
empty_set = set()

# Sets with elements
numbers = {1, 2, 3, 4, 5}
colors = {'red', 'green', 'blue'}
mixed = {1, 'string', 3.14}  # Can contain mixed types (hashable only)

# Creating from other sequences
numbers_set = set([1, 2, 3, 2, 1])  # {1, 2, 3}
string_set = set("hello")  # {'h', 'e', 'l', 'o'}

# Important: Duplicate elements are automatically removed
duplicates = {1, 1, 2, 2, 3, 3}
print(duplicates)  # {1, 2, 3}

# Note: Dictionaries use {} too!
empty_dict = {}  # This is a dict, not a set
print(type(empty_dict))  # <class 'dict'>
```

### Set Operations - Adding and Removing

```python
numbers = {1, 2, 3}

# add() - Add single element
numbers.add(4)
print(numbers)  # {1, 2, 3, 4}

# add() existing element (no effect)
numbers.add(3)
print(numbers)  # {1, 2, 3, 4}

# update() - Add multiple elements
numbers.update([5, 6, 7])
print(numbers)  # {1, 2, 3, 4, 5, 6, 7}

# update() with strings (adds each character)
letters = {'a', 'b'}
letters.update("cd")
print(letters)  # {'a', 'b', 'c', 'd'}

# remove() - Remove element (raises KeyError if not found)
numbers = {1, 2, 3, 4}
numbers.remove(3)
print(numbers)  # {1, 2, 4}
# numbers.remove(10)  # KeyError!

# discard() - Remove element (no error if not found)
numbers.discard(2)
print(numbers)  # {1, 4}
numbers.discard(10)  # No error
print(numbers)  # {1, 4}

# pop() - Remove and return arbitrary element
numbers = {1, 2, 3, 4, 5}
element = numbers.pop()
print(element, numbers)  # Some element and {remaining elements}

# clear() - Remove all elements
numbers.clear()
print(numbers)  # set()
```

### Set Mathematical Operations

```python
set_a = {1, 2, 3, 4, 5}
set_b = {4, 5, 6, 7, 8}

# Union - All elements from both sets
union = set_a | set_b
union = set_a.union(set_b)
print(union)  # {1, 2, 3, 4, 5, 6, 7, 8}

# Intersection - Elements in both sets
intersection = set_a & set_b
intersection = set_a.intersection(set_b)
print(intersection)  # {4, 5}

# Difference - Elements in first set but not second
difference = set_a - set_b
difference = set_a.difference(set_b)
print(difference)  # {1, 2, 3}

# Symmetric Difference - Elements in either set but not both
sym_diff = set_a ^ set_b
sym_diff = set_a.symmetric_difference(set_b)
print(sym_diff)  # {1, 2, 3, 6, 7, 8}

# Subset - Is set_a a subset of set_b?
set_c = {4, 5}
print(set_c <= set_b)  # True (is subset)
print(set_c.issubset(set_b))  # True

# Superset - Is set_b a superset of set_c?
print(set_b >= set_c)  # True (is superset)
print(set_b.issuperset(set_c))  # True

# Disjoint - Do sets have no common elements?
set_d = {9, 10, 11}
print(set_a.isdisjoint(set_d))  # True
print(set_a.isdisjoint(set_b))  # False
```

### Set Membership and Iteration

```python
numbers = {1, 2, 3, 4, 5}
colors = {'red', 'green', 'blue'}

# in operator
print(3 in numbers)      # True
print(10 in numbers)     # False
print('red' in colors)   # True

# not in operator
print(10 not in numbers)  # True

# Iteration
for num in numbers:
    print(num, end=' ')  # Prints each element (unordered)

for color in colors:
    print(color, end=' ')

# Membership with high performance
# Sets use hash tables - O(1) average time
# Much faster than lists for large collections
large_set = set(range(1000000))
print(500000 in large_set)  # Very fast!

# len()
print(len(numbers))  # 5
```

### Set Comprehension

```python
# Simple comprehension
squares = {x**2 for x in range(5)}
print(squares)  # {0, 1, 4, 9, 16}

# With condition
evens = {x for x in range(10) if x % 2 == 0}
print(evens)  # {0, 2, 4, 6, 8}

# Removing duplicates from list
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique = {x for x in numbers}
print(unique)  # {1, 2, 3, 4}

# From string
vowels = {x for x in "hello world" if x in "aeiou"}
print(vowels)  # {'e', 'o'}

# Nested comprehension
coordinates = {(x, y) for x in range(3) for y in range(3)}
print(coordinates)
# {(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)}
```

### Common Set Use Cases

```python
# 1. Remove duplicates from list
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique = list(set(numbers))
print(unique)  # Order may vary

# Better: preserve order
unique = []
seen = set()
for num in numbers:
    if num not in seen:
        unique.append(num)
        seen.add(num)
print(unique)  # [1, 2, 3, 4]

# 2. Find common elements
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]
common = list(set(list1) & set(list2))
print(common)  # [4, 5]

# 3. Find unique elements in one list but not the other
unique_to_list1 = list(set(list1) - set(list2))
print(unique_to_list1)  # [1, 2, 3]

# 4. Fast membership testing
# For checking if element exists
email_list = {...}  # million emails
if email in set(email_list):  # Much faster than list!
    pass

# 5. Get unique values from dictionary keys
data = {'a': 1, 'b': 2, 'c': 1, 'd': 2}
unique_values = set(data.values())
print(unique_values)  # {1, 2}
```

---

# DICTIONARIES - COMPLETE GUIDE {#dictionaries}

## What is a Dictionary?

A dictionary is an **unordered collection of key-value pairs**. Keys must be hashable (unique), values can be anything.

### Creating Dictionaries

```python
# Empty dictionary
empty = {}
empty = dict()

# Dictionary with key-value pairs
person = {'name': 'Alice', 'age': 30, 'city': 'NYC'}
settings = {'theme': 'dark', 'language': 'English', 'notifications': True}

# Using dict() constructor
scores = dict(alice=95, bob=87, charlie=92)
print(scores)  # {'alice': 95, 'bob': 87, 'charlie': 92}

# From list of tuples
pairs = [('a', 1), ('b', 2), ('c', 3)]
numbers_dict = dict(pairs)
print(numbers_dict)  # {'a': 1, 'b': 2, 'c': 3}

# From zip
keys = ['a', 'b', 'c']
values = [1, 2, 3]
numbers_dict = dict(zip(keys, values))
print(numbers_dict)  # {'a': 1, 'b': 2, 'c': 3}

# Dictionary keys must be hashable
# Can be: strings, numbers, tuples
# Cannot be: lists, sets, dictionaries, other mutable types

valid_keys = {1: 'int', 'str': 'string', (1, 2): 'tuple'}
# invalid = {[1, 2]: 'list'}  # TypeError!
```

### Accessing Dictionary Values

```python
person = {'name': 'Alice', 'age': 30, 'city': 'NYC'}

# Direct access with []
print(person['name'])    # 'Alice'
print(person['age'])     # 30

# Using get() - safer (returns None if key doesn't exist)
print(person.get('name'))  # 'Alice'
print(person.get('phone'))  # None
print(person.get('phone', 'No phone'))  # 'No phone' (default value)

# Check if key exists
print('name' in person)      # True
print('phone' in person)     # False

# Accessing non-existent key with []
# person['phone']  # KeyError!

# setdefault() - Get value, set default if not exists
age = person.setdefault('age', 25)
print(age, person)  # 30 {'name': 'Alice', 'age': 30, 'city': 'NYC'}

phone = person.setdefault('phone', '555-1234')
print(phone, person)  # '555-1234' {'name': 'Alice', 'age': 30, 'city': 'NYC', 'phone': '555-1234'}
```

### Modifying Dictionaries

```python
person = {'name': 'Alice', 'age': 30}

# Adding/modifying values
person['city'] = 'NYC'
person['age'] = 31
print(person)  # {'name': 'Alice', 'age': 31, 'city': 'NYC'}

# update() - Add/merge multiple key-value pairs
person.update({'phone': '555-1234', 'email': 'alice@example.com'})
print(person)

# update() with another dictionary
other = {'country': 'USA'}
person.update(other)
print(person)

# pop() - Remove and return value
city = person.pop('city')
print(city, person)  # 'NYC' without 'city' key

# pop() with default
country = person.pop('country', 'Unknown')
print(country, person)

# popitem() - Remove and return last key-value pair (3.7+)
key, value = person.popitem()
print(key, value)

# clear() - Remove all items
copy = person.copy()
copy.clear()
print(copy)  # {}
```

### Dictionary Methods

```python
person = {'name': 'Alice', 'age': 30, 'city': 'NYC'}

# keys() - Get all keys
keys = person.keys()
print(keys)  # dict_keys(['name', 'age', 'city'])
print(list(keys))  # ['name', 'age', 'city']

# values() - Get all values
values = person.values()
print(values)  # dict_values(['Alice', 30, 'NYC'])
print(list(values))  # ['Alice', 30, 'NYC']

# items() - Get all key-value pairs
items = person.items()
print(items)  # dict_items([('name', 'Alice'), ('age', 30), ('city', 'NYC')])
print(list(items))  # [('name', 'Alice'), ('age', 30), ('city', 'NYC')]

# Iterating
for key in person:
    print(key, person[key])

for key, value in person.items():
    print(f"{key}: {value}")

# copy() - Shallow copy
copy = person.copy()
copy['age'] = 25
print(person, copy)  # Different objects

# Deep copy for nested dicts
import copy
nested = {'user': {'name': 'Alice', 'age': 30}}
shallow = nested.copy()
deep = copy.deepcopy(nested)

shallow['user']['age'] = 25
print(nested, shallow)  # Both affected (nested dict is shared)
print(deep)  # Unaffected

# len() - Number of key-value pairs
print(len(person))  # 3
```

### Dictionary Comprehension

```python
# Simple comprehension
squares = {x: x**2 for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# With condition
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}

# Swapping keys and values
original = {'a': 1, 'b': 2, 'c': 3}
swapped = {v: k for k, v in original.items()}
print(swapped)  # {1: 'a', 2: 'b', 3: 'c'}

# From lists
keys = ['a', 'b', 'c', 'd']
values = [1, 2, 3, 4]
result = {k: v for k, v in zip(keys, values)}
print(result)  # {'a': 1, 'b': 2, 'c': 3, 'd': 4}

# String to character counts
word = "hello"
char_count = {char: word.count(char) for char in set(word)}
print(char_count)  # {'h': 1, 'e': 1, 'l': 2, 'o': 1}

# Filtering
data = {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
filtered = {k: v for k, v in data.items() if v > 2}
print(filtered)  # {'c': 3, 'd': 4, 'e': 5}
```

### Advanced Dictionary Patterns

```python
# 1. Default Dictionary (automatically provides default value)
from collections import defaultdict

# Regular dict
regular = {}
# regular['count'] += 1  # KeyError!

# Default dict
counts = defaultdict(int)  # Default value is 0
counts['apple'] += 1
counts['apple'] += 1
counts['banana'] += 1
print(counts)  # defaultdict(<class 'int'>, {'apple': 2, 'banana': 1})

# With list
grouped = defaultdict(list)
grouped['fruits'].append('apple')
grouped['fruits'].append('banana')
grouped['vegetables'].append('carrot')
print(grouped)
# defaultdict(<class 'list'>, {'fruits': ['apple', 'banana'], 'vegetables': ['carrot']})

# With lambda
numbers = defaultdict(lambda: 0)
numbers['count'] += 1

# 2. Ordered Dictionary (maintains insertion order)
from collections import OrderedDict
ordered = OrderedDict()
ordered['first'] = 1
ordered['second'] = 2
ordered['third'] = 3
print(ordered)  # OrderedDict([('first', 1), ('second', 2), ('third', 3)])

# Note: Regular dicts maintain order in Python 3.7+

# 3. Counter (count occurrences)
from collections import Counter
word = "mississippi"
letter_count = Counter(word)
print(letter_count)  # Counter({'i': 4, 's': 4, 'm': 1, 'p': 2})
print(letter_count.most_common(3))  # [('i', 4), ('s', 4), ('p', 2)]

# 4. Nested dictionaries
employees = {
    'emp1': {'name': 'Alice', 'salary': 50000, 'department': 'IT'},
    'emp2': {'name': 'Bob', 'salary': 55000, 'department': 'HR'},
    'emp3': {'name': 'Charlie', 'salary': 52000, 'department': 'IT'}
}

print(employees['emp1']['name'])  # 'Alice'

# Safe access to nested
def get_nested(d, *keys, default=None):
    for key in keys:
        d = d.get(key, {})
    return d if d else default

salary = get_nested(employees, 'emp1', 'salary')
print(salary)  # 50000

# 5. Merge dictionaries (Python 3.9+)
dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3, 'd': 4}
merged = dict1 | dict2  # {'.a': 1, 'b': 2, 'c': 3, 'd': 4}

# Python 3.5+
merged = {**dict1, **dict2}

# update()
dict1.update(dict2)
```

---

# LAMBDA FUNCTIONS - COMPLETE GUIDE {#lambda}

## What is a Lambda Function?

A lambda is a **small anonymous function** defined with the `lambda` keyword. Useful for short operations.

### Basic Lambda Syntax

```python
# Syntax: lambda arguments: expression

# Simple lambda
square = lambda x: x ** 2
print(square(5))  # 25

# Multiple arguments
add = lambda x, y: x + y
print(add(3, 4))  # 7

# Multiple arguments with logic
max_value = lambda a, b, c: max(a, b, c)
print(max_value(10, 5, 8))  # 10

# With default values
greet = lambda name, greeting="Hello": f"{greeting}, {name}!"
print(greet("Alice"))  # Hello, Alice!
print(greet("Bob", "Hi"))  # Hi, Bob!

# With *args
add_all = lambda *args: sum(args)
print(add_all(1, 2, 3, 4, 5))  # 15

# With **kwargs
describe = lambda **kwargs: ', '.join(f"{k}={v}" for k, v in kwargs.items())
print(describe(name="Alice", age=30, city="NYC"))
# name=Alice, age=30, city=NYC
```

### Lambda with Built-in Functions

```python
# map() - Apply function to each element
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# With multiple sequences
a = [1, 2, 3, 4]
b = [10, 20, 30, 40]
sums = list(map(lambda x, y: x + y, a, b))
print(sums)  # [11, 22, 33, 44]

# filter() - Keep elements matching condition
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4, 6, 8, 10]

# Combine filter and map
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
squared_evens = list(map(lambda x: x**2, filter(lambda x: x % 2 == 0, numbers)))
print(squared_evens)  # [4, 16, 36, 64, 100]

# sorted() with key parameter
words = ['apple', 'pie', 'a', 'longer word', 'hi']
sorted_by_length = sorted(words, key=lambda x: len(x))
print(sorted_by_length)  # ['a', 'hi', 'pie', 'apple', 'longer word']

# Sorting complex data
students = [
    {'name': 'Alice', 'grade': 95},
    {'name': 'Bob', 'grade': 87},
    {'name': 'Charlie', 'grade': 92}
]
sorted_by_grade = sorted(students, key=lambda x: x['grade'], reverse=True)
print(sorted_by_grade)
# [{'name': 'Alice', 'grade': 95}, {'name': 'Charlie', 'grade': 92}, {'name': 'Bob', 'grade': 87}]
```

### Lambda with Dictionary and List Operations

```python
# Sorting dictionary by values
scores = {'alice': 95, 'bob': 87, 'charlie': 92, 'dave': 88}
sorted_items = sorted(scores.items(), key=lambda x: x[1], reverse=True)
print(sorted_items)
# [('alice', 95), ('charlie', 92), ('dave', 88), ('bob', 87)]

# Sorting by multiple criteria
students = [
    {'name': 'Alice', 'grade': 95, 'age': 20},
    {'name': 'Bob', 'grade': 95, 'age': 19},
    {'name': 'Charlie', 'grade': 92, 'age': 21}
]
sorted_students = sorted(students, key=lambda x: (-x['grade'], x['age']))
print(sorted_students)

# min()/max() with lambda
students = [
    {'name': 'Alice', 'age': 20},
    {'name': 'Bob', 'age': 25},
    {'name': 'Charlie', 'age': 19}
]
youngest = min(students, key=lambda x: x['age'])
oldest = max(students, key=lambda x: x['age'])
print(youngest, oldest)  # {'name': 'Charlie', 'age': 19} {'name': 'Bob', 'age': 25}

# Filtering nested data
data = [
    {'name': 'Alice', 'scores': [90, 95, 88]},
    {'name': 'Bob', 'scores': [78, 82, 85]},
    {'name': 'Charlie', 'scores': [95, 92, 98]}
]
high_performers = list(filter(lambda x: sum(x['scores'])/len(x['scores']) > 90, data))
print(high_performers)
```

### Lambda in More Complex Scenarios

```python
# 1. Using with reduce() from functools
from functools import reduce

numbers = [1, 2, 3, 4, 5]
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120

# 2. Conditional lambda
is_even = lambda x: x % 2 == 0
print(is_even(4))  # True
print(is_even(5))  # False

# 3. Nested lambdas (rarely needed)
add_multiply = lambda x: lambda y: x + y
add_5 = add_multiply(5)
print(add_5(3))  # 8

# 4. Lambda for dictionary transformations
data = {'a': 1, 'b': 2, 'c': 3}
doubled = {k: (lambda v: v * 2)(v) for k, v in data.items()}
print(doubled)  # {'a': 2, 'b': 4, 'c': 6}

# 5. Using with group operations
from itertools import groupby
data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
grouped = {k: len(list(g)) for k, g in groupby(data)}
print(grouped)  # {1: 1, 2: 2, 3: 3, 4: 4}

# 6. Lambda for data transformation
prices = [19.99, 29.99, 39.99]
with_tax = list(map(lambda p: p * 1.1, prices))
print(with_tax)  # [21.989, 32.989, 43.989]
```

### When NOT to Use Lambda

```python
# DON'T: Complex logic (use regular function instead)
# This is hard to read:
# process = lambda x: [i for i in range(x)] if x > 0 else []

# DO: Use regular function
def process(x):
    if x > 0:
        return list(range(x))
    return []

# DON'T: Multiple statements (lambda only takes expressions)
# This won't work:
# multi = lambda x: y = x + 1; return y

# DO: Use regular function
def add_one(x):
    y = x + 1
    return y

# DON'T: When function is called multiple times (less efficient)
# square = lambda x: x ** 2
# for i in range(1000):
#     square(i)

# DO: Define outside loop
def square(x):
    return x ** 2
for i in range(1000):
    square(i)
```

---

# COMPREHENSIONS - COMPLETE GUIDE {#comprehensions}

## List Comprehensions

```python
# Basic syntax: [expression for item in iterable]

# Simple list comprehension
numbers = [x for x in range(5)]
print(numbers)  # [0, 1, 2, 3, 4]

# With transformation
squares = [x**2 for x in range(5)]
print(squares)  # [0, 1, 4, 9, 16]

# With condition (if)
evens = [x for x in range(10) if x % 2 == 0]
print(evens)  # [0, 2, 4, 6, 8]

# With else
numbers = [x if x % 2 == 0 else -x for x in range(5)]
print(numbers)  # [0, -1, 2, -3, 4]

# Nested loops
pairs = [(x, y) for x in range(3) for y in range(3)]
print(pairs)
# [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]

# Flattening
nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [x for row in nested for x in row]
print(flat)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Complex filtering and transformation
words = ['apple', 'banana', 'cherry', 'date', 'elderberry']
result = [word.upper() for word in words if len(word) > 5]
print(result)  # ['BANANA', 'CHERRY', 'ELDERBERRY']
```

## Dictionary Comprehensions

```python
# Basic syntax: {key_expr: value_expr for item in iterable}

# Simple mapping
numbers = [1, 2, 3, 4, 5]
squares = {x: x**2 for x in numbers}
print(squares)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# With condition
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}

# Transforming keys and values
original = {'a': 1, 'b': 2, 'c': 3}
transformed = {k.upper(): v*2 for k, v in original.items()}
print(transformed)  # {'A': 2, 'B': 4, 'C': 6}

# Inverting dictionary
original = {'a': 1, 'b': 2, 'c': 3}
inverted = {v: k for k, v in original.items()}
print(inverted)  # {1: 'a', 2: 'b', 3: 'c'}

# From two lists
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]
people = {name: age for name, age in zip(names, ages)}
print(people)  # {'Alice': 25, 'Bob': 30, 'Charlie': 35}

# Grouping
words = ['apple', 'apricot', 'banana', 'blueberry', 'cherry']
grouped = {}
for word in words:
    key = word[0]
    if key not in grouped:
        grouped[key] = []
    grouped[key].append(word)
print(grouped)
# {'a': ['apple', 'apricot'], 'b': ['banana', 'blueberry'], 'c': ['cherry']}

# More elegant with comprehension:
from collections import defaultdict
grouped = defaultdict(list)
for word in words:
    grouped[word[0]].append(word)
```

## Set Comprehensions

```python
# Basic syntax: {expression for item in iterable}

# Simple set comprehension
squares = {x**2 for x in range(5)}
print(squares)  # {0, 1, 4, 9, 16}

# With condition
even_squares = {x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0, 4, 16, 36, 64}

# Removing duplicates
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique = {x for x in numbers}
print(unique)  # {1, 2, 3, 4}

# From string
vowels = {x for x in "hello world" if x in "aeiou"}
print(vowels)  # {'e', 'o'}

# From multiple sources
a = [1, 2, 3]
b = [2, 3, 4]
both = {x for x in a if x in b}
print(both)  # {2, 3}
```

---

# FUNCTIONAL PROGRAMMING - map(), filter(), reduce() {#functional}

## map() - Transform Elements

```python
# Syntax: map(function, iterable[, iterable2, ...])
# Returns an iterator of results

numbers = [1, 2, 3, 4, 5]

# Using regular function
def square(x):
    return x ** 2

squared = list(map(square, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# Using lambda
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# With built-in function
strings = ['1', '2', '3', '4', '5']
numbers = list(map(int, strings))
print(numbers)  # [1, 2, 3, 4, 5]

# Map with multiple iterables
a = [1, 2, 3, 4]
b = [10, 20, 30, 40]
sums = list(map(lambda x, y: x + y, a, b))
print(sums)  # [11, 22, 33, 44]

# Type conversions
data = [1, 2, 3]
as_strings = list(map(str, data))
print(as_strings)  # ['1', '2', '3']

# Dot product calculation
def multiply(x, y):
    return x * y

vector1 = [1, 2, 3]
vector2 = [4, 5, 6]
products = list(map(multiply, vector1, vector2))
dot_product = sum(products)
print(dot_product)  # 32
```

## filter() - Select Elements

```python
# Syntax: filter(function, iterable)
# Returns an iterator of elements where function(element) is True

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Using function
def is_even(x):
    return x % 2 == 0

evens = list(filter(is_even, numbers))
print(evens)  # [2, 4, 6, 8, 10]

# Using lambda
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4, 6, 8, 10]

# Filtering strings
words = ['apple', 'a', 'banana', 'pie', 'cherry', 'hi']
long_words = list(filter(lambda x: len(x) > 3, words))
print(long_words)  # ['apple', 'banana', 'cherry']

# Filter with None removes falsy values
data = [0, 1, False, 2, '', 'hello', [], [1, 2], None]
truthy = list(filter(None, data))
print(truthy)  # [1, 2, 'hello', [1, 2]]

# Filtering complex objects
students = [
    {'name': 'Alice', 'grade': 95},
    {'name': 'Bob', 'grade': 78},
    {'name': 'Charlie', 'grade': 92},
    {'name': 'Dave', 'grade': 88}
]
passing = list(filter(lambda x: x['grade'] >= 90, students))
print(passing)
# [{'name': 'Alice', 'grade': 95}, {'name': 'Charlie', 'grade': 92}]
```

## reduce() - Accumulate Values

```python
# Syntax: reduce(function, iterable[, initializer])
# Applies function cumulatively to items

from functools import reduce

# Sum using reduce
numbers = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x + y, numbers)
print(total)  # 15

# Product
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120

# Maximum value
maximum = reduce(lambda x, y: x if x > y else y, numbers)
print(maximum)  # 5

# String concatenation
words = ['Hello', ' ', 'World', '!']
result = reduce(lambda x, y: x + y, words)
print(result)  # 'Hello World!'

# With initializer
numbers = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x + y, numbers, 10)
print(total)  # 25 (10 + 1 + 2 + 3 + 4 + 5)

# Building a dictionary from pairs
pairs = [('a', 1), ('b', 2), ('c', 3)]
result = reduce(lambda d, pair: {**d, pair[0]: pair[1]}, pairs, {})
print(result)  # {'a': 1, 'b': 2, 'c': 3}

# Flattening nested lists
nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = reduce(lambda x, y: x + y, nested)
print(flat)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Note: Often list comprehensions are more readable
# Compare:
# Reduce: result = reduce(lambda x, y: x + y, nested)
# Comprehension: result = [x for row in nested for x in row]
```

## Combining map(), filter(), reduce()

```python
from functools import reduce

# Problem: Get sum of squares of even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Using functional approach
result = reduce(
    lambda x, y: x + y,
    map(lambda x: x**2, filter(lambda x: x % 2 == 0, numbers))
)
print(result)  # 2^2 + 4^2 + 6^2 + 8^2 + 10^2 = 4 + 16 + 36 + 64 + 100 = 220

# More readable: list comprehension
result = sum(x**2 for x in numbers if x % 2 == 0)
print(result)  # 220

# Problem: Transform data
students = [
    {'name': 'Alice', 'scores': [90, 95, 88]},
    {'name': 'Bob', 'scores': [78, 82, 85]},
    {'name': 'Charlie', 'scores': [95, 92, 98]}
]

# Get average scores (functional)
averages = list(map(
    lambda s: (s['name'], sum(s['scores']) / len(s['scores'])),
    students
))
print(averages)
# [('Alice', 91.0), ('Bob', 81.66...), ('Charlie', 95.0)]

# Filter high performers
high_performers = list(filter(
    lambda x: x[1] >= 90,
    averages
))
print(high_performers)  # [('Alice', 91.0), ('Charlie', 95.0)]
```

---

# ADVANCED TECHNIQUES {#advanced}

## Unpacking and Multiple Assignment

```python
# Simple unpacking
a, b, c = [1, 2, 3]
print(a, b, c)  # 1 2 3

# With *
first, *middle, last = [1, 2, 3, 4, 5]
print(first, middle, last)  # 1 [2, 3, 4] 5

# Ignoring values
a, _, c = [1, 2, 3]
print(a, c)  # 1 3

# Nested unpacking
(a, b), (c, d) = [(1, 2), (3, 4)]
print(a, b, c, d)  # 1 2 3 4

# Swapping
a, b = 10, 20
a, b = b, a
print(a, b)  # 20 10

# Extending *
a, *b, c = "hello"
print(a, b, c)  # h ['e', 'l', 'l'] o
```

## Enumerate and Zip

```python
# enumerate() - Get index and value
fruits = ['apple', 'banana', 'cherry']
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
# 0: apple
# 1: banana
# 2: cherry

# With start parameter
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}: {fruit}")
# 1: apple
# 2: banana
# 3: cherry

# zip() - Combine multiple sequences
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]
cities = ['NYC', 'LA', 'Chicago']

for name, age, city in zip(names, ages, cities):
    print(f"{name} is {age} and lives in {city}")
# Alice is 25 and lives in NYC
# Bob is 30 and lives in LA
# Charlie is 35 and lives in Chicago

# Creating dictionary from zip
pairs = dict(zip(names, ages))
print(pairs)  # {'Alice': 25, 'Bob': 30, 'Charlie': 35}

# Unzipping (reverse operation)
pairs = [('a', 1), ('b', 2), ('c', 3)]
letters, numbers = zip(*pairs)
print(letters, numbers)  # ('a', 'b', 'c') (1, 2, 3)
```

## Sorted with Multiple Keys

```python
# Sorting by multiple criteria
students = [
    {'name': 'Alice', 'grade': 95, 'age': 20},
    {'name': 'Bob', 'grade': 95, 'age': 19},
    {'name': 'Charlie', 'grade': 92, 'age': 21},
    {'name': 'Dave', 'grade': 92, 'age': 20}
]

# Sort by grade descending, then age ascending
sorted_students = sorted(students, key=lambda x: (-x['grade'], x['age']))
for s in sorted_students:
    print(s)
# {'name': 'Bob', 'grade': 95, 'age': 19}
# {'name': 'Alice', 'grade': 95, 'age': 20}
# {'name': 'Dave', 'grade': 92, 'age': 20}
# {'name': 'Charlie', 'grade': 92, 'age': 21}

# Using itemgetter (more efficient)
from operator import itemgetter
sorted_students = sorted(students, key=itemgetter('grade', 'age'), reverse=True)

# Using attrgetter for objects
class Student:
    def __init__(self, name, grade, age):
        self.name = name
        self.grade = grade
        self.age = age

students_obj = [
    Student('Alice', 95, 20),
    Student('Bob', 95, 19),
]

from operator import attrgetter
sorted_students = sorted(students_obj, key=attrgetter('grade', 'age'))
```

## Any, All, and Conditional Operations

```python
# all() - Check if all elements are true
print(all([True, True, True]))      # True
print(all([True, False, True]))     # False
print(all([]))                      # True (vacuous truth)

# all() with condition
numbers = [2, 4, 6, 8, 10]
print(all(x % 2 == 0 for x in numbers))  # True

# any() - Check if any element is true
print(any([False, False, True]))    # True
print(any([False, False, False]))   # False
print(any([]))                      # False

# any() with condition
numbers = [1, 2, 3, 4, 5]
print(any(x % 2 == 0 for x in numbers))  # True (2, 4 are even)

# Real-world examples
users = [
    {'name': 'Alice', 'admin': True},
    {'name': 'Bob', 'admin': False},
    {'name': 'Charlie', 'admin': False}
]

# Check if anyone is admin
has_admin = any(u['admin'] for u in users)
print(has_admin)  # True

# Check if everyone is admin
all_admin = all(u['admin'] for u in users)
print(all_admin)  # False
```

---

# INTERVIEW PATTERNS {#patterns}

## Pattern 1: Two-Sum Type Problems

```python
# Problem: Find two numbers that sum to target
def two_sum(numbers, target):
    seen = set()
    for num in numbers:
        complement = target - num
        if complement in seen:
            return (complement, num)
        seen.add(num)
    return None

print(two_sum([2, 7, 11, 15], 9))  # (2, 7)

# Variant: With index
def two_sum_indices(numbers, target):
    num_map = {}
    for i, num in enumerate(numbers):
        complement = target - num
        if complement in num_map:
            return (num_map[complement], i)
        num_map[num] = i
    return None

print(two_sum_indices([2, 7, 11, 15], 9))  # (0, 1)
```

## Pattern 2: Counting Frequencies

```python
# Using Counter
from collections import Counter

def most_common(words):
    counter = Counter(words)
    return counter.most_common(1)[0][0]

print(most_common(['apple', 'banana', 'apple', 'cherry']))  # apple

# Using dictionary
def frequency_map(items):
    freq = {}
    for item in items:
        freq[item] = freq.get(item, 0) + 1
    return freq

print(frequency_map([1, 2, 2, 3, 3, 3]))  # {1: 1, 2: 2, 3: 3}

# Using defaultdict
from collections import defaultdict
def frequency_defaultdict(items):
    freq = defaultdict(int)
    for item in items:
        freq[item] += 1
    return dict(freq)

print(frequency_defaultdict([1, 2, 2, 3, 3, 3]))  # {1: 1, 2: 2, 3: 3}
```

## Pattern 3: Grouping Elements

```python
# Group by key
from collections import defaultdict

def group_by_length(words):
    groups = defaultdict(list)
    for word in words:
        groups[len(word)].append(word)
    return dict(groups)

words = ['a', 'hi', 'apple', 'pie', 'banana']
print(group_by_length(words))
# {1: ['a'], 2: ['hi', 'pie'], 5: ['apple'], 6: ['banana']}

# Using itertools.groupby (requires sorted data)
from itertools import groupby

data = [1, 1, 2, 2, 2, 3, 3, 4]
grouped = {}
for key, group in groupby(data):
    grouped[key] = len(list(group))
print(grouped)  # {1: 2, 2: 3, 3: 2, 4: 1}
```

## Pattern 4: Sliding Window

```python
# Find longest substring without repeating characters
def longest_substring(s):
    char_index = {}
    max_length = 0
    start = 0
    
    for end, char in enumerate(s):
        if char in char_index and char_index[char] >= start:
            start = char_index[char] + 1
        char_index[char] = end
        max_length = max(max_length, end - start + 1)
    
    return max_length

print(longest_substring("abcabcbb"))  # 3 ("abc")
print(longest_substring("bbbbb"))     # 1 ("b")
print(longest_substring("au"))        # 2 ("au")
```

## Pattern 5: Nested Data Access

```python
# Safe access to nested dictionaries
def get_nested(data, keys, default=None):
    for key in keys:
        if isinstance(data, dict):
            data = data.get(key)
        else:
            return default
    return data

data = {
    'user': {
        'profile': {
            'name': 'Alice',
            'age': 30
        }
    }
}

print(get_nested(data, ['user', 'profile', 'name']))  # Alice
print(get_nested(data, ['user', 'settings', 'theme']))  # None
print(get_nested(data, ['user', 'settings', 'theme'], 'dark'))  # dark
```

---

# PRACTICE PROBLEMS {#practice}

## Problem 1: Flatten Nested List

```python
def flatten(lst):
    """Flatten a nested list"""
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

# Test
nested = [1, [2, 3, [4, 5]], 6, [[7, 8], 9]]
print(flatten(nested))  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Alternative: List comprehension
def flatten_comp(lst):
    return [x for item in lst for x in (flatten_comp(item) if isinstance(item, list) else [item])]

# Alternative: itertools
from itertools import chain
def flatten_chain(lst):
    for item in lst:
        if isinstance(item, list):
            yield from flatten_chain(item)
        else:
            yield item
```

## Problem 2: Group Anagrams

```python
def group_anagrams(words):
    """Group words that are anagrams"""
    anagrams = {}
    for word in words:
        # Sort letters to create key
        key = ''.join(sorted(word))
        if key not in anagrams:
            anagrams[key] = []
        anagrams[key].append(word)
    return list(anagrams.values())

# Test
print(group_anagrams(['eat', 'tea', 'ate', 'bat', 'tab', 'cat']))
# [['eat', 'tea', 'ate'], ['bat', 'tab'], ['cat']]

# Alternative using defaultdict
from collections import defaultdict
def group_anagrams_v2(words):
    groups = defaultdict(list)
    for word in words:
        groups[tuple(sorted(word))].append(word)
    return list(groups.values())
```

## Problem 3: Most Frequent Element with Frequency Map

```python
def most_frequent(lst):
    """Find most frequent element"""
    freq = {}
    max_count = 0
    max_element = None
    
    for item in lst:
        freq[item] = freq.get(item, 0) + 1
        if freq[item] > max_count:
            max_count = freq[item]
            max_element = item
    
    return max_element, max_count

# Test
print(most_frequent([1, 1, 1, 2, 2, 3]))  # (1, 3)

# Using Counter
from collections import Counter
def most_frequent_v2(lst):
    counter = Counter(lst)
    most_common = counter.most_common(1)[0]
    return most_common
```

## Problem 4: Merge Sorted Lists

```python
def merge_lists(list1, list2):
    """Merge two sorted lists maintaining order"""
    result = []
    i = j = 0
    
    while i < len(list1) and j < len(list2):
        if list1[i] <= list2[j]:
            result.append(list1[i])
            i += 1
        else:
            result.append(list2[j])
            j += 1
    
    # Add remaining elements
    result.extend(list1[i:])
    result.extend(list2[j:])
    return result

# Test
print(merge_lists([1, 3, 5], [2, 4, 6]))  # [1, 2, 3, 4, 5, 6]

# Simple Python way
def merge_lists_simple(list1, list2):
    return sorted(list1 + list2)
```

## Problem 5: Custom Sorting with Multiple Keys

```python
def sort_by_criteria(students):
    """
    Sort students by grade (descending), 
    then by age (ascending),
    then by name (alphabetically)
    """
    return sorted(
        students,
        key=lambda x: (-x['grade'], x['age'], x['name'])
    )

# Test
students = [
    {'name': 'Alice', 'grade': 95, 'age': 20},
    {'name': 'Bob', 'grade': 95, 'age': 19},
    {'name': 'Charlie', 'grade': 92, 'age': 21},
    {'name': 'David', 'grade': 92, 'age': 20},
    {'name': 'Eve', 'grade': 92, 'age': 20},
]

result = sort_by_criteria(students)
for s in result:
    print(s)
```

---

## 🎯 KEY TAKEAWAYS

### **Lists**
- Mutable, ordered collections
- Methods: append, extend, insert, remove, pop, sort, reverse
- List comprehensions are powerful and readable
- Use for collections where order and mutability matter

### **Tuples**
- Immutable, ordered collections
- Can be dictionary keys
- Slightly faster than lists
- Great for returning multiple values from functions

### **Sets**
- Unordered collections of unique elements
- O(1) membership testing
- Great for deduplication and mathematical operations
- Union, intersection, difference, symmetric difference

### **Dictionaries**
- Key-value stores (O(1) average access)
- Keys must be hashable
- Methods: get, keys, values, items, pop, update
- Dictionary comprehensions are powerful
- defaultdict and Counter are useful from collections module

### **Lambda Functions**
- Short, anonymous functions
- Use with map, filter, sorted, min, max
- Keep them simple and readable
- Prefer regular functions for complex logic

### **Comprehensions**
- List: [expr for item in iterable if condition]
- Dict: {key_expr: val_expr for item in iterable}
- Set: {expr for item in iterable}
- More readable and efficient than loops

### **Functional Programming**
- map(): Transform elements
- filter(): Select elements
- reduce(): Accumulate values
- Often list comprehensions are more readable

---

## 📚 FURTHER LEARNING

1. Practice problems on LeetCode/HackerRank using these patterns
2. Read "Fluent Python" for deeper understanding
3. Explore itertools and functools modules
4. Practice writing clean, idiomatic Python code

