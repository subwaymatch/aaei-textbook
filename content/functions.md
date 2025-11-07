# Functions

Functions are one of the fundamental building blocks in programming. They allow you to encapsulate a piece of code into a reusable unit that can be called multiple times throughout your program.

![An abstract set of lines](images/functions-cover.jpg)

&nbsp;

Let's forget about Python for a moment and go back a few years all the way back to Algebra. Do you remember any expressions that resemble the form of `f(x) = x + 3`?

In this expression, `f` is a function that takes an input `x` and produces an output by adding `3` to it. This is the basic idea behind functions: they take inputs, process them, and produce outputs.

In programming, **functions** serve a similar purpose. They are reusable blocks of code that perform a specific task. Functions help to organize code, make it more readable, and allow for code reuse.

In Python, functions are defined using the `def` keyword, followed by the function name and parentheses.

Here's a simple example of a function that prints a greeting message.

```python
def my_function():
    print("Hello from my function!")
```

To call the function and execute its code, you simply use the function name followed by parentheses.

```python
my_function()
```

Here's the output of the above code:

```
# Output:
Hello from my function!
```

Functions can also take parameters, which are values that you can pass into the function to customize its behavior. Here's an example of a function that takes a parameter and uses it in the greeting message.

```python
def greet(name):
    """This function greets the person passed in as a parameter."""
    print(f"Hello, {name}!")
```

In the example above, we defined a function named `greet` that takes one parameter, `name`. The function prints a greeting message using the provided name.

## ✨ Parameters and Arguments

Functions can take multiple parameters, which are specified within the parentheses in the function definition. When calling the function, you provide arguments that correspond to these parameters.

```python
def add_numbers(a, b):
    return a + b

result = add_numbers(5, 10)
print(result)  # Output: 15
```

In this example, the `add_numbers` function takes two parameters, `a` and `b`, and returns their sum. When we call the function with the arguments `5` and `10`, it returns `15`.

:::{tip} What is the difference between parameters and arguments?

- **Parameters** are the variables listed in the function definition. They act as placeholders for the values that will be passed to the function when it is called.
- **Arguments** are the actual values that are passed to the function when it is called.

They are used interchangeably in casual conversation, but technically, parameters refer to the function's definition, while arguments refer to the function's invocation.
:::

## 🔄 Return Values

Functions can return values using the `return` statement. This allows you to capture the output of a function and use it elsewhere in your code.

```python
def square(x):
    return x * x

result = square(4)
print(result)  # Output: 16
```

In this example, the `square` function takes a number `x` as a parameter and returns its square. When we call the function with the argument `4`, it returns `16`, which we then print.

:::{tip} What happens if a function does not have a return statement?
If a function does not have a `return` statement, it will return `None` by default. This means that if you try to capture the output of such a function, you will get `None`.
:::

:::{hint} What is a `None` value?
`None` is a special constant in Python that represents the absence of a value or a null.

It is often used to indicate that a variable has no value or that a function does not return anything meaningful.

```python
some_variable = None
print(some_variable)  # Output: None

if some_variable is None:
    print("The variable has no value.")

# You can use the logical not operator to check for a None value
if some_variable is not None:
    print("The variable has a value.")
```

:::

If we modify the previous `square()` function to remove the `return` statement:

```{code} python
:label: no-return
:caption: No Return Statement
:linenos:
:emphasize-lines: 2
def square(x):
    print(x * x) # Note: No return statement

result = square(4)
print(result)  # Output: None
```

Here's the output of the above code:

```
16
None
```

The `16` is printed from within the `square` function, but since there is no `return` statement, the function returns `None`, which is then printed as the value of `result`.

:::{tip} Can a function return multiple values?

Yes, a function can return multiple values by separating them with commas in the `return` statement. When you call the function, it will return a tuple containing all the values.

```{code} python
:label: multiple-returns
:caption: Multiple Return Values
:linenos:
:emphasize-lines: 2
def get_coordinates():
    return 10, 20

coordinates = get_coordinates()
print(coordinates)  # Output: (10, 20)
```

:::

## 📝 Examples

Here are a few more examples of functions in Python:

