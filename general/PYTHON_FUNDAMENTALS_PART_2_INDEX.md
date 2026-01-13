# 🐍 PYTHON FUNDAMENTALS PART 2 - COMPLETE INDEX

## Quick Navigation Guide

This comprehensive guide covers Python's core data structures and functional programming concepts with **200+ practical examples**.

---

## 📚 TABLE OF CONTENTS

### 1. **LISTS - Complete Guide**
   - Creating lists (empty, with elements, nested)
   - Indexing and slicing
   - List methods (append, extend, insert, remove, pop)
   - Finding elements (index, count, in operator)
   - Sorting and reversing
   - List comprehensions
   - **35+ practical examples**

### 2. **TUPLES - Complete Guide**
   - Creating tuples (single element, multiple)
   - Indexing and slicing
   - Tuple methods (count, index)
   - Tuple unpacking and multiple assignment
   - Named tuples
   - When to use tuples vs lists
   - **20+ practical examples**

### 3. **SETS - Complete Guide**
   - Creating sets and removing duplicates
   - Adding and removing elements
   - Mathematical operations (union, intersection, difference)
   - Set membership and iteration
   - Set comprehensions
   - Common use cases (deduplication, fast lookup)
   - **30+ practical examples**

### 4. **DICTIONARIES - Complete Guide**
   - Creating dictionaries
   - Accessing values (direct, get, setdefault)
   - Modifying dictionaries (update, pop, clear)
   - Dictionary methods (keys, values, items)
   - Dictionary comprehensions
   - defaultdict, OrderedDict, Counter
   - Nested dictionaries
   - **40+ practical examples**

### 5. **LAMBDA FUNCTIONS - Complete Guide**
   - Basic lambda syntax
   - Using with map(), filter(), sorted()
   - Lambda with dictionaries and lists
   - Multiple arguments and conditions
   - When NOT to use lambda
   - **25+ practical examples**

### 6. **COMPREHENSIONS - Complete Guide**
   - List comprehensions (with conditions, nested, flattening)
   - Dictionary comprehensions
   - Set comprehensions
   - **30+ practical examples**

### 7. **FUNCTIONAL PROGRAMMING - map(), filter(), reduce()**
   - map() for transforming elements
   - filter() for selecting elements
   - reduce() for accumulating values
   - Combining functional operations
   - **20+ practical examples**

### 8. **ADVANCED TECHNIQUES**
   - Unpacking and multiple assignment
   - enumerate() and zip()
   - Sorting with multiple keys
   - any(), all(), and conditional operations
   - **20+ practical examples**

### 9. **INTERVIEW PATTERNS**
   - Two-sum pattern
   - Counting frequencies
   - Grouping elements
   - Sliding window
   - Nested data access
   - **10+ patterns with code**

### 10. **PRACTICE PROBLEMS**
   - Flatten nested lists
   - Group anagrams
   - Most frequent element
   - Merge sorted lists
   - Custom sorting with multiple keys
   - **5 complete problems with solutions**

---

## 🎯 QUICK REFERENCE TABLES

### Data Structure Comparison

| Feature | List | Tuple | Set | Dict |
|---------|------|-------|-----|------|
| **Ordered** | ✅ | ✅ | ❌ | ✅ (3.7+) |
| **Mutable** | ✅ | ❌ | ✅ | ✅ |
| **Unique Elements** | ❌ | ❌ | ✅ | Keys only |
| **Hashable** | ❌ | ✅ | ❌ | ❌ |
| **Use as Dict Key** | ❌ | ✅ | ❌ | ❌ |
| **Performance (access)** | O(n) | O(n) | O(1) avg | O(1) avg |
| **Performance (search)** | O(n) | O(n) | O(1) avg | O(1) avg |
| **Memory** | High | Lower | Medium | High |

### List Methods Quick Reference

| Method | Purpose | Returns | Modifies |
|--------|---------|---------|----------|
| `append(x)` | Add element | None | ✅ |
| `extend(list)` | Add multiple | None | ✅ |
| `insert(i, x)` | Insert at index | None | ✅ |
| `remove(x)` | Remove value | None | ✅ |
| `pop([i])` | Remove and return | Element | ✅ |
| `clear()` | Remove all | None | ✅ |
| `index(x)` | Find index | Index | ❌ |
| `count(x)` | Count occurrences | Count | ❌ |
| `sort()` | Sort in place | None | ✅ |
| `reverse()` | Reverse in place | None | ✅ |
| `copy()` | Shallow copy | New list | ❌ |

