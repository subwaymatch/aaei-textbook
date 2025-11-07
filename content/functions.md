# Functions

Functions are one of the fundamental building blocks in programming. They allow you to encapsulate a piece of code into a reusable unit that can be called multiple times throughout your program.

![An abstract set of lines](images/functions-cover.jpg)

&nbsp;

Let's forget about Python for a moment and go back a few years all the way back to Algebra. Do you remember any expressions that resemble the form of `f(x) = x + 3`?

In this expression, `f` is a function that takes an input `x` and produces an output by adding `3` to it. This is the basic idea behind functions: they take inputs, process them, and produce outputs.

In programming, **functions** serve a similar purpose. They are reusable blocks of code that perform a specific task. Functions help to organize code, make it more readable, and allow for code reuse.

In Python, functions are defined using the `def` keyword, followed by the function name and parentheses.

Here's a simple example of a function that prints a report header.

```python
def print_report_header():
    print("--- Income Statement ---")
    print("For the Year Ended December 31, 2025")
```

To call the function and execute its code, you simply use the function name followed by parentheses.

```python
print_report_header()
```

Here's the output of the above code:

```
# Output:
--- Income Statement ---
For the Year Ended December 31, 2025
```

Functions can also take parameters, which are values that you can pass into the function to customize its behavior. Here's an example of a function that takes a parameter and uses it to calculate sales tax.

```python
def calculate_sales_tax(sales_amount):
    """This function calculates sales tax at a fixed 8% rate."""
    tax = sales_amount * 0.08
    print(f"Sales: ${sales_amount}, Tax: ${tax}")
```

In the example above, we defined a function named `calculate_sales_tax` that takes one parameter, `sales_amount`. The function calculates and prints the tax.

## ✨ Parameters and Arguments

Functions can take multiple parameters, which are specified within the parentheses in the function definition. When calling the function, you provide arguments that correspond to these parameters.

```python
def calculate_net_income(revenue, expenses):
    return revenue - expenses

# Call the function with arguments
net_income = calculate_net_income(150000, 85000)
print(f"Net Income: ${net_income}")  # Output: Net Income: $65000
```

In this example, the `calculate_net_income` function takes two parameters, `revenue` and `expenses`, and returns their difference.

:::{tip} What is the difference between parameters and arguments?

- **Parameters** are the variables listed in the function definition (e.g., `revenue` and `expenses`). They act as placeholders for the values that will be passed to the function when it is called.
- **Arguments** are the actual values that are passed to the function when it is called (e.g., `150000` and `85000`).

They are used interchangeably in casual conversation, but technically, parameters refer to the function's definition, while arguments refer to the function's invocation.

:::

## 🔄 Return Values

Functions can return values using the `return` statement. This allows you to capture the output of a function and use it elsewhere in your code.

```python
def calculate_depreciation(cost, salvage_value, useful_life):
    """Calculates annual straight-line depreciation."""
    return (cost - salvage_value) / useful_life

annual_depreciation = calculate_depreciation(50000, 10000, 5)
print(f"Annual Depreciation: ${annual_depreciation}")  # Output: Annual Depreciation: $8000.0
```

In this example, the `calculate_depreciation` function takes three parameters and returns the calculated annual depreciation. We capture this returned value in the `annual_depreciation` variable.

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

If we modify a function to `print` instead of `return`:

```{code} python
:label: no-return
:caption: No Return Statement
:linenos:
:emphasize-lines: 3
def print_depreciation(cost, salvage_value, useful_life):
    """Calculates and prints annual straight-line depreciation."""
    print((cost - salvage_value) / useful_life) # Note: No return statement

result = print_depreciation(50000, 10000, 5)
print(result)
```

Here's the output of the above code:

```
8000.0
None
```

The `8000.0` is printed from _within_ the `print_depreciation` function, but since there is no `return` statement, the function returns `None`. The final `print(result)` line prints this `None` value.

:::{tip} Can a function return multiple values?

