# 🎯 PYTHON FUNDAMENTALS PART 2 - PRACTICE PROBLEMS

## Practice Set: Master Lists, Tuples, Sets, Dictionaries, and Lambda Functions

**Total: 25+ Problems with Complete Solutions**

---

## EASY PROBLEMS (1-5)

### Problem 1: Sum of Even Numbers

**Difficulty:** Easy  
**Topics:** Lists, Lambda, Functional Programming  
**Expected Time:** 5 minutes

**Problem Statement:**
Given a list of numbers, return the sum of all even numbers using functional programming.

**Examples:**
```
Input: [1, 2, 3, 4, 5, 6]
Output: 12 (2 + 4 + 6)

Input: [10, 15, 20, 25]
Output: 30 (10 + 20)

Input: [1, 3, 5, 7]
Output: 0
```

**Constraints:**
- 1 ≤ list length ≤ 1000
- 0 ≤ values ≤ 1000

**Solutions:**

```python
# Solution 1: Using filter() and sum()
def sum_evens_v1(numbers):
    return sum(filter(lambda x: x % 2 == 0, numbers))

# Solution 2: Using list comprehension
def sum_evens_v2(numbers):
    return sum(x for x in numbers if x % 2 == 0)

# Solution 3: Using map() and filter()
def sum_evens_v3(numbers):
    return sum(map(int, filter(lambda x: x % 2 == 0, numbers)))

# Solution 4: Traditional loop
def sum_evens_v4(numbers):
    total = 0
    for num in numbers:
        if num % 2 == 0:
            total += num
    return total

# Test cases
print(sum_evens_v1([1, 2, 3, 4, 5, 6]))      # 12
print(sum_evens_v2([10, 15, 20, 25]))        # 30
print(sum_evens_v3([1, 3, 5, 7]))            # 0
print(sum_evens_v1([2, 4, 6, 8, 10]))        # 30
```

**Time Complexity:** O(n)  
**Space Complexity:** O(1)  
**Key Concepts:** Lambda, filter(), list comprehension, functional programming

---

### Problem 2: Remove Duplicates (Preserve Order)

**Difficulty:** Easy  
**Topics:** Lists, Dictionaries, Sets  
**Expected Time:** 5 minutes

**Problem Statement:**
Given a list with duplicate elements, return a new list with duplicates removed while preserving the original order.

**Examples:**
```
Input: [1, 2, 2, 3, 1, 4]
Output: [1, 2, 3, 4]

Input: ['a', 'b', 'a', 'c', 'b']
Output: ['a', 'b', 'c']

Input: [1, 1, 1, 1]
Output: [1]
```

**Constraints:**
- 1 ≤ list length ≤ 10000
- Elements are comparable

**Solutions:**

```python
# Solution 1: Using dict.fromkeys() - Python 3.7+
def remove_duplicates_v1(lst):
    return list(dict.fromkeys(lst))

# Solution 2: Using set with manual tracking (O(n))
def remove_duplicates_v2(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            result.append(item)
            seen.add(item)
    return result

# Solution 3: Using list comprehension (doesn't preserve order well)
def remove_duplicates_v3(lst):
    return list(set(lst))  # Warning: loses order!

# Solution 4: More elegant with enumerate
def remove_duplicates_v4(lst):
    seen = set()
    return [x for x in lst if not (x in seen or seen.add(x))]

# Test cases
print(remove_duplicates_v1([1, 2, 2, 3, 1, 4]))      # [1, 2, 3, 4]
print(remove_duplicates_v2(['a', 'b', 'a', 'c', 'b']))  # ['a', 'b', 'c']
print(remove_duplicates_v2([1, 1, 1, 1]))            # [1]
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)  
**Key Concepts:** Sets, dictionaries, order preservation, hash tables

---

### Problem 3: Flatten List (One Level)

**Difficulty:** Easy  
**Topics:** Lists, Comprehensions  
**Expected Time:** 5 minutes

**Problem Statement:**
Given a list of lists, flatten it to a single list.

**Examples:**
```
Input: [[1, 2], [3, 4], [5, 6]]
Output: [1, 2, 3, 4, 5, 6]

Input: [['a'], ['b', 'c'], ['d']]
Output: ['a', 'b', 'c', 'd']

Input: [[1, 2, 3]]
Output: [1, 2, 3]
```

**Solutions:**

```python
# Solution 1: Nested list comprehension
def flatten_v1(lst):
    return [x for sublist in lst for x in sublist]

