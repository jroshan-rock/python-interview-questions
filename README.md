# 100 Core Python Interview Questions in 2026

<div>
<p align="center">
<a href="https://devinterview.io/questions/web-and-mobile-development/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fweb-and-mobile-development-github-img.jpg?alt=media&token=1b5eeecc-c9fb-49f5-9e03-50cf2e309555" alt="web-and-mobile-development" width="100%">
</a>
</p>

#### You can also find all 100 answers here 👉 [Devinterview.io - Python](https://devinterview.io/questions/web-and-mobile-development/python-interview-questions)

<br>

## 1. What are the _key features_ of _Python_?

**Python** is a versatile and popular programming language known for its simplicity, **elegant syntax**, and a vast ecosystem of libraries. Let's look at some of the key features that make Python stand out.

### Key Features of Python

#### 1. Interpreted and Interactive

Python uses an interpreter, allowing developers to run code **line-by-line**, making it ideal for rapid prototyping and debugging.

#### 2. Easy to Learn and Read

Python's **clean, readable syntax**, often resembling plain English, reduces the cognitive load for beginners and experienced developers alike.

#### 3. Cross-Platform Compatibility

Python is versatile, running on various platforms, such as Windows, Linux, and macOS, without requiring platform-specific modifications.

#### 4. Modular and Scalable

Developers can organize their code into modular packages and reusabale functions.

#### 5. Rich Library Ecosystem

The Python Package Index (PyPI) hosts over 260,000 libraries, providing solutions for tasks ranging from web development to data analytics.

#### 6. Exceptionally Versatile

From web applications to scientific computing, Python is equally proficient in diverse domains.

#### 7. Memory Management

Python seamlessly allocates and manages memory, shielding developers from low-level tasks, such as memory deallocation.

#### 8. Dynamically Typed

Python infers the data type of a variable during execution, easing the declartion and manipulation of variables.

#### 9. Object-Oriented

Python supports object-oriented paradigms, where everything is an **object**, offering attributes and methods to manipulate data.

#### 10. Extensible

With its C-language API, developers can integrate performance-critical tasks and existing C modules with Python.
<br>

## 2. How is _Python_ executed?

**Python** source code is processed through various steps before it can be executed. Let's explore the key stages in this process.

### Compilation & Interpretation

Python code goes through both **compilation** and **interpretation**. 

- **Bytecode Compilation**: High-level Python code is transformed into low-level bytecode by the Python interpreter with the help of a compiler. Bytecode is a set of instructions that Python's virtual machine (PVM) can understand and execute.
  
- **On-the-fly Interpretation**: The PVM reads and executes bytecode instructions in a step-by-step manner.
  
This dual approach known as "compile and then interpret" is what sets Python (and certain other languages) apart. 

### Bytecode versus Machine Code Execution

While some programming languages compile directly to machine code, Python compiles to bytecode. This bytecode is then executed by the Python virtual machine. This extra step of bytecode execution **can make Python slower** in certain use-cases when compared to languages that compile directly to machine code.

The advantage, however, is that bytecode is platform-independent. A Python program can be run on any machine with a compatible PVM, ensuring cross-platform support.

### Source Code to Bytecode: Compilation Steps

1. **Lexical Analysis**: The source code is broken down into tokens, identifying characters and symbols for Python to understand.
2. **Syntax Parsing**: Tokens are structured into a parse tree to establish the code's syntax and grammar.
3. **Semantic Analysis**: Code is analyzed for its meaning and context, ensuring it's logically sound.
4. **Bytecode Generation**: Based on the previous steps, bytecode instructions are created.

### Just-In-Time (JIT) Compilation

While Python typically uses a combination of interpretation and compilation, **JIT** boosts efficiency by selectively compiling parts of the program that are frequently used or could benefit from optimization.

JIT compiles sections of the program to machine code on-the-fly. This direct machine code generation for frequently executed parts can significantly speed up those segments, blurring the line between traditional interpreters and compilers.

### Code Example: Disassembly of Bytecode

```python
import dis

def example_func():
    return 15 * 20

# Disassemble to view bytecode instructions
dis.dis(example_func)
```

Disassembling code using Python's `dis` module can reveal the underlying bytecode instructions that the PVM executes. Here's the disassembled output for the above code:

```plaintext
  4           0 LOAD_CONST               2 (300)
              2 RETURN_VALUE
```
<br>

## 3. What is _PEP 8_ and why is it important?