Yes, a function can return multiple values by separating them with commas in the `return` statement. When you call the function, it will return a tuple containing all the values.

```{code} python
:label: multiple-returns
:caption: Multiple Return Values
:linenos:
:emphasize-lines: 4-4
def get_trial_balance_totals():
    total_debits = 150000
    total_credits = 150000
    return total_debits, total_credits

# You can "unpack" the returned tuple into multiple variables
debits, credits = get_trial_balance_totals()

print(f"Debits: {debits}, Credits: {credits}")  # Output: Debits: 150000, Credits: 150000
```

:::

## 📝 Examples

Here are a few more examples of functions in Python:

```python
def calculate_current_ratio(current_assets, current_liabilities):
    return current_assets / current_liabilities

ratio = calculate_current_ratio(100000, 50000)
print(f"Current Ratio: {ratio}")  # Output: Current Ratio: 2.0
```

```python
def is_material(misstatement, materiality_threshold):
    """Checks if a misstatement is material."""
    return misstatement > materiality_threshold

print(is_material(5000, 10000))  # Output: False
print(is_material(12000, 10000)) # Output: True
```

```python
def do_debits_equal_credits(total_debits, total_credits):
    """Checks if a trial balance is in balance."""
    return total_debits == total_credits

print(do_debits_equal_credits(150000, 150000))  # Output: True
print(do_debits_equal_credits(150000, 149000))  # Output: False
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

For example, consider a `FixedAsset` class. An object of this class could represent a specific asset, with attributes like `cost`, `salvage_value`, and `useful_life`, and methods like `calculate_depreciation()` and `get_book_value()`. :::

:::

Here's an example to illustrate the difference between functions and methods:

```{code} python
:label: function-example
:caption: Function Example
:linenos:
:emphasize-lines: 2-3
# Function
def format_currency(amount):
    return f"${amount:,.2f}" # Formats a number as U.S. currency

# Using the function
print(format_currency(150000))  # Output: $150,000.00
```

In @function-example, `format_currency()` is a standalone function that takes an amount and returns a formatted string.

```{code} python
:label: method-example
:caption: Method Example
:linenos:
:emphasize-lines: 2-12

# Method
class FixedAsset:
    def __init__(self, name, cost, useful_life):
        self.name = name
        self.cost = cost
        self.useful_life = useful_life
        self.age = 0 # Initial age is 0

    def calculate_book_value(self):
        # (Simplified straight-line, no salvage)
        depreciation = (self.cost / self.useful_life) * self.age
        return self.cost - depreciation

# Using the method
asset = FixedAsset("Delivery Van", 50000, 5)
asset.age = 2 # The asset is now 2 years old
print(asset.calculate_book_value())  # Output: 30000.0
```

In @method-example, `calculate_book_value()` is a method defined within the `FixedAsset` class. It operates on an instance of the class (an object) and uses the object's `cost`, `useful_life`, and `age` attributes to return its current book value.

## 🌟 Why are Functions Important?

When you start writing more complex programs, you'll find that functions become essential for organizing your code and making it more manageable. Here are some reasons why functions are important:

1.  **Code Reusability**: Functions allow you to write a piece of code once and reuse it multiple times. (e.g., you can call `calculate_depreciation()` for thousands of different assets).
2.  **Modularity**: Functions help break down complex problems into smaller, manageable pieces. Each function can focus on a specific task (e.g., one function calculates depreciation, another checks for materiality).
3.  **Readability**: Functions improve the readability of your code by providing meaningful names for specific tasks. This makes it easier for others (and yourself) to understand what the code does.
4.  **Maintainability**: If you need to change the behavior of a specific task (e.g., change from straight-line to double-declining depreciation), you only need to modify the function in one place.
5.  **Testing and Debugging**: Functions can be tested independently, making it easier to identify and fix bugs in your code.
6.  **Abstraction**: Functions allow you to abstract away complex logic, enabling you to focus on higher-level concepts (e.g., you can just _use_ `calculate_book_value()` without needing to remember the exact formula inside it).
