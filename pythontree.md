# Python Documentation Tree

## Overview
- **What is Python?**
  - A high-level, interpreted programming language known for its readability and versatility.
- **Key Concepts**
  - Syntax and Structure
  - Data Types and Variables
  - Control Flow

## Basic

### Variables and Data Types
- **Defining Variables**
  - **Scenario**: Create and initialize variables with different data types
  - **Sample Code**:
    ```python
    # Integer
    age = 25
    # Float
    height = 5.9
    # String
    name = "Alice"
    # Boolean
    is_student = True
    ```
  - **Sample Output**:
    ```python
    print(age)        # 25
    print(height)     # 5.9
    print(name)       # Alice
    print(is_student) # True
    ```

### Basic Operations
- **Arithmetic Operations**
  - **Scenario**: Perform basic arithmetic calculations
  - **Sample Code**:
    ```python
    a = 10
    b = 5
    sum_result = a + b
    product_result = a * b
    ```
  - **Sample Output**:
    ```python
    print(sum_result)      # 15
    print(product_result)  # 50
    ```

### Control Flow
- **Conditional Statements**
  - **Scenario**: Implement basic if-else conditions
  - **Sample Code**:
    ```python
    number = 10
    if number > 0:
        result = "Positive"
    else:
        result = "Non-positive"
    ```
  - **Sample Output**:
    ```python
    print(result)  # Positive
    ```

### Functions
- **Defining and Calling Functions**
  - **Scenario**: Define and call a simple function
  - **Sample Code**:
    ```python
    def greet(name):
        return f"Hello, {name}!"

    message = greet("Alice")
    ```
  - **Sample Output**:
    ```python
    print(message)  # Hello, Alice!
    ```

## Moderate

### Lists and Dictionaries
- **Working with Lists**
  - **Scenario**: Perform list operations like adding and accessing elements
  - **Sample Code**:
    ```python
    fruits = ["apple", "banana", "cherry"]
    fruits.append("date")
    first_fruit = fruits[0]
    ```
  - **Sample Output**:
    ```python
    print(fruits)       # ['apple', 'banana', 'cherry', 'date']
    print(first_fruit)  # apple
    ```

- **Working with Dictionaries**
  - **Scenario**: Use dictionaries to store and retrieve key-value pairs
  - **Sample Code**:
    ```python
    student = {"name": "Alice", "age": 21}
    student["major"] = "Computer Science"
    ```
  - **Sample Output**:
    ```python
    print(student)  # {'name': 'Alice', 'age': 21, 'major': 'Computer Science'}
    ```

### File I/O
- **Reading and Writing Files**
  - **Scenario**: Read from and write to a file
  - **Sample Code**:
    ```python
    # Write to a file
    with open("example.txt", "w") as file:
        file.write("Hello, world!")

    # Read from a file
    with open("example.txt", "r") as file:
        content = file.read()
    ```
  - **Sample Output**:
    ```python
    print(content)  # Hello, world!
    ```

### Error Handling
- **Try-Except Blocks**
  - **Scenario**: Handle exceptions using try-except
  - **Sample Code**:
    ```python
    try:
        result = 10 / 0
    except ZeroDivisionError:
        result = "Cannot divide by zero"
    ```
  - **Sample Output**:
    ```python
    print(result)  # Cannot divide by zero
    ```

## Advanced

### Object-Oriented Programming
- **Creating Classes and Objects**
  - **Scenario**: Define and use classes and objects
  - **Sample Code**:
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age

        def greet(self):
            return f"Hello, my name is {self.name}."

    person = Person("Alice", 30)
    ```
  - **Sample Output**:
    ```python
    print(person.greet())  # Hello, my name is Alice.
    ```

### Decorators
- **Using Decorators**
  - **Scenario**: Apply a decorator to modify function behavior
  - **Sample Code**:
    ```python
    def decorator_function(func):
        def wrapper():
            print("Something is happening before the function.")
            func()
            print("Something is happening after the function.")
        return wrapper

    @decorator_function
    def say_hello():
        print("Hello!")

    say_hello()
    ```
  - **Sample Output**:
    ```python
    Something is happening before the function.
    Hello!
    Something is happening after the function.
    ```

### Generators
- **Using Generators**
  - **Scenario**: Create a generator to yield a sequence of values
  - **Sample Code**:
    ```python
    def count_up_to(max):
        count = 1
        while count <= max:
            yield count
            count += 1

    counter = count_up_to(5)
    ```
  - **Sample Output**:
    ```python
    print(list(counter))  # [1, 2, 3, 4, 5]
    ```

### Context Managers
- **Creating and Using Context Managers**
  - **Scenario**: Implement a context manager for resource management
  - **Sample Code**:
    ```python
    class FileManager:
        def __init__(self, filename):
            self.filename = filename

        def __enter__(self):
            self.file = open(self.filename, 'w')
            return self.file

        def __exit__(self, exc_type, exc_value, traceback):
            self.file.close()

    with FileManager("test.txt") as f:
        f.write("Using context managers!")
    ```
  - **Sample Output**:
    ```python
    # No direct output; verify file content with 'cat test.txt'
    # Content of test.txt: Using context managers!
    ```

## Filtering Code Based on Level

### Basic
- **Basic Code**: For learning syntax, basic operations, and simple control flow.
- **Examples**: Variable operations, basic I/O, and simple function definitions.

### Moderate
- **Moderate Code**: For practical use, involving data structures, file operations, and error handling.
- **Examples**: Working with lists and dictionaries, reading/writing files, and handling exceptions.

### Advanced
- **Advanced Code**: For deeper understanding and applying complex concepts like OOP, decorators, and generators.
- **Examples**: Creating classes, using decorators to modify functions, and managing resources with context managers.