**PEP 8** is the official **Style Guide for Python Code**, established via a **Python Enhancement Proposal**. It defines the conventions for formatting and structuring Python code to maximize **readability**, **consistency**, and **maintainability**. 

As Guido van Rossum noted, "code is read much more often than it is written." Adhering to PEP 8 ensures that different developers can collaborate seamlessly by reducing the cognitive load required to understand foreign codebases.

### Key Design Principles

*   **Readability**: Prioritizes human comprehension; if a style choice makes code harder to read, readability takes precedence.
*   **Consistency**: Encourages a uniform "look and feel" across the entire Python ecosystem.
*   **The "Pythonic" Way**: Promotes the philosophy that there should be one—and preferably only one—obvious way to do it.

### Formatting and Structure

#### Base Rules
*   **Indentation**: Use exactly **4 spaces** per indentation level. Do not use tabs.
*   **Line Length**: Limit lines to a maximum of **79 characters**. This allows side-by-side code review and prevents wrapping on smaller displays.
*   **Blank Lines**: Use two blank lines to surround top-level function and class definitions. Use a single blank line to separate methods inside a class.

#### Naming Styles
*   **Classes**: Use `CapWords` (PascalCase).
*   **Functions and Variables**: Use `lower_case_with_underscores` (snake_case).
*   **Constants**: Use `UPPER_CASE_WITH_UNDERSCORES`.
*   **Modules**: Use short, all-lowercase names; underscores are discouraged unless necessary for readability.

#### Whitespace Usage
*   **Operators**: Surround assignment ($=$), comparisons ($==, <, >$), and Booleans (`and`, `or`) with a single space.
*   **Delimiters**: Avoid extraneous whitespace immediately inside parentheses, brackets, or braces. Always follow a comma or semicolon with a space.

#### Documentation
*   **Docstrings**: Use triple double quotes (`"""`) for all public modules, functions, classes, and methods.
*   **Comments**: Ensure comments are up-to-date and clearly explain the "why" rather than the "what."

### Example: PEP 8 Compliant Implementation

Below is a modern, compliant script demonstrating proper class structure and naming:

```python
import os

class DirectoryScanner:
    """Provides utilities for scanning file systems."""

    def __init__(self, target_directory):
        self.target_directory = target_directory

    def scan_files(self):
        """Walks the directory and prints full paths."""
        for root, _, files in os.walk(self.target_directory):
            for filename in files:
                file_path = os.path.join(root, filename)
                print(file_path)

if __name__ == "__main__":
    scanner = DirectoryScanner("/path/to/data")
    scanner.scan_files()
```
<br>

## 4. How is memory allocation and garbage collection handled in _Python_?

In Python, **memory allocation** and **garbage collection** are managed automatically by the Python runtime, primarily through the **Python Memory Manager**.

### Memory Allocation

Python manages a private **Heap** containing all Python objects and data structures. The management of this heap is performed internally:

*   **Hierarchical Allocation**: Python uses a specialized allocator called `obmalloc` for small objects (typically $\le 512$ bytes). It organizes memory into **Arenas** ($256$ KB), which are subdivided into **Pools** ($4$ KB), and finally into **Blocks**.
*   **Object-Specific Allocators**: Different types (e.g., `int`, `list`) may have dedicated allocators to improve efficiency and reduce fragmentation.
*   **Raw Memory**: For large objects, Python bypasses its internal pool system and requests memory directly from the operating system's heap using the standard C `malloc()`.
*   **Stack vs. Heap**: While the **Heap** stores the actual objects, the **Stack** stores references to those objects and the call frames for function execution.

### Garbage Collection

Python uses **Reference Counting** as its primary mechanism, supplemented by a **Generational Garbage Collector** to handle complex cases.

#### Reference Counting

Every Python object contains a field in its header called `ob_refcnt`.
*   When a reference to an object is created, the count increases.
*   When a reference is deleted or goes out of scope, the count decreases.
*   If $ref\_count == 0$, the memory is immediately deallocated.

```python
import sys

a = [1, 2, 3]
print(sys.getrefcount(a))  # Output: 2 (variable 'a' and the argument to getrefcount)
b = a
print(sys.getrefcount(a))  # Output: 3
```

#### Generational Garbage Collector

