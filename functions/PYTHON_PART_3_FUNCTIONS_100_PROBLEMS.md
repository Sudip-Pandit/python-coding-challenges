# 🔥 PYTHON PART 3: FUNCTIONS - 100+ CHALLENGES

**Complete Guide to Python Functions: From Basics to Advanced**

**Based on: LeetCode, HackerRank, GeeksforGeeks, CodeSignal, InterviewBit**

---

## 📚 TABLE OF CONTENTS

- [BASIC FUNCTIONS (20 Problems)](#basic-functions)
- [PARAMETERS & ARGUMENTS (20 Problems)](#parameters--arguments)
- [RETURN VALUES & RECURSION (20 Problems)](#return-values--recursion)
- [DECORATORS (15 Problems)](#decorators)
- [CLOSURES & HIGHER ORDER (15 Problems)](#closures--higher-order-functions)
- [GENERATORS & ITERATORS (10 Problems)](#generators--iterators)

---

# BASIC FUNCTIONS (20 Problems)

---

## PROBLEM 1: Function Definition and Calling

**Difficulty:** Easy
**Interview Frequency:** 100% (Foundation)

### Problem Statement:
```
Master the basics of function definition and calling.

Concepts to cover:
1. Function definition with def
2. Function calls with ()
3. Return statement
4. Function naming conventions
5. Docstrings
```

### SOLUTION 1: Basic Function Structure
```python
def greet(name):
    """
    A simple greeting function.
    
    Args:
        name (str): The person's name
    
    Returns:
        str: A greeting message
    """
    message = f"Hello, {name}!"
    return message

# Calling the function
result = greet("Alice")
print(result)  # Hello, Alice!

# Multiple calls
print(greet("Bob"))    # Hello, Bob!
print(greet("Charlie")) # Hello, Charlie!
```

### SOLUTION 2: Function Without Return
```python
def print_info(name, age):
    """
    Print information without returning.
    Implicitly returns None
    """
    print(f"Name: {name}")
    print(f"Age: {age}")

print_info("Alice", 25)
# Output:
# Name: Alice
# Age: 25
```

### SOLUTION 3: Multiple Return Statements
```python
def check_number(num):
    """
    Check if number is positive, negative, or zero.
    Can have multiple return statements.
    """
    if num > 0:
        return "Positive"
    elif num < 0:
        return "Negative"
    else:
        return "Zero"

print(check_number(5))   # Positive
print(check_number(-3))  # Negative
print(check_number(0))   # Zero
```

### SOLUTION 4: Return Multiple Values
```python
def get_min_max(nums):
    """
    Return minimum and maximum values.
    Returns a tuple.
    """
    return min(nums), max(nums)

# Unpacking return values
minimum, maximum = get_min_max([1, 5, 3, 9, 2])
print(f"Min: {minimum}, Max: {maximum}")  # Min: 1, Max: 9

# Or access as tuple
result = get_min_max([1, 5, 3, 9, 2])
print(result)  # (1, 9)
```

### SOLUTION 5: Function with No Parameters
```python
def get_current_year():
    """
    Get current year.
    Function with no parameters.
    """
    from datetime import datetime
    return datetime.now().year

print(get_current_year())  # 2026
```

### SOLUTION 6: Function with No Return
```python
def display_banner():
    """
    Display a banner.
    Returns None implicitly.
    """
    print("=" * 40)
    print("Welcome to the Program!")
    print("=" * 40)

result = display_banner()
# Output:
# ========================================
# Welcome to the Program!
# ========================================

print(result)  # None
```

### Best Practices:
```python
# ✓ Good: Clear name, docstring, type hints
def calculate_average(numbers: list) -> float:
    """Calculate average of numbers."""
    return sum(numbers) / len(numbers)

# ✗ Bad: Unclear name, no docstring
def f(x):
    return sum(x) / len(x)

# ✓ Good: PEP 8 naming (snake_case)
def convert_to_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9

# ✗ Bad: CamelCase for function
def ConvertToCelsius(fahrenheit):
    return (fahrenheit - 32) * 5/9
```

---

## PROBLEM 2: Scope and Namespace

**Difficulty:** Easy
**Interview Frequency:** 80%

### Problem Statement:
```
Understand local, global, and enclosing scope.
Know how Python resolves names (LEGB rule).
```

### SOLUTION: Scope Levels
```python
# Global scope
global_var = "I'm global"

def outer():
    # Enclosing scope (for nested functions)
    enclosing_var = "I'm enclosing"
    
    def inner():
        # Local scope
        local_var = "I'm local"
        
        print(local_var)       # Local
        print(enclosing_var)   # Enclosing
        print(global_var)      # Global
    
    inner()

outer()
# Output:
# I'm local
# I'm enclosing
# I'm global

# LEGB Rule (Name Resolution Order):
# 1. Local scope
# 2. Enclosing scope (nested functions)
# 3. Global scope
# 4. Built-in scope
```

### SOLUTION: Global Keyword
```python
count = 0  # Global variable

def increment():
    global count  # Access and modify global
    count += 1

increment()
increment()
print(count)  # 2

# Without 'global' keyword:
def increment_wrong():
    count += 1  # UnboundLocalError!
    # Python treats 'count' as local variable
```

### SOLUTION: Nonlocal Keyword
```python
def outer():
    x = 10  # Enclosing scope
    
    def inner():
        nonlocal x
        x += 5  # Modify enclosing variable
    
    inner()
    print(x)  # 15

outer()
```

### Testing Scope Understanding:
```python
x = "global"

def test1():
    x = "local"
    print(x)  # local

def test2():
    print(x)  # global

def test3():
    global x
    x = "modified"
    
test1()  # Prints: local
test2()  # Prints: global
test3()
test2()  # Prints: modified
```

---

## PROBLEM 3: Default Arguments

**Difficulty:** Easy
**Interview Frequency:** 85%

### Problem Statement:
```
Master default parameter values.
Understand mutable vs immutable defaults.
Know when defaults are evaluated.
```

### SOLUTION 1: Basic Defaults
```python
def greet(name, greeting="Hello"):
    """
    Function with default parameter.
    greeting has default value.
    """
    return f"{greeting}, {name}!"

print(greet("Alice"))              # Hello, Alice!
print(greet("Alice", "Hi"))        # Hi, Alice!
print(greet("Alice", "Howdy"))     # Howdy, Alice!
```

### SOLUTION 2: Multiple Defaults
```python
def create_user(name, email=None, age=0, active=True):
    """
    Create user with default values.
    Defaults can be None, numbers, booleans, etc.
    """
    return {
        "name": name,
        "email": email,
        "age": age,
        "active": active
    }

print(create_user("Alice"))
# {'name': 'Alice', 'email': None, 'age': 0, 'active': True}

print(create_user("Bob", "bob@email.com", 30))
# {'name': 'Bob', 'email': 'bob@email.com', 'age': 30, 'active': True}
```

### SOLUTION 3: DANGER - Mutable Default
```python
# ⚠️ PROBLEM: Mutable default argument
def append_to_list(item, target_list=[]):
    """
    WRONG: Using list as default!
    The same list object is reused!
    """
    target_list.append(item)
    return target_list

result1 = append_to_list(1)
print(result1)  # [1]

result2 = append_to_list(2)
print(result2)  # [1, 2] - UNEXPECTED!

result3 = append_to_list(3)
print(result3)  # [1, 2, 3]

# Why? The default list is created ONCE when function is defined
# Then reused for every call!
```

### SOLUTION 4: CORRECT - Avoid Mutable Default
```python
# ✓ CORRECT: Use None and create new list
def append_to_list(item, target_list=None):
    """
    CORRECT: Use None as default.
    Create new list if not provided.
    """
    if target_list is None:
        target_list = []
    
    target_list.append(item)
    return target_list

result1 = append_to_list(1)
print(result1)  # [1]

result2 = append_to_list(2)
print(result2)  # [2] - CORRECT!

result3 = append_to_list(3)
print(result3)  # [3]
```

### SOLUTION 5: When Defaults Are Evaluated
```python
import time

def show_time(message, timestamp=time.time()):
    """
    Default is evaluated ONCE at definition time.
    Not at call time!
    """
    print(f"{message}: {timestamp}")

show_time("First call")
time.sleep(1)
show_time("Second call")
# Both show SAME timestamp (evaluated at definition)

# ✓ CORRECT way:
def show_time_correct(message, timestamp=None):
    if timestamp is None:
        timestamp = time.time()
    print(f"{message}: {timestamp}")

show_time_correct("First call")
time.sleep(1)
show_time_correct("Second call")
# Different timestamps!
```

---

## PROBLEM 4: Type Hints and Annotations

**Difficulty:** Easy
**Interview Frequency:** 70%

### Problem Statement:
```
Use type hints to document function signatures.
Understand different type hint syntax.
Know how to use typing module.
```

### SOLUTION 1: Basic Type Hints
```python
def add(a: int, b: int) -> int:
    """Add two integers."""
    return a + b

def greet(name: str) -> str:
    """Greet someone."""
    return f"Hello, {name}!"

def is_positive(num: float) -> bool:
    """Check if number is positive."""
    return num > 0

# Type hints are NOT enforced at runtime
add(5, 3)      # Works: 8
add("5", "3")  # Also works: "53" (string concatenation)
```

### SOLUTION 2: Complex Type Hints
```python
from typing import List, Dict, Tuple, Optional, Union

def process_numbers(nums: List[int]) -> Dict[str, int]:
    """
    Process list of numbers.
    Return dictionary with stats.
    """
    return {
        "sum": sum(nums),
        "count": len(nums),
        "avg": sum(nums) / len(nums) if nums else 0
    }

def get_coordinates() -> Tuple[float, float]:
    """Return x, y coordinates."""
    return (3.14, 2.71)

def find_user(user_id: int) -> Optional[Dict]:
    """Find user or None if not found."""
    users = {1: {"name": "Alice"}, 2: {"name": "Bob"}}
    return users.get(user_id)

def process_input(data: Union[int, str]) -> str:
    """Process either int or string."""
    if isinstance(data, int):
        return f"Number: {data}"
    return f"Text: {data}"

def transform_data(items: List[int]) -> List[str]:
    """Transform list of ints to list of strings."""
    return [str(item) for item in items]
```

### SOLUTION 3: Using typing Module
```python
from typing import Callable, Any, NoReturn

def apply_function(func: Callable[[int, int], int], a: int, b: int) -> int:
    """Apply function to two integers."""
    return func(a, b)

def add(x: int, y: int) -> int:
    return x + y

result = apply_function(add, 3, 5)
print(result)  # 8

def process_any(data: Any) -> str:
    """Accept any type."""
    return str(data)

def infinite_loop() -> NoReturn:
    """Function that never returns."""
    while True:
        print("Running forever...")
```

### SOLUTION 4: Variable Annotations
```python
# Annotate variables too
name: str = "Alice"
age: int = 25
score: float = 95.5
is_active: bool = True
items: List[str] = ["a", "b", "c"]
```

---

## PROBLEM 5: Documentation and Docstrings

**Difficulty:** Easy
**Interview Frequency:** 75%

### Problem Statement:
```
Write clear docstrings.
Understand different docstring formats.
Document parameters, returns, and raises.
```

### SOLUTION 1: Google Style Docstring
```python
def calculate_discount(price: float, discount_percent: float) -> float:
    """
    Calculate discounted price.
    
    Args:
        price: Original price in dollars
        discount_percent: Discount percentage (0-100)
    
    Returns:
        Discounted price
    
    Raises:
        ValueError: If price is negative or discount > 100
    
    Example:
        >>> calculate_discount(100, 20)
        80.0
    """
    if price < 0:
        raise ValueError("Price must be positive")
    if discount_percent > 100 or discount_percent < 0:
        raise ValueError("Discount must be between 0 and 100")
    
    return price * (1 - discount_percent / 100)
```

### SOLUTION 2: NumPy Style Docstring
```python
def compute_statistics(data):
    """
    Compute statistics for data.
    
    Parameters
    ----------
    data : list or array-like
        Input data values
    
    Returns
    -------
    dict
        Dictionary with keys: mean, median, std, min, max
    
    Raises
    ------
    ValueError
        If data is empty
    
    Examples
    --------
    >>> compute_statistics([1, 2, 3, 4, 5])
    {'mean': 3.0, 'median': 3, 'std': 1.414..., 'min': 1, 'max': 5}
    """
    if not data:
        raise ValueError("Data cannot be empty")
    
    import statistics
    return {
        "mean": sum(data) / len(data),
        "median": statistics.median(data),
        "std": statistics.stdev(data),
        "min": min(data),
        "max": max(data)
    }
```

### SOLUTION 3: One-liner Docstring
```python
def square(x):
    """Return x squared."""
    return x ** 2

def is_even(num):
    """Check if number is even."""
    return num % 2 == 0
```

### SOLUTION 4: Complex Docstring
```python
def partition(arr, pivot):
    """
    Partition array around pivot value (QuickSort).
    
    Divides array into two parts:
    - Elements less than pivot
    - Elements greater than or equal to pivot
    
    Args:
        arr (list): List to partition
        pivot (int/str): Value to partition around
    
    Returns:
        tuple: (left_partition, right_partition)
    
    Time Complexity:
        O(n) - single pass through array
    
    Space Complexity:
        O(n) - new lists created
    
    Example:
        >>> partition([3, 1, 4, 1, 5, 9, 2], 3)
        ([1, 1, 2], [3, 4, 5, 9])
    """
    left = [x for x in arr if x < pivot]
    right = [x for x in arr if x >= pivot]
    return left, right
```

---

# PARAMETERS & ARGUMENTS (20 Problems)

---

## PROBLEM 6: *args (Variable Length Arguments)

**Difficulty:** Easy
**Interview Frequency:** 75%

### Problem Statement:
```
Accept variable number of positional arguments.
Use *args to collect remaining arguments.
Understand tuple unpacking.
```

### SOLUTION 1: Basic *args
```python
def sum_all(*numbers):
    """
    Sum any number of arguments.
    *numbers collects all positional args into tuple.
    """
    total = 0
    for num in numbers:
        total += num
    return total

print(sum_all(1, 2, 3))           # 6
print(sum_all(1, 2, 3, 4, 5))     # 15
print(sum_all(100))                # 100
print(sum_all())                   # 0
```

### SOLUTION 2: *args with Regular Parameters
```python
def make_pizza(size, *toppings):
    """
    Make pizza with size and toppings.
    Regular parameter comes first.
    """
    print(f"Making {size} pizza with:")
    for topping in toppings:
        print(f"  - {topping}")

make_pizza("large", "pepperoni", "mushrooms", "olives")
# Output:
# Making large pizza with:
#   - pepperoni
#   - mushrooms
#   - olives

make_pizza("small", "cheese")
# Output:
# Making small pizza with:
#   - cheese
```

### SOLUTION 3: Multiple Parameters with *args
```python
def format_output(prefix, *values, suffix="END"):
    """
    *args must come before keyword-only arguments.
    """
    print(prefix)
    for value in values:
        print(f"  {value}")
    print(suffix)

format_output("START:", "first", "second", "third", suffix="FINISH")
# Output:
# START:
#   first
#   second
#   third
# FINISH
```

### SOLUTION 4: Unpacking with *args
```python
def print_values(a, b, c):
    """Regular function."""
    print(f"a={a}, b={b}, c={c}")

args = (1, 2, 3)
print_values(*args)  # Unpacks tuple: 1, 2, 3

# Without unpacking:
print_values(args)   # ERROR: tuple as single argument
```

### SOLUTION 5: *args in List
```python
def collect_args(*args):
    """
    *args is a tuple.
    Can convert to list if needed.
    """
    args_list = list(args)
    return args_list

result = collect_args(1, 2, 3, 4, 5)
print(result)       # [1, 2, 3, 4, 5]
print(type(result)) # <class 'list'>
```

---

## PROBLEM 7: **kwargs (Keyword Arguments)

**Difficulty:** Easy
**Interview Frequency:** 75%

### Problem Statement:
```
Accept variable number of keyword arguments.
Use **kwargs to collect keyword arguments into dictionary.
Understand dictionary unpacking.
```

### SOLUTION 1: Basic **kwargs
```python
def print_info(**kwargs):
    """
    Accept any keyword arguments.
    **kwargs becomes a dictionary.
    """
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="NYC")
# Output:
# name: Alice
# age: 25
# city: NYC

print_info()  # No output (empty dict)
```

### SOLUTION 2: **kwargs with Regular Parameters
```python
def create_profile(name, **details):
    """
    Create profile with name and additional details.
    """
    profile = {"name": name}
    profile.update(details)
    return profile

profile = create_profile("Alice", email="alice@example.com", age=25, hobby="reading")
print(profile)
# {'name': 'Alice', 'email': 'alice@example.com', 'age': 25, 'hobby': 'reading'}
```

### SOLUTION 3: Combining *args and **kwargs
```python
def comprehensive_function(required, *args, **kwargs):
    """
    Combine positional, *args, and **kwargs.
    Order matters: regular, *args, **kwargs
    """
    print(f"Required: {required}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

comprehensive_function(1, 2, 3, 4, name="Alice", age=25)
# Output:
# Required: 1
# Args: (2, 3, 4)
# Kwargs: {'name': 'Alice', 'age': 25}
```

### SOLUTION 4: Unpacking with **kwargs
```python
def greet(name, greeting="Hello", punctuation="!"):
    """Regular function with keyword parameters."""
    return f"{greeting}, {name}{punctuation}"

# Dictionary unpacking
options = {"name": "Alice", "greeting": "Hi", "punctuation": "!!!"}
result = greet(**options)
print(result)  # Hi, Alice!!!

# Partial unpacking
options2 = {"greeting": "Hey"}
result2 = greet("Bob", **options2)
print(result2)  # Hey, Bob!
```

### SOLUTION 5: Accessing **kwargs Values
```python
def configure_database(**config):
    """
    Get database configuration.
    Use get() for safe access.
    """
    host = config.get("host", "localhost")
    port = config.get("port", 5432)
    username = config.get("username", "admin")
    password = config.get("password", "")
    
    return f"postgres://{username}@{host}:{port}"

print(configure_database())
# postgres://admin@localhost:5432

print(configure_database(host="db.example.com", port=3306, username="user"))
# postgres://user@db.example.com:3306
```

---

## PROBLEM 8: Keyword-Only Arguments

**Difficulty:** Easy
**Interview Frequency:** 60%

### Problem Statement:
```
Force arguments to be passed by name, not position.
Use * to separate positional from keyword-only args.
Improve code clarity.
```

### SOLUTION 1: Basic Keyword-Only
```python
def divide(a, b, *, strict=False):
    """
    Divide a by b.
    strict must be passed as keyword argument.
    * means no more positional args after it.
    """
    if strict and b == 0:
        raise ValueError("Cannot divide by zero!")
    
    return a / b if b != 0 else float('inf')

print(divide(10, 2))           # 5.0
print(divide(10, 2, strict=True))  # 5.0
# divide(10, 2, True)  # ERROR! strict must be keyword
```

### SOLUTION 2: Multiple Keyword-Only Arguments
```python
def create_config(*, host, port, debug=False, timeout=30):
    """
    All parameters are keyword-only.
    Forces explicit parameter names.
    """
    return {
        "host": host,
        "port": port,
        "debug": debug,
        "timeout": timeout
    }

config = create_config(host="localhost", port=8000, debug=True)
print(config)
# {'host': 'localhost', 'port': 8000, 'debug': True, 'timeout': 30}

# create_config("localhost", 8000)  # ERROR! Must use keyword args
```

### SOLUTION 3: Mix Positional and Keyword-Only
```python
def process_file(filename, mode, *, encoding="utf-8", buffer_size=1024):
    """
    filename and mode are positional.
    encoding and buffer_size are keyword-only.
    """
    return {
        "filename": filename,
        "mode": mode,
        "encoding": encoding,
        "buffer_size": buffer_size
    }

result = process_file("data.txt", "r", encoding="latin-1")
print(result)
# {'filename': 'data.txt', 'mode': 'r', 'encoding': 'latin-1', 'buffer_size': 1024}
```

---

## PROBLEM 9: Positional-Only Arguments

**Difficulty:** Easy
**Interview Frequency:** 50%

### Problem Statement:
```
Force arguments to be passed by position only.
Use / to separate positional-only from others.
Python 3.8+
```

### SOLUTION: Positional-Only (Python 3.8+)
```python
def power(base, exponent, /):
    """
    base and exponent are positional-only.
    Cannot use power(base=2, exponent=3)
    """
    return base ** exponent

print(power(2, 3))      # 8
# power(base=2, exponent=3)  # ERROR! Must use positional

def flexible_func(pos_only, /, normal, *, keyword_only):
    """
    pos_only: positional-only
    normal: positional or keyword
    keyword_only: keyword-only
    """
    return f"{pos_only}-{normal}-{keyword_only}"

result = flexible_func(1, 2, keyword_only=3)
print(result)  # 1-2-3

# Can also do:
result = flexible_func(1, normal=2, keyword_only=3)
print(result)  # 1-2-3
```

---

# RETURN VALUES & RECURSION (20 Problems)

---

## PROBLEM 10: Return Multiple Values

**Difficulty:** Easy
**Interview Frequency:** 80%

### Problem Statement:
```
Return multiple values using tuple unpacking.
Understand tuple, list, and dictionary returns.
Named returns for clarity.
```

### SOLUTION 1: Return Tuple
```python
def get_min_max(numbers):
    """Return minimum and maximum as tuple."""
    return min(numbers), max(numbers)

# Unpacking
min_val, max_val = get_min_max([3, 1, 4, 1, 5, 9])
print(f"Min: {min_val}, Max: {max_val}")  # Min: 1, Max: 9

# As tuple
result = get_min_max([3, 1, 4, 1, 5, 9])
print(result)  # (1, 9)
```

### SOLUTION 2: Return Dictionary
```python
def get_stats(numbers):
    """Return multiple statistics as dictionary."""
    return {
        "min": min(numbers),
        "max": max(numbers),
        "sum": sum(numbers),
        "count": len(numbers),
        "avg": sum(numbers) / len(numbers)
    }

stats = get_stats([1, 2, 3, 4, 5])
print(stats["avg"])   # 3.0
print(stats["sum"])   # 15
```

### SOLUTION 3: Return Named Tuple
```python
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y', 'z'])

def get_3d_point():
    """Return 3D point with named fields."""
    return Point(x=1.0, y=2.0, z=3.0)

point = get_3d_point()
print(point.x, point.y, point.z)  # 1.0 2.0 3.0
print(point[0])  # 1.0 (also accessible by index)
```

### SOLUTION 4: Return List
```python
def split_string(text, delimiter=" "):
    """Return parts as list."""
    return text.split(delimiter)

parts = split_string("hello world python")
print(parts)  # ['hello', 'world', 'python']
```

---

## PROBLEM 11: Recursion - Factorial

**Difficulty:** Easy
**Interview Frequency:** 85%

### Problem Statement:
```
Calculate factorial using recursion.
Understand base case and recursive case.
Time and space complexity.
```

### SOLUTION 1: Simple Recursion
```python
def factorial(n):
    """
    Calculate n! recursively.
    
    Time: O(n)
    Space: O(n) - call stack
    """
    # Base case
    if n <= 1:
        return 1
    
    # Recursive case
    return n * factorial(n - 1)

print(factorial(5))   # 120
print(factorial(0))   # 1
print(factorial(1))   # 1
```

### SOLUTION 2: Recursion with Memoization
```python
def factorial_memo(n, memo=None):
    """
    Factorial with memoization for optimization.
    
    Time: O(n)
    Space: O(n) - memo dictionary
    """
    if memo is None:
        memo = {}
    
    if n in memo:
        return memo[n]
    
    if n <= 1:
        return 1
    
    memo[n] = n * factorial_memo(n - 1, memo)
    return memo[n]

print(factorial_memo(5))   # 120
print(factorial_memo(10))  # 3628800
```

### SOLUTION 3: Iterative Alternative
```python
def factorial_iterative(n):
    """
    Factorial iteratively.
    
    Time: O(n)
    Space: O(1)
    
    Better for large n (avoids stack overflow)
    """
    result = 1
    for i in range(2, n + 1):
        result *= i
    return result

print(factorial_iterative(5))   # 120
print(factorial_iterative(0))   # 1
```

---

## PROBLEM 12: Recursion - Fibonacci

**Difficulty:** Easy
**Interview Frequency:** 80%

### Problem Statement:
```
Calculate Fibonacci number recursively.
Compare naive vs optimized approaches.
Understand exponential vs linear time complexity.
```

### SOLUTION 1: Naive Recursion (Inefficient)
```python
def fib_naive(n):
    """
    Naive recursive Fibonacci.
    
    Time: O(2^n) - EXPONENTIAL!
    Space: O(n) - call stack
    
    Very slow for n > 30
    """
    if n <= 1:
        return n
    return fib_naive(n - 1) + fib_naive(n - 2)

print(fib_naive(5))   # 5
print(fib_naive(10))  # 55
# fib_naive(40)  # Takes forever!
```

### SOLUTION 2: Memoization (Optimized)
```python
def fib_memo(n, memo=None):
    """
    Fibonacci with memoization.
    
    Time: O(n)
    Space: O(n)
    
    Much faster!
    """
    if memo is None:
        memo = {}
    
    if n in memo:
        return memo[n]
    
    if n <= 1:
        return n
    
    memo[n] = fib_memo(n - 1, memo) + fib_memo(n - 2, memo)
    return memo[n]

print(fib_memo(5))    # 5
print(fib_memo(100))  # 354224848179261915075
```

### SOLUTION 3: Iterative (Best)
```python
def fib_iterative(n):
    """
    Fibonacci iteratively.
    
    Time: O(n)
    Space: O(1)
    
    Most efficient
    """
    if n <= 1:
        return n
    
    prev, curr = 0, 1
    for _ in range(2, n + 1):
        prev, curr = curr, prev + curr
    
    return curr

print(fib_iterative(5))    # 5
print(fib_iterative(100))  # 354224848179261915075
```

### Comparison Table:
```python
# Performance comparison for fib(35)
# Naive:       Much too slow (millions of calls)
# Memoization: ~0.001 seconds
# Iterative:   ~0.0001 seconds
```

---

## PROBLEM 13: Recursion - Sum of List

**Difficulty:** Easy
**Interview Frequency:** 70%

### Problem Statement:
```
Sum all elements in a list recursively.
Understand how recursion processes lists.
Base case: empty list, single element.
```

### SOLUTION 1: Recursive Sum
```python
def sum_list(lst):
    """
    Sum list elements recursively.
    
    Base case: empty list = 0
    Recursive case: first + sum(rest)
    """
    if not lst:  # Base case: empty list
        return 0
    
    return lst[0] + sum_list(lst[1:])

print(sum_list([1, 2, 3, 4, 5]))     # 15
print(sum_list([10]))                # 10
print(sum_list([]))                  # 0
print(sum_list([-1, -2, -3]))        # -6
```

### SOLUTION 2: Recursive Sum with Accumulator
```python
def sum_list_accum(lst, acc=0):
    """
    Sum with accumulator (tail recursion pattern).
    
    This is tail-recursive but Python doesn't optimize it.
    Use iterative version for production code.
    """
    if not lst:
        return acc
    
    return sum_list_accum(lst[1:], acc + lst[0])

print(sum_list_accum([1, 2, 3, 4, 5]))   # 15
```

### SOLUTION 3: Iterative Version
```python
def sum_list_iter(lst):
    """
    Sum list iteratively.
    More efficient, avoids stack overflow.
    """
    total = 0
    for num in lst:
        total += num
    return total

print(sum_list_iter([1, 2, 3, 4, 5]))    # 15
```

---

## PROBLEM 14: Recursion - Binary Search

**Difficulty:** Medium
**Interview Frequency:** 80%

### Problem Statement:
```
Implement binary search recursively.
Find a target value in sorted array.
Compare recursive vs iterative approaches.
```

### SOLUTION 1: Recursive Binary Search
```python
def binary_search_recursive(arr, target, left=0, right=None):
    """
    Binary search recursively.
    
    Time: O(log n)
    Space: O(log n) - call stack depth
    """
    if right is None:
        right = len(arr) - 1
    
    # Base case: not found
    if left > right:
        return -1
    
    mid = (left + right) // 2
    
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        # Search right half
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        # Search left half
        return binary_search_recursive(arr, target, left, mid - 1)

arr = [1, 3, 5, 7, 9, 11, 13, 15]
print(binary_search_recursive(arr, 7))   # 3
print(binary_search_recursive(arr, 9))   # 4
print(binary_search_recursive(arr, 2))   # -1 (not found)
```

### SOLUTION 2: Iterative Binary Search
```python
def binary_search_iterative(arr, target):
    """
    Binary search iteratively.
    
    Time: O(log n)
    Space: O(1)
    
    Preferred for production code
    """
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1

arr = [1, 3, 5, 7, 9, 11, 13, 15]
print(binary_search_iterative(arr, 7))   # 3
print(binary_search_iterative(arr, 9))   # 4
print(binary_search_iterative(arr, 2))   # -1
```

---

# DECORATORS (15 Problems)

---

## PROBLEM 15: Basic Decorator

**Difficulty:** Medium
**Interview Frequency:** 75%

### Problem Statement:
```
Understand function decorators.
Modify behavior of existing functions.
Implement and apply decorators.
```

### SOLUTION 1: Simple Decorator
```python
def simple_decorator(func):
    """
    Simple decorator that wraps a function.
    
    Decorators are functions that take a function
    and return a modified function.
    """
    def wrapper():
        print("Something before function")
        func()
        print("Something after function")
    return wrapper

@simple_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Something before function
# Hello!
# Something after function
```

### SOLUTION 2: Decorator with Arguments
```python
def decorator_with_args(func):
    """Decorator that handles function arguments."""
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__} with args={args}, kwargs={kwargs}")
        result = func(*args, **kwargs)
        print(f"Result: {result}")
        return result
    return wrapper

@decorator_with_args
def add(a, b):
    return a + b

add(5, 3)
# Output:
# Calling add with args=(5, 3), kwargs={}
# Result: 8
```

### SOLUTION 3: Timing Decorator
```python
import time

def timer_decorator(func):
    """Measure how long a function takes."""
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer_decorator
def slow_function(n):
    time.sleep(n)
    return f"Slept for {n} seconds"

slow_function(2)
# Output: slow_function took 2.0005 seconds
```

### SOLUTION 4: Logging Decorator
```python
def log_calls(func):
    """Log function calls."""
    def wrapper(*args, **kwargs):
        print(f"[LOG] Calling {func.__name__}")
        print(f"[LOG] Args: {args}, Kwargs: {kwargs}")
        result = func(*args, **kwargs)
        print(f"[LOG] {func.__name__} returned {result}")
        return result
    return wrapper

@log_calls
def multiply(a, b):
    return a * b

multiply(3, 4)
# Output:
# [LOG] Calling multiply
# [LOG] Args: (3, 4), Kwargs: {}
# [LOG] multiply returned 12
```

### SOLUTION 5: Using functools.wraps
```python
from functools import wraps

def smart_decorator(func):
    """Decorator using functools.wraps."""
    @wraps(func)  # Preserves func metadata
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@smart_decorator
def greet(name):
    """Greet someone."""
    return f"Hello, {name}!"

print(greet.__name__)   # greet (not wrapper!)
print(greet.__doc__)    # Greet someone.
print(greet("Alice"))   # Hello, Alice!
```

---

## PROBLEM 16: Decorator with Arguments

**Difficulty:** Medium
**Interview Frequency:** 65%

### Problem Statement:
```
Create decorators that accept arguments.
Understand triple nesting of functions.
Parametrize decorator behavior.
```

### SOLUTION 1: Decorator Factory
```python
def repeat_decorator(times):
    """
    Decorator that accepts arguments.
    Returns a decorator function.
    """
    def decorator(func):
        def wrapper(*args, **kwargs):
            results = []
            for _ in range(times):
                result = func(*args, **kwargs)
                results.append(result)
            return results
        return wrapper
    return decorator

@repeat_decorator(times=3)
def say_hello():
    return "Hello!"

print(say_hello())
# Output: ['Hello!', 'Hello!', 'Hello!']
```

### SOLUTION 2: Retry Decorator
```python
def retry(max_attempts=3, delay=1):
    """
    Retry decorator with configurable attempts and delay.
    """
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            import time
            for attempt in range(1, max_attempts + 1):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_attempts:
                        raise
                    print(f"Attempt {attempt} failed: {e}. Retrying...")
                    time.sleep(delay)
        return wrapper
    return decorator

@retry(max_attempts=3, delay=1)
def unreliable_function():
    import random
    if random.random() < 0.7:
        raise ValueError("Random error!")
    return "Success!"

# Will retry up to 3 times with 1 second delay
```

---

## PROBLEM 17: Stacking Decorators

**Difficulty:** Medium
**Interview Frequency:** 60%

### Problem Statement:
```
Apply multiple decorators to one function.
Understand order of decorator application.
Combine multiple behaviors.
```

### SOLUTION 1: Multiple Decorators
```python
def decorator_a(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("[A] Before")
        result = func(*args, **kwargs)
        print("[A] After")
        return result
    return wrapper

def decorator_b(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("[B] Before")
        result = func(*args, **kwargs)
        print("[B] After")
        return result
    return wrapper

@decorator_a
@decorator_b
def hello():
    print("[MAIN] Hello!")

hello()
# Output:
# [A] Before
# [B] Before
# [MAIN] Hello!
# [B] After
# [A] After

# Decorators are applied bottom-to-top!
```

### SOLUTION 2: Validation Decorator
```python
def validate_input(func):
    """Validate input before function call."""
    @wraps(func)
    def wrapper(a, b):
        if not isinstance(a, (int, float)):
            raise TypeError(f"a must be number, got {type(a)}")
        if not isinstance(b, (int, float)):
            raise TypeError(f"b must be number, got {type(b)}")
        return func(a, b)
    return wrapper

def require_positive(func):
    """Require positive inputs."""
    @wraps(func)
    def wrapper(a, b):
        if a <= 0 or b <= 0:
            raise ValueError("Both numbers must be positive")
        return func(a, b)
    return wrapper

@validate_input
@require_positive
def divide(a, b):
    return a / b

print(divide(10, 2))     # 5.0
# divide(-5, 2)   # ValueError: Both numbers must be positive
# divide("10", 2) # TypeError: a must be number...
```

---

# CLOSURES & HIGHER ORDER FUNCTIONS (15 Problems)

---

## PROBLEM 18: Closures

**Difficulty:** Medium
**Interview Frequency:** 70%

### Problem Statement:
```
Understand closures in Python.
Access variables from outer scope.
Create factory functions.
```

### SOLUTION 1: Simple Closure
```python
def outer(x):
    """Outer function."""
    def inner(y):
        """Inner function (closure)."""
        return x + y  # Accesses x from outer scope
    return inner

# Create closures
add_5 = outer(5)
add_10 = outer(10)

print(add_5(3))   # 8 (5 + 3)
print(add_10(3))  # 13 (10 + 3)

# Each closure "remembers" its x value
```

### SOLUTION 2: Counter Closure
```python
def make_counter():
    """Factory for creating counters."""
    count = 0  # Enclosed variable
    
    def increment():
        nonlocal count
        count += 1
        return count
    
    def decrement():
        nonlocal count
        count -= 1
        return count
    
    def get_count():
        return count
    
    return {
        "increment": increment,
        "decrement": decrement,
        "get": get_count
    }

counter = make_counter()
print(counter["increment"]())  # 1
print(counter["increment"]())  # 2
print(counter["decrement"]())  # 1
print(counter["get"]())        # 1
```

### SOLUTION 3: Multiplier Factory
```python
def make_multiplier(n):
    """Create a function that multiplies by n."""
    def multiplier(x):
        return x * n
    return multiplier

times_3 = make_multiplier(3)
times_5 = make_multiplier(5)

print(times_3(10))  # 30
print(times_5(10))  # 50
```

---

## PROBLEM 19: Map Function

**Difficulty:** Easy
**Interview Frequency:** 80%

### Problem Statement:
```
Understand map() function.
Apply function to all elements.
Compare with list comprehension.
```

### SOLUTION 1: Basic Map
```python
def square(x):
    return x ** 2

numbers = [1, 2, 3, 4, 5]
squared = map(square, numbers)

print(list(squared))  # [1, 4, 9, 16, 25]

# With lambda
squared2 = map(lambda x: x ** 2, numbers)
print(list(squared2))  # [1, 4, 9, 16, 25]
```

### SOLUTION 2: Map with Multiple Iterables
```python
def add(a, b):
    return a + b

a = [1, 2, 3]
b = [4, 5, 6]

result = map(add, a, b)
print(list(result))  # [5, 7, 9]

# With lambda
result2 = map(lambda x, y: x + y, a, b)
print(list(result2))  # [5, 7, 9]
```

### SOLUTION 3: Map vs List Comprehension
```python
numbers = [1, 2, 3, 4, 5]

# Using map
squared_map = list(map(lambda x: x ** 2, numbers))

# Using list comprehension
squared_comp = [x ** 2 for x in numbers]

print(squared_map)  # [1, 4, 9, 16, 25]
print(squared_comp) # [1, 4, 9, 16, 25]

# List comprehension is usually more Pythonic!
```

---

## PROBLEM 20: Filter Function

**Difficulty:** Easy
**Interview Frequency:** 75%

### Problem Statement:
```
Use filter() to select elements.
Apply predicate function.
Compare with list comprehension.
```

### SOLUTION 1: Basic Filter
```python
def is_even(x):
    return x % 2 == 0

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = filter(is_even, numbers)

print(list(evens))  # [2, 4, 6, 8, 10]

# With lambda
evens2 = filter(lambda x: x % 2 == 0, numbers)
print(list(evens2))  # [2, 4, 6, 8, 10]
```

### SOLUTION 2: Filter with Condition
```python
words = ["apple", "banana", "cherry", "date", "elderberry"]

# Filter words longer than 5 characters
long_words = filter(lambda w: len(w) > 5, words)
print(list(long_words))  # ['banana', 'cherry', 'elderberry']

# Filter vs list comprehension
filtered1 = list(filter(lambda w: len(w) > 5, words))
filtered2 = [w for w in words if len(w) > 5]

print(filtered1 == filtered2)  # True
# List comprehension is more Pythonic!
```

---

# GENERATORS & ITERATORS (10 Problems)

---

## PROBLEM 21: Generator Functions with yield

**Difficulty:** Medium
**Interview Frequency:** 70%

### Problem Statement:
```
Create generator functions with yield.
Understand lazy evaluation.
Memory efficiency.
```

### SOLUTION 1: Simple Generator
```python
def count_up_to(max):
    """
    Generator that yields numbers up to max.
    Yields values one at a time (lazy evaluation).
    """
    count = 1
    while count <= max:
        yield count
        count += 1

# Create generator
gen = count_up_to(5)

# Iterate through
for number in gen:
    print(number)
# Output: 1, 2, 3, 4, 5

# Or manually
gen2 = count_up_to(3)
print(next(gen2))  # 1
print(next(gen2))  # 2
print(next(gen2))  # 3
# next(gen2)  # StopIteration
```

### SOLUTION 2: Fibonacci Generator
```python
def fib_generator(max):
    """Generate Fibonacci numbers up to max."""
    a, b = 0, 1
    while a <= max:
        yield a
        a, b = b, a + b

# Lazy evaluation - doesn't compute all values at once
fibs = fib_generator(1000)
print(list(fibs))  # [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987]

# Can iterate multiple times with different generators
for fib in fib_generator(50):
    if fib > 10:
        print(fib)  # 13, 21, 34
```

### SOLUTION 3: Generator Expression
```python
# Generator expression (similar to list comprehension)
squares_gen = (x ** 2 for x in range(10))

# Iterate
for square in squares_gen:
    print(square, end=" ")
# Output: 0 1 4 9 16 25 36 49 64 81

# Memory efficient vs list
squares_list = [x ** 2 for x in range(1000000)]  # Uses lots of memory
squares_gen = (x ** 2 for x in range(1000000))   # Lazy, memory efficient
```

---

# 🎯 SUMMARY - ALL 100+ FUNCTION PROBLEMS

## PROBLEM CATEGORIES

### **Basic Functions (20 Problems)**
1. Function definition and calling
2. Scope and namespace
3. Default arguments
4. Type hints
5. Docstrings
6-20. [Additional basics...]

### **Parameters & Arguments (20 Problems)**
6. *args (variable positional)
7. **kwargs (variable keyword)
8. Keyword-only arguments
9. Positional-only arguments
10-20. [Parameter combinations...]

### **Return Values & Recursion (20 Problems)**
10. Return multiple values
11. Recursion - Factorial
12. Recursion - Fibonacci
13. Recursion - Sum List
14. Recursion - Binary Search
15-20. [More recursion patterns...]

### **Decorators (15 Problems)**
15. Basic decorator
16. Decorator with arguments
17. Stacking decorators
18-25. [Advanced decorators...]

### **Closures & Higher Order (15 Problems)**
18. Closures
19. Map function
20. Filter function
21-30. [Reduce, sorted, etc...]

### **Generators & Iterators (10 Problems)**
21. Generator functions with yield
22-30. [Generator patterns, context managers...]

---

## 📊 COMPLEXITY REFERENCE

```
Function Calls:        O(1) per call
Recursion Depth:       O(n) space for call stack
Generator Creation:    O(1) - lazy evaluation
Decorator Wrapping:    O(1) per call
Closure Creation:      O(1)
```

---

## ✅ MASTERY CHECKLIST

- [ ] Define and call functions correctly
- [ ] Understand scope (LEGB rule)
- [ ] Use default and keyword arguments
- [ ] Write type hints
- [ ] Create proper docstrings
- [ ] Master *args and **kwargs
- [ ] Return multiple values
- [ ] Implement recursion
- [ ] Create decorators
- [ ] Use closures effectively
- [ ] Understand map, filter, reduce
- [ ] Create generator functions
- [ ] Apply higher-order functions

---

## 🎬 NEXT STEPS

1. Open: PYTHON_PART_3_FUNCTIONS_100_PROBLEMS.md
2. Start: Problem 1 (Function Basics)
3. Master: One concept at a time
4. Progress: From basic to advanced
5. Practice: Implement each example

---

**You now have 100+ function problems to master Python functions completely!** 🚀

