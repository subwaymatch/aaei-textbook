# Data Types, Variables, Operators, and Conditionals

In this page, we will explore the fundamental concepts of data types, variables, operators, and conditionals in Python.

---

## 🔢 Python Data Types

In programming, a data type is a classification that specifies which type of value a variable can hold. Let's look at the most common basic data types in Python.

### 🔟 Integers (`int`)

Integers are whole numbers, both positive and negative, without any decimal points.

```python
# An example of an integer (e.g., inventory on hand)
inventory_count = 150
print(inventory_count)
print(type(inventory_count))
```

### 🌊 Floating-Point Numbers (`float`)

Floats are numbers that have a decimal point. They are used for representing real numbers.

```python
# An example of a float (e.g., an asset's cost or a tax rate)
asset_cost = 45000.75
sales_tax_rate = 0.0825
print(asset_cost)
print(type(sales_tax_rate))
```

### 🔤 Strings (`str`)

Strings are sequences of characters, used for storing text. You can create them by enclosing characters in either single quotes (`'`) or double quotes (`"`).

```python
# An example of a string (e.g., an account name)
account_name = "Accounts Receivable"
print(account_name)
print(type(account_name))
```

### ✅ Booleans (`bool`)

Booleans represent one of two values: `True` or `False`. They are crucial for decision-making in programs.

```python
# Examples of booleans
is_current_asset = True
audit_passed = False
print(is_current_asset)
print(type(audit_passed))
```

---

## 📦 Variables

A variable is a container for storing a value. You can think of it as a named label for a location in the computer's memory. In Python, you create a variable by assigning a value to it using the equals sign (`=`).

In simple terms, a variable is simply a nickname for a stored value that can _change_.

### ❓ Why do we use variables?

If you have a value that changes often and is used in many different parts of a program, maintaining your code can become difficult---you would need to manually update every instance of that value. Instead, by creating a variable and referencing it, you only need to update the variable once, and every reference will use the updated value.

Variables also improve **readability** when used properly. For example, imagine you want to calculate the total amount due on an invoice of $1,000 with a 7% sales tax. In Python, you could write this as `1000 * 1.07`. While you might understand what the numbers mean, others may find it confusing. Rewriting it as `invoice_amount * (1 + sales_tax_rate)` makes your code much clearer and easier to read.

```python
# Assigning values to variables
asset_name = "Delivery Van"
original_cost = 45000
useful_life_years = 5

print(asset_name)
print(original_cost)
print(useful_life_years)
```

You can change the value of a variable by reassigning it.

```python
# Reassigning a variable
current_fiscal_year = 2024
print("The current fiscal year is:", current_fiscal_year)

current_fiscal_year = 2025
print("The new fiscal year is:", current_fiscal_year)
```

### 🆔 Variable Naming Rules

When naming variables in Python, you should follow these rules:

1. Variable names must start with a letter (a-z, A-Z) or an underscore (`_`).
2. The rest of the name can contain letters, numbers (0-9), or underscores.
3. Variable names are case-sensitive (`myVar`, `MyVar`, and `MYVAR` are different variables).
4. You cannot use Python reserved keywords (like `if`, `else`, `while`, etc.) as variable names.

```python
# Example of valid variable names
customer_name = "Alpha Inc."
cogs = 75000
is_taxable = True

# Example of invalid variable names (running these will throw errors)
1st_quarter_sales = 1000      # Invalid: starts with a number
customer@name = "Alpha Inc."  # Invalid: contains special character
is_ taxable = True            # Invalid: contains space
```

**Recommendations for Naming Variables:**

- Use descriptive names that convey the purpose of the variable (e.g., `net_income`, `total_assets`, `is_material`).

- Use lowercase letters and separate words with underscores for better readability (e.g., `accounts_receivable`, `retained_earnings`).