# Solution 2: Using itertools.chain
from itertools import chain
def flatten_v2(lst):
    return list(chain(*lst))

# Solution 3: Using extend in loop
def flatten_v3(lst):
    result = []
    for sublist in lst:
        result.extend(sublist)
    return result

# Solution 4: Using sum() with empty list
def flatten_v4(lst):
    return sum(lst, [])  # Not recommended (O(n²) for strings)

# Test cases
print(flatten_v1([[1, 2], [3, 4], [5, 6]]))     # [1, 2, 3, 4, 5, 6]
print(flatten_v1([['a'], ['b', 'c'], ['d']]))   # ['a', 'b', 'c', 'd']
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)  
**Key Concepts:** List comprehension, nested loops, itertools

---

### Problem 4: Count Frequencies

**Difficulty:** Easy  
**Topics:** Dictionaries, Collections  
**Expected Time:** 5 minutes

**Problem Statement:**
Given a list, return a dictionary with each element as key and its count as value.

**Examples:**
```
Input: ['a', 'b', 'a', 'c', 'b', 'a']
Output: {'a': 3, 'b': 2, 'c': 1}

Input: [1, 2, 2, 3, 3, 3]
Output: {1: 1, 2: 2, 3: 3}

Input: ['x']
Output: {'x': 1}
```

**Solutions:**

```python
# Solution 1: Using Counter from collections
from collections import Counter
def count_freq_v1(lst):
    return dict(Counter(lst))

# Solution 2: Using defaultdict
from collections import defaultdict
def count_freq_v2(lst):
    freq = defaultdict(int)
    for item in lst:
        freq[item] += 1
    return dict(freq)

# Solution 3: Using get() method
def count_freq_v3(lst):
    freq = {}
    for item in lst:
        freq[item] = freq.get(item, 0) + 1
    return freq

# Solution 4: Using setdefault()
def count_freq_v4(lst):
    freq = {}
    for item in lst:
        freq.setdefault(item, 0)
        freq[item] += 1
    return freq

# Solution 5: Dictionary comprehension with count()
def count_freq_v5(lst):
    return {item: lst.count(item) for item in set(lst)}

# Test cases
print(count_freq_v1(['a', 'b', 'a', 'c', 'b', 'a']))  # {'a': 3, 'b': 2, 'c': 1}
print(count_freq_v3([1, 2, 2, 3, 3, 3]))             # {1: 1, 2: 2, 3: 3}
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)  
**Key Concepts:** Dictionaries, Counter, defaultdict

---

### Problem 5: Sort Pairs by Sum

**Difficulty:** Easy  
**Topics:** Tuples, Sorting, Lambda  
**Expected Time:** 5 minutes

**Problem Statement:**
Given a list of tuples (pairs), sort them by their sum in descending order.

**Examples:**
```
Input: [(1, 2), (5, 3), (2, 4)]
Output: [(5, 3), (2, 4), (1, 2)]  # sums: 8, 6, 3

Input: [(10, 1), (5, 5), (3, 3)]
Output: [(10, 1), (5, 5), (3, 3)]  # sums: 11, 10, 6
```

**Solutions:**

```python
# Solution 1: Using sorted with lambda
def sort_by_sum_v1(pairs):
    return sorted(pairs, key=lambda x: sum(x), reverse=True)

# Solution 2: Using sorted with sum
def sort_by_sum_v2(pairs):
    return sorted(pairs, key=lambda x: x[0] + x[1], reverse=True)

# Solution 3: Using tuple unpacking
def sort_by_sum_v3(pairs):
    return sorted(pairs, key=lambda a, b: a + b, reverse=True)  # Won't work!

# Correct version
def sort_by_sum_v3_fixed(pairs):
    return sorted(pairs, key=lambda x: x[0] + x[1], reverse=True)

# Solution 4: List comprehension approach (less efficient)
def sort_by_sum_v4(pairs):
    return [p for _, p in sorted([(sum(p), p) for p in pairs], reverse=True)]