Reference counting alone cannot reclaim **Circular References** (e.g., Object A points to B, and B points to A). To solve this, Python's `gc` module uses a **Cycle-Detecting** algorithm.
*   **Generations**: Objects are stored in three generations: $G_0$, $G_1$, and $G_2$.
*   **Promotion**: New objects start in $G_0$. If they survive a collection cycle, they are moved to $G_1$, and eventually $G_2$.
*   **Thresholds**: Garbage collection is triggered when the number of allocations minus deallocations exceeds a predefined **Threshold**. $G_0$ is scanned most frequently, while $G_2$ is scanned least often, as older objects are statistically more likely to persist.

### Memory Management in Python vs. C

Python's memory architecture differs significantly from manual management languages:

*   **Abstraction**: In C, developers use `malloc()` and `free()`. In Python, the **Memory Manager** abstracts this, preventing **Memory Leaks** and **Dangling Pointers**.
*   **Overhead**: Python objects have higher overhead because every object must store its **Type Pointer** and **Reference Count**. A simple integer in Python occupies significantly more memory than a 4-byte `int` in C.
*   **Performance**: While Python's automatic management increases developer productivity, the overhead of the **Generational GC** and **Reference Counting** can result in "stop-the-world" pauses, whereas C provides deterministic memory performance.
<br>

## 5. What are the _built-in data types_ in _Python_?

Python offers numerous **built-in data types** that provide varying functionalities and utilities for efficient memory management and data manipulation.

### Immutable Data Types

#### 1. int
Represents arbitrary-precision integers, such as `42` or `-10`. In Python 3, there is no "long" type; **int** handles all integer sizes automatically.

#### 2. float
Represents double-precision floating-point numbers, such as `3.14` or `-0.001`.

#### 3. complex
Used for mathematical computations involving a real and an imaginary part, represented as $z = a + bj$, where $j = \sqrt{-1}$.

#### 4. bool
A subclass of integers representing logical values: `True` (1) and `False` (0).

#### 5. str
An immutable sequence of **Unicode characters**. Python strings support extensive slicing and formatting capabilities.

#### 6. tuple
An ordered, immutable collection of items. **Tuples** are often used to store heterogeneous data and can be used as keys in dictionaries.

#### 7. frozenset
An immutable version of a set. It is hashable and contains unique elements, making it suitable as a dictionary key or an element of another set.

#### 8. bytes
An immutable sequence of single bytes (8-bit values). It is primarily used for handling **binary data**, such as images or network packets.

#### 9. range
Represents an immutable sequence of numbers, typically used for iterating in loops. It is memory-efficient as it generates values on demand.

#### 10. NoneType
The type for the singleton object `None`, which is used to signal the absence of a value or a default state.

### Mutable Data Types

#### 1. list
A dynamic, ordered collection of items. **Lists** are highly versatile, supporting indexing, slicing, and various in-place modifications.

#### 2. set
An unordered collection of unique, hashable items. **Sets** provide optimized $O(1)$ average-time complexity for membership testing.

#### 3. dict
A collection of **key-value pairs**. Since Python 3.7+, dictionaries maintain insertion order as a language feature.

#### 4. bytearray
A mutable counterpart to `bytes`. It allows in-place modification of binary sequences without creating new objects.

#### 5. memoryview
A generalized pointer that allows accessing the internal data of an object (that supports the **buffer protocol**) without copying.

#### 6. array (array.array)
A space-efficient storage for basic values (integers, floats) constrained to a single type. It is available via the `array` module.

#### 7. deque (collections.deque)
A double-ended queue designed for fast $O(1)$ appends and pops from both ends, provided by the `collections` module.

#### 8. object
The most fundamental base type in Python. Every class inherits from **object**, and it can be instantiated to create a unique sentinel.

#### 9. types.SimpleNamespace
A simple object that allows for the attribution of arbitrary properties. It is often used as a lightweight alternative to a class.

#### 10. types.FunctionType
The internal type for user-defined functions. Like most objects in Python, functions are first-class citizens and support attribute assignment.

```python
# Illustrating core built-in types
integer_val = 10                        # int
string_val = "Python 2026"              # str
list_val = [1, 2, 3]                    # list (mutable)
tuple_val = (1, 2, 3)                   # tuple (immutable)
dict_val = {"key": "value"}             # dict (mapping)

# Using complex numbers and sets
complex_num = 2 + 3j
unique_elements = {1, 2, 2, 3}          # Result: {1, 2, 3}
```
<br>

## 6. Explain the difference between a _mutable_ and _immutable_ object.

The distinction between **mutable** and **immutable** objects is a fundamental concept in Python that dictates how data is stored, accessed, and modified in memory.