### Dictionary Methods Quick Reference

| Method | Purpose | Returns | Example |
|--------|---------|---------|---------|
| `get(key)` | Get value | Value or None | `d.get('a', 'default')` |
| `keys()` | Get all keys | dict_keys | `list(d.keys())` |
| `values()` | Get all values | dict_values | `list(d.values())` |
| `items()` | Get key-value pairs | dict_items | `list(d.items())` |
| `pop(key)` | Remove and return | Value | `d.pop('a')` |
| `update(d)` | Merge dicts | None | `d.update({'b': 2})` |
| `clear()` | Remove all | None | `d.clear()` |
| `copy()` | Shallow copy | New dict | `d.copy()` |
| `setdefault(k,v)` | Get or set | Value | `d.setdefault('a', 1)` |

### Set Operations

| Operation | Syntax | Meaning |
|-----------|--------|---------|
| Union | `a \| b` or `a.union(b)` | All elements from both |
| Intersection | `a & b` or `a.intersection(b)` | Common elements |
| Difference | `a - b` or `a.difference(b)` | In a but not b |
| Symmetric Diff | `a ^ b` or `a.symmetric_difference(b)` | In either but not both |
| Subset | `a <= b` or `a.issubset(b)` | All elements of a in b |
| Superset | `a >= b` or `a.issuperset(b)` | a contains all of b |
| Disjoint | `a.isdisjoint(b)` | No common elements |

---

## 💡 COMMON PATTERNS & SOLUTIONS

### Pattern: Default Values in Dictionary

```python
# Problem: Avoid KeyError when accessing missing keys
# Solution 1: Using get()
value = d.get('key', default_value)

# Solution 2: Using setdefault()
d.setdefault('key', default_value)

# Solution 3: Using defaultdict
from collections import defaultdict
d = defaultdict(int)
d['count'] += 1  # No KeyError!
```

### Pattern: Counting Elements

```python
# Problem: Count occurrences of elements
# Solution 1: Manual dict
freq = {}
for item in items:
    freq[item] = freq.get(item, 0) + 1

# Solution 2: Counter
from collections import Counter
freq = Counter(items)
freq.most_common(3)  # Top 3

# Solution 3: defaultdict
from collections import defaultdict
freq = defaultdict(int)
for item in items:
    freq[item] += 1
```

### Pattern: Remove Duplicates While Preserving Order

```python
# Problem: Remove duplicates but keep order
# Solution 1: dict.fromkeys() (3.7+, dict maintains order)
unique = list(dict.fromkeys(items))

# Solution 2: Manual with set
seen = set()
unique = []
for item in items:
    if item not in seen:
        unique.append(item)
        seen.add(item)

# Solution 3: List comprehension (slower)
unique = []
for item in items:
    if item not in unique:  # O(n) check!
        unique.append(item)
```

### Pattern: Grouping Elements

```python
# Problem: Group items by some key
# Solution 1: defaultdict
from collections import defaultdict
groups = defaultdict(list)
for item in items:
    groups[key_function(item)].append(item)

# Solution 2: Dictionary comprehension
groups = {}
for item in items:
    key = key_function(item)
    if key not in groups:
        groups[key] = []
    groups[key].append(item)

# Solution 3: itertools.groupby (requires sorted data)
from itertools import groupby
groups = {}
for key, group in groupby(sorted_items, key=key_function):
    groups[key] = list(group)
```

### Pattern: Sorting Complex Objects

```python
# Single key
sorted_list = sorted(data, key=lambda x: x['score'])

# Multiple keys (grade desc, then age asc)
sorted_list = sorted(data, key=lambda x: (-x['grade'], x['age']))

# Using itemgetter (more efficient)
from operator import itemgetter
sorted_list = sorted(data, key=itemgetter('grade', 'age'))

# Using attrgetter for objects
from operator import attrgetter
sorted_list = sorted(objects, key=attrgetter('name', 'age'))
```

### Pattern: Safe Nested Dictionary Access

