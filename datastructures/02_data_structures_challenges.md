# Data Structures - 100 Coding Challenges

Master Python data structures with comprehensive challenges on Lists, Tuples, Sets, and Dictionaries.

---

## 📋 Table of Contents

1. [Lists (25 Problems)](#lists)
2. [Tuples (15 Problems)](#tuples)
3. [Sets (20 Problems)](#sets)
4. [Dictionaries (40 Problems)](#dictionaries)

---

## Lists

### Problem 1: Find Maximum and Minimum
**Difficulty**: Easy

**Problem**: Find the maximum and minimum elements in a list.

**Solution**:
```python
def find_max_min(lst):
    """Find maximum and minimum in a list"""
    if not lst:
        return None, None
    return max(lst), min(lst)

# Test case
numbers = [3, 7, 1, 9, 4, 2]
max_val, min_val = find_max_min(numbers)
print(f"Max: {max_val}, Min: {min_val}")  # Max: 9, Min: 1
```

---

### Problem 2: Remove Duplicates
**Difficulty**: Easy

**Problem**: Remove duplicates from a list while preserving order.

**Solution**:
```python
def remove_duplicates(lst):
    """Remove duplicates preserving order"""
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

# Alternative using dict.fromkeys()
def remove_duplicates_alt(lst):
    return list(dict.fromkeys(lst))

# Test case
numbers = [1, 2, 2, 3, 4, 4, 5]
print(remove_duplicates(numbers))  # [1, 2, 3, 4, 5]
```

---

### Problem 3: List Comprehension - Squares
**Difficulty**: Easy

**Problem**: Create a list of squares of numbers from 1 to n.

**Solution**:
```python
def squares_list(n):
    """Generate list of squares using list comprehension"""
    return [x**2 for x in range(1, n+1)]

# Alternative without list comprehension
def squares_list_loop(n):
    squares = []
    for x in range(1, n+1):
        squares.append(x**2)
    return squares

# Test case
print(squares_list(5))  # [1, 4, 9, 16, 25]
```

---

### Problem 4: Flatten Nested List
**Difficulty**: Medium

**Problem**: Flatten a nested list (one level deep).

**Solution**:
```python
def flatten_list(nested_list):
    """Flatten one level of nesting"""
    result = []
    for item in nested_list:
        if isinstance(item, list):
            result.extend(item)
        else:
            result.append(item)
    return result

# Using list comprehension
def flatten_list_comp(nested_list):
    return [item for sublist in nested_list for item in (sublist if isinstance(sublist, list) else [sublist])]

# Test case
nested = [[1, 2], [3, 4], [5, 6]]
print(flatten_list(nested))  # [1, 2, 3, 4, 5, 6]
```

---

### Problem 5: Find Second Largest
**Difficulty**: Medium

**Problem**: Find the second largest element in a list.

**Solution**:
```python
def second_largest(lst):
    """Find second largest element"""
    if len(lst) < 2:
        return None
    
    # Remove duplicates and sort
    unique_sorted = sorted(set(lst), reverse=True)
    
    if len(unique_sorted) < 2:
        return None
    
    return unique_sorted[1]

# Alternative without sorting
def second_largest_efficient(lst):
    if len(lst) < 2:
        return None
    
    first = second = float('-inf')
    
    for num in lst:
        if num > first:
            second = first
            first = num
        elif num > second and num != first:
            second = num
    
    return second if second != float('-inf') else None

# Test case
numbers = [10, 20, 4, 45, 99, 45]
print(second_largest(numbers))  # 45
```

---

### Problem 6: Rotate List
**Difficulty**: Medium

**Problem**: Rotate a list by k positions to the right.

**Solution**:
```python
def rotate_list(lst, k):
    """Rotate list k positions to the right"""
    if not lst:
        return lst
    
    n = len(lst)
    k = k % n  # Handle k > n
    
    return lst[-k:] + lst[:-k] if k else lst

# Test case
numbers = [1, 2, 3, 4, 5]
print(rotate_list(numbers, 2))  # [4, 5, 1, 2, 3]
```

---

### Problem 7: Merge Two Sorted Lists
**Difficulty**: Medium

**Problem**: Merge two sorted lists into one sorted list.

**Solution**:
```python
def merge_sorted_lists(list1, list2):
    """Merge two sorted lists"""
    result = []
    i, j = 0, 0
    
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

# Test case
list1 = [1, 3, 5, 7]
list2 = [2, 4, 6, 8]
print(merge_sorted_lists(list1, list2))  # [1, 2, 3, 4, 5, 6, 7, 8]
```

---

### Problem 8: Find Common Elements
**Difficulty**: Easy

**Problem**: Find common elements between two lists.

**Solution**:
```python
def find_common(list1, list2):
    """Find common elements"""
    return list(set(list1) & set(list2))

# Alternative preserving order
def find_common_ordered(list1, list2):
    set2 = set(list2)
    return [x for x in list1 if x in set2]

# Test case
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]
print(find_common(list1, list2))  # [4, 5]
```

---

### Problem 9: Chunk List
**Difficulty**: Medium

**Problem**: Split a list into chunks of size n.

**Solution**:
```python
def chunk_list(lst, chunk_size):
    """Split list into chunks"""
    return [lst[i:i+chunk_size] for i in range(0, len(lst), chunk_size)]

# Test case
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(chunk_list(numbers, 3))  # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

---

### Problem 10: List Difference
**Difficulty**: Easy

**Problem**: Find elements in list1 that are not in list2.

**Solution**:
```python
def list_difference(list1, list2):
    """Find elements in list1 not in list2"""
    return list(set(list1) - set(list2))

# Preserving order
def list_difference_ordered(list1, list2):
    set2 = set(list2)
    return [x for x in list1 if x not in set2]

# Test case
list1 = [1, 2, 3, 4, 5]
list2 = [3, 4, 5, 6, 7]
print(list_difference(list1, list2))  # [1, 2]
```

---

### Problems 11-25: Additional List Challenges

**Problem 11**: Count occurrences of each element
**Problem 12**: Find pairs with given sum
**Problem 13**: Move zeros to end
**Problem 14**: Reverse list in place
**Problem 15**: Check if list is sorted
**Problem 16**: Find missing number in sequence
**Problem 17**: Partition list by condition
**Problem 18**: Sliding window maximum
**Problem 19**: Remove element by value
**Problem 20**: Interleave two lists
**Problem 21**: Find longest consecutive sequence
**Problem 22**: Product of array except self
**Problem 23**: Kadane's algorithm (max subarray sum)
**Problem 24**: Dutch National Flag problem
**Problem 25**: Rain water trapping

---

## Tuples

### Problem 26: Tuple Operations
**Difficulty**: Easy

**Problem**: Demonstrate basic tuple operations.

**Solution**:
```python
# Creating tuples
tuple1 = (1, 2, 3)
tuple2 = 4, 5, 6  # Parentheses optional
single_element = (1,)  # Comma required for single element

# Accessing elements
print(tuple1[0])     # 1
print(tuple1[-1])    # 3

# Slicing
print(tuple1[1:3])   # (2, 3)

# Concatenation
combined = tuple1 + tuple2
print(combined)      # (1, 2, 3, 4, 5, 6)

# Repetition
repeated = tuple1 * 2
print(repeated)      # (1, 2, 3, 1, 2, 3)

# Count and index
numbers = (1, 2, 2, 3, 2, 4)
print(numbers.count(2))   # 3
print(numbers.index(3))   # 3
```

---

### Problem 27: Tuple Unpacking
**Difficulty**: Easy

**Problem**: Demonstrate various tuple unpacking techniques.

**Solution**:
```python
# Basic unpacking
coordinates = (10, 20)
x, y = coordinates
print(f"x={x}, y={y}")

# Extended unpacking
numbers = (1, 2, 3, 4, 5)
first, *middle, last = numbers
print(f"first={first}, middle={middle}, last={last}")

# Swapping values
a, b = 5, 10
a, b = b, a
print(f"a={a}, b={b}")

# Unpacking in loops
points = [(1, 2), (3, 4), (5, 6)]
for x, y in points:
    print(f"Point: ({x}, {y})")
```

---

### Problem 28: Named Tuples
**Difficulty**: Medium

**Problem**: Use named tuples for better code readability.

**Solution**:
```python
from collections import namedtuple

# Define named tuple
Point = namedtuple('Point', ['x', 'y'])
Person = namedtuple('Person', ['name', 'age', 'city'])

# Create instances
p1 = Point(10, 20)
person1 = Person('Alice', 30, 'New York')

# Access by name
print(f"Point: ({p1.x}, {p1.y})")
print(f"Person: {person1.name}, {person1.age}, {person1.city}")

# Access by index
print(p1[0])  # 10

# Convert to dictionary
print(person1._asdict())
```

---

### Problem 29: Tuple vs List Performance
**Difficulty**: Medium

**Problem**: Compare tuple and list performance.

**Solution**:
```python
import timeit

# Creation time
list_time = timeit.timeit('[1, 2, 3, 4, 5]', number=1000000)
tuple_time = timeit.timeit('(1, 2, 3, 4, 5)', number=1000000)

print(f"List creation: {list_time:.6f}")
print(f"Tuple creation: {tuple_time:.6f}")
print(f"Tuple is {list_time/tuple_time:.2f}x faster")

# Memory usage
import sys
my_list = [1, 2, 3, 4, 5]
my_tuple = (1, 2, 3, 4, 5)

print(f"List size: {sys.getsizeof(my_list)} bytes")
print(f"Tuple size: {sys.getsizeof(my_tuple)} bytes")
```

---

### Problem 30: Return Multiple Values
**Difficulty**: Easy

**Problem**: Use tuples to return multiple values from a function.

**Solution**:
```python
def get_stats(numbers):
    """Return multiple statistics"""
    return (
        sum(numbers),
        len(numbers),
        sum(numbers) / len(numbers) if numbers else 0,
        max(numbers) if numbers else None,
        min(numbers) if numbers else None
    )

numbers = [10, 20, 30, 40, 50]
total, count, average, maximum, minimum = get_stats(numbers)

print(f"Total: {total}")
print(f"Count: {count}")
print(f"Average: {average}")
print(f"Max: {maximum}")
print(f"Min: {minimum}")
```

---

### Problems 31-40: Additional Tuple Challenges

**Problem 31**: Convert list of tuples to dictionary
**Problem 32**: Sort list of tuples
**Problem 33**: Find tuple with max/min value
**Problem 34**: Tuple comprehension (generator expression)
**Problem 35**: Nested tuple access
**Problem 36**: Immutability demonstration
**Problem 37**: Tuple as dictionary key
**Problem 38**: Count elements in nested tuples
**Problem 39**: Zip multiple iterables
**Problem 40**: Enumerate with tuples

---

## Sets

### Problem 41: Set Operations
**Difficulty**: Easy

**Problem**: Demonstrate basic set operations.

**Solution**:
```python
# Creating sets
set1 = {1, 2, 3, 4, 5}
set2 = {4, 5, 6, 7, 8}

# Union
print(f"Union: {set1 | set2}")              # {1, 2, 3, 4, 5, 6, 7, 8}
print(f"Union: {set1.union(set2)}")

# Intersection
print(f"Intersection: {set1 & set2}")       # {4, 5}
print(f"Intersection: {set1.intersection(set2)}")

# Difference
print(f"Difference: {set1 - set2}")         # {1, 2, 3}
print(f"Difference: {set1.difference(set2)}")

# Symmetric Difference
print(f"Sym Diff: {set1 ^ set2}")           # {1, 2, 3, 6, 7, 8}
print(f"Sym Diff: {set1.symmetric_difference(set2)}")

# Subset/Superset
set3 = {1, 2}
print(f"Is subset: {set3 <= set1}")         # True
print(f"Is superset: {set1 >= set3}")       # True
```

---

### Problem 42: Remove Duplicates Using Set
**Difficulty**: Easy

**Problem**: Remove duplicates from a list using sets.

**Solution**:
```python
def remove_duplicates(lst):
    """Remove duplicates using set (order not preserved)"""
    return list(set(lst))

def remove_duplicates_ordered(lst):
    """Remove duplicates preserving order"""
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

# Test cases
numbers = [1, 2, 2, 3, 4, 4, 5, 1]
print(remove_duplicates(numbers))
print(remove_duplicates_ordered(numbers))
```

---

### Problem 43: Find Unique Elements
**Difficulty**: Easy

**Problem**: Find elements that appear only once.

**Solution**:
```python
def find_unique_elements(lst):
    """Find elements appearing only once"""
    from collections import Counter
    counts = Counter(lst)
    return [item for item, count in counts.items() if count == 1]

# Alternative using sets
def find_unique_set(lst):
    all_items = set(lst)
    duplicates = set([x for x in lst if lst.count(x) > 1])
    return list(all_items - duplicates)

# Test case
numbers = [1, 2, 2, 3, 4, 4, 5]
print(find_unique_elements(numbers))  # [1, 3, 5]
```

---

### Problem 44: Check Disjoint Sets
**Difficulty**: Easy

**Problem**: Check if two sets have no common elements.

**Solution**:
```python
def are_disjoint(set1, set2):
    """Check if sets are disjoint"""
    return set1.isdisjoint(set2)

# Alternative
def are_disjoint_alt(set1, set2):
    return len(set1 & set2) == 0

# Test cases
set1 = {1, 2, 3}
set2 = {4, 5, 6}
set3 = {3, 4, 5}

print(are_disjoint(set1, set2))  # True
print(are_disjoint(set1, set3))  # False
```

---

### Problem 45: Set Comprehension
**Difficulty**: Easy

**Problem**: Create sets using set comprehension.

**Solution**:
```python
# Squares of even numbers
even_squares = {x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0, 4, 16, 36, 64}

# Vowels from a string
text = "hello world"
vowels = {char for char in text if char in 'aeiou'}
print(vowels)  # {'e', 'o'}

# Unique words
sentence = "the quick brown fox jumps over the lazy dog"
unique_words = {word for word in sentence.split()}
print(len(unique_words))  # 8 (excluding duplicate 'the')
```

---

### Problem 46: Frozen Sets
**Difficulty**: Medium

**Problem**: Demonstrate the use of frozen sets.

**Solution**:
```python
# Regular sets can't be elements of other sets
# But frozensets can

# Creating frozenset
fset1 = frozenset([1, 2, 3])
fset2 = frozenset([4, 5, 6])

# Set of frozensets
set_of_sets = {fset1, fset2}
print(set_of_sets)

# Frozensets as dictionary keys
cache = {
    frozenset([1, 2]): "result1",
    frozenset([3, 4]): "result2"
}
print(cache[frozenset([1, 2])])  # result1

# Immutability
try:
    fset1.add(4)  # This will raise AttributeError
except AttributeError as e:
    print("Frozensets are immutable")
```

---

### Problems 47-60: Additional Set Challenges

**Problem 47**: Find symmetric difference of multiple sets
**Problem 48**: Power set generation
**Problem 49**: Check if one set is subset of another
**Problem 50**: Find all subsets of a set
**Problem 51**: Set partition problem
**Problem 52**: Jaccard similarity
**Problem 53**: Find common elements in multiple sets
**Problem 54**: Update set in place
**Problem 55**: Clear vs reinitialize set
**Problem 56**: Set operations with conditionals
**Problem 57**: Find longest consecutive sequence
**Problem 58**: Valid Sudoku using sets
**Problem 59**: Word uniqueness checker
**Problem 60**: Set-based graph representation

---

## Dictionaries

### Problem 61: Dictionary Basics
**Difficulty**: Easy

**Problem**: Demonstrate basic dictionary operations.

**Solution**:
```python
# Creating dictionaries
person = {
    'name': 'John',
    'age': 30,
    'city': 'New York'
}

# Different ways to create
dict1 = dict(name='Alice', age=25)
dict2 = dict([('a', 1), ('b', 2)])
dict3 = {x: x**2 for x in range(5)}

# Accessing values
print(person['name'])        # John
print(person.get('age'))     # 30
print(person.get('phone', 'Not found'))  # Not found

# Adding/updating
person['email'] = 'john@example.com'
person.update({'phone': '123-456', 'age': 31})

# Removing
removed = person.pop('email')
last_item = person.popitem()

# Keys, values, items
print(person.keys())
print(person.values())
print(person.items())
```

---

### Problem 62: Count Word Frequency
**Difficulty**: Easy

**Problem**: Count frequency of words in a text.

**Solution**:
```python
def count_word_frequency(text):
    """Count word frequency"""
    words = text.lower().split()
    frequency = {}
    
    for word in words:
        frequency[word] = frequency.get(word, 0) + 1
    
    return frequency

# Using Counter
from collections import Counter

def count_word_frequency_counter(text):
    words = text.lower().split()
    return dict(Counter(words))

# Test case
text = "hello world hello python world"
print(count_word_frequency(text))
# {'hello': 2, 'world': 2, 'python': 1}
```

---

### Problem 63: Merge Dictionaries
**Difficulty**: Easy

**Problem**: Merge multiple dictionaries.

**Solution**:
```python
# Method 1: Using update()
def merge_dicts_update(*dicts):
    result = {}
    for d in dicts:
        result.update(d)
    return result

# Method 2: Using unpacking (Python 3.5+)
def merge_dicts_unpack(*dicts):
    result = {}
    for d in dicts:
        result = {**result, **d}
    return result

# Method 3: Using | operator (Python 3.9+)
def merge_dicts_operator(dict1, dict2):
    return dict1 | dict2

# Test case
dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 3, 'c': 4}
dict3 = {'d': 5}

print(merge_dicts_update(dict1, dict2, dict3))
# {'a': 1, 'b': 3, 'c': 4, 'd': 5}
```

---

### Problem 64: Invert Dictionary
**Difficulty**: Easy

**Problem**: Swap keys and values in a dictionary.

**Solution**:
```python
def invert_dict(d):
    """Invert dictionary (assuming unique values)"""
    return {v: k for k, v in d.items()}

# Handle duplicate values
def invert_dict_duplicates(d):
    """Invert dict handling duplicate values"""
    inverted = {}
    for k, v in d.items():
        if v in inverted:
            if isinstance(inverted[v], list):
                inverted[v].append(k)
            else:
                inverted[v] = [inverted[v], k]
        else:
            inverted[v] = k
    return inverted

# Test case
original = {'a': 1, 'b': 2, 'c': 3}
print(invert_dict(original))  # {1: 'a', 2: 'b', 3: 'c'}

duplicate_values = {'a': 1, 'b': 2, 'c': 1}
print(invert_dict_duplicates(duplicate_values))  # {1: ['a', 'c'], 2: 'b'}
```

---

### Problem 65: Dictionary Comprehension
**Difficulty**: Easy

**Problem**: Create dictionaries using comprehension.

**Solution**:
```python
# Square numbers
squares = {x: x**2 for x in range(1, 6)}
print(squares)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Filter even numbers
numbers = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
evens = {k: v for k, v in numbers.items() if v % 2 == 0}
print(evens)  # {'b': 2, 'd': 4}

# String length
words = ['apple', 'banana', 'cherry']
word_lengths = {word: len(word) for word in words}
print(word_lengths)  # {'apple': 5, 'banana': 6, 'cherry': 6}
```

---

### Problem 66: Nested Dictionaries
**Difficulty**: Medium

**Problem**: Work with nested dictionaries.

**Solution**:
```python
# Student records
students = {
    'student1': {
        'name': 'Alice',
        'grades': {'math': 90, 'english': 85},
        'age': 20
    },
    'student2': {
        'name': 'Bob',
        'grades': {'math': 75, 'english': 80},
        'age': 21
    }
}

# Access nested values
print(students['student1']['name'])  # Alice
print(students['student1']['grades']['math'])  # 90

# Update nested values
students['student1']['grades']['science'] = 95

# Iterate nested dict
for student_id, info in students.items():
    print(f"{student_id}: {info['name']}")
    for subject, grade in info['grades'].items():
        print(f"  {subject}: {grade}")
```

---

### Problem 67: Default Dictionary
**Difficulty**: Medium

**Problem**: Use defaultdict for cleaner code.

**Solution**:
```python
from collections import defaultdict

# Group items by category
def group_by_category(items):
    """Group items using defaultdict"""
    grouped = defaultdict(list)
    
    for item, category in items:
        grouped[category].append(item)
    
    return dict(grouped)

# Count characters
def count_chars(text):
    char_count = defaultdict(int)
    for char in text:
        char_count[char] += 1
    return dict(char_count)

# Test cases
items = [('apple', 'fruit'), ('carrot', 'vegetable'), 
         ('banana', 'fruit'), ('broccoli', 'vegetable')]
print(group_by_category(items))

text = "hello"
print(count_chars(text))  # {'h': 1, 'e': 1, 'l': 2, 'o': 1}
```

---

### Problem 68: OrderedDict
**Difficulty**: Medium

**Problem**: Maintain insertion order (before Python 3.7).

**Solution**:
```python
from collections import OrderedDict

# OrderedDict maintains insertion order
ordered = OrderedDict()
ordered['first'] = 1
ordered['second'] = 2
ordered['third'] = 3

print(list(ordered.keys()))  # ['first', 'second', 'third']

# Move to end
ordered.move_to_end('first')
print(list(ordered.keys()))  # ['second', 'third', 'first']

# Note: In Python 3.7+, regular dicts maintain insertion order
regular = {'first': 1, 'second': 2, 'third': 3}
print(list(regular.keys()))  # ['first', 'second', 'third']
```

---

### Problem 69: Dictionary Sorting
**Difficulty**: Medium

**Problem**: Sort dictionary by keys and values.

**Solution**:
```python
# Sort by key
def sort_by_key(d):
    return dict(sorted(d.items()))

# Sort by value
def sort_by_value(d, reverse=False):
    return dict(sorted(d.items(), key=lambda x: x[1], reverse=reverse))

# Test case
scores = {'Alice': 85, 'Bob': 92, 'Charlie': 78, 'David': 95}

print(sort_by_key(scores))
# {'Alice': 85, 'Bob': 92, 'Charlie': 78, 'David': 95}

print(sort_by_value(scores, reverse=True))
# {'David': 95, 'Bob': 92, 'Alice': 85, 'Charlie': 78}
```

---

### Problem 70: Find Key by Value
**Difficulty**: Easy

**Problem**: Find key(s) for a given value.

**Solution**:
```python
def find_key_by_value(d, value):
    """Find first key with given value"""
    for k, v in d.items():
        if v == value:
            return k
    return None

def find_all_keys_by_value(d, value):
    """Find all keys with given value"""
    return [k for k, v in d.items() if v == value]

# Test case
grades = {'Alice': 90, 'Bob': 85, 'Charlie': 90, 'David': 78}
print(find_key_by_value(grades, 90))        # Alice
print(find_all_keys_by_value(grades, 90))   # ['Alice', 'Charlie']
```

---

### Problems 71-100: Additional Dictionary Challenges

**Problem 71**: Create dictionary from two lists
**Problem 72**: Group anagrams using dictionary
**Problem 73**: Deep copy vs shallow copy
**Problem 74**: Dictionary from list of tuples
**Problem 75**: Filter dictionary by condition
**Problem 76**: Update nested dictionary values
**Problem 77**: Check if dictionary is subset
**Problem 78**: Most common element
**Problem 79**: Dictionary of dictionaries
**Problem 80**: Convert dictionary to JSON
**Problem 81**: Recursive dictionary traversal
**Problem 82**: Dictionary key with max value
**Problem 83**: Remove keys from dictionary
**Problem 84**: Check if two dicts are equal
**Problem 85**: Dictionary get with default factory
**Problem 86**: Pretty print nested dictionary
**Problem 87**: Flatten nested dictionary
**Problem 88**: Dictionary intersection
**Problem 89**: Create histogram from data
**Problem 90**: Cache using dictionary
**Problem 91**: Two sum problem using dict
**Problem 92**: Group students by grade
**Problem 93**: Phone book implementation
**Problem 94**: Word count in file
**Problem 95**: Configuration management
**Problem 96**: Memoization with dict
**Problem 97**: Sparse matrix using dict
**Problem 98**: Graph representation
**Problem 99**: LRU cache implementation
**Problem 100**: Multi-level dictionary access

---

## 🎯 Practice Tips

1. **Understand When to Use What**:
   - Lists: Ordered, mutable, allow duplicates
   - Tuples: Ordered, immutable, allow duplicates
   - Sets: Unordered, mutable, no duplicates
   - Dictionaries: Key-value pairs, fast lookup

2. **Time Complexity**:
   - List: O(1) append, O(n) search
   - Set: O(1) add/remove/search
   - Dict: O(1) add/remove/search by key

3. **Choose the Right Data Structure**:
   - Need order? → List or Tuple
   - Need unique elements? → Set
   - Need key-value mapping? → Dictionary

---

## 📊 Difficulty Distribution

- **Easy**: 50 problems
- **Medium**: 45 problems
- **Hard**: 5 problems

---

**Happy Coding! 🐍**
