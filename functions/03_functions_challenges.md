# Functions - 100 Coding Challenges

Master Python functions from basics to advanced concepts including lambda, decorators, generators, and more.

---

## 📋 Table of Contents

1. [Basic Functions (Problems 1-20)](#basic-functions)
2. [Function Parameters (Problems 21-35)](#function-parameters)
3. [Lambda Functions (Problems 36-45)](#lambda-functions)
4. [Higher-Order Functions (Problems 46-60)](#higher-order-functions)
5. [Recursion (Problems 61-75)](#recursion)
6. [Decorators (Problems 76-85)](#decorators)
7. [Generators (Problems 86-95)](#generators)
8. [Advanced Concepts (Problems 96-100)](#advanced-concepts)

---

## Basic Functions

### Problem 1: Simple Function Definition
**Difficulty**: Easy

**Problem**: Create a function that greets a person by name.

**Solution**:
```python
def greet(name):
    """Greet a person by name"""
    return f"Hello, {name}!"

# Test
print(greet("Alice"))  # Hello, Alice!
```

---

### Problem 2: Function with Multiple Parameters
**Difficulty**: Easy

**Problem**: Create a function to calculate the area of a rectangle.

**Solution**:
```python
def calculate_area(length, width):
    """Calculate area of rectangle"""
    return length * width

# Test
print(calculate_area(5, 3))  # 15
```

---

### Problem 3: Function with Return Statement
**Difficulty**: Easy

**Problem**: Create a function that returns multiple values.

**Solution**:
```python
def get_min_max(numbers):
    """Return minimum and maximum from a list"""
    return min(numbers), max(numbers)

# Test
nums = [3, 7, 1, 9, 4]
minimum, maximum = get_min_max(nums)
print(f"Min: {minimum}, Max: {maximum}")  # Min: 1, Max: 9
```

---

### Problem 4: Function with Default Parameters
**Difficulty**: Easy

**Problem**: Create a power function with default exponent of 2.

**Solution**:
```python
def power(base, exponent=2):
    """Calculate power with default exponent of 2"""
    return base ** exponent

# Test
print(power(5))      # 25 (5^2)
print(power(5, 3))   # 125 (5^3)
```

---

### Problem 5: Docstring Best Practices
**Difficulty**: Easy

**Problem**: Create a well-documented function.

**Solution**:
```python
def calculate_bmi(weight, height):
    """
    Calculate Body Mass Index (BMI).
    
    Parameters:
    -----------
    weight : float
        Weight in kilograms
    height : float
        Height in meters
    
    Returns:
    --------
    float
        BMI value
    
    Example:
    --------
    >>> calculate_bmi(70, 1.75)
    22.86
    """
    return weight / (height ** 2)

# Test
print(calculate_bmi(70, 1.75))  # 22.857142857142858
print(help(calculate_bmi))
```

---

### Problems 6-20: Basic Function Challenges

**Problem 6**: Check if number is even
**Problem 7**: Calculate factorial
**Problem 8**: Check if string is palindrome
**Problem 9**: Count vowels in string
**Problem 10**: Find sum of digits
**Problem 11**: Convert temperature (C to F)
**Problem 12**: Check if number is prime
**Problem 13**: Find GCD of two numbers
**Problem 14**: Reverse a string
**Problem 15**: Check if year is leap year
**Problem 16**: Calculate compound interest
**Problem 17**: Find nth Fibonacci number
**Problem 18**: Count words in string
**Problem 19**: Check if perfect number
**Problem 20**: Calculate average of numbers

---

## Function Parameters

### Problem 21: *args - Variable Arguments
**Difficulty**: Medium

**Problem**: Create a function that accepts any number of arguments.

**Solution**:
```python
def sum_all(*args):
    """Sum any number of arguments"""
    return sum(args)

# Test
print(sum_all(1, 2, 3))           # 6
print(sum_all(1, 2, 3, 4, 5))     # 15
print(sum_all(10, 20))            # 30
```

---

### Problem 22: **kwargs - Keyword Arguments
**Difficulty**: Medium

**Problem**: Create a function that accepts any keyword arguments.

**Solution**:
```python
def print_info(**kwargs):
    """Print all keyword arguments"""
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Test
print_info(name="Alice", age=30, city="New York")
# name: Alice
# age: 30
# city: New York
```

---

### Problem 23: Combining *args and **kwargs
**Difficulty**: Medium

**Problem**: Create a flexible function with both positional and keyword arguments.

**Solution**:
```python
def flexible_function(required, *args, **kwargs):
    """Demonstrate *args and **kwargs together"""
    print(f"Required: {required}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

# Test
flexible_function(1, 2, 3, 4, name="Alice", age=30)
# Required: 1
# Args: (2, 3, 4)
# Kwargs: {'name': 'Alice', 'age': 30}
```

---

### Problem 24: Keyword-Only Arguments
**Difficulty**: Medium

**Problem**: Force certain parameters to be passed as keywords.

**Solution**:
```python
def create_user(name, *, age, email):
    """Create user with keyword-only parameters"""
    return {
        'name': name,
        'age': age,
        'email': email
    }

# Test
user = create_user("Alice", age=30, email="alice@example.com")
print(user)

# This will raise TypeError:
# user = create_user("Alice", 30, "alice@example.com")
```

---

### Problem 25: Positional-Only Arguments (Python 3.8+)
**Difficulty**: Medium

**Problem**: Force certain parameters to be passed positionally.

**Solution**:
```python
def divide(a, b, /):
    """Divide with positional-only parameters"""
    return a / b

# Test
print(divide(10, 2))  # 5.0

# This will raise TypeError:
# print(divide(a=10, b=2))
```

---

### Problems 26-35: Parameter Challenges

**Problem 26**: Function with mutable default argument (and fix)
**Problem 27**: Unpack list as arguments
**Problem 28**: Unpack dictionary as arguments
**Problem 29**: Type hints with parameters
**Problem 30**: Optional parameters with None
**Problem 31**: Parameter validation
**Problem 32**: Builder pattern with kwargs
**Problem 33**: Forwarding arguments
**Problem 34**: Named parameters only
**Problem 35**: Complex parameter combinations

---

## Lambda Functions

### Problem 36: Basic Lambda
**Difficulty**: Easy

**Problem**: Create simple lambda functions.

**Solution**:
```python
# Square function
square = lambda x: x ** 2
print(square(5))  # 25

# Add two numbers
add = lambda x, y: x + y
print(add(3, 4))  # 7

# Check if even
is_even = lambda x: x % 2 == 0
print(is_even(4))  # True
```

---

### Problem 37: Lambda with Conditional
**Difficulty**: Easy

**Problem**: Use lambda with if-else.

**Solution**:
```python
# Max of two numbers
max_num = lambda a, b: a if a > b else b
print(max_num(10, 20))  # 20

# Absolute value
abs_value = lambda x: x if x >= 0 else -x
print(abs_value(-5))  # 5

# Grade classifier
grade = lambda score: 'Pass' if score >= 50 else 'Fail'
print(grade(65))  # Pass
```

---

### Problem 38: Lambda for Sorting
**Difficulty**: Medium

**Problem**: Use lambda functions for custom sorting.

**Solution**:
```python
# Sort by length
words = ['apple', 'pie', 'banana', 'cat']
sorted_words = sorted(words, key=lambda x: len(x))
print(sorted_words)  # ['pie', 'cat', 'apple', 'banana']

# Sort tuples by second element
pairs = [(1, 5), (3, 2), (2, 8), (4, 1)]
sorted_pairs = sorted(pairs, key=lambda x: x[1])
print(sorted_pairs)  # [(4, 1), (3, 2), (1, 5), (2, 8)]

# Sort dictionaries by value
data = [{'name': 'Alice', 'age': 30},
        {'name': 'Bob', 'age': 25},
        {'name': 'Charlie', 'age': 35}]
sorted_data = sorted(data, key=lambda x: x['age'])
print(sorted_data)
```

---

### Problem 39: Lambda with Map
**Difficulty**: Easy

**Problem**: Use lambda with map function.

**Solution**:
```python
# Square all numbers
numbers = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x**2, numbers))
print(squares)  # [1, 4, 9, 16, 25]

# Convert to uppercase
words = ['hello', 'world', 'python']
upper_words = list(map(lambda x: x.upper(), words))
print(upper_words)  # ['HELLO', 'WORLD', 'PYTHON']
```

---

### Problem 40: Lambda with Filter
**Difficulty**: Easy

**Problem**: Use lambda with filter function.

**Solution**:
```python
# Filter even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4, 6, 8, 10]

# Filter positive numbers
numbers = [-5, -2, 0, 3, 7, -1, 10]
positives = list(filter(lambda x: x > 0, numbers))
print(positives)  # [3, 7, 10]
```

---

### Problems 41-45: Lambda Challenges

**Problem 41**: Lambda with reduce
**Problem 42**: Nested lambdas
**Problem 43**: Lambda in list comprehension
**Problem 44**: Lambda for transformation
**Problem 45**: When NOT to use lambda

---

## Higher-Order Functions

### Problem 46: Function as Argument
**Difficulty**: Medium

**Problem**: Create a function that accepts another function as parameter.

**Solution**:
```python
def apply_operation(numbers, operation):
    """Apply operation to all numbers"""
    return [operation(n) for n in numbers]

# Define operations
def square(x):
    return x ** 2

def double(x):
    return x * 2

# Test
numbers = [1, 2, 3, 4, 5]
print(apply_operation(numbers, square))   # [1, 4, 9, 16, 25]
print(apply_operation(numbers, double))   # [2, 4, 6, 8, 10]
```

---

### Problem 47: Function Returning Function
**Difficulty**: Medium

**Problem**: Create a function that returns another function.

**Solution**:
```python
def create_multiplier(n):
    """Create a multiplier function"""
    def multiplier(x):
        return x * n
    return multiplier

# Test
double = create_multiplier(2)
triple = create_multiplier(3)

print(double(5))  # 10
print(triple(5))  # 15
```

---

### Problem 48: Closure
**Difficulty**: Medium

**Problem**: Demonstrate closure in Python.

**Solution**:
```python
def create_counter():
    """Create a counter using closure"""
    count = 0
    
    def increment():
        nonlocal count
        count += 1
        return count
    
    return increment

# Test
counter1 = create_counter()
counter2 = create_counter()

print(counter1())  # 1
print(counter1())  # 2
print(counter2())  # 1 (separate counter)
```

---

### Problem 49: Map Function
**Difficulty**: Easy

**Problem**: Use map to transform data.

**Solution**:
```python
# Square numbers
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

# Convert strings to integers
str_numbers = ['1', '2', '3', '4', '5']
int_numbers = list(map(int, str_numbers))
print(int_numbers)  # [1, 2, 3, 4, 5]

# Map with multiple iterables
list1 = [1, 2, 3]
list2 = [10, 20, 30]
sums = list(map(lambda x, y: x + y, list1, list2))
print(sums)  # [11, 22, 33]
```

---

### Problem 50: Filter Function
**Difficulty**: Easy

**Problem**: Use filter to select data.

**Solution**:
```python
# Filter even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4, 6, 8, 10]

# Filter strings by length
words = ['apple', 'pie', 'banana', 'cat', 'dog']
long_words = list(filter(lambda x: len(x) > 3, words))
print(long_words)  # ['apple', 'banana']
```

---

### Problem 51: Reduce Function
**Difficulty**: Medium

**Problem**: Use reduce to aggregate data.

**Solution**:
```python
from functools import reduce

# Sum of numbers
numbers = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x + y, numbers)
print(total)  # 15

# Product of numbers
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120

# Find maximum
maximum = reduce(lambda x, y: x if x > y else y, numbers)
print(maximum)  # 5
```

---

### Problems 52-60: Higher-Order Function Challenges

**Problem 52**: Compose functions
**Problem 53**: Partial application
**Problem 54**: Currying
**Problem 55**: Function pipeline
**Problem 56**: Memoization decorator
**Problem 57**: Retry decorator
**Problem 58**: Custom map implementation
**Problem 59**: Custom filter implementation
**Problem 60**: Custom reduce implementation

---

## Recursion

### Problem 61: Factorial with Recursion
**Difficulty**: Easy

**Problem**: Calculate factorial using recursion.

**Solution**:
```python
def factorial(n):
    """Calculate factorial recursively"""
    # Base case
    if n == 0 or n == 1:
        return 1
    # Recursive case
    return n * factorial(n - 1)

# Test
print(factorial(5))  # 120
print(factorial(0))  # 1
```

---

### Problem 62: Fibonacci with Recursion
**Difficulty**: Easy

**Problem**: Generate Fibonacci number using recursion.

**Solution**:
```python
def fibonacci(n):
    """Calculate nth Fibonacci number"""
    # Base cases
    if n <= 0:
        return 0
    elif n == 1:
        return 1
    # Recursive case
    return fibonacci(n-1) + fibonacci(n-2)

# Optimized with memoization
def fibonacci_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 0:
        return 0
    elif n == 1:
        return 1
    memo[n] = fibonacci_memo(n-1, memo) + fibonacci_memo(n-2, memo)
    return memo[n]

# Test
print(fibonacci(6))        # 8
print(fibonacci_memo(50))  # Fast calculation
```

---

### Problem 63: Sum of Digits - Recursive
**Difficulty**: Easy

**Problem**: Calculate sum of digits recursively.

**Solution**:
```python
def sum_digits(n):
    """Sum digits recursively"""
    # Base case
    if n < 10:
        return n
    # Recursive case
    return n % 10 + sum_digits(n // 10)

# Test
print(sum_digits(12345))  # 15
```

---

### Problem 64: Power Function - Recursive
**Difficulty**: Medium

**Problem**: Calculate power recursively with optimization.

**Solution**:
```python
def power(base, exp):
    """Calculate power recursively"""
    # Base cases
    if exp == 0:
        return 1
    if exp == 1:
        return base
    
    # Optimized recursive case
    half = power(base, exp // 2)
    if exp % 2 == 0:
        return half * half
    else:
        return base * half * half

# Test
print(power(2, 10))  # 1024
print(power(3, 5))   # 243
```

---

### Problem 65: Binary Search - Recursive
**Difficulty**: Medium

**Problem**: Implement binary search recursively.

**Solution**:
```python
def binary_search(arr, target, left=0, right=None):
    """Binary search recursive implementation"""
    if right is None:
        right = len(arr) - 1
    
    # Base case: element not found
    if left > right:
        return -1
    
    mid = (left + right) // 2
    
    # Element found
    if arr[mid] == target:
        return mid
    # Search left half
    elif arr[mid] > target:
        return binary_search(arr, target, left, mid - 1)
    # Search right half
    else:
        return binary_search(arr, target, mid + 1, right)

# Test
sorted_arr = [1, 3, 5, 7, 9, 11, 13, 15]
print(binary_search(sorted_arr, 7))   # 3
print(binary_search(sorted_arr, 10))  # -1
```

---

### Problems 66-75: Recursion Challenges

**Problem 66**: Tower of Hanoi
**Problem 67**: GCD using recursion
**Problem 68**: Reverse string recursively
**Problem 69**: Check palindrome recursively
**Problem 70**: Flatten nested list
**Problem 71**: Count occurrences in nested list
**Problem 72**: Tree traversal
**Problem 73**: Generate permutations
**Problem 74**: Generate combinations
**Problem 75**: N-Queens problem

---

## Decorators

### Problem 76: Simple Decorator
**Difficulty**: Medium

**Problem**: Create a basic decorator.

**Solution**:
```python
def my_decorator(func):
    """Simple decorator"""
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

# Test
say_hello()
# Before function call
# Hello!
# After function call
```

---

### Problem 77: Decorator with Arguments
**Difficulty**: Medium

**Problem**: Create decorator that works with function arguments.

**Solution**:
```python
def log_arguments(func):
    """Decorator to log function arguments"""
    def wrapper(*args, **kwargs):
        print(f"Arguments: {args}, {kwargs}")
        result = func(*args, **kwargs)
        print(f"Result: {result}")
        return result
    return wrapper

@log_arguments
def add(a, b):
    return a + b

# Test
add(3, 5)
# Arguments: (3, 5), {}
# Result: 8
```

---

### Problem 78: Timer Decorator
**Difficulty**: Medium

**Problem**: Create a decorator to measure execution time.

**Solution**:
```python
import time
from functools import wraps

def timer(func):
    """Measure execution time"""
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    return "Done"

# Test
slow_function()
# slow_function took 1.0001 seconds
```

---

### Problem 79: Decorator with Parameters
**Difficulty**: Hard

**Problem**: Create a decorator that accepts parameters.

**Solution**:
```python
def repeat(times):
    """Decorator to repeat function execution"""
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

# Test
greet("Alice")
# Hello, Alice!
# Hello, Alice!
# Hello, Alice!
```

---

### Problem 80: Multiple Decorators
**Difficulty**: Medium

**Problem**: Apply multiple decorators to a function.

**Solution**:
```python
def uppercase(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result.upper()
    return wrapper

def exclaim(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result + "!"
    return wrapper

@uppercase
@exclaim
def greet(name):
    return f"hello, {name}"

# Test
print(greet("alice"))  # HELLO, ALICE!
```

---

### Problems 81-85: Decorator Challenges

**Problem 81**: Cache/Memoization decorator
**Problem 82**: Authentication decorator
**Problem 83**: Retry decorator with exponential backoff
**Problem 84**: Rate limiting decorator
**Problem 85**: Class-based decorator

---

## Generators

### Problem 86: Simple Generator
**Difficulty**: Easy

**Problem**: Create a basic generator function.

**Solution**:
```python
def count_up_to(n):
    """Generate numbers from 1 to n"""
    count = 1
    while count <= n:
        yield count
        count += 1

# Test
for num in count_up_to(5):
    print(num)
# 1 2 3 4 5
```

---

### Problem 87: Fibonacci Generator
**Difficulty**: Medium

**Problem**: Generate Fibonacci sequence using generator.

**Solution**:
```python
def fibonacci_generator(n):
    """Generate first n Fibonacci numbers"""
    a, b = 0, 1
    count = 0
    while count < n:
        yield a
        a, b = b, a + b
        count += 1

# Test
for num in fibonacci_generator(10):
    print(num, end=' ')
# 0 1 1 2 3 5 8 13 21 34
```

---

### Problem 88: Generator Expression
**Difficulty**: Easy

**Problem**: Use generator expressions.

**Solution**:
```python
# Generator expression for squares
squares = (x**2 for x in range(10))
print(list(squares))  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Memory efficient for large datasets
large_gen = (x for x in range(1000000))
print(sum(x for x in large_gen if x % 2 == 0))
```

---

### Problem 89: Infinite Generator
**Difficulty**: Medium

**Problem**: Create an infinite sequence generator.

**Solution**:
```python
def infinite_sequence():
    """Generate infinite sequence"""
    num = 0
    while True:
        yield num
        num += 1

# Test (with limit)
gen = infinite_sequence()
for _ in range(5):
    print(next(gen))
# 0 1 2 3 4
```

---

### Problem 90: File Reading Generator
**Difficulty**: Medium

**Problem**: Create a generator for reading large files.

**Solution**:
```python
def read_large_file(file_path):
    """Read file line by line using generator"""
    with open(file_path, 'r') as file:
        for line in file:
            yield line.strip()

# Test
# for line in read_large_file('large_file.txt'):
#     process(line)
```

---

### Problems 91-95: Generator Challenges

**Problem 91**: Prime number generator
**Problem 92**: Generator pipeline
**Problem 93**: Sliding window generator
**Problem 94**: Permutation generator
**Problem 95**: Tree traversal generator

---

## Advanced Concepts

### Problem 96: Function Annotations
**Difficulty**: Medium

**Problem**: Use type hints and annotations.

**Solution**:
```python
def add_numbers(a: int, b: int) -> int:
    """Add two numbers with type hints"""
    return a + b

def process_data(data: list[int]) -> dict[str, float]:
    """Process data with complex type hints"""
    return {
        'sum': sum(data),
        'average': sum(data) / len(data) if data else 0
    }

# Test
result = add_numbers(5, 3)
stats = process_data([1, 2, 3, 4, 5])
print(stats)
```

---

### Problem 97: Function Introspection
**Difficulty**: Medium

**Problem**: Inspect function properties.

**Solution**:
```python
def sample_function(a, b, c=10):
    """Sample function for inspection"""
    return a + b + c

# Introspection
print(sample_function.__name__)       # sample_function
print(sample_function.__doc__)        # Sample function for inspection
print(sample_function.__defaults__)   # (10,)
print(sample_function.__code__.co_varnames)  # ('a', 'b', 'c')

# Using inspect module
import inspect
print(inspect.signature(sample_function))
```

---

### Problem 98: Partial Functions
**Difficulty**: Medium

**Problem**: Create partial functions using functools.

**Solution**:
```python
from functools import partial

def power(base, exponent):
    return base ** exponent

# Create specialized functions
square = partial(power, exponent=2)
cube = partial(power, exponent=3)

# Test
print(square(5))  # 25
print(cube(3))    # 27
```

---

### Problem 99: Function Composition
**Difficulty**: Hard

**Problem**: Compose multiple functions.

**Solution**:
```python
def compose(*functions):
    """Compose functions right to left"""
    def inner(arg):
        result = arg
        for func in reversed(functions):
            result = func(result)
        return result
    return inner

# Helper functions
def add_one(x):
    return x + 1

def double(x):
    return x * 2

def square(x):
    return x ** 2

# Compose
pipeline = compose(square, double, add_one)
print(pipeline(3))  # ((3 + 1) * 2)^2 = 64
```

---

### Problem 100: Context Manager as Function
**Difficulty**: Hard

**Problem**: Create context manager using contextlib.

**Solution**:
```python
from contextlib import contextmanager

@contextmanager
def timer_context(name):
    """Context manager for timing code blocks"""
    import time
    start = time.time()
    print(f"Starting {name}")
    try:
        yield
    finally:
        end = time.time()
        print(f"{name} took {end - start:.4f} seconds")

# Test
with timer_context("My Operation"):
    import time
    time.sleep(1)
    print("Doing work...")
# Starting My Operation
# Doing work...
# My Operation took 1.0001 seconds
```

---

## 🎯 Practice Tips

1. **Start Simple**: Master basic functions before moving to advanced topics
2. **Understand Scope**: Learn local, global, and nonlocal scopes
3. **Write Reusable Code**: Create functions that can be used in multiple contexts
4. **Document Well**: Always write clear docstrings
5. **Test Thoroughly**: Test edge cases and different input types

---

## 📊 Key Concepts Summary

- **Basic Functions**: Definition, parameters, return values
- **Advanced Parameters**: *args, **kwargs, type hints
- **Lambda**: Anonymous functions for simple operations
- **Higher-Order**: Functions as first-class objects
- **Recursion**: Functions calling themselves
- **Decorators**: Modifying function behavior
- **Generators**: Memory-efficient iterators
- **Advanced**: Closures, partial functions, composition

---

**Happy Coding! 🐍**