### Key Distinctions

- **Mutable Objects**: These objects allow their internal state or content to be changed in-place after creation without changing their unique identity (`id()`).
- **Immutable Objects**: These objects cannot be altered once created. Any operation that appears to modify an immutable object actually creates a new object with a different identity.

### Common Examples

- **Mutable**: `list`, `set`, `dict`, `bytearray`.
- **Immutable**: `int`, `float`, `str`, `tuple`, `frozenset`, `bytes`, `bool`.

### Code Example: Immutability vs. Mutability

The following code demonstrates how Python handles these two types differently:

```python
# Immutable objects (str, tuple)
text = "Hello"
my_tuple = (1, 2, 3)

try:
    text[0] = 'M'       # Raises TypeError: 'str' object does not support item assignment
    my_tuple[0] = 100   # Raises TypeError
except TypeError as e:
    print(f"Error: {e}")

# Mutable objects (list, dict)
my_list = [1, 2, 3]
original_id = id(my_list)

my_list.append(4)       # Modified in-place
print(id(my_list) == original_id)  # Output: True (Identity remains the same)

# Reassignment (Not Mutation)
x = 10
print(id(x))
x += 1                  # Creates a new int object; x now points to a new id
print(id(x))
```

### Benefits & Trade-Offs

#### Safety and Hashability
**Immutable** objects are inherently **thread-safe** and provide **data integrity** because their state cannot be changed by side effects. Furthermore, only immutable objects (or those containing only immutable elements) are **hashable**, allowing them to be used as **dictionary keys** or elements in a **set**.

#### Performance
**Mutable** objects are generally more efficient for large datasets. Modifying a collection in-place has a time complexity of $O(1)$ for many operations, whereas "modifying" an immutable object requires a full copy of the data, resulting in $O(n)$ complexity.

### Impact on Operations

- **Memory and Performance**: Python optimizes memory for small immutable objects (like short strings or integers) through a process called **interning**. For mutable objects, memory is managed via dynamic resizing.
- **Function Arguments**: Python uses **Pass-by-Assignment**. If a **mutable** object is passed to a function, modifications persist outside the function scope. If an **immutable** object is passed, the original variable remains unchanged because any "modification" inside the function creates a local reference to a new object.
<br>

## 7. How do you _handle exceptions_ in _Python_?

**Exception handling** in Python is a structured mechanism used to manage errors gracefully, ensuring that a program does not crash unexpectedly. It relies on a specific block-based syntax to catch, process, and recover from exceptions.

### Core Components

The standard syntax for handling exceptions involves four primary blocks:

- **`try`**: Contains the code that might raise an exception.
- **`except`**: Executes only if an exception occurs in the `try` block. It is best practice to catch specific exceptions rather than using a bare `except:`.
- **`else`**: Executes only if no exceptions were raised in the `try` block.
- **`finally`**: Executes regardless of whether an exception occurred. This is primarily used for **resource cleanup**, such as closing network sockets or database cursors.

```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("Error: The file was not found.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
else:
    print("Read successful.")
finally:
    if 'file' in locals():
        file.close()
```

### Raising and Chaining Exceptions

The `raise` statement triggers an exception manually. In modern Python, **Exception Chaining** (introduced in Python 3.11 and refined) allows you to preserve the original cause of an error using the `from` keyword.

```python
def process_data(data):
    try:
        return data["id"]
    except KeyError as e:
        # Chaining provides context for debugging
        raise ValueError("Invalid record format") from e
```

### Context Managers (`with` statement)

The `with` keyword simplifies exception handling by automatically managing resources. It uses the **Context Manager** protocol (`__enter__` and `__exit__` methods) to ensure cleanup occurs even if an exception is raised within the block.

```python
with open("example.txt", "w") as f:
    f.write("Hello, World!")
# File is closed automatically here.
```

### Exception Groups and `except*`

As of Python 3.11+, you can handle multiple unrelated exceptions simultaneously using `ExceptionGroup`. This is particularly useful in asynchronous programming or concurrent execution. The `except*` syntax allows you to catch specific types within a group.

```python
try:
    raise ExceptionGroup("Task errors", [ValueError("Fail A"), TypeError("Fail B")])
except* ValueError as eg:
    print(f"Handled ValueErrors: {eg.exceptions}")
except* TypeError as eg:
    print(f"Handled TypeErrors: {eg.exceptions}")
```

### Controlling Flow: `pass` and `continue`