# Test cases
print(sort_by_sum_v1([(1, 2), (5, 3), (2, 4)]))    # [(5, 3), (2, 4), (1, 2)]
print(sort_by_sum_v2([(10, 1), (5, 5), (3, 3)]))  # [(10, 1), (5, 5), (3, 3)]
```

**Time Complexity:** O(n log n)  
**Space Complexity:** O(n)  
**Key Concepts:** Tuples, sorting, lambda, key functions

---

## MEDIUM PROBLEMS (6-15)

### Problem 6: Group by Length

**Difficulty:** Medium  
**Topics:** Dictionaries, defaultdict, Grouping  
**Expected Time:** 10 minutes

**Problem Statement:**
Given a list of words, group them by their length into a dictionary.

**Examples:**
```
Input: ['apple', 'pie', 'a', 'banana', 'hi', 'cherry']
Output: {1: ['a'], 2: ['pi', 'hi'], 5: ['apple'], 6: ['banana', 'cherry']}

Input: ['cat', 'dog', 'elephant', 'bird']
Output: {3: ['cat', 'dog', 4: ['bird'], 8: ['elephant']}
```

**Solutions:**

```python
# Solution 1: Using defaultdict
from collections import defaultdict
def group_by_length_v1(words):
    groups = defaultdict(list)
    for word in words:
        groups[len(word)].append(word)
    return dict(groups)

# Solution 2: Using regular dict with get()
def group_by_length_v2(words):
    groups = {}
    for word in words:
        length = len(word)
        if length not in groups:
            groups[length] = []
        groups[length].append(word)
    return groups

# Solution 3: Using dict comprehension (requires pre-processing)
def group_by_length_v3(words):
    return {
        length: [w for w in words if len(w) == length]
        for length in set(len(w) for w in words)
    }

# Test cases
print(group_by_length_v1(['apple', 'pie', 'a', 'banana', 'hi', 'cherry']))
# {5: ['apple'], 3: ['pie'], 1: ['a'], 6: ['banana', 'cherry'], 2: ['hi']}
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)  
**Key Concepts:** defaultdict, grouping patterns, dictionaries

---

### Problem 7: Most Frequent Element

**Difficulty:** Medium  
**Topics:** Dictionaries, Counter, Sorting  
**Expected Time:** 10 minutes

**Problem Statement:**
Given a list, find the most frequent element. If there's a tie, return any one.

**Examples:**
```
Input: [1, 1, 1, 2, 2, 3]
Output: 1

Input: ['a', 'b', 'a', 'c', 'b', 'a']
Output: 'a'

Input: [1]
Output: 1
```

**Solutions:**

```python
# Solution 1: Using Counter
from collections import Counter
def most_frequent_v1(lst):
    return Counter(lst).most_common(1)[0][0]

# Solution 2: Using dictionary and max()
def most_frequent_v2(lst):
    freq = {}
    for item in lst:
        freq[item] = freq.get(item, 0) + 1
    return max(freq, key=freq.get)

# Solution 3: Using dict comprehension
def most_frequent_v3(lst):
    freq = {item: lst.count(item) for item in set(lst)}
    return max(freq, key=freq.get)

# Test cases
print(most_frequent_v1([1, 1, 1, 2, 2, 3]))      # 1
print(most_frequent_v2(['a', 'b', 'a', 'c', 'b', 'a']))  # 'a'
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)  
**Key Concepts:** Counter, max with key, dictionaries

---

### Problem 8: Merge Two Dictionaries

**Difficulty:** Medium  
**Topics:** Dictionaries, Merging  
**Expected Time:** 10 minutes

**Problem Statement:**
Given two dictionaries, merge them. If keys overlap, sum the values.

**Examples:**
```
Input: {'a': 1, 'b': 2}, {'b': 3, 'c': 4}
Output: {'a': 1, 'b': 5, 'c': 4}

Input: {1: 'a', 2: 'b'}, {2: 'c', 3: 'd'}
Output: {1: 'a', 2: 'bc', 3: 'd'}
```

**Solutions:**

```python
# Solution 1: Using update() and get()
def merge_dicts_v1(dict1, dict2):
    result = dict1.copy()
    for key, value in dict2.items():
        result[key] = result.get(key, 0) + value
    return result

# Solution 2: Python 3.9+ merge operator
def merge_dicts_v2(dict1, dict2):
    return dict1 | dict2  # Overwrites keys

# Solution 3: Using defaultdict
from collections import defaultdict
def merge_dicts_v3(dict1, dict2):
    result = defaultdict(int)
    for d in [dict1, dict2]:
        for key, value in d.items():
            result[key] += value
    return dict(result)

# Solution 4: Using unpacking
def merge_dicts_v4(dict1, dict2):
    return {**dict1, **dict2}