```python
# Problem: Avoid KeyError with nested dicts
# Solution 1: Using get() chain
value = d.get('key1', {}).get('key2', {}).get('key3')

# Solution 2: Try-except
try:
    value = d['key1']['key2']['key3']
except KeyError:
    value = None

# Solution 3: Helper function
def get_nested(d, *keys, default=None):
    for key in keys:
        if isinstance(d, dict):
            d = d.get(key)
        else:
            return default
    return d
```

---

## 🔥 PERFORMANCE TIPS

### Lists
- **append()** is O(1) amortized
- **insert(0, x)** is O(n) - avoid for large lists
- **remove()** is O(n) - searches for value
- **Slicing** creates a copy (use itertools for memory efficiency)

### Tuples
- Faster than lists for immutable data
- Can be used as dict keys
- Slightly less memory than lists

### Sets
- **add()** is O(1) average
- **Membership test (in)** is O(1) average - much faster than list!
- Use for deduplication and fast lookup
- Set operations are very efficient

### Dictionaries
- **Average O(1)** access, worst case O(n)
- **keys(), values(), items()** are views - memory efficient
- Use dictionary instead of list for fast lookups
- defaultdict and Counter have small overhead

### Comprehensions vs Loops
- Comprehensions are typically 10-30% faster
- More memory efficient than map/filter
- More readable for most cases

### Lambda vs Named Functions
- Lambda has slight overhead vs named function
- Named functions are clearer and easier to debug
- Use lambda only for short, one-off operations

---

## 🎓 LEARNING PATH

### Day 1: Lists
- [ ] Read Lists section completely
- [ ] Code all examples
- [ ] Understand list methods
- [ ] Practice list comprehensions
- [ ] Solve 3 list-based interview problems

### Day 2: Tuples & Sets
- [ ] Read Tuples section
- [ ] Understand immutability
- [ ] Read Sets section
- [ ] Learn set operations
- [ ] Solve 2 tuple and 2 set problems

### Day 3: Dictionaries
- [ ] Read Dictionaries section
- [ ] Learn all dictionary methods
- [ ] Understand dict comprehensions
- [ ] Explore defaultdict, Counter
- [ ] Solve 3 dictionary-based problems

### Day 4: Lambda & Comprehensions
- [ ] Read Lambda section
- [ ] Practice lambda with map/filter
- [ ] Read Comprehensions section
- [ ] Understand all comprehension types
- [ ] Solve problems using lambdas

### Day 5: Functional Programming & Advanced
- [ ] Read functional programming section
- [ ] Practice map, filter, reduce
- [ ] Learn unpacking and zip/enumerate
- [ ] Understand multiple key sorting
- [ ] Solve complex problems

### Day 6: Patterns & Practice
- [ ] Read interview patterns
- [ ] Study pattern implementations
- [ ] Solve all 5 practice problems
- [ ] Review weaker areas
- [ ] Create cheat sheet

### Day 7: Integration & Mastery
- [ ] Mix all concepts
- [ ] Solve difficult problems
- [ ] Speed challenges (10 min per problem)
- [ ] Explain solutions clearly
- [ ] Build confidence

---

## ✅ MASTERY CHECKLIST

### Lists
- [ ] Create and initialize lists
- [ ] Use indexing and slicing
- [ ] Add/remove elements correctly
- [ ] Know when to use which method
- [ ] Write efficient list comprehensions
- [ ] Understand shallow vs deep copy

### Tuples
- [ ] Create single and multiple element tuples
- [ ] Use tuple unpacking
- [ ] Understand immutability benefits
- [ ] Use tuples as dict keys
- [ ] Know namedtuples usage

### Sets
- [ ] Create sets and remove duplicates
- [ ] Use set operations correctly
- [ ] Know set comprehension syntax
- [ ] Understand O(1) membership
- [ ] Use for optimization

### Dictionaries
- [ ] Create and access dictionaries
- [ ] Handle missing keys safely
- [ ] Use dict comprehensions
- [ ] Merge dictionaries
- [ ] Use defaultdict appropriately
- [ ] Handle nested dictionaries

### Lambda Functions
- [ ] Write simple lambda functions
- [ ] Use with map, filter, sorted
- [ ] Know when NOT to use lambda
- [ ] Write readable code