Inside an `except` block, you can control the program's flow:
- **`pass`**: Silently ignores the error.
- **`continue`**: Skips the current iteration of a loop and moves to the next.

```python
for item in dataset:
    try:
        validate(item)
    except ValidationError:
        continue  # Skip invalid items and keep processing
```

### Global Exception Hooks

For unhandled exceptions at the top level, Python provides `sys.excepthook`. This allows developers to define a custom global handler for logging or reporting before the program terminates.

```python
import sys

def custom_hook(type, value, traceback):
    print(f"Critical System Failure: {value}")

sys.excepthook = custom_hook
```

_Note_: `sys.excepthook` does not trigger for `SystemExit` or during interactive sessions.
<br>

## 8. What is the difference between _list_ and _tuple_?

**Lists** and **Tuples** are ordered sequences in Python, but they differ significantly in mutability, performance, and storage behavior.

### Key Distinctions

- **Mutability**: Lists are **mutable**, meaning elements can be added, removed, or modified after creation. Tuples are **immutable**; their state cannot be changed once instantiated.
- **Memory & Performance**: Tuples have a lower memory footprint. Lists allocate extra space to facilitate $O(1)$ amortized appends, whereas tuples are allocated the exact amount of memory required. This makes tuples slightly faster for iteration and creation.
- **Hashability**: Because they are immutable, tuples (containing only hashable elements) are **hashable** and can be used as **dictionary keys** or **set** elements. Lists are unhashable and will raise a `TypeError` if used as keys.

### When to Use Each

- **Lists** are ideal for collections of items that require frequent updates, resizing, or sorting during the program's execution.
- **Tuples** are preferred for fixed data structures, protecting data from accidental modification, and for use as constant keys in mapping types.

### Syntax

#### List: Example

```python
my_list = ["apple", "banana"]
my_list.append("cherry")
my_list[1] = "blackberry"
```

#### Tuple: Example

```python
my_tuple = (1, 2, 3, 4)
# Unpacking a tuple
a, b, c, d = my_tuple
# my_tuple[0] = 5  # This would raise a TypeError
```
<br>

## 9. How do you create a _dictionary_ in _Python_?

In **Python**, a **dictionary** is an **ordered** (since version 3.7) collection of `key:value` pairs that provides $O(1)$ average time complexity for lookups. They are highly optimized and serve as one of the most fundamental data structures in the language.

### Key Concepts

- **Keys**: Must be **unique** and **hashable** (immutable types like `str`, `int`, or `tuple`).
- **Values**: Can be of any data type and can be duplicated.
- **Ordered**: Dictionaries maintain the **insertion order** of items.
- **Mutable**: You can add, remove, or change items after the dictionary is created.

### Creation Methods

There are several idiomatic ways to create a dictionary in Python:

1. **Literal Syntax**: Defining pairs within curly braces `{}`.
2. **`dict()` Constructor**: Using keyword arguments or a list of tuples.
3. **Dictionary Comprehension**: Generating a dictionary dynamically using an iterable.
4. **`zip()` Function**: Mapping two separate iterables (keys and values) together.
5. **`fromkeys()` Method**: Creating a dictionary with a predefined set of keys and a optional default value.

### Examples

#### Literal Definition
The most common and readable way to initialize a dictionary.

```python
# Creating a dictionary using literals
student = {
    "name": "John Doe",
    "age": 21,
    "courses": ["Math", "Physics"]
}
```

#### The `dict()` Constructor
Useful when keys are valid identifiers or when converting other sequences into a dictionary.

```python
# Using keyword arguments
user = dict(username="jdoe", status="active", id=452)

# Using a list of tuples (sequence of key-value pairs)
data = dict([("id", 1), ("type", "admin")])
```

#### Dictionary Comprehension
A concise way to transform one iterable into a dictionary, similar to list comprehensions.

```python
# Squaring numbers using comprehension
squares = {x: x**2 for x in range(1, 6)}
# Result: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

#### Using `zip()`
Ideal for merging two distinct lists/tuples into a dictionary mapping.

```python
keys = ["CPU", "GPU", "RAM"]
values = ["Intel i7", "NVIDIA RTX", "32GB"]