# Test cases
print(merge_dicts_v1({'a': 1, 'b': 2}, {'b': 3, 'c': 4}))  # {'a': 1, 'b': 5, 'c': 4}
```

**Time Complexity:** O(n + m)  
**Space Complexity:** O(n + m)  
**Key Concepts:** Dictionary operations, merging, unpacking

---

### Problem 9: Two Sum with Indices

**Difficulty:** Medium  
**Topics:** Dictionaries, Hash Maps, Two Pointers  
**Expected Time:** 10 minutes

**Problem Statement:**
Given a list of numbers and a target, find two different indices where numbers sum to target.

**Examples:**
```
Input: [2, 7, 11, 15], target = 9
Output: (0, 1)  # 2 + 7 = 9

Input: [3, 2, 4], target = 6
Output: (1, 2)  # 2 + 4 = 6

Input: [3, 3], target = 6
Output: (0, 1)
```

**Constraints:**
- Each input has exactly one solution
- Cannot use same index twice

**Solutions:**

```python
# Solution 1: Using dictionary (hash map)
def two_sum_v1(numbers, target):
    seen = {}
    for i, num in enumerate(numbers):
        complement = target - num
        if complement in seen:
            return (seen[complement], i)
        seen[num] = i
    return None

# Solution 2: Using set (only returns values, not indices)
def two_sum_v2(numbers, target):
    seen = set()
    for num in numbers:
        complement = target - num
        if complement in seen:
            return (complement, num)
        seen.add(num)

# Solution 3: Two pointer approach (requires sorted)
def two_sum_v3(numbers, target):
    left, right = 0, len(numbers) - 1
    while left < right:
        total = numbers[left] + numbers[right]
        if total == target:
            return (left, right)
        elif total < target:
            left += 1
        else:
            right -= 1
    return None

# Solution 4: Brute force (O(n²))
def two_sum_v4(numbers, target):
    for i in range(len(numbers)):
        for j in range(i + 1, len(numbers)):
            if numbers[i] + numbers[j] == target:
                return (i, j)
    return None

# Test cases
print(two_sum_v1([2, 7, 11, 15], 9))  # (0, 1)
print(two_sum_v1([3, 2, 4], 6))       # (1, 2)
```

**Time Complexity:** O(n)  
**Space Complexity:** O(n)  
**Key Concepts:** Hash maps, dictionaries, two pointers

---

### Problem 10: Custom Sort by Multiple Keys

**Difficulty:** Medium  
**Topics:** Sorting, Lambda, Dictionaries  
**Expected Time:** 10 minutes

**Problem Statement:**
Given a list of dictionaries (students), sort by grade descending, then by name ascending.

**Examples:**
```
Input: [
    {'name': 'Alice', 'grade': 95},
    {'name': 'Bob', 'grade': 95},
    {'name': 'Charlie', 'grade': 92}
]
Output: [
    {'name': 'Alice', 'grade': 95},  # Bob has same grade but comes after (sorted by name)
    {'name': 'Bob', 'grade': 95},
    {'name': 'Charlie', 'grade': 92}
]
```

**Solutions:**

```python
# Solution 1: Using lambda with tuple (grade desc, name asc)
def sort_students_v1(students):
    return sorted(students, key=lambda x: (-x['grade'], x['name']))

# Solution 2: Using itemgetter
from operator import itemgetter
def sort_students_v2(students):
    return sorted(students, key=itemgetter('grade', 'name'), reverse=True)
    # Note: This doesn't work perfectly for mixed sort orders

# Solution 3: Multiple sorted calls (Schwartzian transform)
def sort_students_v3(students):
    result = sorted(students, key=lambda x: x['name'])  # Sort by name first
    result = sorted(result, key=lambda x: x['grade'], reverse=True)  # Then by grade
    return result

# Test cases
students = [
    {'name': 'Alice', 'grade': 95},
    {'name': 'Bob', 'grade': 95},
    {'name': 'Charlie', 'grade': 92},
    {'name': 'David', 'grade': 92}
]
print(sort_students_v1(students))
```

**Time Complexity:** O(n log n)  
**Space Complexity:** O(n)  
**Key Concepts:** Sorting, lambda, multiple sort keys, negative values for reverse

---

### Problem 11: Anagram Groups

**Difficulty:** Medium  
**Topics:** Dictionaries, Sorting, Grouping  
**Expected Time:** 15 minutes

**Problem Statement:**
Given a list of words, group anagrams together.

**Examples:**
```
Input: ['eat', 'tea', 'ate', 'bat', 'tab', 'cat']
Output: [['eat', 'tea', 'ate'], ['bat', 'tab'], ['cat']]
        or any grouping of anagrams

