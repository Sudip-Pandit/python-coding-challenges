# Python Tuples - 100 Coding Challenges with Solutions

Complete guide to mastering Python tuples with 100 problems from basic to advanced.

---

## 📋 Quick Navigation

- **Basic Operations (1-15)**: Creation, access, operations
- **Indexing & Slicing (16-25)**: Slicing patterns, chunks, rotation
- **Tuple Methods (26-35)**: count(), index(), immutability
- **Unpacking (36-45)**: Basic, extended, nested unpacking
- **Named Tuples (46-55)**: Collections.namedtuple, typing
- **Tuple vs List (56-65)**: Performance, when to use
- **Nested Tuples (66-75)**: Matrices, trees, deep nesting
- **Advanced (76-90)**: Set ops, combinatorics, algorithms
- **Real-World (91-100)**: Coordinates, databases, state machines

**Total**: 100 problems | **Difficulty**: 35 Easy, 50 Medium, 15 Hard

---

## Complete Problem List

### Basic Operations (1-15)
1. Create tuples (parentheses, packing, constructor)
2. Access elements (positive/negative indexing)
3. Get tuple length
4. Check element existence (in operator)
5. Count occurrences (count method)
6. Find index (index method, find all)
7. Concatenate tuples (+, unpacking)
8. Repeat elements (* operator)
9. Compare tuples (==, <, >)
10. Find min/max values
11. Sum tuple elements
12. Convert tuple ↔ list
13. Reverse tuple (slicing, reversed())
14. Sort tuple (sorted(), custom key)
15. Create from variables (packing)

### Indexing and Slicing (16-25)
16. Basic slicing ([start:end:step])
17. Modify via conversion (immutability workaround)
18. Get first N elements ([:n])
19. Get last N elements ([-n:])
20. Get every Nth element ([::n])
21. Extract odd/even positions
22. Get middle element(s)
23. Rotate tuple (left/right)
24. Extract alternating elements
25. Chunk into parts

### Tuple Methods (26-35)
26. count() method deep dive
27. index() with start/end parameters
28. Immutability demonstration
29. Tuple as dictionary key (hashable)
30. Tuple packing/unpacking
31. Tuple comprehension (generator)
32. Convert string → tuple
33. Hash values (hashable property)
34. Tuple vs list performance
35. Type conversions

### Unpacking (36-45)
36. Basic unpacking (a, b = tuple)
37. Extended unpacking (*rest)
38. Unpacking in loops (for x, y in tuples)
39. Function return unpacking
40. Swapping variables
41. Nested unpacking
42. Unpacking with ignoring (_)
43. Unpacking arguments (*args)
44. Unpacking in comprehensions
45. Unpacking with zip

### Named Tuples (46-55)
46. Create named tuple (namedtuple())
47. Named tuple methods (_asdict, _make, _replace)
48. Named tuples with defaults
49. Extend with custom methods (inheritance)
50. Data structures (Student, Employee records)
51. Named tuple vs dictionary
52. Type hints with NamedTuple
53. Serialization (JSON, CSV)
54. Factory functions (dynamic creation)
55. Validation in named tuples

### Tuple vs List (56-65)
56. Immutability demonstration
57. Memory efficiency comparison
58. Speed comparison (creation, access, iteration)
59. When to use tuples (guidelines)
60. Convert based on need
61. Dictionary keys (tuples yes, lists no)
62. Set membership (hashable requirement)
63. Safety benefits (immutability)
64. Syntax differences
65. Decision framework

### Nested Tuples (66-75)
66. Create nested structures
67. Access nested elements ([i][j])
68. Flatten nested tuples (recursive)
69. Matrix operations (add, multiply, transpose)
70. Traverse nested (row-wise, column-wise, spiral)
71. Find in nested (recursive search)
72. Count depth (max nesting level)
73. Convert nested tuple ↔ list
74. Nested comprehension
75. Tree structures (binary trees, n-ary)