### Comprehensions
- [ ] List comprehensions with conditions
- [ ] Nested and complex comprehensions
- [ ] Dictionary comprehensions
- [ ] Set comprehensions
- [ ] Know performance benefits

### Functional Programming
- [ ] Use map() for transformations
- [ ] Use filter() for selections
- [ ] Use reduce() for accumulation
- [ ] Combine operations efficiently
- [ ] Know when lists are better

### Advanced
- [ ] Unpack variables
- [ ] Use enumerate and zip
- [ ] Sort by multiple keys
- [ ] Use any/all efficiently
- [ ] Handle complex data structures

---

## 🚀 INTERVIEW TIPS

### What Interviewers Test
1. **Knowledge** - Know all data structures and methods
2. **Judgment** - Choose right structure for problem
3. **Efficiency** - Optimize for time and space
4. **Readability** - Write clean, pythonic code
5. **Communication** - Explain your approach

### Best Practices
- **Choose the right structure**
  - Need uniqueness? Use sets
  - Need key-value? Use dicts
  - Need order? Use lists or tuples
  - Need immutability? Use tuples

- **Use Pythonic idioms**
  - Dictionary comprehensions over loops
  - `in` operator for membership (fast with sets/dicts)
  - unpacking over indexing
  - defaultdict to avoid KeyError

- **Optimize when needed**
  - Use sets for O(1) lookups instead of lists
  - Use dict instead of list for key-based access
  - Avoid list.insert(0, x) - use deque instead
  - Use generator expressions for large data

- **Handle edge cases**
  - Empty collections
  - Single element
  - Duplicate elements
  - None values
  - Type mismatches

---

## 📖 EXAMPLE PROBLEMS

### Problem 1: Word Frequency
```python
words = ['apple', 'banana', 'apple', 'cherry', 'banana', 'apple']
freq = {}
for word in words:
    freq[word] = freq.get(word, 0) + 1
print(freq)  # {'apple': 3, 'banana': 2, 'cherry': 1}
```

### Problem 2: Unique Elements
```python
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
unique = list(dict.fromkeys(numbers))  # Preserves order
print(unique)  # [1, 2, 3, 4]
```

### Problem 3: Merge Two Lists
```python
a = [1, 3, 5]
b = [2, 4, 6]
result = sorted(a + b)  # or merge algorithm
print(result)  # [1, 2, 3, 4, 5, 6]
```

### Problem 4: Find Common Elements
```python
a = [1, 2, 3, 4, 5]
b = [4, 5, 6, 7, 8]
common = list(set(a) & set(b))
print(common)  # [4, 5]
```

### Problem 5: Group by First Letter
```python
words = ['apple', 'apricot', 'banana', 'blueberry', 'cherry']
from collections import defaultdict
groups = defaultdict(list)
for word in words:
    groups[word[0]].append(word)
print(dict(groups))
# {'a': ['apple', 'apricot'], 'b': ['banana', 'blueberry'], 'c': ['cherry']}
```

---

## 🔗 CONNECTIONS TO OTHER CONCEPTS

### How These Connect to Problem Solving

1. **Lists** - Used in array-based problems
2. **Tuples** - Return multiple values, hashable keys
3. **Sets** - Deduplication, mathematical problems
4. **Dictionaries** - Caching, mapping problems
5. **Lambda** - Sorting, filtering, transformations
6. **Comprehensions** - Efficient data building
7. **Map/Filter** - Functional problem solving
8. **Patterns** - Recognizing common structures

### Next Topics to Learn
- String operations and methods
- Classes and objects
- Exception handling
- File operations
- Modules and imports
- Decorators
- Generators and iterators

---

## 📞 QUICK REFERENCE LINKS

- **Lists**: Use for ordered, mutable collections with methods like append, remove, sort
- **Tuples**: Use for immutable, hashable collections and multiple returns
- **Sets**: Use for unique, unordered, fast membership testing
- **Dicts**: Use for key-value mapping with O(1) average access
- **Lambda**: Use for short, one-off functions with map/filter/sorted
- **Comprehensions**: Use for efficient, readable data construction
- **Functional**: Use map/filter/reduce for transformations and filtering

---

**Master these fundamentals and you'll be ready for any Python interview!** 🚀

