# Object-Oriented Programming - 100 Coding Challenges

Master Python OOP concepts from basic classes to advanced design patterns.

---

## 📋 Table of Contents

1. [Classes and Objects (Problems 1-15)](#classes-and-objects)
2. [Attributes and Methods (Problems 16-30)](#attributes-and-methods)
3. [Inheritance (Problems 31-45)](#inheritance)
4. [Polymorphism (Problems 46-55)](#polymorphism)
5. [Encapsulation (Problems 56-65)](#encapsulation)
6. [Magic Methods (Problems 66-80)](#magic-methods)
7. [Class Methods and Static Methods (Problems 81-90)](#class-and-static-methods)
8. [Advanced OOP (Problems 91-100)](#advanced-oop)

---

## Classes and Objects

### Problem 1: Basic Class
**Difficulty**: Easy

**Problem**: Create a simple class and instantiate objects.

**Solution**:
```python
class Person:
    """A simple Person class"""
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"Hi, I'm {self.name} and I'm {self.age} years old"

# Test
person1 = Person("Alice", 30)
person2 = Person("Bob", 25)

print(person1.introduce())  # Hi, I'm Alice and I'm 30 years old
print(person2.introduce())  # Hi, I'm Bob and I'm 25 years old
```

---

### Problem 2: Bank Account Class
**Difficulty**: Easy

**Problem**: Create a BankAccount class with deposit and withdraw methods.

**Solution**:
```python
class BankAccount:
    """Bank account with basic operations"""
    
    def __init__(self, account_number, balance=0):
        self.account_number = account_number
        self.balance = balance
    
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            return f"Deposited ${amount}. New balance: ${self.balance}"
        return "Invalid amount"
    
    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            return f"Withdrew ${amount}. New balance: ${self.balance}"
        return "Invalid amount or insufficient funds"
    
    def get_balance(self):
        return f"Current balance: ${self.balance}"

# Test
account = BankAccount("12345", 1000)
print(account.deposit(500))      # Deposited $500. New balance: $1500
print(account.withdraw(200))     # Withdrew $200. New balance: $1300
print(account.get_balance())     # Current balance: $1300
```

---

### Problem 3: Rectangle Class
**Difficulty**: Easy

**Problem**: Create a Rectangle class with area and perimeter methods.

**Solution**:
```python
class Rectangle:
    """Rectangle with area and perimeter calculations"""
    
    def __init__(self, length, width):
        self.length = length
        self.width = width
    
    def area(self):
        return self.length * self.width
    
    def perimeter(self):
        return 2 * (self.length + self.width)
    
    def is_square(self):
        return self.length == self.width

# Test
rect = Rectangle(10, 5)
print(f"Area: {rect.area()}")           # Area: 50
print(f"Perimeter: {rect.perimeter()}") # Perimeter: 30
print(f"Is square: {rect.is_square()}") # Is square: False
```

---

### Problem 4: Student Class
**Difficulty**: Easy

**Problem**: Create a Student class with grade calculation.

**Solution**:
```python
class Student:
    """Student with grade management"""
    
    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        self.grades = []
    
    def add_grade(self, grade):
        if 0 <= grade <= 100:
            self.grades.append(grade)
        else:
            print("Invalid grade. Must be between 0 and 100")
    
    def get_average(self):
        if self.grades:
            return sum(self.grades) / len(self.grades)
        return 0
    
    def get_letter_grade(self):
        avg = self.get_average()
        if avg >= 90:
            return 'A'
        elif avg >= 80:
            return 'B'
        elif avg >= 70:
            return 'C'
        elif avg >= 60:
            return 'D'
        else:
            return 'F'

# Test
student = Student("Alice", "S12345")
student.add_grade(85)
student.add_grade(90)
student.add_grade(78)
print(f"Average: {student.get_average():.2f}")        # Average: 84.33
print(f"Letter Grade: {student.get_letter_grade()}")  # Letter Grade: B
```

---

### Problem 5: Counter Class
**Difficulty**: Easy

**Problem**: Create a Counter class that can increment and decrement.

**Solution**:
```python
class Counter:
    """Simple counter class"""
    
    def __init__(self, initial_value=0):
        self.value = initial_value
    
    def increment(self, amount=1):
        self.value += amount
    
    def decrement(self, amount=1):
        self.value -= amount
    
    def reset(self):
        self.value = 0
    
    def get_value(self):
        return self.value

# Test
counter = Counter()
counter.increment(5)
counter.increment()
print(counter.get_value())  # 6
counter.decrement(2)
print(counter.get_value())  # 4
counter.reset()
print(counter.get_value())  # 0
```

---

### Problems 6-15: Basic Class Challenges

**Problem 6**: Book class with title, author, ISBN
**Problem 7**: Temperature converter class
**Problem 8**: Shopping cart class
**Problem 9**: Time class (hours, minutes, seconds)
**Problem 10**: Date class with validation
**Problem 11**: Circle class with radius
**Problem 12**: Employee class with salary
**Problem 13**: Car class with make, model, year
**Problem 14**: Library management class
**Problem 15**: Point class in 2D space

---

## Attributes and Methods

### Problem 16: Class vs Instance Variables
**Difficulty**: Medium

**Problem**: Demonstrate class and instance variables.

**Solution**:
```python
class Dog:
    """Dog class with class and instance variables"""
    
    # Class variable
    species = "Canis familiaris"
    total_dogs = 0
    
    def __init__(self, name, age):
        # Instance variables
        self.name = name
        self.age = age
        Dog.total_dogs += 1
    
    def description(self):
        return f"{self.name} is {self.age} years old"
    
    @classmethod
    def get_total_dogs(cls):
        return f"Total dogs: {cls.total_dogs}"

# Test
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

print(dog1.species)              # Canis familiaris
print(Dog.species)               # Canis familiaris
print(Dog.get_total_dogs())      # Total dogs: 2
```

---

### Problem 17: Property Decorator
**Difficulty**: Medium

**Problem**: Use @property for getters and setters.

**Solution**:
```python
class Temperature:
    """Temperature class with property decorators"""
    
    def __init__(self, celsius=0):
        self._celsius = celsius
    
    @property
    def celsius(self):
        return self._celsius
    
    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self._celsius = value
    
    @property
    def fahrenheit(self):
        return (self._celsius * 9/5) + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9

# Test
temp = Temperature(25)
print(f"{temp.celsius}°C = {temp.fahrenheit}°F")  # 25°C = 77.0°F
temp.fahrenheit = 98.6
print(f"{temp.celsius:.1f}°C")  # 37.0°C
```

---

### Problem 18: Instance Method, Class Method, Static Method
**Difficulty**: Medium

**Problem**: Demonstrate all three method types.

**Solution**:
```python
class MyClass:
    """Demonstration of different method types"""
    
    class_variable = 0
    
    def __init__(self, value):
        self.instance_variable = value
    
    # Instance method
    def instance_method(self):
        return f"Instance: {self.instance_variable}"
    
    # Class method
    @classmethod
    def class_method(cls):
        return f"Class: {cls.class_variable}"
    
    # Static method
    @staticmethod
    def static_method(x, y):
        return x + y

# Test
obj = MyClass(10)
print(obj.instance_method())              # Instance: 10
print(MyClass.class_method())             # Class: 0
print(MyClass.static_method(5, 3))        # 8
```

---

### Problem 19: Computed Properties
**Difficulty**: Medium

**Problem**: Create properties that compute values.

**Solution**:
```python
class Person:
    """Person with computed properties"""
    
    def __init__(self, first_name, last_name, birth_year):
        self.first_name = first_name
        self.last_name = last_name
        self.birth_year = birth_year
    
    @property
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
    
    @property
    def age(self):
        from datetime import datetime
        current_year = datetime.now().year
        return current_year - self.birth_year

# Test
person = Person("John", "Doe", 1990)
print(person.full_name)  # John Doe
print(person.age)        # Calculated based on current year
```

---

### Problem 20: Private Attributes
**Difficulty**: Medium

**Problem**: Implement private attributes with name mangling.

**Solution**:
```python
class BankAccount:
    """Bank account with private balance"""
    
    def __init__(self, initial_balance):
        self.__balance = initial_balance  # Private attribute
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return True
        return False
    
    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False
    
    @property
    def balance(self):
        return self.__balance

# Test
account = BankAccount(1000)
account.deposit(500)
print(account.balance)  # 1500
# print(account.__balance)  # AttributeError
```

---

### Problems 21-30: Attributes and Methods Challenges

**Problem 21**: Lazy property evaluation
**Problem 22**: Descriptor protocol
**Problem 23**: Method chaining
**Problem 24**: Singleton pattern
**Problem 25**: Factory method
**Problem 26**: Builder pattern
**Problem 27**: Computed read-only properties
**Problem 28**: Cached properties
**Problem 29**: Method overloading simulation
**Problem 30**: Dynamic attribute access

---

## Inheritance

### Problem 31: Single Inheritance
**Difficulty**: Easy

**Problem**: Create a base class and inherit from it.

**Solution**:
```python
class Animal:
    """Base Animal class"""
    
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        pass

class Dog(Animal):
    """Dog inherits from Animal"""
    
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    """Cat inherits from Animal"""
    
    def speak(self):
        return f"{self.name} says Meow!"

# Test
dog = Dog("Buddy")
cat = Cat("Whiskers")
print(dog.speak())  # Buddy says Woof!
print(cat.speak())  # Whiskers says Meow!
```

---

### Problem 32: Super() Function
**Difficulty**: Medium

**Problem**: Use super() to extend parent class methods.

**Solution**:
```python
class Vehicle:
    """Base Vehicle class"""
    
    def __init__(self, make, model):
        self.make = make
        self.model = model
    
    def info(self):
        return f"{self.make} {self.model}"

class Car(Vehicle):
    """Car extends Vehicle"""
    
    def __init__(self, make, model, num_doors):
        super().__init__(make, model)
        self.num_doors = num_doors
    
    def info(self):
        base_info = super().info()
        return f"{base_info}, {self.num_doors} doors"

# Test
car = Car("Toyota", "Camry", 4)
print(car.info())  # Toyota Camry, 4 doors
```

---

### Problem 33: Multiple Inheritance
**Difficulty**: Hard

**Problem**: Demonstrate multiple inheritance and MRO.

**Solution**:
```python
class Flyer:
    """Can fly"""
    def fly(self):
        return "I can fly!"

class Swimmer:
    """Can swim"""
    def swim(self):
        return "I can swim!"

class Duck(Flyer, Swimmer):
    """Duck can both fly and swim"""
    def quack(self):
        return "Quack!"

# Test
duck = Duck()
print(duck.fly())    # I can fly!
print(duck.swim())   # I can swim!
print(duck.quack())  # Quack!

# Check Method Resolution Order
print(Duck.__mro__)
```

---

### Problem 34: Abstract Base Class
**Difficulty**: Medium

**Problem**: Create an abstract base class.

**Solution**:
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    """Abstract Shape class"""
    
    @abstractmethod
    def area(self):
        pass
    
    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    """Concrete Rectangle class"""
    
    def __init__(self, length, width):
        self.length = length
        self.width = width
    
    def area(self):
        return self.length * self.width
    
    def perimeter(self):
        return 2 * (self.length + self.width)

# Test
# shape = Shape()  # TypeError: Can't instantiate abstract class
rect = Rectangle(10, 5)
print(f"Area: {rect.area()}")           # Area: 50
print(f"Perimeter: {rect.perimeter()}") # Perimeter: 30
```

---

### Problem 35: Method Overriding
**Difficulty**: Easy

**Problem**: Override parent class methods.

**Solution**:
```python
class Employee:
    """Base Employee class"""
    
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
    
    def get_bonus(self):
        return self.salary * 0.1

class Manager(Employee):
    """Manager with different bonus calculation"""
    
    def get_bonus(self):
        return self.salary * 0.2

class Executive(Manager):
    """Executive with even higher bonus"""
    
    def get_bonus(self):
        return self.salary * 0.3

# Test
emp = Employee("John", 50000)
mgr = Manager("Alice", 80000)
exec = Executive("Bob", 120000)

print(f"Employee bonus: ${emp.get_bonus()}")   # $5000.0
print(f"Manager bonus: ${mgr.get_bonus()}")    # $16000.0
print(f"Executive bonus: ${exec.get_bonus()}")  # $36000.0
```

---

### Problems 36-45: Inheritance Challenges

**Problem 36**: Diamond problem resolution
**Problem 37**: Mixins implementation
**Problem 38**: Interface implementation
**Problem 39**: Template method pattern
**Problem 40**: Strategy pattern with inheritance
**Problem 41**: Polymorphic collections
**Problem 42**: Type checking with isinstance
**Problem 43**: Composition vs inheritance
**Problem 44**: Protected members
**Problem 45**: Cooperative multiple inheritance

---

## Polymorphism

### Problem 46: Polymorphic Methods
**Difficulty**: Medium

**Problem**: Demonstrate polymorphism with different classes.

**Solution**:
```python
class Shape:
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14159 * self.radius ** 2

class Square(Shape):
    def __init__(self, side):
        self.side = side
    
    def area(self):
        return self.side ** 2

class Triangle(Shape):
    def __init__(self, base, height):
        self.base = base
        self.height = height
    
    def area(self):
        return 0.5 * self.base * self.height

# Polymorphic behavior
def print_area(shape):
    print(f"Area: {shape.area()}")

# Test
shapes = [Circle(5), Square(4), Triangle(3, 6)]
for shape in shapes:
    print_area(shape)
```

---

### Problem 47: Duck Typing
**Difficulty**: Medium

**Problem**: Demonstrate duck typing in Python.

**Solution**:
```python
class Duck:
    def quack(self):
        return "Quack quack!"
    
    def fly(self):
        return "Flap flap!"

class Person:
    def quack(self):
        return "I'm imitating a duck!"
    
    def fly(self):
        return "I wish I could fly!"

def make_it_quack(duck):
    """If it quacks like a duck..."""
    print(duck.quack())
    print(duck.fly())

# Test - both work!
duck = Duck()
person = Person()

make_it_quack(duck)
make_it_quack(person)
```

---

### Problems 48-55: Polymorphism Challenges

**Problem 48**: Operator overloading
**Problem 49**: Protocol-based polymorphism
**Problem 50**: Generic functions
**Problem 51**: Type hints with Union
**Problem 52**: Covariance and contravariance
**Problem 53**: Liskov substitution principle
**Problem 54**: Interface segregation
**Problem 55**: Dependency injection

---

## Encapsulation

### Problem 56: Public, Protected, Private
**Difficulty**: Medium

**Problem**: Demonstrate different access levels.

**Solution**:
```python
class MyClass:
    def __init__(self):
        self.public = "Public attribute"
        self._protected = "Protected attribute"
        self.__private = "Private attribute"
    
    def get_private(self):
        return self.__private
    
    def _protected_method(self):
        return "Protected method"
    
    def __private_method(self):
        return "Private method"
    
    def access_private_method(self):
        return self.__private_method()

# Test
obj = MyClass()
print(obj.public)                    # Works
print(obj._protected)                # Works (convention only)
# print(obj.__private)               # AttributeError
print(obj.get_private())             # Private attribute
print(obj._protected_method())       # Works (convention only)
print(obj.access_private_method())   # Private method
```

---

### Problems 57-65: Encapsulation Challenges

**Problem 57**: Getters and setters
**Problem 58**: Read-only properties
**Problem 59**: Immutable classes
**Problem 60**: Information hiding
**Problem 61**: Access control with descriptors
**Problem 62**: Protecting class invariants
**Problem 63**: Validation in setters
**Problem 64**: Lazy initialization
**Problem 65**: Facade pattern

---

## Magic Methods

### Problem 66: String Representation
**Difficulty**: Easy

**Problem**: Implement __str__ and __repr__.

**Solution**:
```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
    
    def __str__(self):
        return f"{self.title} by {self.author}"
    
    def __repr__(self):
        return f"Book('{self.title}', '{self.author}', {self.year})"

# Test
book = Book("1984", "George Orwell", 1949)
print(str(book))   # 1984 by George Orwell
print(repr(book))  # Book('1984', 'George Orwell', 1949)
```

---

### Problem 67: Arithmetic Operators
**Difficulty**: Medium

**Problem**: Implement arithmetic magic methods.

**Solution**:
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)
    
    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)
    
    def __str__(self):
        return f"Vector({self.x}, {self.y})"

# Test
v1 = Vector(2, 3)
v2 = Vector(4, 1)
v3 = v1 + v2
v4 = v1 * 3
print(v3)  # Vector(6, 4)
print(v4)  # Vector(6, 9)
```

---

### Problem 68: Comparison Operators
**Difficulty**: Medium

**Problem**: Implement comparison magic methods.

**Solution**:
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __eq__(self, other):
        return self.age == other.age
    
    def __lt__(self, other):
        return self.age < other.age
    
    def __le__(self, other):
        return self.age <= other.age
    
    def __gt__(self, other):
        return self.age > other.age
    
    def __ge__(self, other):
        return self.age >= other.age

# Test
p1 = Person("Alice", 30)
p2 = Person("Bob", 25)
print(p1 > p2)   # True
print(p1 == p2)  # False
```

---

### Problems 69-80: Magic Methods Challenges

**Problem 69**: __len__ and __getitem__
**Problem 70**: __setitem__ and __delitem__
**Problem 71**: __iter__ and __next__
**Problem 72**: __contains__
**Problem 73**: __call__
**Problem 74**: __enter__ and __exit__ (context manager)
**Problem 75**: __hash__
**Problem 76**: __format__
**Problem 77**: __bool__
**Problem 78**: __del__ (destructor)
**Problem 79**: __getattr__ and __setattr__
**Problem 80**: __new__ vs __init__

---

## Class and Static Methods

### Problem 81: Alternative Constructors
**Difficulty**: Medium

**Problem**: Create alternative constructors using @classmethod.

**Solution**:
```python
from datetime import datetime

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    @classmethod
    def from_birth_year(cls, name, birth_year):
        age = datetime.now().year - birth_year
        return cls(name, age)
    
    @classmethod
    def from_string(cls, person_str):
        name, age = person_str.split(',')
        return cls(name, int(age))

# Test
p1 = Person("Alice", 30)
p2 = Person.from_birth_year("Bob", 1990)
p3 = Person.from_string("Charlie,25")
```

---

### Problems 82-90: Class and Static Methods Challenges

**Problem 82**: Utility methods with @staticmethod
**Problem 83**: Factory pattern
**Problem 84**: Registry pattern
**Problem 85**: Counting instances
**Problem 86**: Configuration management
**Problem 87**: Caching with class methods
**Problem 88**: Abstract class methods
**Problem 89**: Enum with class methods
**Problem 90**: Method decoration order

---

## Advanced OOP

### Problem 91: Metaclass
**Difficulty**: Hard

**Problem**: Create a simple metaclass.

**Solution**:
```python
class SingletonMeta(type):
    """Metaclass for Singleton pattern"""
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=SingletonMeta):
    def __init__(self):
        self.connection = "Connected"

# Test
db1 = Database()
db2 = Database()
print(db1 is db2)  # True - same instance
```

---

### Problems 92-100: Advanced OOP Challenges

**Problem 92**: Descriptor protocol
**Problem 93**: Context managers
**Problem 94**: Custom iterators
**Problem 95**: Observer pattern
**Problem 96**: Decorator pattern
**Problem 97**: Chain of responsibility
**Problem 98**: Command pattern
**Problem 99**: State pattern
**Problem 100**: MVC pattern implementation

---

## 🎯 OOP Design Principles

### SOLID Principles:
1. **Single Responsibility**: One class, one responsibility
2. **Open/Closed**: Open for extension, closed for modification
3. **Liskov Substitution**: Subtypes must be substitutable
4. **Interface Segregation**: Many specific interfaces > one general
5. **Dependency Inversion**: Depend on abstractions, not concretions

---

**Happy Coding! 🐍**