# Pairing keys and values into a dictionary
specs = dict(zip(keys, values))
```

#### Using `fromkeys()`
Used to initialize a dictionary with a specific set of keys and a shared default value.

```python
keys = ["task1", "task2", "task3"]
# Initializes all keys with the value "Pending"
todo_list = dict.fromkeys(keys, "Pending")
```
<br>

## 10. What is the difference between _==_ and _is operator_ in _Python_?

Both the **`==`** and **`is`** operators in Python facilitate different types of comparisons:

- The **`==`** operator evaluates **value equality**. it checks if the data held by two objects is equivalent by invoking the `__eq__` method.
- The **`is`** operator evaluates **object identity**. It verifies if two variables point to the exact same instance in memory.

In Python, every object has a unique identifier. The **`is`** operator compares these memory addresses. If $id(a) = id(b)$, then `a is b` evaluates to `True`.

#### Comparison Logic
- **`is`**: Compares the **identity** (memory address) of two objects.
- **`==`**: Compares the **value** (contents) of two objects.

#### Code Example
```python
# Initialize two lists with identical values
list_a = [1, 2, 3]
list_b = [1, 2, 3]
list_c = list_a

print(list_a == list_b)  # True: The values are the same
print(list_a is list_b)  # False: They are different objects in memory
print(list_a is list_c)  # True: Both point to the same memory address
```

#### Best Practices for Usage
- **`==`**: Use for standard equality comparisons, such as comparing strings, numbers, or data structures.
- **`is`**: Use exclusively when comparing against **singletons**, most commonly for **`None`** checks (e.g., `if val is None:`), to ensure identity-level precision.
<br>

## 11. How does a _Python function_ work?

**Python functions** are first-class objects that encapsulate logic, enable reusability, and manage state through scoping. In Python, a function is an instance of the `function` class, allowing it to be passed as an argument, returned from other functions, and assigned to variables.

### Key Components

- **Function Signature**: Defined by the `def` keyword, it includes the name, parameters (positional, keyword, or variadic), and optional **type hints**.
- **Function Body**: An indented block of code containing the logic. Python compiles this into **bytecode** upon definition.
- **Return Statement**: Explicitly exits a function with a value. If omitted, the function implicitly returns the `None` singleton.
- **Function Object**: When defined, Python creates a name binding in the current namespace that points to the function object stored in memory.

### Execution Process

When a function is invoked, the Python interpreter performs the following steps:

1. **Frame Creation**: A **Frame Object** is pushed onto the **Call Stack**. This frame encapsulates the execution environment, including the local symbol table and the evaluation stack.
2. **Parameter Binding**: Arguments are assigned to parameters using **pass-by-object-reference**. If a mutable object (e.g., a `list`) is passed, modifications inside the function affect the original object.
3. **Bytecode Execution**: The Python Virtual Machine (PVM) executes the function's bytecode sequentially. The **instruction pointer** tracks the current operation.
4. **Return and Cleanup**: Upon a `return` or reaching the end of the block, the return value is passed back to the calling context, and the frame is popped from the stack, making local variables eligible for **garbage collection**.

### Scope and Variable Resolution

Python uses the **LEGB Rule** to resolve names during execution:

#### The LEGB Rule
- **Local (L)**: Names assigned within the function (and not declared global).
- **Enclosing (E)**: Names in the local scope of any enclosing functions (relevant for closures).
- **Global (G)**: Names assigned at the top level of the module or declared via the `global` keyword.
- **Built-in (B)**: Names pre-assigned in the Python `builtins` module (e.g., `len`, `range`).

```python
def outer_function(x: int):
    # Enclosing scope
    y = 10 
    
    def inner_function(z: int) -> float:
        # Local scope accessing Enclosing and Global
        return (x + y + z) * 1.0 
    
    return inner_function