Input: ['a']
Output: [['a']]
```

**Constraints:**
- Words contain lowercase letters
- Result order doesn't matter

**Solutions:**

```python
# Solution 1: Using sorted characters as key
def group_anagrams_v1(words):
    anagrams = {}
    for word in words:
        key = ''.join(sorted(word))
        if key not in anagrams:
            anagrams[key] = []
        anagrams[key].append(word)
    return list(anagrams.values())

# Solution 2: Using defaultdict
from collections import defaultdict
def group_anagrams_v2(words):
    groups = defaultdict(list)
    for word in words:
        key = tuple(sorted(word))  # Use tuple for hashability
        groups[key].append(word)
    return list(groups.values())

# Solution 3: Using dict comprehension
def group_anagrams_v3(words):
    return list({
        ''.join(sorted(word)): [w for w in words if ''.join(sorted(w)) == ''.join(sorted(word))]
        for word in words
    }.values())

# Test cases
print(group_anagrams_v1(['eat', 'tea', 'ate', 'bat', 'tab', 'cat']))
# [['eat', 'tea', 'ate'], ['bat', 'tab'], ['cat']]
```

**Time Complexity:** O(n * k log k) where k is average word length  
**Space Complexity:** O(n)  
**Key Concepts:** Sorting, dictionaries, grouping, hashing

---

### Problem 12: Symmetric Difference of Sets

**Difficulty:** Medium  
**Topics:** Sets, Set Operations  
**Expected Time:** 10 minutes

**Problem Statement:**
Given two lists, find elements that are in either list but not in both.

**Examples:**
```
Input: [1, 2, 3, 4], [3, 4, 5, 6]
Output: [1, 2, 5, 6]

Input: ['a', 'b'], ['b', 'c']
Output: ['a', 'c']
```

**Solutions:**

```python
# Solution 1: Using set symmetric difference
def symmetric_diff_v1(list1, list2):
    set1, set2 = set(list1), set(list2)
    return list(set1 ^ set2)

# Solution 2: Manual using set operations
def symmetric_diff_v2(list1, list2):
    set1, set2 = set(list1), set(list2)
    return list((set1 - set2) | (set2 - set1))

# Solution 3: Using symmetric_difference method
def symmetric_diff_v3(list1, list2):
    return list(set(list1).symmetric_difference(set(list2)))

# Test cases
print(symmetric_diff_v1([1, 2, 3, 4], [3, 4, 5, 6]))  # [1, 2, 5, 6]
```

**Time Complexity:** O(n + m)  
**Space Complexity:** O(n + m)  
**Key Concepts:** Sets, symmetric difference, set operations

---

### Problem 13: Find Common Elements

**Difficulty:** Medium  
**Topics:** Sets, Intersection  
**Expected Time:** 10 minutes

**Problem Statement:**
Given multiple lists, find elements present in all of them.

**Examples:**
```
Input: [1, 2, 3, 4], [3, 4, 5], [3, 4, 6]
Output: [3, 4]

Input: ['a', 'b', 'c'], ['b', 'c', 'd'], ['c', 'd', 'e']
Output: ['c']
```

**Solutions:**

```python
# Solution 1: Using set intersection
def common_elements_v1(lists):
    if not lists:
        return []
    return list(set(lists[0]).intersection(*lists[1:]))

# Solution 2: Using reduce and intersection
from functools import reduce
def common_elements_v2(lists):
    if not lists:
        return []
    return list(reduce(lambda x, y: x & y, [set(l) for l in lists]))

# Solution 3: Manual approach
def common_elements_v3(lists):
    if not lists:
        return []
    common = set(lists[0])
    for lst in lists[1:]:
        common &= set(lst)
    return list(common)

# Test cases
print(common_elements_v1([[1, 2, 3, 4], [3, 4, 5], [3, 4, 6]]))  # [3, 4]
```

**Time Complexity:** O(n * m) where n is number of lists, m is average list length  
**Space Complexity:** O(m)  
**Key Concepts:** Sets, intersection, reduce function

---

## HARD PROBLEMS (16-25)

### Problem 14: Longest Substring Without Repeating

**Difficulty:** Hard  
**Topics:** Sliding Window, Dictionaries  
**Expected Time:** 20 minutes

**Problem Statement:**
Given a string, find the length of the longest substring without repeating characters.

**Examples:**
```
Input: "abcabcbb"
Output: 3  # "abc"

