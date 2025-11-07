# Data Types, Variables, Operators, and Conditionals

In this page, we will explore the fundamental concepts of data types, variables, operators, and conditionals in Python.

---

## 🔢 Python Data Types

In programming, a data type is a classification that specifies which type of value a variable can hold. Let's look at the most common basic data types in Python.

### 🔟 Integers (`int`)

Integers are whole numbers, both positive and negative, without any decimal points.

```python
# An example of an integer
my_integer = 10
print(my_integer)
print(type(my_integer))
```

### 🌊 Floating-Point Numbers (`float`)

Floats are numbers that have a decimal point. They are used for representing real numbers.

```python
# An example of a float
my_float = 3.14159
print(my_float)
print(type(my_float))
```

:::{note} What are Complex Numbers?

Python also supports complex numbers, which are used in advanced mathematical computations.

Complex numbers are numbers that have both a real part and an imaginary part. They are often used in advanced mathematics, physics, and engineering. Python's built-in `complex` type allows you to work with complex numbers easily.

For example, a complex number can be written as `3 + 4j`, where `3` is the real part and `4j` is the imaginary part. The `j` denotes the imaginary unit, which is the square root of -1.

```python
z = 3 + 4j      # complex number
print(z)        # (3+4j)
print(z.real)   # 3.0
print(z.imag)   # 4.0
```

In this course, you will never encounter complex numbers.

:::

### 🔤 Strings (`str`)

Strings are sequences of characters, used for storing text. You can create them by enclosing characters in either single quotes (`'`) or double quotes (`"`).

```python
# An example of a string
my_string = "Hello, Python!"
print(my_string)
print(type(my_string))
```

### ✅ Booleans (`bool`)

Booleans represent one of two values: `True` or `False`. They are crucial for decision-making in programs.

```python
# Examples of booleans
is_learning = True
is_difficult = False
print(is_learning)
print(type(is_difficult))
```

:::{note} ⚡ Everything in Python is an Object
In Python, even "primitive-looking" values like 5, 3.14, or "hello" are actually objects. So unlike in languages like C, Java, or JavaScript, Python doesn't have true primitives in the sense of raw, low-level values. Instead, everything is an instance of some class.
:::

---

## 📦 Variables

A variable is a container for storing a value. You can think of it as a named label for a location in the computer's memory. In Python, you create a variable by assigning a value to it using the equals sign (`=`).

In simple terms, a variable is simply a nickname for a stored value that can _change_.

### ❓ Why do we use variables?

If you have a value that changes often and is used in many different parts of a program, maintaining your code can become difficult—you would need to manually update every instance of that value. Instead, by creating a variable and referencing it, you only need to update the variable once, and every reference will use the updated value.

Variables also improve **readability** when used properly. For example, imagine you want to calculate the after-tax price (at a tax rate of 10%) of an item that costs 2 dollars. In Python, you could write this as `2 * 1.10`. While you might understand what the numbers mean, others may find it confusing. Rewriting it as `before_tax_price * (1 + tax_rate)` makes your code much clearer and easier to read.

```python
# Assigning values to variables
name = "Alice"
age = 30
height_meters = 1.7

print(name)
print(age)
print(height_meters)
```

You can change the value of a variable by reassigning it.

```python
# Reassigning a variable
current_year = 2023
print("The current year is:", current_year)

current_year = 2024
print("The new year is:", current_year)
```

### 🆔 Variable Naming Rules

When naming variables in Python, you should follow these rules:

1. Variable names must start with a letter (a-z, A-Z) or an underscore (`_`).
2. The rest of the name can contain letters, numbers (0-9), or underscores.
3. Variable names are case-sensitive (`myVar`, `MyVar`, and `MYVAR` are different variables).
4. You cannot use Python reserved keywords (like `if`, `else`, `while`, etc.) as variable names.

```python
# Example of valid variable names
first_name = "Alice"
age = 30
is_student = True

# Example of invalid variable names (uncommenting these will cause errors)
# 1st_name = "Alice"
# age@ = 30
# is student = True
```

**Recommendations for Naming Variables:**

- Use descriptive names that convey the purpose of the variable (e.g., `age`, `total_price`, `is_valid`).
- Use lowercase letters and separate words with underscores for better readability (e.g., `first_name`, `total_amount`).