# Usage
closure = outer_function(5)
result = closure(3) # Result: 18.0
```

### Advanced Function Mechanics

- **Closures**: Functions that "remember" values from their enclosing lexical scope even after the outer function has finished executing.
- **Decorators**: Higher-order functions that take a function as an argument and return a new function, typically to extend behavior without modifying the source code.
- **Stack Limits**: Python imposes a maximum recursion depth (default is often 1000) to prevent infinite recursion from exhausting the C stack.

### Avoiding Side Effects

Functions should ideally be **pure**—returning values based solely on inputs without modifying global state. Using the `nonlocal` or `global` keywords allows modification of outer scopes but increases complexity and reduces the predictability of the code. Encapsulating logic within functions ensures that data $x$ processed by $f(x)$ remains isolated, enhancing maintainability.
<br>

## 12. What is a _lambda function_, and where would you use it?

A **lambda function**, or **lambda** for short, is a small, **anonymous function** defined using the `lambda` keyword in Python. Unlike standard functions defined with `def`, lambdas are used for short-lived operations where a formal name is unnecessary.

### Distinctive Features

#### Anonymity
Lambdas are not bound to a name in the traditional sense, making them ideal for **one-off** utility tasks within a localized scope.

#### Single Expression Body
The body is strictly limited to a **single expression**. This facilitates brevity but prevents the use of multiple statements or complex logic within the function body.

#### Implicit Return
There is no explicit `return` statement; the evaluated result of the expression is returned automatically. The syntax follows: $\text{lambda arguments: expression}$.

#### Conciseness
Lambdas streamline code by allowing function definitions in-place, reducing the overhead of defining a full function for simple transformations.

### Common Use Cases

#### Map, Filter, and Reduce
Functions like `map()` and `filter()` often take a lambda as an argument to define transformations or predicates on the fly. For instance, squaring elements in a list:
```python
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, numbers)) # [1, 4, 9, 16]
```
Note: For `reduce()`, you must import it from the `functools` module.

#### Sorting and Min/Max
Lambdas serve as a **custom key** for sorting complex data structures. This is highly effective for ordering objects or dictionaries by specific attributes:
```python
data = [{'name': 'Alice', 'age': 30}, {'name': 'Bob', 'age': 25}]
# Sort by age
sorted_data = sorted(data, key=lambda x: x['age'])
```

#### Callbacks
Lambdas are frequently used in GUI frameworks or asynchronous programming as **callbacks**, where a function must be passed as an argument to be executed when an event occurs.

#### Higher-Order Functions
They are useful as return values from other functions to create specialized behaviors (closures) without naming every intermediate function.

### Notable Limitations

#### Readability
Named functions are generally preferred when the logic is not immediately obvious. Overusing lambdas or using them for complex logic can make the codebase difficult to maintain.

#### Documentation and Debugging
Lambdas cannot contain **docstrings**, making them harder to document. Additionally, because they are anonymous, tracebacks will identify them only as `<lambda>`, which can complicate the debugging process compared to named functions.
<br>

## 13. Explain _*args_ and _**kwargs_ in _Python_.

In **Python**, `*args` and `**kwargs` are special syntaxes used in function definitions to allow a **variable number of arguments** to be passed. 

`*args` collects extra positional arguments into a **tuple**, while `**kwargs` collects extra keyword arguments into a **dictionary**.

### **\*args**: Variable Number of Positional Arguments

- **How it Works**: The asterisk `*` is the unpacking operator. When used in a function parameter list, it packs all remaining positional arguments into a **tuple**. While the name `args` is a standard convention, only the `*` is syntactically required.
- **Use-Case**: Use `*args` when the exact number of input values is unknown or when creating functions that act as wrappers for other tools.

#### Code Example: "*args"

```python
def sum_all(*args):
    result = 0
    # args is treated as a tuple
    for num in args:
        result += num
    return result

print(sum_all(1, 2, 3, 4))  # Output: 10
```

### **\*\*kwargs**: Variable Number of Keyword Arguments

- **How it Works**: The double asterisk `**` is used to capture any named (keyword) arguments that were not explicitly defined in the parameter list. These are stored in a **dictionary** where the keys are the argument names and the values are the argument values.
- **Use-Case**: This is commonly used in **class inheritance** or **decorators** to pass configuration parameters to internal functions without explicitly naming every possible argument.

#### Code Example: "**kwargs"

```python
def print_values(**kwargs):
    # kwargs is treated as a dictionary
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_values(name="John", age=30, city="New York")
# Output:
# name: John
# age: 30
# city: New York
```

### Argument Order and Syntax Rules

When combining different types of parameters, Python requires a specific order in the function signature to avoid ambiguity:
1. Standard positional arguments.
2. `*args` (Variable positional).
3. Keyword-only arguments.
4. `**kwargs` (Variable keyword).

For example, a function signature might look like:
`def complex_function(a, b, *args, name="Default", **kwargs):`

This structure ensures that Python can correctly assign values to the corresponding variables during the function call.
<br>

## 14. What are _decorators_ in _Python_?

In Python, a **decorator** is a design pattern and a language feature that allows you to dynamically modify or extend the behavior of functions or classes without permanently changing their source code. They are a form of **metaprogramming** where one function modifies another.

### How Decorators Work

- **Higher-Order Functions**: Decorators are functions that take another function as an argument and return a new function.
- **Closures**: They rely on Python’s support for closures to "wrap" the original function, allowing code execution both before and after the target function runs.
- **First-Class Objects**: Since functions in Python are first-class objects, they can be passed as arguments, assigned to variables, and returned from other functions.

### Common Use Cases

- **Authorization**: Checking user permissions before executing a route or method.
- **Logging and Profiling**: Measuring execution time ($\Delta t$) or recording function calls.
- **Caching/Memoization**: Storing results of expensive computations (e.g., `@functools.cache`).
- **Validation**: Enforcing type checks or data constraints on input arguments.
- **Rate Limiting**: Controlling how often a function can be called within a specific timeframe.

### Implementing Decorators

#### Basic Decorator
Using `functools.wraps` is essential in modern Python to preserve the original function's **metadata** (like `__name__` and `__doc__`).

```python
from functools import wraps
from typing import Callable, Any