Input: "bbbbb"
Output: 1  # "b"

Input: "pwwkew"
Output: 3  # "wke"
```

**Solutions:**

```python
# Solution 1: Using sliding window with dictionary
def longest_substring_v1(s):
    char_index = {}
    max_length = 0
    start = 0
    
    for end, char in enumerate(s):
        if char in char_index and char_index[char] >= start:
            start = char_index[char] + 1
        char_index[char] = end
        max_length = max(max_length, end - start + 1)
    
    return max_length

# Solution 2: Using set (less efficient)
def longest_substring_v2(s):
    max_length = 0
    char_set = set()
    start = 0
    
    for end in range(len(s)):
        while s[end] in char_set:
            char_set.remove(s[start])
            start += 1
        char_set.add(s[end])
        max_length = max(max_length, end - start + 1)
    
    return max_length

# Test cases
print(longest_substring_v1("abcabcbb"))  # 3
print(longest_substring_v1("bbbbb"))    # 1
print(longest_substring_v1("pwwkew"))   # 3
```

**Time Complexity:** O(n)  
**Space Complexity:** O(min(n, charset_size))  
**Key Concepts:** Sliding window, hash map, two pointers

---

### Problem 15: LRU Cache Implementation

**Difficulty:** Hard  
**Topics:** Dictionaries, Ordering, Data Structures  
**Expected Time:** 25 minutes

**Problem Statement:**
Implement an LRU (Least Recently Used) Cache with get and put operations. Capacity is fixed.

**Constraints:**
- get(key): Get value and mark as recently used
- put(key, value): Insert and mark as recently used
- When capacity exceeded, remove least recently used

**Solutions:**

```python
# Solution 1: Using OrderedDict
from collections import OrderedDict
class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity
    
    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)  # Mark as recently used
        return self.cache[key]
    
    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)  # Remove least recently used

# Solution 2: Using collections.deque + dictionary
from collections import deque
class LRUCache_v2:
    def __init__(self, capacity):
        self.cache = {}
        self.access_order = deque()
        self.capacity = capacity
    
    def get(self, key):
        if key not in self.cache:
            return -1
        self.access_order.remove(key)
        self.access_order.append(key)
        return self.cache[key]
    
    def put(self, key, value):
        if key in self.cache:
            self.access_order.remove(key)
        elif len(self.cache) == self.capacity:
            least_used = self.access_order.popleft()
            del self.cache[least_used]
        
        self.cache[key] = value
        self.access_order.append(key)

# Test cases
cache = LRUCache(2)
cache.put(1, 1)
cache.put(2, 2)
print(cache.get(1))      # 1
cache.put(3, 3)          # Evicts 2
print(cache.get(2))      # -1 (evicted)
print(cache.get(3))      # 3
```

**Time Complexity:** O(1) for get and put  
**Space Complexity:** O(capacity)  
**Key Concepts:** Dictionaries, OrderedDict, design patterns, capacity management

---

## CHALLENGE PROBLEMS (21-25)

### Problem 20: Unique Triplets (3Sum)

**Difficulty:** Hard  
**Topics:** Sets, Sorting, Two Pointers  
**Expected Time:** 25 minutes

**Problem Statement:**
Find all unique triplets in array that sum to zero. Triplets must be unique.

**Examples:**
```
Input: [-1, 0, 1, 2, -1, -4]
Output: [[-1, -1, 2], [-1, 0, 1]]

Input: [0, 0, 0]
Output: [[0, 0, 0]]
```

**Solutions:**

```python
# Solution 1: Two pointer approach
def three_sum_v1(nums):
    nums.sort()
    result = []
    
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        
        if nums[i] > 0:
            break
        
        left, right = i + 1, len(nums) - 1
        while left < right:
            total = nums[i] + nums[left] + nums[right]
            
            if total == 0:
                result.append([nums[i], nums[left], nums[right]])
                while left < right and nums[left] == nums[left + 1]:
                    left += 1
                while left < right and nums[right] == nums[right - 1]:
                    right -= 1
                left += 1
                right -= 1
            elif total < 0:
                left += 1
            else:
                right -= 1
    
    return result

