# Strings

A string is a sequence of characters enclosed in either single quotes (`'`) or double quotes (`"`). Strings are used to represent text data in Python.

## ✨ Creating Strings

You can create a string by enclosing characters in quotes. Both single and double quotes can be used interchangeably.

```python
account_name = "Accounts Payable"
audit_opinion = 'Unqualified Opinion'
```

:::{seealso} Triple Quotes for Multi-line Strings

Python also supports triple quotes (`'''` or `"""`) for creating multi-line strings. This is useful for strings that span multiple lines or for including both single and double quotes within the string without needing to escape them.

```python
multi_line_string = """Journal Entry Memo:
To record the purchase of office supplies
on account from Supplies Inc."""
```

:::

---

## 🔧 String Operations

### ➕ Concatenation

You can concatenate (combine) strings using the `+` operator.

```python
greeting = "Hello, " + "future CPAs!"
print(greeting)  # Output: Hello, future CPAs!
```

### ✖️ Repetition

You can repeat a string multiple times using the `*` operator.

```python
laugh = "Ha" * 3
print(laugh)  # Output: HaHaHa
```

### 📏 String Length

You can find the length of a string using the `len()` function.

```python
my_string = "ACCY"
print(len(my_string))  # Output: 4
```

---

## 🛠️ String Methods

Strings come with a variety of built-in methods that allow you to manipulate and work with them. Here are some commonly used string methods:

- Changing case: `.lower()`, `.upper()`, `.title()`, `.capitalize()`, `.swapcase()`
- Whitespace removal: `.strip()`, `.lstrip()`, `.rstrip()`
- Searching: `.find()`, `.index()`, `.count()`
- Replacing: `.replace()`
- Splitting and joining: `.split()`, `.join()`
- Checking properties: `.startswith()`, `.endswith()`, `.isalnum()`, `.isalpha()`, `.isdigit()`

We'll explore a few of these methods with examples.

### 🔡 `lower()` and 🔠 `upper()`

These methods convert a string to lowercase or uppercase, respectively.

```python
text = "Audit Evidence"
print(text.lower())  # Output: audit evidence
print(text.upper())  # Output: AUDIT EVIDENCE
```

### 🧹 `strip()`

This method removes any leading and trailing whitespace from a string.

```python
account_from_excel = "   Cash   "
print(account_from_excel.strip())  # Output: "Cash"
```

### ♻️ `replace()`

```python
text = "Accounts Receivable"
print(text.replace("Receivable", "Payable"))  # Output: "Accounts Payable"
```

This method replaces occurrences of a specified substring with another substring.

### ✂️ `split()`

This method splits a string into a list of substrings based on a specified delimiter (default is whitespace).

```python
text = "I love data analytics"
words = text.split()
print(words)  # Output: ['I', 'love', 'data', 'analytics']
```

### 🔗 `join()`

This method joins a list of strings into a single string, with a specified separator.

```python
accounts_list = ['Cash', 'Inventory', 'Equipment']
# Join the list into a single string, separated by a pipe '|'
joined_string = '|'.join(accounts_list)
print(joined_string)  # Output: "Cash|Inventory|Equipment"
```

### 🔍 `find()`

This method returns the lowest index of the substring if found in the string. If not found, it returns -1.

```python
text = "Cost of Goods Sold"
index = text.find("Goods")
print(index)  # Output: 10
```

---

## 📚 Strings as Ordered Collections

Although it is not a collection type like lists or dictionaries, strings can be treated as collections of characters, allowing you to iterate over them using loops.

```python
acronym = "FIFO" # First In, First Out

for char in acronym:
    print(char)
```

Here's the output of the above code:

```
# Output:
F
I
F
O
```

You can access individual characters in a string using indexing, similar to lists.

```python
first_char = acronym[0]   	# 'F'
last_char = acronym[-1] 	# 'O'
```

### ✂️ Slicing a String

You can extract a substring from a string using slicing.

```python
my_string = "ILLINI"
substring = my_string[1:4]
print(substring)  # Output: LLI
```

Remember that the start index is inclusive, while the end index is exclusive.