def my_decorator(func: Callable) -> Callable:
    @wraps(func)
    def wrapper(*args: Any, **kwargs: Any) -> Any:
        print("Logic executed before the function.")
        result = func(*args, **kwargs)
        print("Logic executed after the function.")
        return result
    return wrapper

@my_decorator
def say_hello(name: str) -> None:
    """Greets the user."""
    print(f"Hello, {name}!")

say_hello("Alice")
```

#### Decorators with Arguments
To pass arguments to the decorator itself, you must implement an additional nesting level (a **decorator factory**).

```python
def repeat(times: int) -> Callable:
    def decorator(func: Callable) -> Callable:
        @wraps(func)
        def wrapper(*args: Any, **kwargs: Any) -> Any:
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(times=3)
def greet() -> None:
    print("Execution...")
```

### The @ Syntax and Metadata Preservation

The `@decorator` syntax is **syntactic sugar**. The following two approaches are equivalent:

```python
# Modern Syntax
@my_decorator
def func(): ...

# Manual Equivalent
func = my_decorator(func)
```

Without the use of `@wraps(func)`, the decorated function would lose its identity, appearing to introspection tools as the internal `wrapper` function rather than the original `func`. This preservation is critical for debugging, documentation generators, and IDE autocompletion in professional 2026 development environments.
<br>

## 15. How can you create a _module_ in _Python_?

You can **create** a Python module through the following standard methods:

- **Define**: Save a Python file with a `.py` extension. This file acts as a **module**, where the filename (without the extension) serves as the module name.
- **Package Initialization**: To organize multiple modules into a **package**, place an `__init__.py` file inside the directory. This file can be empty or execute initialization code for the package.

Next, use the **import** statement to access the module and its functionality within your project.

### Code Example: Creating a `math_operations` Module

#### Module Definition

Save the below code as a file named `math_operations.py`:

```python
# math_operations.py

def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    """Returns the result of $\frac{x}{y}$"""
    if y == 0:
        raise ValueError("Cannot divide by zero.")
    return x / y
```

#### Module Usage

You can utilize the `math_operations` module by using **import** as shown below:

```python
import math_operations

# Access functions using the module prefix
result = math_operations.add(4, 5)
print(result)  # Output: 9

result = math_operations.divide(10, 5)
print(result)  # Output: 2.0
```

Alternatively, use the `from` syntax to import specific members directly into the **local namespace**:

```python
from math_operations import add, subtract

result = add(3, 2)
print(result) # Output: 5
```

### Best Practice
To ensure the module is professional and reusable, follow these **Best Practices**:

- **Namespace Safety**: Avoid using `from module import *` as it can lead to **name collisions** and reduces code readability.
- **Execution Guard**: Use the `__name__` global variable to prevent code from executing automatically when the module is imported.

```python
def main():
    # Logic for manual testing
    print("Testing add function:", add(10, 20))

if __name__ == "__main__":
    main()
```

This ensures that the block following `if __name__ == "__main__":` only runs when the script is executed directly, keeping the module "clean" for external imports.
<br>



#### Explore all 100 answers here 👉 [Devinterview.io - Python](https://devinterview.io/questions/web-and-mobile-development/python-interview-questions)

<br>

<a href="https://devinterview.io/questions/web-and-mobile-development/">
<img src="https://firebasestorage.googleapis.com/v0/b/dev-stack-app.appspot.com/o/github-blog-img%2Fweb-and-mobile-development-github-img.jpg?alt=media&token=1b5eeecc-c9fb-49f5-9e03-50cf2e309555" alt="web-and-mobile-development" width="100%">
</a>
</p>