# Test cases
print(three_sum_v1([-1, 0, 1, 2, -1, -4]))  # [[-1, -1, 2], [-1, 0, 1]]
```

**Time Complexity:** O(n²)  
**Space Complexity:** O(1) if not counting output  
**Key Concepts:** Sorting, two pointers, duplicate handling

---

### Problem 21: Word Break (Dynamic Programming + Dictionaries)

**Difficulty:** Hard  
**Topics:** DP, Sets, Dictionaries  
**Expected Time:** 25 minutes

**Problem Statement:**
Given a string and dictionary, determine if string can be segmented using dictionary words.

**Examples:**
```
Input: s = "leetcode", dict = ["leet", "code"]
Output: True

Input: s = "applepenapple", dict = ["apple", "pen"]
Output: True

Input: s = "catsandog", dict = ["cat", "cats", "and", "sand", "dog"]
Output: False
```

**Solutions:**

```python
# Solution 1: Dynamic Programming
def word_break_v1(s, word_dict):
    word_set = set(word_dict)
    dp = [False] * (len(s) + 1)
    dp[0] = True
    
    for i in range(1, len(s) + 1):
        for j in range(i):
            if dp[j] and s[j:i] in word_set:
                dp[i] = True
                break
    
    return dp[len(s)]

# Solution 2: BFS approach
from collections import deque
def word_break_v2(s, word_dict):
    word_set = set(word_dict)
    queue = deque([0])
    visited = set([0])
    
    while queue:
        start = queue.popleft()
        if start == len(s):
            return True
        
        for end in range(start + 1, len(s) + 1):
            if end not in visited and s[start:end] in word_set:
                visited.add(end)
                queue.append(end)
    
    return False

# Test cases
print(word_break_v1("leetcode", ["leet", "code"]))  # True
print(word_break_v1("applepenapple", ["apple", "pen"]))  # True
```

**Time Complexity:** O(n²)  
**Space Complexity:** O(n)  
**Key Concepts:** DP, sets, string segmentation, BFS

---

### Problem 22: Merge K Sorted Lists

**Difficulty:** Hard  
**Topics:** Lists, Heaps, Merging  
**Expected Time:** 25 minutes

**Problem Statement:**
Merge k sorted lists into one sorted list.

**Examples:**
```
Input: [[1,4,5], [1,3,4], [2,6]]
Output: [1,1,2,1,3,4,4,5,6]

Input: []
Output: []

Input: [[]]
Output: []
```

**Solutions:**

```python
# Solution 1: Using heapq
import heapq

def merge_k_lists_v1(lists):
    # Filter out empty lists
    lists = [lst for lst in lists if lst]
    
    # Create min heap with (value, list_index, element_index)
    heap = []
    for i, lst in enumerate(lists):
        heapq.heappush(heap, (lst[0], i, 0))
    
    result = []
    while heap:
        val, list_idx, elem_idx = heapq.heappop(heap)
        result.append(val)
        
        if elem_idx + 1 < len(lists[list_idx]):
            next_val = lists[list_idx][elem_idx + 1]
            heapq.heappush(heap, (next_val, list_idx, elem_idx + 1))
    
    return result

# Solution 2: Simple sorting (less efficient)
def merge_k_lists_v2(lists):
    all_elements = []
    for lst in lists:
        all_elements.extend(lst)
    return sorted(all_elements)

# Test cases
print(merge_k_lists_v1([[1,4,5], [1,3,4], [2,6]]))  # [1,1,2,1,3,4,4,5,6]
```

**Time Complexity:** O(n log k) where n is total elements, k is number of lists  
**Space Complexity:** O(n)  
**Key Concepts:** Heaps, merging, priority queues

---

### Problem 23: Group Words That Are Anagrams (Complex)

**Difficulty:** Hard  
**Topics:** Dictionaries, Sorting, Complex Grouping  
**Expected Time:** 20 minutes

**Problem Statement:**
Given a list of words, group all anagrams together and return groups in alphabetical order of each group's first character sorted word.

**Solutions:**

```python
def group_anagrams_complex(words):
    from collections import defaultdict
    
    # Group by sorted characters
    groups = defaultdict(list)
    for word in words:
        key = ''.join(sorted(word))
        groups[key].append(word)
    
    # Sort each group and the groups themselves
    result = []
    for key in sorted(groups.keys()):
        result.append(sorted(groups[key]))
    
    return result

