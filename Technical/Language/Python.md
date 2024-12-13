## **1. Basics: Variables, Data Types, and Input/Output**

### **Code Example: Hello World, Variables, and Input**
```python
# Print a greeting
print("Hello, Python!")

# Assigning variables
name = "Alice"
age = 25
height = 5.4  # Float

# Input from the user
user_name = input("Enter your name: ")
print(f"Hello, {user_name}! Welcome to Python.")
```

### **Key Concepts**
- Variables store data. Types: `int`, `float`, `str`, `bool`, etc.
- Use `input()` to take input and `print()` for output.
- **String Interpolation**: `f"..."` for formatted strings.

---

## **2. Conditional Statements**

### **Code Example: If/Else**
```python
# A simple grading system
score = int(input("Enter your score: "))

if score >= 90:
    print("Grade: A")
elif score >= 75:
    print("Grade: B")
elif score >= 60:
    print("Grade: C")
else:
    print("Grade: F")
```

### **Key Concepts**
- `if`, `elif`, `else`: Python uses indentation (not braces!) to define blocks.
- Conditions use comparison operators: `==`, `!=`, `<`, `>`, `<=`, `>=`.

---

## **3. Loops**

### **Code Example: For and While**
```python
# For loop example
for i in range(1, 6):  # Loops from 1 to 5
    print(f"Count: {i}")

# While loop example
counter = 5
while counter > 0:
    print(f"Countdown: {counter}")
    counter -= 1
```

### **Key Concepts**
- **`range(start, stop, step)`**: Generates numbers for loops.
- Loops simplify repetitive tasks.

---

## **4. Functions**

### **Code Example: Functions and Return Values**
```python
# Function to calculate factorial
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

print(f"Factorial of 5 is {factorial(5)}")
```

### **Key Concepts**
- Functions organize reusable logic with `def`.
- Recursion: A function calls itself to solve smaller subproblems.

---

## **5. Lists and Dictionaries**

### **Code Example: Lists**
```python
# Create and manipulate a list
fruits = ["apple", "banana", "cherry"]
fruits.append("orange")  # Add an element
print(fruits[1])  # Access by index
print(len(fruits))  # Length of the list
```

### **Code Example: Dictionaries**
```python
# Create and use a dictionary
person = {"name": "Alice", "age": 25, "city": "New York"}
print(person["name"])
person["age"] = 26  # Update a value
print(person)
```

### **Key Concepts**
- **Lists**: Ordered, mutable collections (like arrays).
- **Dictionaries**: Key-value pairs for fast lookups.

---

## **6. Classes and OOP**

### **Code Example: Object-Oriented Programming**
```python
# Define a class
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says Woof!"

# Create an object
my_dog = Dog("Buddy", 3)
print(my_dog.bark())
```

### **Key Concepts**
- Classes model real-world entities.
- `__init__`: Constructor to initialize objects.

---

## **7. File Handling**

### **Code Example: Read/Write Files**
```python
# Write to a file
with open("example.txt", "w") as file:
    file.write("Hello, file handling!")

# Read from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

### **Key Concepts**
- Use `with open()` to handle files. It automatically closes the file.

---

## **8. Error Handling**

### **Code Example: Try/Except**
```python
# Handle errors gracefully
try:
    number = int(input("Enter a number: "))
    print(f"Square: {number ** 2}")
except ValueError:
    print("That's not a valid number!")
```

### **Key Concepts**
- Handle runtime errors using `try` and `except`.

---

## **9. Libraries and Modules**

### **Code Example: Using Built-in and Third-Party Modules**
```python
# Import math module
import math
print(math.sqrt(16))  # Square root