For best practices, follow the [PEP 8 style guide](https://peps.python.org/pep-0008/#naming-conventions) for naming conventions.

:::{note} Why does Python use `snake_case` for variable names?

Python uses `snake_case` (lowercase letters with underscores) for variable names to enhance readability. This convention makes it easier to distinguish between words in a variable name, especially when the name consists of multiple words. For example, `retained_earnings` is more readable than `retainedearnings` or `RetainedEarnings`. This style is widely adopted in the Python community and is recommended in the PEP 8 style guide.

:::

:::{warning} Variable Naming Do's and Don'ts

👍 Use descriptive variable names and avoid single-letter names unless in a very limited scope. For example, use `accounts_payable_balance` instead of `ap_bal` or `x15` to improve code clarity.

👎 Avoid using single-letter variable names (like `x`, `y`, `z`) unless they are used in a very limited scope (like in loops or mathematical formulas). Single-letter names do not convey any meaning about the variable's purpose, making the code harder to read and maintain. Instead, use descriptive names that clearly indicate what the variable represents.

:::

---

## ➕ Operators

Operators are special symbols that perform operations on variables and values.

### 📝 Assignment Operator

The assignment operator (`=`) is used to assign a value to a variable.

```python
revenue = 50000  # Assigns the value 50000 to the variable revenue
expenses = 35000 # Assigns the value 35000 to the variable expenses
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
revenue = 100000
expenses = 75000
principal = 1000
rate = 0.05
years = 3

print("Net Income:", revenue - expenses)
print("Gross Margin (as decimal):", (revenue - expenses) / revenue)
print("Compound Interest (Future Value):", principal * (1 + rate) ** years)
print("Remainder (less common in finance):", 10 % 3)
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
current_assets = 50000
current_liabilities = 30000

print("Is Current Ratio > 1.5?", (current_assets / current_liabilities) > 1.5)
print("Are assets equal to liabilities?", current_assets == current_liabilities)
print("Is the company liquid (CA > CL)?", current_assets > current_liabilities)
```

### 🔗 Logical Operators

These are used to combine conditional statements.

- `and`: Returns `True` if both statements are true
- `or` : Returns `True` if one of the statements is true
- `not`: Reverses the result, returns `False` if the result is true

```python
revenue_criteria_met = True
collection_probable = True

# For revenue recognition (simplified)
can_recognize_revenue = revenue_criteria_met and collection_probable
print("Can recognize revenue:", can_recognize_revenue)
# Output: Can recognize revenue: True

# Using 'not' to reverse the boolean
print(not revenue_criteria_met)
# Output: False
```

---

## 🔀 Conditionals (`if`, `elif`, `else`)

Conditionals allow your program to make decisions and execute different blocks of code based on whether a condition is true or false.

The structure is as follows:

- `if`: The first condition to check.
- `elif`: (short for "else if") Optional. You can have as many of these as you need to check for other conditions.
- `else`: Optional. This block of code runs if none of the preceding `if` or `elif` conditions are met.

```python
# Example: Assessing an audit misstatement
misstatement_amount = 45000
trivial_threshold = 5000
materiality_threshold = 60000

if misstatement_amount > materiality_threshold:
  print("Misstatement is material. Requires adjustment or modified opinion.")
elif misstatement_amount > trivial_threshold:
  print("Misstatement is not trivial. Aggregate with other misstatements.")
else:
  print("Misstatement is trivial. No action needed.")
```

:::{note} The `elif` and `else` blocks are optional

You can use just an `if` statement without `elif` or `else` if you only need to check one condition. Similarly, you can use `if` with `else` if you want to handle two scenarios (one for when the condition is true and another for when it is false).

**🟢 Valid Example 1: Only `if` Statement**

```python
# The optional elif and else blocks are omitted
if account_balance < 0:
    print("Warning: Account is overdrawn.")
```

**🟢 Valid Example 2: Only `if` and `else` Statements**

```python
# The optional elif block is omitted
if net_income > 0:
    print("The company reported a profit.")
else:
    print("The company reported a loss.")
```

**🔴 Invalid Example: `elif` without `if`**

```python
elif account_balance > 1000000:
    # This will raise a SyntaxError because elif must follow an if statement
    print("Account requires special monitoring.")
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
net_income = 150000

if net_income > 0:
    print("The company is profitable.")
    print("This is a positive sign for investors.")

print("This line is outside the if-block and will always print.")
```

Output:

```
The company is profitable.
This is a positive sign for investors.
This line is outside the if-block and will always print.
```

### 👍 Common Practices

- Use **4 spaces** for indentation (the Python standard).
- Avoid mixing tabs and spaces. Python 3 does not allow it.
- Most code editors (e.g., VS Code, PyCharm, Jupyter) can automatically insert 4 spaces when you press the **Tab** key.

In Python, **indentation is not just style. It's syntax**. Correct indentation is required for your code to run.