### Advanced Operations (76-90)
76. Tuple intersection
77. Tuple union
78. Tuple difference
79. Cartesian product (itertools.product)
80. Permutations (itertools.permutations)
81. Combinations (itertools.combinations)
82. Zip operations (zip, zip_longest, unzip)
83. Grouping (groupby, custom grouping)
84. Sliding window
85. Chunking strategies
86. Rotation algorithms
87. Partition by predicate
88. Deduplication (ordered/unordered)
89. Frequency analysis
90. Transformation pipelines

### Real-World Applications (91-100)
91. Coordinate system (2D/3D points, distance)
92. RGB color system (hex, blending)
93. Database records (users, products, orders)
94. Time series data (timestamps, statistics)
95. Geographic coordinates (lat/lon, haversine)
96. Financial transactions (deposits, withdrawals)
97. Configuration management (settings)
98. Event logging system
99. Graph representation (nodes, edges)
100. State machine (transitions, events)

---

## Sample Solutions

Here are detailed solutions for select key problems:

### Problem 1: Create Tuples
```python
# Multiple creation methods
fruits = ('apple', 'banana')      # Parentheses
coords = 10, 20                   # Packing
nums = tuple([1, 2, 3])          # Constructor
single = (42,)                    # Single (comma!)
empty = ()                        # Empty
from_str = tuple('hello')         # From iterable
```

### Problem 29: Tuple as Dict Key
```python
# Tuples are hashable - perfect for keys
locations = {}
locations[(0, 0)] = 'origin'
locations[(10, 20)] = 'point A'

# Cache with tuple keys
cache = {}
cache[(5, 10)] = expensive_calc(5, 10)
```

### Problem 37: Extended Unpacking
```python
first, *middle, last = (1, 2, 3, 4, 5)
# first=1, middle=[2,3,4], last=5

# Ignore middle
first, *_, last = (1, 2, 3, 4, 5)
# first=1, last=5
```

### Problem 46: Named Tuples
```python
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(10, 20)
print(p.x, p.y)  # 10 20

# With defaults (Python 3.7+)
Person = namedtuple('Person', ['name', 'age'], 
                    defaults=['Unknown', 0])
```

### Problem 68: Flatten Nested
```python
def flatten(nested):
    result = ()
    for item in nested:
        if isinstance(item, tuple):
            result += flatten(item)
        else:
            result += (item,)
    return result

nested = (1, (2, (3, 4)), 5)
print(flatten(nested))  # (1, 2, 3, 4, 5)
```

### Problem 79: Cartesian Product
```python
from itertools import product

colors = ('red', 'blue')
sizes = ('S', 'M', 'L')

combinations = tuple(product(colors, sizes))
# (('red', 'S'), ('red', 'M'), ('red', 'L'),
#  ('blue', 'S'), ('blue', 'M'), ('blue', 'L'))
```

### Problem 91: Coordinate System
```python
from collections import namedtuple
from math import sqrt

Point = namedtuple('Point', ['x', 'y'])

def distance(p1, p2):
    return sqrt((p2.x-p1.x)**2 + (p2.y-p1.y)**2)

p1 = Point(0, 0)
p2 = Point(3, 4)
print(distance(p1, p2))  # 5.0
```

---

## Key Concepts Summary

### Tuple Characteristics
- **Immutable**: Cannot change after creation
- **Ordered**: Elements have defined order
- **Indexed**: Access by position [0], [1], etc.
- **Hashable**: Can be dict keys (if all elements hashable)
- **Memory efficient**: Less overhead than lists
- **Faster**: Creation and access faster than lists

### When to Use Tuples
✅ Fixed data that shouldn't change
✅ Function return multiple values
✅ Dictionary keys
✅ Set elements
✅ Performance-critical code
✅ Data integrity (immutability)

### When to Use Lists
✅ Data that needs modification
✅ Dynamic size requirements
✅ Need list methods (append, remove, etc.)
✅ Homogeneous collections that grow

### Common Patterns

**Multiple Returns**:
```python
def get_stats(data):
    return min(data), max(data), sum(data)/len(data)

minimum, maximum, average = get_stats([1,2,3,4,5])
```