# Test cases
words = ['listen', 'silent', 'enlist', 'evil', 'live', 'vile']
print(group_anagrams_complex(words))
# [['enlist', 'listen', 'silent'], ['evil', 'live', 'vile']]
```

---

### Problem 24: Intersection and Union Operations

**Difficulty:** Hard  
**Topics:** Sets, Multiple Lists  
**Expected Time:** 20 minutes

**Problem Statement:**
Given multiple lists, find:
1. Intersection (common to all)
2. Union (all unique elements)
3. Differences (unique to each)

**Solutions:**

```python
def set_operations(lists):
    if not lists:
        return {
            'intersection': [],
            'union': [],
            'differences': []
        }
    
    set_lists = [set(lst) for lst in lists]
    
    # Intersection
    intersection = set_lists[0]
    for s in set_lists[1:]:
        intersection &= s
    
    # Union
    union = set()
    for s in set_lists:
        union |= s
    
    # Differences (unique to each set)
    differences = {}
    for i, s in enumerate(set_lists):
        unique = s.copy()
        for j, other in enumerate(set_lists):
            if i != j:
                unique -= other
        if unique:
            differences[f"unique_to_{i}"] = list(unique)
    
    return {
        'intersection': sorted(list(intersection)),
        'union': sorted(list(union)),
        'differences': differences
    }

# Test cases
lists = [[1, 2, 3, 4], [3, 4, 5, 6], [4, 5, 6, 7]]
print(set_operations(lists))
```

---

### Problem 25: Nested List Comprehension Challenge

**Difficulty:** Hard  
**Topics:** Comprehensions, Nested Data  
**Expected Time:** 20 minutes

**Problem Statement:**
Given nested data structure, flatten and transform in one comprehension.

**Examples:**
```
Input: [
    {'name': 'Alice', 'scores': [90, 95, 88]},
    {'name': 'Bob', 'scores': [78, 82, 85]},
    {'name': 'Charlie', 'scores': [95, 92, 98]}
]

Output: {
    'Alice': {'avg': 91.0, 'max': 95, 'min': 88},
    'Bob': {'avg': 81.67, 'max': 85, 'min': 78},
    'Charlie': {'avg': 95.0, 'max': 98, 'min': 92}
}
```

**Solutions:**

```python
# Solution 1: Using dict comprehension with calculation
def transform_nested_data(data):
    return {
        person['name']: {
            'avg': sum(person['scores']) / len(person['scores']),
            'max': max(person['scores']),
            'min': min(person['scores'])
        }
        for person in data
    }

# Solution 2: More readable with helper function
def process_scores(scores):
    return {
        'avg': round(sum(scores) / len(scores), 2),
        'max': max(scores),
        'min': min(scores)
    }

def transform_nested_data_v2(data):
    return {person['name']: process_scores(person['scores']) for person in data}

# Test cases
data = [
    {'name': 'Alice', 'scores': [90, 95, 88]},
    {'name': 'Bob', 'scores': [78, 82, 85]},
    {'name': 'Charlie', 'scores': [95, 92, 98]}
]
result = transform_nested_data(data)
for name, stats in result.items():
    print(f"{name}: {stats}")
```

---

## SUMMARY OF KEY CONCEPTS

### By Difficulty

**Easy (1-5):**
- Basic list operations
- Simple filtering and counting
- Tuple operations
- Lambda basics

**Medium (6-15):**
- Dictionary grouping
- Multiple data structure usage
- Set operations
- Sorting with custom keys
- Hash map patterns

**Hard (16-25):**
- Sliding window
- LRU Cache design
- Multiple algorithm combination
- Complex nested structures
- Optimization strategies

### By Data Structure

**Lists:** 1, 3, 4, 6, 12
**Tuples:** 5
**Sets:** 12, 13, 20
**Dictionaries:** 4, 6, 7, 8, 9, 10, 11, 14, 21
**Lambda/Comprehensions:** 1, 5, 9, 10, 25
**Advanced:** 14, 15, 20, 21, 22, 23

---

## 🎯 PRACTICE STRATEGY

1. **Solve without looking at solutions** (10-15 min)
2. **Check your solution** against provided ones
3. **Understand each approach** and its trade-offs
4. **Optimize for time and space**
5. **Code again from memory** next day
6. **Explain to someone else**
7. **Modify the problem** (different constraints, etc.)

---

**You now have 25+ complete problems to master Python fundamentals!** 🚀