```python
def multiply(a, b):
    return a * b
result = multiply(3, 4)
print(result)  # Output: 12
```

```python
def is_even(number):
    return number % 2 == 0
print(is_even(4))  # Output: True
print(is_even(5))  # Output: False
```

```python
def is_absolute_equal(a, b):
    return abs(a) == abs(b)
print(is_absolute_equal(-5, 5))  # Output: True
print(is_absolute_equal(-5, 4))  # Output: False
```

## 🛠️ Built-in Functions

Python comes with many built-in functions that you can use without needing to define them yourself. Some common built-in functions include:

- `print()`: Outputs text to the console.
- `len()`: Returns the length of a collection (like a list or string).
- `type()`: Returns the type of an object.
- `int()`, `float()`, `str()`: Convert values to integers, floats
- `sum()`: Returns the sum of a collection of numbers.
- `max()`, `min()`: Return the maximum or minimum value from a collection.
- `abs()`: Returns the absolute value of a number.
- `round()`: Rounds a floating-point number to the nearest integer or to a specified number of decimal places.
- `sorted()`: Returns a sorted list from the elements of any iterable.
- `range()`: Generates a sequence of numbers, often used in loops.
- `input()`: Reads a line of input from the user.
- `help()`: Provides help information about a function or module.
- `dir()`: Lists the attributes and methods of an object.
- `enumerate()`: Adds a counter to an iterable and returns it as an enumerate object.

## ⚖️ Functions vs Methods

In Python, the terms "function" and "method" are often used interchangeably, but they have distinct meanings.

- **Function**: A function is a standalone block of code that performs a specific task. It is defined using the `def` keyword and can be called independently. Functions can take parameters and return values.

- **Method**: A method is a function that is associated with an _object_. It is defined within a class and is called on an instance of that class. Methods can access and modify the object's attributes and are typically used to perform operations related to the object.

:::{hint} What is an _object_?
In Python, an object is an instance of a class. Everything in Python is an object, including data types like integers, strings, lists, and even functions and classes themselves.

This may sound confusing at first, but think of an object as a collection of data (attributes) and behaviors (methods) that are bundled together.

For example, consider a `Car` class. An object of this class could represent a specific car, with attributes like `make`, `model`, and `year`, and methods like `start()` and `stop()`. Each car object can have its own unique values for these attributes and can perform the behaviors defined by the methods.
:::

Here's an example to illustrate the difference between functions and methods:

```{code} python
:label: function-example
:caption: Function Example
:linenos:
:emphasize-lines: 2-3
# Function
def greet(name):
    return f"Hello, {name}!"

# Using the function
print(greet("Kingfisher"))  # Output: Hello, Kingfisher!
```

In @function-example, `greet()` is a standalone function that takes a parameter `name` and returns a greeting message.

```{code} python
:label: method-example
:caption: Method Example
:linenos:
:emphasize-lines: 2-7

# Method
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):
        return f"Hello, {self.name}!"

# Using the method
person = Person("Kingfisher")
print(person.greet())  # Output: Hello, Kingfisher!
```

In @method-example, `greet()` is a method defined within the `Person` class. It operates on an instance of the class and uses the instance's `name` attribute to return a greeting message.

## 🌟 Why are Functions Important?

When you start writing more complex programs, you'll find that functions become essential for organizing your code and making it more manageable. Here are some reasons why functions are important:

1. **Code Reusability**: Functions allow you to write a piece of code once and reuse it multiple times throughout your program. This reduces redundancy and makes your code more efficient.
2. **Modularity**: Functions help break down complex problems into smaller, manageable pieces. Each function can focus on a specific task, making it easier to understand and maintain the code.
3. **Readability**: Functions improve the readability of your code by providing meaningful names for specific tasks. This makes it easier for others (and yourself) to understand what the code does.
4. **Maintainability**: If you need to change the behavior of a specific task, you only need to modify the function in one place, rather than changing the same code in multiple locations.
5. **Testing and Debugging**: Functions can be tested independently, making it easier to identify and fix bugs in your code.
6. **Abstraction**: Functions allow you to abstract away complex logic, enabling you to focus on higher-level concepts without getting bogged down in implementation details.