**Swapping**:
```python
a, b = b, a  # Swap using tuple packing/unpacking
```

**Enumeration**:
```python
for index, value in enumerate(my_tuple):
    print(f"{index}: {value}")
```

**Zip Parallel Iteration**:
```python
names = ('Alice', 'Bob')
ages = (25, 30)
for name, age in zip(names, ages):
    print(f"{name}: {age}")
```

---

## Performance Tips

1. **Use tuples for constants**: `COLORS = ('red', 'green', 'blue')`
2. **Prefer named tuples**: More readable than index access
3. **Cache with tuple keys**: Fast lookup with hashability
4. **Return tuples from functions**: Clean multiple returns
5. **Use in set operations**: Fast membership testing

---

## Common Mistakes to Avoid

❌ **Forgetting comma in single tuple**: `(42)` is int, not tuple
✅ **Correct**: `(42,)` is a tuple

❌ **Trying to modify**: `my_tuple[0] = 10` raises TypeError
✅ **Convert to list, modify, convert back**

❌ **Using list as dict key**: Lists aren't hashable
✅ **Use tuple instead**: `{(1, 2): 'value'}`

❌ **Shallow vs deep copy confusion** with nested structures
✅ **Use copy.deepcopy() for nested mutable objects**

---

## Practice Recommendations

### Beginner (Problems 1-30)
- Focus on: Creation, access, basic operations
- Time: 1-2 weeks, 2-3 problems/day
- Goal: Understand tuple fundamentals

### Intermediate (Problems 31-70)
- Focus on: Unpacking, named tuples, nested structures
- Time: 2-3 weeks, 3-4 problems/day
- Goal: Master tuple techniques

### Advanced (Problems 71-100)
- Focus on: Algorithms, real-world applications
- Time: 2-3 weeks, 3-5 problems/day
- Goal: Apply tuples in complex scenarios

### Total Timeline: 6-8 weeks for complete mastery

---

## Interview Questions

Common tuple questions you might encounter:

1. **Difference between tuple and list?**
   - Immutability, performance, use cases

2. **Why use tuples as dictionary keys?**
   - Hashability requirement

3. **How to modify a tuple?**
   - Convert to list, modify, convert back

4. **What's tuple unpacking?**
   - Assigning tuple elements to variables

5. **Named tuples vs regular tuples?**
   - Named access vs index access

6. **Performance: tuple vs list?**
   - Tuples faster for creation/iteration

7. **Can tuples contain mutable objects?**
   - Yes, but then tuple isn't hashable

8. **Single element tuple syntax?**
   - Must include trailing comma: `(42,)`

---

## Additional Resources

### Python Documentation
- [Tuples and Sequences](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences)
- [collections.namedtuple](https://docs.python.org/3/library/collections.html#collections.namedtuple)
- [typing.NamedTuple](https://docs.python.org/3/library/typing.html#typing.NamedTuple)

### Recommended Reading
- Python Cookbook (tuple recipes)
- Effective Python (Item 19: Prefer tuples)
- Fluent Python (Chapter on data structures)

### Practice Platforms
- LeetCode (tuple problems)
- HackerRank (Python track)
- Codewars (tuple kata)

---

## Next Steps

After mastering tuples:

1. **Sets** (20-30 challenges)
   - Set operations, unique elements
   - Mathematical set theory
   - Performance optimization

2. **Dictionaries** (40-50 challenges)
   - Key-value pairs, nested dicts
   - Dictionary comprehensions
   - Advanced dict operations

3. **Combined Challenges**
   - Use all data structures together
   - Real-world projects
   - Algorithm implementation

---

## Conclusion

You now have 100 comprehensive tuple challenges covering:
- ✅ All tuple operations and methods
- ✅ Performance optimization
- ✅ Named tuples and typing
- ✅ Real-world applications
- ✅ Interview preparation

**Remember**: Practice consistently, understand the concepts, and apply them in real projects!

---

**🐍 Happy Coding! Master tuples and level up your Python skills! 🚀**

---

*Created: January 2026 | Problems: 100 | Difficulty: Easy to Hard*