# Install and use third-party library (e.g., requests)
# pip install requests
import requests
response = requests.get("https://api.github.com")
print(response.status_code)
```

### **Key Concepts**
- Standard library provides many utilities.
- Use `pip` to install third-party libraries.

---

## **10. Advanced Topics**

### **List Comprehensions**
```python
# Quick way to create lists
squares = [x ** 2 for x in range(1, 6)]
print(squares)
```

### **Lambda Functions**
```python
# Anonymous functions
add = lambda x, y: x + y
print(add(3, 5))
```

### **Decorators**
```python
# Add functionality to functions
def log(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@log
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
```

---

## **11. Generators**

### **Code Example: Efficient Iteration**
```python
# Generator for Fibonacci numbers
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fibonacci(10):
    print(num)
```

### **Key Concepts**
- **Generators**: Functions that yield values one at a time using `yield`, instead of returning them all at once.
- Saves memory compared to building large lists.

---

## **12. Iterators**

### **Code Example: Custom Iterator**
```python
class Counter:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current > self.end:
            raise StopIteration
        self.current += 1
        return self.current - 1

counter = Counter(1, 5)
for num in counter:
    print(num)
```

### **Key Concepts**
- Define `__iter__()` and `__next__()` to make objects iterable.
- Use `StopIteration` to end iteration.

---

## **13. Context Managers**

### **Code Example: Custom Context Manager**
```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        self.file.close()

with FileManager("example.txt", "w") as file:
    file.write("Hello, Context Manager!")
```

### **Key Concepts**
- Automate resource management with `__enter__` and `__exit__`.
- Useful for files, database connections, etc.

---

## **14. Python’s `collections` Module**

### **Code Example: Defaultdict and Counter**
```python
from collections import defaultdict, Counter

# defaultdict example
dd = defaultdict(int)
dd["a"] += 1
print(dd)  # Output: defaultdict(<class 'int'>, {'a': 1})

# Counter example
words = ["apple", "banana", "apple"]
count = Counter(words)
print(count)  # Output: Counter({'apple': 2, 'banana': 1})
```

### **Key Features**
- `defaultdict`: Provides default values for missing keys.
- `Counter`: Counts occurrences of items in a collection.

---

## **15. Functional Programming**

### **Code Example: Map, Filter, Reduce**
```python
from functools import reduce

# Map: Apply function to each element
squares = list(map(lambda x: x**2, range(5)))
print(squares)  # Output: [0, 1, 4, 9, 16]

# Filter: Keep elements meeting a condition
evens = list(filter(lambda x: x % 2 == 0, range(5)))
print(evens)  # Output: [0, 2, 4]

# Reduce: Aggregate values
product = reduce(lambda x, y: x * y, range(1, 5))
print(product)  # Output: 24
```

### **Key Concepts**
- Functional programming enables concise, expressive operations.

---

## **16. Python’s `itertools` Module**

### **Code Example: Infinite Iterators**
```python
import itertools

# Infinite iterator
counter = itertools.count(start=1, step=2)
for num in itertools.islice(counter, 5):
    print(num)  # Output: 1, 3, 5, 7, 9
```

### **Key Features**
- `count()`, `cycle()`, and `repeat()` for infinite iterators.
- `combinations()` and `permutations()` for advanced combinatorics.

---

## **17. Regular Expressions**

### **Code Example: Matching Patterns**
```python
import re

text = "My phone number is 123-456-7890."
pattern = r"\d{3}-\d{3}-\d{4}"

match = re.search(pattern, text)
if match:
    print(match.group())  # Output: 123-456-7890
```

### **Key Concepts**
- `re.search()`: Finds the first match.
- `re.findall()`: Returns all matches as a list.

---

## **18. Python’s `os` and `sys` Modules**

### **Code Example: File and Directory Operations**
```python
import os

# List files in the current directory
print(os.listdir())

# Create a new directory
os.mkdir("new_folder")
```

### **Code Example: Command-Line Arguments**
```python
import sys

# Print command-line arguments
print(sys.argv)  # Output: List of arguments passed to the script
```

---

## **19. Python’s `json` Module**

### **Code Example: JSON Serialization**
```python
import json

# Serialize
data = {"name": "Alice", "age": 25}
json_data = json.dumps(data)
print(json_data)  # Output: '{"name": "Alice", "age": 25}'

# Deserialize
parsed_data = json.loads(json_data)
print(parsed_data["name"])  # Output: Alice
```

### **Key Concepts**
- Use `json.dumps()` to convert Python objects to JSON.
- Use `json.loads()` to parse JSON strings.

---

## **20. Asynchronous Programming with `asyncio`**

### **Code Example: Async Functions**
```python
import asyncio

async def greet():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(greet())
```

### **Key Concepts**
- Use `async def` to define asynchronous functions.
- Use `await` to pause execution.

---

## **21. Python’s `dataclasses` Module**

### **Code Example: Simplified Data Models**
```python
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int

person = Person("Alice", 25)
print(person)  # Output: Person(name='Alice', age=25)
```

### **Key Concepts**
- Reduces boilerplate for creating classes.
- Supports immutability with `frozen=True`.

---

## **22. Best Practices**

1. **Use Type Annotations**:
   ```python
   def add(a: int, b: int) -> int:
       return a + b
   ```

2. **Follow PEP 8**:
   - Use meaningful variable names.
   - Limit lines to 79 characters.

3. **Write Unit Tests**:
   ```python
   import unittest

   class TestMath(unittest.TestCase):
       def test_add(self):
           self.assertEqual(add(2, 3), 5)
   ```

4. **Handle Exceptions Gracefully**:
   - Avoid bare `except`.

---

### **Resources**
1. [Python Official Docs](https://docs.python.org/3/)
2. [Real Python](https://realpython.com/)
3. [PEP 8 Style Guide](https://www.python.org/dev/peps/pep-0008/)