For best practices, follow the [PEP 8 style guide](https://peps.python.org/pep-0008/#naming-conventions) for naming conventions.

:::{note} Why does Python use `snake_case` for variable names?
Python uses `snake_case` (lowercase letters with underscores) for variable names to enhance readability. This convention makes it easier to distinguish between words in a variable name, especially when the name consists of multiple words. For example, `total_price` is more readable than `totalprice` or `TotalPrice`. This style is widely adopted in the Python community and is recommended in the PEP 8 style guide.
:::

:::{warning} Variable Naming Do's and Don'ts
👍 Use descriptive variable names and avoid single-letter names unless in a very limited scope. For example, use `user_age` instead of `my_variable15` to improve code clarity.

👎 Avoid using single-letter variable names (like `x`, `y`, `z`) unless they are used in a very limited scope (like in loops or mathematical formulas). Single-letter names do not convey any meaning about the variable's purpose, making the code harder to read and maintain. Instead, use descriptive names that clearly indicate what the variable represents.
:::

---

## ➕ Operators

Operators are special symbols that perform operations on variables and values.

### 📝 Assignment Operator

The assignment operator (`=`) is used to assign a value to a variable.

```python
x = 5  # Assigns the value 5 to the variable x
y = 10 # Assigns the value 10 to the variable y
```

### ➗ Arithmetic Operators

These are used to perform mathematical operations.

- `+` : Addition
- `-` : Subtraction
- `*` : Multiplication
- `/` : Division
- `**`: Exponent (Power)
- `%` : Modulus (Remainder)

```python
a = 10
b = 3

print("Addition:", a + b)
print("Division:", a / b)
print("Exponent:", a ** b)
print("Remainder:", a % b)
```

### ⚖️ Comparison Operators

These are used to compare two values and result in a boolean (`True` or `False`).

- `==`: Equal to
- `!=`: Not equal to
- `>` : Greater than
- `<` : Less than
- `>=`: Greater than or equal to
- `<=`: Less than or equal to

```python
x = 5
y = 10

print("Is x equal to y?", x == y)
print("Is x less than y?", x < y)
print("Is y not equal to 10?", y != 10)
```

### 🔗 Logical Operators

These are used to combine conditional statements.

- `and`: Returns `True` if both statements are true
- `or` : Returns `True` if one of the statements is true
- `not`: Reverses the result, returns `False` if the result is true

```python
age = 25
has_ticket = True

# The person is old enough AND has a ticket
can_enter = (age >= 18) and (has_ticket == True)
print("Can enter the venue:", can_enter)

# Using 'not' to reverse the boolean
is_raining = False
print("Is it not raining?", not is_raining)
```

---

## 🔀 Conditionals (`if`, `elif`, `else`)

Conditionals allow your program to make decisions and execute different blocks of code based on whether a condition is true or false.

The structure is as follows:

- `if`: The first condition to check.
- `elif`: (short for "else if") Optional. You can have as many of these as you need to check for other conditions.
- `else`: Optional. This block of code runs if none of the preceding `if` or `elif` conditions are met.

```python
temperature = 22

if temperature > 30:
  print("It's a hot day! Stay hydrated.")
elif temperature > 20:
  print("The weather is nice and warm.")
elif temperature > 10:
  print("It's a bit chilly, consider a jacket.")
else:
  print("It's cold outside. Bundle up!")
```

:::{note} The `elif` and `else` blocks are optional

You can use just an `if` statement without `elif` or `else` if you only need to check one condition. Similarly, you can use `if` with `else` if you want to handle two scenarios (one for when the condition is true and another for when it is false).

**🟢 Valid Example 1: Only `if` Statement**

```python
# The optional elif and else blocks are omitted
if city == "Urbana":
    print("Welcome to Urbana!")
```

**🟢 Valid Example 2: Only `if` and `else` Statements**

```python
# The optional elif block is omitted
if chipotle.is_open():
    print("Let's get some burritos!")
else:
    print("Chipotle is closed. Let's try somewhere else.")
```

**🔴 Invalid Example: `elif` without `if`**

```python
elif temperature > 20:
    # This will raise a SyntaxError because elif must follow an if statement
    print("The weather is nice and warm.")
```

:::

---

## 📏 Indentation in Python

**⚠️ Reminder:** Unlike many programming languages that use braces `{}` or keywords to mark code blocks, **Python uses indentation**. This means that the amount of whitespace at the beginning of a line is significant and determines the structure of your code.

### ❗ Why Indentation Matters

- Indentation groups lines of code together into **blocks**.
- A block of code could be part of a function, a loop, a conditional, or a class.
- All lines in the same block must be indented by the **same amount**.

If indentation is inconsistent, Python will raise an `IndentationError`.

### 🧩 Example: Conditional Block

```python
x = 10

if x > 5:
    print("x is greater than 5")
    print("This line is also inside the if-block")

print("This line is outside the if-block")
```

Output:

```
x is greater than 5
This line is also inside the if-block
This line is outside the if-block
```

### 👍 Common Practices

- Use **4 spaces** for indentation (the Python standard).
- Avoid mixing tabs and spaces. Python 3 does not allow it.
- Most code editors (e.g., VS Code, PyCharm, Jupyter) can automatically insert 4 spaces when you press the **Tab** key.

In Python, **indentation is not just style. It's syntax**. Correct indentation is required for your code to run.
